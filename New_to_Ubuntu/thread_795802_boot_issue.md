---
title: "boot issue"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by kellogs908 on 2008-05-15
I installed the last version of ubuntu on my laptop and I loved it, however becuase of some problems I had with my schools wireless network and due to the fact that I use specialed programs such as autocad for engineering purposes I had to dual boot. Yestreday I decided to make some copies of dvd's onto my harddrive, so that when I got home from college i could put them on an external drive I had already taken home for backup purposes. In order to do so I had to delete the ubuntu partition for more room (I had already planned to do a complete reformat once I got home). I figured that if i deleted the ubuntu partition windows would boot up like normal windows does, (my computer boots up windows and ubunutu through GRUB and I didnt ake that into account) anyways is there anyways I can boot up windows again without reformating, I dont want to lose some docmunets on there and some music, as well as the time i already put into copying a lot of my dvd's 

thanks

---

### Post by phidia on 2008-05-15
Get the [Super Grub Disk]("http://www.supergrubdisk.org/") that should allow you to boot windows again.

Or read and implement [this]("http://support.microsoft.com/kb/314503").

---

### Post by Tatty on 2008-05-15
Your GRUB information is stored by default on your ubuntu partition in /boot, so deleting that partition will cause problems.

However this is very easy to rectify if you have a windows install disc... [http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/](http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/)

---

### Post by kellogs908 on 2008-05-15
thanks guys figured it out, the process for vista a a little differnt than the second link, slight change since xp, you use bootrec.exe and then it tells you how to use fxmbr, found an article on it, thanks for the help this forum never dissapoints

---

