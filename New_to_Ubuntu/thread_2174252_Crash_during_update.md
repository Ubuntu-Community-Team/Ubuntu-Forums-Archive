---
title: "Crash during update"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by lpierce65 on 2013-09-13
I have been using unbuntu for some time on one of my computers. I got where i was comfortable with it but not knowing everything I need to know.  Yesterday while doing  a regular files update it asked to restart which i did.  when it restarted it went to a black screen and looked like it dong some sort of  check  it stopped with the checking battery status. it will not  boot up now..  I would not think this its a equipment  problem since i was doing an update.  have I lost all my files ?   ( they were back up to the cloud free version )  if anyone has any ideas how to get the computer going again would be much appreciated..

Larry Pierce

---

### Post by Impavidus on 2013-09-13
Which version of Ubuntu? Can you remember what was updated?

You are usually asked to reboot after an update if it was something with X or a new kernel. Can you get to the grub menu and select an old kernel? Maybe that helps to get the computer booted at least.

I don't think you've lost your files. This is more likely a graphics driver issue.

---

### Post by lpierce65 on 2013-09-14
thanks for your reply  but what you described is over my head  dont know what or how to get to the grub menu does make me feel better that i may not have lost the files

---

### Post by lpierce65 on 2013-09-14
pretty sure I was using the latest  edition, 12.xx

---

### Post by grentthevampire on 2013-09-14
The grub menu is the text-based option menu where you choose your OS or kernel version
somethign like this :[http://viswanathj.files.wordpress.com/2011/02/grub-menu.png](http://viswanathj.files.wordpress.com/2011/02/grub-menu.png)
now if you have something like that you could  an older kernel version in which your previous set up works...

and regarding about the files... since this is a software update im pretty sure that nothing in your files was modified or deleted in any way

---

### Post by Impavidus on 2013-09-14
If you don't see the grub menu when you boot the computer, try hitting shift repeatedly as soon as the bios screen clears (the screen with the name of the manufacturer and things like that; it's usually present). Then try booting an older kernel. Watch the version numbers. Depending on your version of Ubuntu, the old kernels may be in the submenu "older kernels" or "advanced options" or something like that.

---

### Post by lpierce65 on 2013-09-15
thanks for the replies will try your suggestions !

---

### Post by lpierce65 on 2013-09-15
That worked  !! went througI  had it up and working.. unfortunately  I thought it still need the update so I ran it, wwengt through the update  again.. then came up toa black screen.. with the following..

Ubuntu 12.04.03 LTS  Larry-MS-7518  tty1

Larry-MS-7518- Login :

I don't have a clue what this login in would be  in my sate of memory  I think this was where I went bad the last time.. is there a recovery  or a place to find the log in info  I really dont think I have ever seen this  login before

---

### Post by Impavidus on 2013-09-15
That's the console login you get when the graphical interface doesn't start. It shows you tty1. The graphical interface should be on tt7. Try ctrl+alt+F7 to get there. Also, I think you can log in and start the graphical interface with **startx**. Not sure though.

Did you get this login using the latest kernel or using an older one? If the latest, try using an older one until this problem is solved. I don't have much experience with these problems, so I hope somebody else can help you.

---

### Post by lpierce65 on 2013-09-15
Ive went to one that worked.. Now it seems my problem is in changing/resetting my passwords  since I cant seem to recall what they were.. On restart it always asks me for the Keyring password I must get it correct  but have no clue what I need a keyring for .  is there a way  change recover reset passwords?  BTW is say my software is up to date now but  I don&#8217;t want to shut down to  haft to reenter passwords to authenticate again until i can change them  and Remember them..

---

