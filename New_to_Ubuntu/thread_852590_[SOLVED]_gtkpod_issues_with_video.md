---
title: "[SOLVED] gtkpod issues with video"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by eatlotsoffruits on 2008-07-07
Hi all,

I am currently using amarok to manage my music on my ipod but would like to load some movies on there as well.  I read several threads that suggest using gtkpod to sync movies with an ipod and have downloaded it and tried to use it.  The problem is that gtkpod claims that it cannot load movies without the mp4v2 library.  is this a normal library that comes with gtkpod and, if not, how can i get it?  Thanks!

---

### Post by crobinson55331 on 2008-07-07
I had teh same problem but I solved it by using gtkpod-acc instead of just gtkpod.  After using Handbrake to convert dvd files or television files recorded on my computer, I can convert them to mp4 using "ipod low resolution" option in handbrake and sync with ipod using gtkpod-acc.  It works like a charm.

---

### Post by mkokotovich on 2008-07-07
Assuming your videos are in the correct format, you should be able to use gtkpod, but you need to install the aac version.

So do:

```
sudo apt-get remove gtkpod
```

and then

```
sudo apt-get install gtkpod-aac
```

That should do it...


[edit] oops, too slow

---

### Post by eatlotsoffruits on 2008-07-08
i removed gtkpod and installed gtkpod-aac just as you wrote it above but i still get an error message when i try to add a movie file to the local folder of gtkpod.  Here's the error message that appears:

Import of '/media/OneTouch 4/Movies/FightClub.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.
The following track could not be processed (filetype is known but analysis failed): '/media/OneTouch 4/Movies/FightClub.mp4'

I'm pretty slow when it comes to installing or compiling pretty much anything...how do i compile gtkpod together with the mp4v2 library?

some (perhaps pertinent details):
I'm running Gutsy, I use Amarok with my ipod and, after some updates to the libraries, it's working great.  I also am using an 80G ipod and already have several movies in the mp4 format.

Thanks for your advice/help!

---

### Post by eatlotsoffruits on 2008-07-09
So can anyone tell me how to get that library?  Or suggest something other than gtkpod that i can use for ipod video?

---

### Post by mkokotovich on 2008-07-14
Sorry for the delay

I believe that Gutsy's version of gtkpod didn't work for me when I was trying to add movies.

If you don't mind the hassle of upgrading to Hardy, I would go for it, and I bet it'll fix your issues.  That would be the easiest way to get things to work.  There are other ways, but they seem harder right now.

---

### Post by eatlotsoffruits on 2008-07-15
no problem about the delay.  In fact, thanks for replying at all!  I'll give upgrading to Hardy a shot and report back on how it went.

---

### Post by mkokotovich on 2008-07-15
Sounds good. Just remember to install gtkpod-aac, and that should do it.  If it isn't working... well let's just hope it works :-P

---

### Post by eatlotsoffruits on 2008-07-16
I upgraded to Hardy last night and installed gtkpod-aac....it worked like a charm!  Thanks so much for your help!

---

### Post by mkokotovich on 2008-07-17
You're welcome, I'm glad it worked!

---

