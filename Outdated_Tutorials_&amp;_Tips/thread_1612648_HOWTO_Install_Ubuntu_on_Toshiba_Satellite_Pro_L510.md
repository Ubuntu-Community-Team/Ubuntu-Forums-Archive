---
title: "HOWTO: Install Ubuntu on Toshiba Satellite Pro L510"
date: 2010-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Bucky Ball on 2010-11-03
*** UPDATE: I installed 10.04 LTS yesterday (9/7/2011) and all problems seem to be fixed. Picked up my internal wireless and an external dongle (both Realtek but different chips) out of the box and works fine, as do 10.10 and 11.04, both of which I have installed also. So, this HOWTO is probably redundant but if you are still having problems, by all means, this thread may have a clue that helps you out.

Wireless is still unstable in all releases but I have discovered that is my particular internal wireless card (Realtek RTL8191SEvB, not Ubuntu's fault). The external dongle works great, as does ethernet cable. Good luck and happy Ubuntuing! ;)

[CENTER] ***
[/CENTER]
 
Hi all,

The machine is a Toshiba Satellite Pro L510, model  PSLGXA-002002; an Australian model. This method will probably work for  other models as well so if you're having trouble installing, give it a  go. NOTHING in here can do any harm. 

I resigned myself to no  Ubuntu on my brand new machine after trying every version from 8.04 LTS  to 10.10. Then I put two and two together at 3am when I found myself  sitting in front of a fully operational Toshiba Ubuntu notebook, almost  by accident, about 48 hours later, so hope this can help some folks!

In  the end, it's easy. But you need to be prepared to use a Ubuntu release  with at least kernel 2.6.35.*, which at this point is Maverick Meerkat,  Ubuntu 10.10. Aparently 2.6.36.* works even better but haven't gone  there ... yet. 

My only problem with this solution? I ALWAYS use  LTS releases so this is against my grain ... you may be able to update  the latest 10.04 LTS (or 8.04 LTS?) to a newer kernel but this is NOT  covered here.

So, it's about this easy:

***_STAGE 1:_***
1/ Download Maverick Meerkat 10.10, burn a CD and boot from it.
2/  When you get to the purple screen with the two icons down the bottom,  PRESS ESCAPE. You will now be at the 'Try Ubuntu without installing'  page.
3/ Hit F6. Select 'acpi=off' from the pop-up list by selecting then hitting enter, then hit escape.
4/  Select 'Try Ubuntu without installing'. Wait while Ubuntu loads from  disk. DON'T PANIC! This can take sometime, even on powerful machines.
5/ Eventually, you should be sitting in front of the Maverick Meerkat 10.10 desktop, and ain't that sweet!

If  you got this far and things are good, excellent. Go ahead and install  Ubuntu by clicking the icon on the desktop. (Again, be patient; this can  take some time and seem like nothing is happening at times.) 

***_STAGE 2:_***
Once installed, reboot (removing the installation media when prompted) and follow what I'm about to say next carefully as it is _VERY IMPORTANT_.  If you omit this next bit, you will reboot into a sea of scrolling  errors in a shell (which could be the very problem you've been having  previously):

