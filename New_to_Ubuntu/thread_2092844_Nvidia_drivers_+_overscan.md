---
title: "Nvidia drivers + overscan"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by RabidSquirrel on 2012-12-09
Ubuntu 12.10 64bit + GTX 560

I'm aware that there are problems with the current Nvidia card drivers. I got the drivers and ended up seeing nothing but my desktop image when my computer restarted. I managed to remove the update, and I used the "fix" found on the linked page but it didn't work. 

[http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers](http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers)

After spending half a day on Google with no luck I'm asking here for any solution to fixing my overscan problem. I'm not at all sure that installing the drivers will even help but I don't know what else to try. There's no screen adjustment options in System Settings. My TV is 5+ years old and has no options to fix it. I'm willing to switch to an older version of Ubuntu or the drivers or whatever will make it work. 

Also I'd like to know how to get 1600x900 resolution. It's not available in System Settings and 1920x1080 makes everything too small.

I literally just installed Linux today and I'd appreciate a very detailed step by step answer if possible. I'm sad to say it's not making a very good first impression.

---

### Post by johnycsf on 2012-12-09
[https://www.youtube.com/watch?v=iYWzMvlj2RQ](https://www.youtube.com/watch?v=iYWzMvlj2RQ)
:)

---

### Post by RabidSquirrel on 2012-12-09
My sound runs through my video card so I can't hear anything in the video. :P The title leads me to believe it won't be very helpful though...

Anyway, I tried installing the drivers one more time just for the hell of it. They worked, kind of, but my display settings insisted I have a 7 inch screen and I had to use 720x480 resolution...

Edit: I don't remember what it said before but after removing the drivers it still says I have a 7 inch screen (actually 40). It does let me use 1920x1080 again though.

---

### Post by johnycsf on 2012-12-09
LOL Linus explains that Nvidia isn't really linux friendly.

See if you can download drivers for your video card from the nvidia website.
That resolution sucks I'm sorry. 
But does it let you change the resolution at all?

---

### Post by RabidSquirrel on 2012-12-09
I downloaded the drivers from nvidia's site but it came as a .run file. I double clicked it and it took 40 minutes to open in a text editor. (???) I don't know what to do with it.

It didn't let me change resolution with drivers installed. Without them I get a few options, bot nothing between 1920x1080 and 1024x728 or something like that.

---

### Post by RabidSquirrel on 2012-12-10
I figured out how to install a .run file, but when I try it says something like 'you need to disconnect from x server.' I looked up how to do that, but when I do I use the same command to install the drivers and it can't find them. I think it might be a problem with the filepath being different with x disabled? 

I have practically no experience using the terminal. Can I get a video or very specific instructions on how to install with a .run file by disabling x? Sorry if I'm not using proper terminology, like I said I just installed Linux yesterday.

EDIT: I have no idea how I managed it, but somehow I got the drivers installed. Unfortunately, Nvidia settings has no overscan options for my TV. I guess I'll be using Win7 until I can afford a new one.

---

