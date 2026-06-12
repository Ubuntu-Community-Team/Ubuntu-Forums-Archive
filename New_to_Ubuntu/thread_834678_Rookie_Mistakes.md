---
title: "Rookie Mistakes"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by drunkardivan on 2008-06-19
Wow. I just had to share these with the community. I've been using Ubuntu for about a year now, so I'm fairly comfortable with it. I've set up four laptops to dual-boot, and two desktops to just run Ubuntu.

What I'm saying is, I've done installs before.

Thanks to a computer class I'm taking, I was given a Dell Vostro 1000 running XP. As soon as I got it home, time to set up another dual-boot. I was overconfident, and that got the best of me. 

First stupid move- I tend to make my Ubuntu installs small, since I can get to my Windows files via Ubuntu, but not vice-versa. I was installing Gutsy, because it has the slider to size the partition. I didn't pay attention to which one I was resizing, and ended up with an 11 GB XP partition and 60 GB for Ubuntu. While this is perhaps how things should be, it's not the ideal set-up in my mind. I was shattered, and really not looking forward to reinstalling two OS's. Right before I took the nuclear option, I decided to do a quick Google search. And Linux saved my skin. Thanks to Gparted being on the Live CD, I was able to easily switch the partition sizes. What would have been a few hours' work was done in a few minutes. Whew.

Second brain freeze- I couldn't get the box to update. Nothing was showing in System -> Administration -> Hardware Drivers to allow me to install the restricted drivers. I finally decided to exercise my CLI-fu, and (feeling rather smug about remembering the command) typed sudo apt-get install update. Nothing. What the heck was I doing wrong? Decided to go to Synaptic and see if I'd forgotten something. As I was scrolling down, I saw "Software Sources". Oh, yeah, I guess that might help just a tad. Enabled everything, and my box is now happily installing its 227 updates.

I hope someone gets a laugh at my expense, and maybe a reminder that, no matter how many times you've done something, it's always good to take your time and make sure you're doing things the right way.

As carpenters say, "Measure twice, cut once".

---

### Post by tjwoosta on 2008-06-19
haha yea, i think we all make careless mistakes sometimes

glad to hear you got it all sorted out


by the way 
> First stupid move- I tend to make my Ubuntu installs small, **since I can get to my Windows files via Ubuntu, but not vice-versa.**

this is not true

you can acess your ubuntu partition from windows extreamly easily

you simply have to install an ext3 read/write compatibility driver in windows

this might help
[http://ubuntuforums.org/showthread.php?t=194279]("http://ubuntuforums.org/showthread.php?t=194279")

here is the direct link to the driver i use [http://www.fs-driver.org/download.html]("http://www.fs-driver.org/download.html")

(just run setup in windows then reboot, easy)

---

### Post by Duck2006 on 2008-06-19
ext2 drivers in windozes will let you see and write to your linux partitions.

---

### Post by jualin on 2008-06-19
I have done it before you can access your linux partition from windows, just follow the guide.

---

### Post by mivo on 2008-06-19
One of the bigger problems, in my opinion, is that people don't make a separate /home partition (10 GB for /, rest for /home). Having one makes reinstalls and upgrades so much easier and more convenient.

---

