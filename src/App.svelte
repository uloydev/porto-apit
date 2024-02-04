<script>
  import "boxicons";
  import "./app.css";
  import About from "./lib/About.svelte";
  import Hero from "./lib/Hero.svelte";

  let experiences = [
    {
      title: "Video Editor",
      date: "Nov 2017 - Jan 2023",
      description: [
        "Lorem ipsum dolor sit amet consectetur 1.",
        "Lorem ipsum dolor sit amet consectetur 2.",
        "Lorem ipsum dolor sit amet consectetur 3.",
        "Lorem ipsum dolor sit amet consectetur 4.",
      ],
    },
    {
      title: "Art Director",
      date: "Nov 2017 - Jan 2023",
      description: [
        "Lorem ipsum dolor sit amet consectetur 1.",
        "Lorem ipsum dolor sit amet consectetur 2.",
        "Lorem ipsum dolor sit amet consectetur 3.",
        "Lorem ipsum dolor sit amet consectetur 4.",
      ],
    },
  ];

  let portfolios = [
    {
      name: "Portfolio 1",
      link: "https://daisyui.com/images/stock/photo-1625726411847-8cbb60cc71e6.jpg",
      isVideo: false,
    },
    {
      name: "Portfolio 2",
      link: "https://www.youtube.com/embed/BIdaq6EwzFc?enablejsapi=1",
      isVideo: true,
    },
    {
      name: "Portfolio 3",
      link: "https://daisyui.com/images/stock/photo-1625726411847-8cbb60cc71e6.jpg",
      isVideo: false,
    },
  ];

  function handleAnchorClick (event) {
		event.preventDefault()
		const link = event.currentTarget
		const anchorId = new URL(link.href).hash.replace('#', '')
		const anchor = document.getElementById(anchorId)
		window.scrollTo({
			top: anchor.offsetTop,
			behavior: 'smooth'
		})
	}
</script>

