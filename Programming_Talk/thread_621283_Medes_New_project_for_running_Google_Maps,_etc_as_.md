---
title: "Medes: New project for running Google Maps, etc as desktop applications"
date: 2007-11-23
forum: Programming Talk
---

### Post by SeanHodges on 2007-11-23
I've been working on a project for running web applications outside of the browser. It's a very new project, and theres a fair bit left to do. However, it does work, and already provides me a way to run Google Maps and Pandora radio outside of Firefox.

I'm aware of Prism, Webrunner, Adobe Air, etc, but there are some significant differences in direction between these programs compared to Medes. I plan to provide some details on this in the near future.

Feel free to download the packages I created for Gutsy (both i386 and AMD64 are available) or compile the source code (be sure to check out the README for instructions).

[http://seanhodges.co.uk/~sean/medes/](http://seanhodges.co.uk/~sean/medes/)

Any feedback/help will be more than welcome, technical or otherwise. I am working on this with an open mind to functionality. This is my first project targeting the Linux platform, as well as with C++, so be sure to give me pointers if I've done something wrong.

Cheers,

Sean

---

### Post by SeanHodges on 2007-12-08
I now have an entry on Launchpad for all things Medes!

[https://launchpad.net/medes](https://launchpad.net/medes)

Unfortunately, I'm not able to put my code on there at this point as it doesn't support Git VCS. I will continue to use the project website (provided above) to host the packages and source code, and will use Launchpad for most other development tasks.

I'll hopefully have release 0.0.2 available over the next day or two, which will include a dynamic menu bar, and rules for handling Javascript actions.

I also plan to set up a more suitable website for the project, so I can stop treating this forum like a blog :)

---

### Post by SeanHodges on 2007-12-09
Medes 0.0.2 has been released:

[http://www.seanhodges.co.uk/~sean/medes/](http://www.seanhodges.co.uk/~sean/medes/)

---

### Post by SeanHodges on 2007-12-13
Medes 0.0.3 has been released. 

Nothing major, more bug fixes, new keyboard accelerators on menus, and added the application icon to the windows (and task bar).

---

### Post by kriwil on 2007-12-13
great app!
this is what I looking for :)

but I'm missing progess/status bar, is there any possiblity that will be added?
thank you again for the great app :)

---

### Post by Tomosaur on 2007-12-14
Looks interesting, but I think Firefox + tabbed browsing is 'cleaner'. I like the idea of desktop / website integration, but I think I'll wait to see what you can come up with before I start using it properly :P

---

### Post by SeanHodges on 2007-12-15
> I'm missing progress/status bar, is there any possibility that will be added?

Thanks for your encouraging comments kriwil!

I will look into adding a progress bar for the next release. It will definitely be useful, and even fairly vital for users on low bandwidth connections. Hopefully a more desktop-oriented solution will be introduced in the future, but for now I'll plan to add a simple progress indicator.

> Looks interesting, but I think Firefox + tabbed browsing is 'cleaner'. I like the idea of desktop / website integration, but I think I'll wait to see what you can come up with before I start using it properly :P

I see where you're coming from Tomosaur, and I concur to some degree. The objective of Medes is to target a specific set of regularly-used websites; ones that some people wish wouldn't terminate when they accidentally closed the entire browser window, and would prefer to fire up more quickly than Firefox can currently offer. There are some other planned benefits, but there's not much point me dwelling on functionality that doesn't yet exist.

If you do decide to give it a spin, be sure to let me know of any reservations you have about the concept. I'm hoping that this project could evolve into something that lots of people can find useful; as currently it only meets my own needs, and anyone who happens to use the same websites that I use.

---

### Post by xtacocorex on 2007-12-15
> **Tomosaur said:**
> Looks interesting, but I think Firefox + tabbed browsing is 'cleaner'. I like the idea of desktop / website integration, but I think I'll wait to see what you can come up with before I start using it properly :P
Think of this as something similar to a [Sherlock]("http://en.wikipedia.org/wiki/Sherlock_(software)") plugin for OS X.  I actually just discovered that program on my Macbook yesterday and found it very useful.  I think if SeanHodges can get the niche users excited about this, he may have a successful program.

