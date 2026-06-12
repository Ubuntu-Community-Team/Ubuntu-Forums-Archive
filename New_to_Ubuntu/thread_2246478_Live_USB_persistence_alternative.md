---
title: "Live USB persistence alternative?"
date: 2014-10-01
forum: New to Ubuntu
---

### Post by foster5 on 2014-10-01
Hi guys, and thanks in advance for reading over this post and helping me out. I really appreciate it.

So my goal, (and I'm not sure if this is feasible or not) is to be able to go to any of my computers, *friends, family, or the ones at my school* stick my small USB thumdrive in, and bootup a personalized Ubuntu OS with all my settings. This way I have something that I can navigate around easier on the web, mostley. I'm not trying to save videogames or anything. Just a few small applications and bookmarks, really.

Since I can't get persistence to work. (I've tried like 5 different methods to the T and now I'm stuck with an error message saying "videomode not found" "booting in blind mode" in the bootup menu for the pre release of Linux USB loader 2 (mac) by sevenbitstech on github. Which has a persistence allocation and creates the casper-rw file.

Right now I've been using my USB kingston 16gb flashdrive. I figured it would be faster than any hard disk western digital drive. Even if it is 16gb apposed to 2 tb. 

[B]So I'm wondering if there's an alternative to persistence? 

[/B]Maybe clonezilla will work? Even if I have to stick in an additional USB drive to transfer over the settings, and store additional files, that would work for me. However, there's a certain appeal to me of having one single USB stick that holds the key to my personal preferences. And if I could set the wireless driver every time myself (even if takes 3 extra minutes) and download the settings from online or something that would almost be preferable. Because that way I'm the only one who has access to the settings...

When I say settings, I mostly meant the wireless drivers. I was trying to save myself 3 minutesvery time I booted up. But it's not the end of the world. I've almost not even gotten to the other programs and files because I haven't had much time to work on those yet because I've been hungup with persistence and trying to get it to work. I'm on a macbook pro with nvidia graphics (I get this wierd purple-messed-up login screen where there should be the linux logo bar.) But then the live OS works just fine after that.... It's a 2009 macbook pro but I'd like to be able to basically bootup on almost any computer. Or the most possible. That's the whole point of this project, really... I mean, partitioning my SSD on my macbook pro and just installing linux isn't the issue. I could do that in a heartbeat. But I've already partitioned it for windows as well and I just feel like it's overkill.

Any tips, ideas, or help would be greatly appreciated, thanks!

-Fozt3r

---

### Post by ibjsb4 on 2014-10-01
You could just do a regular install.  This will cut down the life of your flashdrive because of the number of read/writes, but its not like you will be using it all the time either.  You could also disable journaling in ext4 or just use ext2 which does not have journaling to cut down the read/writes.  

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+turn+off+journaling&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+turn+off+journaling&sa=Search&cof=FORID:9)

Since you want to use it on a varity of computers, go with something like Xubuntu.  Ubuntu/Unity will not easily adapt to changing environments.  I'm guessing a mac will run xubuntu, I have never own a mac :)

---

