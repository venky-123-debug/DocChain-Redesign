<script>
  import Logo from "../components/Logo.svelte"
  import Logout from "../components/Logout.svelte"
  import Nav from "../components/Nav.svelte"
  import SmallScreenNavbar from "../components/Small_screen_navbar.svelte"
  import Header from "../components/Header.svelte"
  import Fileupload from "../components/Fileupload.svelte"
  export let id
  let hideNavbar = true
  const hideNav = () => {
    hideNavbar = true
  }
  console.log(id)
  const showNav = () => {
    if (hideNavbar == false) {
      hideNavbar = true
    } else {
      hideNavbar = false
    }
  }

  let Black = true,
    Yellow = false,
    Red = false,
    Gray = false
  const changeClr = (e) => {
    ;(Black = false), (Yellow = false), (Red = false), (Gray = false)
    if (e.detail == "Black") {
      Black = true
    }
    if (e.detail == "Yellow") {
      Yellow = true
    }
    if (e.detail == "Red") {
      Red = true
    }
    if (e.detail == "Gray") {
      Gray = true
    }
  }
</script>

<svelte:head>
  <title>Add Data</title>
</svelte:head>

<div
  class:bg-black={Black}
  class:bg-yellow-700={Yellow}
  class:bg-red-700={Red}
  class="width1200px width1024px transform ease-in-out delay-1000 duration-1000 translate-x-6 overflow-auto"
>
  <div
    class="h-full hidden pl-2 py-4 lg:flex flex-col items-start justify-between"
  >
    <Logo />
    <Nav />
    <Logout on:theme={changeClr} />
  </div>
  <div
    class="w-full flex flex-col bg-white text-gray-900 rounded-md p-4 ml-4 overflow-auto"
  >
    <div class="lg:hidden block">
      <Header on:navShow={showNav} />
    </div>
    <Fileupload {id} />
  </div>
  <!--small screen navbar-->
  <button
    class:hidden={hideNavbar}
    on:click|self={hideNav}
    class="bg-white/50 flex lg:hidden items-start justify-start absolute inset-0 p-8"
  >
    <SmallScreenNavbar />
  </button>
</div>