<main data-theme="dracula">
  <div class="navbar bg-base-100 px-20 fixed w-full z-10 top-0">
    <div class="flex-1">
      <a href="#greeting" class="btn btn-ghost text-4xl">Pizz.</a>
    </div>
    <div class="flex-none">
      <ul class="menu menu-horizontal px-1">
        <li><a href="#greeting" on:click={handleAnchorClick}>Greeting</a></li>
        <li><a href="#aboutme" on:click={handleAnchorClick}>About Me</a></li>
        <li><a href="#experience" on:click={handleAnchorClick}>Experience</a></li>
        <li><a href="#portfolio" on:click={handleAnchorClick}>Portfolio</a></li>
        <li><a href="#contact" on:click={handleAnchorClick}>Contact</a></li>
      </ul>
      <!-- <ThemeSelector /> -->
    </div>
  </div>
  <Hero />
  <About />
  <section id="experience" class="pt-32 min-h-screen">
    <p class="text-center text-5xl mb-10 font-medium">Experience</p>
    <p class="text-center text-2xl mb-20">
      Here is a quick summary of my most recent experiences
    </p>
    {#each experiences as experience}
      <div
        class="card bg-base-content/80 px-16 py-8 w-3/4 rounded-xl mx-auto mb-12 text-primary-content"
      >
        <div class="card-body">
          <h2
            class="card-title text-center text-4xl mb-8 font-medium flex flex-row items-center justify-center whitespace-nowrap"
          >
            <span class="inline-block h-[5px] bg-primary-content w-full"
            ></span>{experience.title}<span
              class="inline-block h-[5px] bg-primary-content w-full"
            ></span>
          </h2>
          <div class="flex justify-between items-end">
            <ul class="list-disc list-inside text-x">
              {#each experience.description as desc}
                <li class="mb-4">{desc}</li>
              {/each}
            </ul>
            <p class="text-lg text-end">{experience.date}</p>
          </div>
        </div>
      </div>
    {/each}
  </section>

  <section class="min-h-screen pt-16" id="portfolio">
    <h2 class="text-5xl text-center mb-16 font-medium">Portfolio</h2>
    <div class="flex items-center justify-center">
      <div class="carousel w-3/5">
        {#each portfolios as porto, index}
          <div id={"slide" + index + 1} class="carousel-item relative w-full">
            {#if porto.isVideo}
              <iframe
                title={porto.name}
                class="w-full aspect-video"
                src={porto.link}
                frameborder="0"
                allow="autoplay; encrypted-media"
                allowfullscreen
              ></iframe>
            {:else}
              <img alt={porto.name} src={porto.link} class="w-full" />
            {/if}
          </div>
        {/each}
      </div>
    </div>
    <p class="text-center mt-5">Swipe to next</p>
  </section>

  <section id="contact" class="pt-32 min-h-screen">
    <div class="bg-base-content/80 rounded-2xl flex items-center">
      <div class="p-8 my-4 w-3/5 mr-auto rounded-2xl">
        <div class="flex">
          <h1 class="font-bold uppercase text-5xl text-primary-content">
            Get in touch
          </h1>
        </div>
        <div class="grid grid-cols-1 gap-5 md:grid-cols-2 mt-5">
          <input
            class="w-full bg-primary-content/90 text-base mt-2 p-3 rounded-lg focus:outline-none focus:shadow-outline"
            type="text"
            placeholder="First Name*"
          />
          <input
            class="w-full bg-primary-content/90 text-base mt-2 p-3 rounded-lg focus:outline-none focus:shadow-outline"
            type="text"
            placeholder="Last Name*"
          />
          <input
            class="w-full bg-primary-content/90 text-base mt-2 p-3 rounded-lg focus:outline-none focus:shadow-outline"
            type="email"
            placeholder="Email*"
          />
          <input
            class="w-full bg-primary-content/90 text-base mt-2 p-3 rounded-lg focus:outline-none focus:shadow-outline"
            type="number"
            placeholder="Phone*"
          />
        </div>
        <div class="my-4">
          <textarea
            placeholder="Message*"
            class="w-full h-32 bg-primary-content/90 text-base mt-2 p-3 rounded-lg focus:outline-none focus:shadow-outline"
          ></textarea>
        </div>
        <div class="my-2 w-1/2 lg:w-1/4">
          <button
            class="uppercase text-sm font-bold tracking-wide bg-[rgba(0,0,0,0.8)] text-gray-100 p-3 rounded-lg w-full
                        focus:outline-none focus:shadow-outline"
          >
            Send Message
          </button>
        </div>
      </div>

      <div class="w-2/5 ml-auto">
        <div
          class="flex flex-col text-white bg-[rgba(0,0,0,0.8)] px-8 py-12 rounded-2xl"
        >
          <p class="font-bold text-2xl my-4">
            What's next? Feel free to reach out to me if you're looking for a
            video editor, have a query, or simply want to connect.
          </p>
          <p class="text-2xl my-4">Don't call me kak.</p>

          <div class="flex my-4 w-2/3">
            <div class="flex flex-col">
              <i class="fas fa-map-marker-alt pt-2 pr-2" />
            </div>
            <div class="flex flex-col">
              <h2 class="text-2xl">Workspace</h2>
              <p class="text-gray-400">
                5555 Tailwind RD, Pleasant Grove, UT 73533
              </p>
            </div>
          </div>

          <div class="flex my-4 w-2/3">
            <div class="flex flex-col">
              <i class="fas fa-phone-alt pt-2 pr-2" />
            </div>
            <div class="flex flex-col">
              <h2 class="text-2xl">Call Me</h2>
              <p class="text-gray-400">Tel: xxx-xxx-xxx</p>
            </div>
          </div>

          <div class="flex my-4 w-2/3">
            <a href=""
              ><box-icon
                type="logo"
                name="instagram-alt"
                class="w-10 h-10"
                color="#fff"
              ></box-icon></a
            >
            <a href=""
              ><box-icon
                name="linkedin-square"
                type="logo"
                class="w-10 h-10"
                color="#fff"
              ></box-icon></a
            >
          </div>
        </div>
      </div>
    </div>
  </section>
</main>
