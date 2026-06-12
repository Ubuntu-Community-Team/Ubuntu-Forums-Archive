---
title: "getting more grip on usplash"
date: 2009-05-03
forum: Programming Talk
---

### Post by RaumTrug on 2009-05-03
recently I got fed-up with the standard ubuntu bootsplash and had a look at how to create own modules for usplash. to my delight I found the basic architecture to be "able" not only to cast static images onto the screen, but 25 fps animations...wich already works well with things like animated bitmaps, one just has to load all frames into the object, etc...
however, I'd like to go a little further and make demostyle realtime generated animations/effects - oldschool stuff should meet the prerequisites of low cpu load, low resolution and palleted colordepth very well.

unfortunately the usplash architecture doesn't provide means for this, most notably access to the framebuffer or means to pass a backbuffer to the library in order to let it update the screen itself.
is there probably any "workaround" for this, _without_ having to modify the usplash library itself as it is right now? I want my animations not only running on my own pc, but share them with others, not having to entice them to warble around with their system too much ;)

I thought about a few approaches to acchieve this, but am to timid of trying them out, in order not to render my sole pc unbootable; so I ask you to tell what you think about them:

-1. try to get access to the framebuffer via bogl; bogl.h features a putpixel method, boglP.h features a pointer to screen mem...but what happens if usplash decides to use the svgalib drivers...and is it possible to access the bogl internals in usplash this way, as it's most probably statically linked? if it's possible, would there be any way to find out wich driver usplash is using from the init method, and then get a framebuffer pointer for/from the right library?

-2. probably the "safer" method: usplash provides means to put a bitmap onto screen, but the headers say it's run-length encoded. the easiest method would of course be using a screen-sized usplash_bitmap as backbuffer, and render to screen by "putting" it. any ideas/help on how to get a standard 8bit backbuffer in this format?

-3. usplash does no retrace syncing, wich is very annoying even at the simple standard theme "pulsating" bar: it's teared horizontally almost all the time. any ideas on how to get this working properly? I fear the idea of having to watch a fullscreen animation that's spliced-up all the time...

also, does the usplash plugin really _have_ to provide a screen sized background image? it's a waste of space and memory, better for my approach would be to provide only the desired resolution(s) instead of having to suplly empty bitmaps in each resolution supported...any ideas on how to avoid wasting this memory?

-TraumFlug

[edit] ...oops, I accidentally postet this to the wrong forum!! this should be in the "Programming Talk", not in the "Dev Link" forum, of course; my first post here, I apologise for this, won't happen again. ...now could this be moved...? [/edit]

---

### Post by RaumTrug on 2009-05-05
while this thread lay dormant in the wrong forum, I did some research on my own, the results of I want to share here, but that also raised new questions that probably programmers more experienced than me could answer.

as of first, I found that the usplash_pixmap data is _not_ run length encoded at all (unlike the headers state...), and that's one explanation why the usplash themes are so big in size!
the good point on this is that you can easily generate your own graphics and store it in the pixmap .data field, using it as a backbuffer - it's just linear 8bit pixel colors data - and put it to screen with usplash_put. say hello to the possibility of realtime animated bootsplashs :)
also fighting my way through the usplash sources I found there's most probably (unless I've overseen something somewhere) no need to define the whole bitmap in your plugin, so I'll try to just define a pixmap with width, heigth, ncols and a dummy pallete, leaving the data field empty, for each resolution I wish to support. all you have to take care of is that you define _all_ of the draw functions in the theme struct, otherwise the pixmap will be used by usplash itself trying to put it to the screen, most probably resulting in noise put to the display :D
I've also seen that in newer versions of usplash there's no more need to supply one pixmap for every resolution, but there'll still be lots of older usplash vers running on our planet...

as for the retrace syncing, I've added a "bug" description (regarding the image tearing that results from not using it...) to the project's website, suggesting a sync function should be implemented, but untill that's done one day I want to think about a way of doing it with older versions of usplash.
my idea is supplying versions of the needed code in the plugin itself, trying to find out wich lib. is used by usplash (bogl framebuffer or svgalib) in the theme->init function so that the animate_step routines can use it before putting the backbuffer to screen. just how could I find out wich gfx.lib is used...from within the theme? and is svgalib compiled into usplash by default, and often used...?

also I found the animate_step function, that I'm interested in for doing my core animation code, is called via do_animate, that is hooked to a "signal handler", and I guess that's somekind of interrupt/timed thread running in the background. I don't know about the details of such, and I'm wondering on how it would react if it triggered do_animate while the last triggered instance is still running (because the animation takes too long to be calculated, or is still waiting for retrace)? I'd of course like to watch for that myself, so I can drop a frame or two to make sure the animation runs at the correct speed, and doesn't slow down instead. any pointers/weblinks regarding that topic?

-thanks for your patience! ;)

---