---

### Post by Brindled on 2007-12-16
> **SeanHodges said:**
>  The objective of Medes is to target a specific set of regularly-used websites; ones that some people wish wouldn't terminate when they accidentally closed the entire browser window, and would prefer to fire up more quickly than Firefox can currently offer.



i like it a LOT!

i've used pandora for the last two years or so, and i definitely like the fact it now has its own process, thanks to you.

i also use google maps a good bit, and i do like how big the map window is over my browser's size.

i might just have to create a facebook account to see it in effect.

keep up the great work! 

ps. pandora did cause a popup. i understand that's apart of it, and have dealt with it in the past. this will not deter my use of Medes.

Thanks Sean, You ROCK!!! :guitar:

---

### Post by SeanHodges on 2007-12-17
Brindled, xtacocorex,

Thanks for your input. I'll be sure to keep moving forward on this project, I feel after a bit more work it should be ready to start advertising outside of this programming thread. It won't be finished by a long shot but it would be good to get some more testers and contributors on board...

xtacocorex, I'll be sure to take a close look at Sherlock, perhaps there are some ideas that could be leveraged from it.

Brindled, It's good to hear you are making good use out of Medes, I'm hoping to start supporting more websites from now on, just as soon as I've made sure people can choose to only install the ones they want. I've noticed the Pandora xmas banner was added recently, I think the internal advert dropping feature in Medes will remove it, but can't test this right now.

Thanks again :)

---

### Post by SeanHodges on 2007-12-17
I've just released Medes 0.0.4 - trying to keep the releases frequent :)

I've added a status bar with page load progress indicator (optional to the website configuration).

I've also had to drop the Google Docs application, it was having some difficulties with Medes because of some weird session handling it's trying to do. I'll reinstate it once I've fixed the problem, but for now I've added 2 new examples to replace it:

[LIST]
[*]G-Mail
[*]Ubuntu Community Documentation (Wiki)
[/LIST]

This will probably be the last release provided in this way. My next plan is to split up the websites from the Medes "core" package, and start providing a package per website over a repository. This way people can choose to install only Web applications that they actually use.

As always, the new release can be downloaded at [http://www.seanhodges.co.uk/~sean/medes/](http://www.seanhodges.co.uk/~sean/medes/)

---

### Post by Nekiruhs on 2007-12-17
I'm interested. Just curious how is this different from Prism? I use Prism in Windows and love it. Is this essentially a clone, or are there key differences? Either way I'm interested.

---

### Post by Brindled on 2007-12-17
I am now using Medes along with the Freewins plugin for Compiz with it sitting next to my browser. This allows quick access (focus) and a quick glance to see what is playing or has played without clicking on it (or a tab for that matter).  however, interaction with Medes is a little difficult using freewins because the interface gets  put out of sync with what you see in any given window. hopefully, that will be addressed with later versions of Freewins if possible. 

[IMG]http://www.hotlinkthis.com/albums/data/544/medium/Medes-Freewin_IA.jpg[/IMG]

just a suggestion, but maybe there's room for a myspace Medes? (no luaghing)

Thanks again

---

### Post by SeanHodges on 2007-12-20
> **Nekiruhs said:**
> I'm interested. Just curious how is this different from Prism? I use Prism in Windows and love it. Is this essentially a clone, or are there key differences? Either way I'm interested.

I was hoping to write an article on the differences between Medes and Prism/Silverlight/Air from both an end-user and technical POV. I've been really busy recently with the Christmas holiday looming, but I will get around to it promise!

Brindled, that Freewins plugin looks really neat, I'll be sure to check it out myself in the near future :) MySpace is one of the next planned websites to be added, though I want to sort out the packaging before I add any more (which will probably be this weekend).

---