1/ At the start menu listing your operating systems,  select Ubuntu (If you don't get a selection you have one operating  system installed and need to hit any key at the blank screen to bring it  up I believe);
2/ Press 'e' to edit the kernel line;
3/ Find the line that ends in 'quiet splash' and make the last part look like this, the new, added entry in bold:

```
quiet splash **acpi=copy_dsdt**
```4/ Press CONTROL+x to boot into the kernel.

Did  this work? If so, you should be logged on and sitting in front of your  new install and you need to make the kernel line change permanent. So  ... there are a couple more things to do and you should be swinging.

***_STAGE 3:_***
1/ Open a terminal. Don't panic,  there is not much to do here and it is short and painless. Just copy and  paste the commands from here so they are right. 
2/ In a terminal enter:

```
sudo cp /etc/default/grub /etc/default/grub.backup
```This makes a copy of the file in case of mishap.

3/ Enter in a terminal:

```
sudo nano /etc/default/grub
```4/ If there is one (if there's not copy and paste/add the one below the other GRUB_CMDLINE instructions), find the line that reads:
```
GRUB_CMDLINE_LINUX=""
```and change it to:

```
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
```5/ Hit CONTROL+x, then 'y', then 'Enter' to save and exit file.
6/ Type:
```
sudo update-grub
```... and you're done! Reboot and this time you don't need to edit the menu entry, just choose Ubuntu and hit enter. 

Wireless  should work out of the box. Once online you will be offered drivers for  you ATI graphics. Install them and you are basically up and running.  You might find a few buglets but this release is great and will rock  more as updates arrive so enjoy!

For me there is only one real  issue: Wireless worked 'out of the box' but for some odd reason it is  totally unstable and therefore unsable. Works fine in Windows 7 but  ducks and weaves from 100% connection to around 50%. Am working on a fix  for this which will post here along with anything else that comes up.

* An update on the wireless issue: I emailed Realtek and they tell me the driver is for 32bit systems. A bit poor on their part IMHO. 

So, with any luck you should be up and running now. Hope I've helped a few of you Toshiba owners out there. Enjoy! :)

---

### Post by imdead on 2011-02-19
Strange thing Bucky Ball I can get my Toshiba L510 to boot up on a Ubuntu or Kubuntu or Xubuntu 11.04 Alpha 2 with no problems out of the box, its only when it comes to the older ones that has the problem that's all.

---

### Post by Bucky Ball on 2011-02-20
That is strange. Only problem I can see with that is that is cutting edge and bound to be unstable at times. Don't really know why these instructions aren't working for you on 10.10 as you have the same model as me. Where is the install breaking?

---

### Post by imdead on 2011-02-20
Sorry Bucky Ball I haven't tried your way of using Ubuntu 10.10 at all, because I didn't know about how to do that & I came across the newer version first & I tried it & it worked strait of from the word go all I've had the problems with this OS was the Video Card driver & I've fixed that problem myself so what do you think I should do then go to your version or keep on with on what I've got?

---

### Post by Bucky Ball on 2011-02-20
Put it this way: 11.04 is not released yet (April 2011 release time, thus the name) so is still testing (all probs in the Natty Narwhal Testing forum therefore) . There will be issues, a few or lots, who knows. 10.10 is released and reasonably stable (at least on my machine). If I could get 10.04 LTS working on my machine I would be using that as it is LTS (long term support) and supported until April 2013 (server version until 2015). Have a look here:

[http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html)

If 11.04 is working perhaps stick with it. You will learn about Ubuntu as you fix problems if and when they crop up. It is really more about the kernel. Perhaps the kernel used in 11.04 has the Toshiba patch and some other tweaks already there so you don't need the steps in my post (10.10 has the Toshiba patch but you need 'acpi=copy_dsdt' in grub to use it, 10.04 doesn't and needs to be recompiled).

I think the decision's yours on this one. Good luck. ;)

BTW, how did you fix the video driver? The newer kernels are not ATI ready at this point but maybe that has changed (they pick up the drivers in 'Additional Drivers' but won't install them). I am currently using 2.6.35.24 with no problems with 'acpi=copy_dsdt' applied in grub.

---

### Post by imdead on 2011-02-20
Well I download ATI drivers from the ATI site I know its not tested by Ubuntu but it worked, they must have put something with the driver for it to work or I wood have been asking for some help on here.

---

### Post by gurlsee on 2011-03-15
The XP Home product key sticker is still on the bottom of the unit; all  he needs is a CD and whatever Toshiba-centric drivers might be  necessary.

[contemporary furniture](http://www.moderncollections.com/) | [modern lounge chairs](http://www.moderncollections.com/modern-lounge-chairs.html)

---

### Post by theburrus1 on 2011-07-29
Thanks a lot Bucky Ball for the excellent step by step. I was having that exact same problem. I'm a novice with Ubuntu but still was able to install it successfully as dual boot alongside Windows 7, and on a Toshiba laptop L655D at that.Really appreciate it!

---

### Post by Bucky Ball on 2011-07-30
> **theburrus1 said:**
> Thanks a lot Bucky Ball for the excellent step by step. I was having that exact same problem. 

Pleasure, thanks, glad it helped and all works, and welcome to the forums. ;)

Out of curiousity, what release did you install? I have recently installed 10.04 and 11.04 alongside 10.10 and Win 7 and had no probs installing either without using my guide. The Toshiba patch that was originally not in 10.04 is now perhaps included.

---

