---
title: "Eclipse as an alternative to Visual Studio"
date: 2008-06-24
forum: Programming Talk
---

### Post by remu on 2008-06-24
Hello everyone,
I'm currently taking an intro to C Programming course, and am doing all of my coding with gedit, compiling with gcc and MINOR debugging with gdb (which confuses me quite often). I recently had a major problem with one of my assignments, and my friend was using Visual Studio 2008, so he took a look at my code, and told me that the reason I was getting a segmentation fault was because my 2 dimensional array was only passing the first element. Anyways...this left me quite impressed, because he was relying on the debugger for that info, and once I got that info, I had my program fixed and working nicely.

So, my question is, is there someway of turning Eclipse, or any other IDE for that matter, into a powerful alternative to Visual Studio? I remember seeing a screen shot of someone running Eclipse for C programming, with the debugger and everything running. I've been reading online, and have tried many things, but have not been able to get Eclipse working properly for me. I've installed it, with the C programming plugin, I think its called CDT or something like that. But I am lost. I was wondering if there is a tutorial, or how to, which can guide me into setting up Eclipse or some other IDE, and possibly a crash course into the functions.

Your input is highly appreciated.
Thanks

---

### Post by Can+~ on 2008-06-24
> **remu said:**
> So, my question is, is there someway of turning Eclipse, or any other IDE for that matter, into a powerful alternative to Visual Studio? I remember seeing a screen shot of someone running Eclipse for C programming, with the debugger and everything running. I've been reading online, and have tried many things, but have not been able to get Eclipse working properly for me. I've installed it, with the C programming plugin, I think its called CDT or something like that. But I am lost. I was wondering if there is a tutorial, or how to, which can guide me into setting up Eclipse or some other IDE, and possibly a crash course into the functions.

Your input is highly appreciated.
Thanks

If your problem is installing, then:
[PHP]sudo apt-get install eclipse eclipse-cdt[/PHP]

And the image you said.. [is this one](http://img.photobucket.com/albums/v517/CanXp/outofbounds.png)?

*edit*
Also! I once made a video on how to set a project on eclipse (on ogg) and uploaded it to mediafire:
[http://www.mediafire.com/download.php?nxxsdwlyz1l](http://www.mediafire.com/download.php?nxxsdwlyz1l)

---

### Post by remu on 2008-06-24
Yes, thats the image! I should have spent the two seconds to search for it, but I was in class, and posted this between breaks.

And thanks for that video, it cleared something up for me, mainly that filters thing when you hit run. However, when you open it as a project...does that create a make file for you? Because for my needs, I just require source code to hand in after I've compiled it to make sure it works.

I'm not too sure on what "make" files do, and if they are needed for my uses.

---

