---
title: "Kernel Update??"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by 577 Jersey on 2012-11-13
Hi guys,,
 Newbie Ubuntu 12.04 lover here,,just curious if my kernel will update by itself through the update manager?

Also should we update our kernel and how often,,even if system seems to run fine,,and is there anything us newbies should be aware of when trying this,,like deleting old kernels,,how and why?

 Thanks a million!!

 Tommy:guitar:

---

### Post by Bucky Ball on 2012-11-13
> **577 Jersey said:**
> ... just curious if my kernel will update by itself through the update manager?

Yes.

> **577 Jersey said:**
> Also should we update our kernel and how often,,even if system seems to run fine,,and is there anything us newbies should be aware of when trying this,,like deleting old kernels,,how and why?

 

The first part of this, because of the answer to your original question, is redundant. 

Kernel updates generally have improvements and bug fixes so just take 'em when they come. If there is a bad apple, which occasionally happens but almost never with LTS releases, news of that normally gets to the forums pretty quickly so you can be forewarned if you want to check or are in any doubt. 

I would take them as they come. You can see what you are about to update in the Update Manager so just have a look there for kernel updates. You'll see them when they're available. You don't need to do anything but hit the Go button! ;)

As for deleting old kernels, you can, but they don't take up much room, are dormant and use no resources when not being used, but you can remove/rearrange them from the grub menu list at boot by using something like Grub Customizer:

[http://us.yhs4.search.yahoo.com/yhs/search;_ylt=A0oGdOaASKJQaDwARAql87UF?p=grub%20customizer&fr=altavista&fr2=sfp]("http://us.yhs4.search.yahoo.com/yhs/search;_ylt=A0oGdOaASKJQaDwARAql87UF?p=grub%20customizer&fr=altavista&fr2=sfp")

To delete, find the kernel number you want to delete, open Synaptic Package Manager or Software Centre and look for it. Delete all instances.

---

### Post by 577 Jersey on 2012-11-13
Wow,,
 Very good,,thank you!!

The kernel thing had me scratchin my head for a while there..lol

 BTW-Great forum here,,I was using mint 13 mate for some time,,but like Ubuntu better.

---

### Post by Bucky Ball on 2012-11-13
Glad it made things clearer. Yea, the community is a big part of the Ubuntu experience. Enjoy the OS, the learning curve, and the forums. I think Mint is based on Ubuntu/Debian so shouldn't be that much of a shock to the system, although I've never used Mint myself. ;)

---

### Post by 577 Jersey on 2012-11-13
Mint is a great distro,,

 I would say one of the best for somebody coming over from windblows like me.I found a few things to be buggy with it that bothered me.My experience with 12.04 has been very pleasant so far.
The only problem I ran into was after I installed and tried a couple dock programs,along with that compize(for wobbly windows),,things got a little strange there for a while...lol

Now I just have 12.04 settup with the basic packages that are
recommended and I could not be happier.Im not a big fan of the eye candy packages,,simpler is better for me.

 HAGO

 Tommy

---

### Post by Bucky Ball on 2012-11-13
If you don't need the eye candy or bells and whistles, you might like to try xfce4, the desktop environment used by Xubuntu (or even install Xubuntu on another partition to have a good try). Very configurable and easy to use, pared back, slick and fast.

Of course, you might be in love with Unity, but many aren't and changed to Xubuntu and other things when Unity became the default desktop environment for Ubuntu.

---

### Post by dannyboy79 on 2012-11-13
it's always good to keep 1 or 2 older kernels in case something goes wrong with the new kernel. Just my 2 cents.

****READ ONLY IF WANTING TO BOOT TO OLDER KERNEL****
You can boot to an earlier kernel by hitting shift during bootup to bring up grub boot menu and then choose the older kernel, to make it permanent without removing the new kernel which didn't work for you, you'd update GRUB_DEFAULT= setting within /etc/default/grub; the first "menuentry" has a value of "0". SO the second kernel line is normally the recovery one and then after that is the last kernel installed which would be 2, after editing /etc/default/grub, you will want to run sudo update-grub to make it stick.

---

### Post by 577 Jersey on 2012-11-13
Thank you guys for the super info,,
 I will check out Xubunbtu,,and keep my eye out for those kernel updates.

---

### Post by dannyboy79 on 2012-11-13
> **577 Jersey said:**
> Thank you guys for the super info,,
 I will check out Xubunbtu,,and keep my eye out for those kernel updates.
forgot to mention, if you happen to download Nvidia drivers from their website and ran their Nvidia_installer_script.sh (or whatever it's named) you may have to run it again after a kernel update since the nvidia driver is compiled against the current running kernel at that time. So if after a kernel update and restart, you're presented with a black screen, this may be why

---

### Post by philinux on 2012-11-13
I usually delete old kernels after I know the new one works fine. I did this a while back and got 4 gigs back. 

I use this. See step five. I just copy and paste it in. I usually do the dry run first.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I think one of the guis can do it. Maybe ubuntu tweak. Cant remember.

---

### Post by 577 Jersey on 2012-11-13
> **philinux said:**
> I usually delete old kernels after I know the new one works fine. I did this a while back and got 4 gigs back. 

I use this. See step five. I just copy and paste it in. I usually do the dry run first.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I think one of the guis can do it. Maybe ubuntu tweak. Cant remember.I read the info in the link and its all way above my head right now...lol..Im lucky if I can install using the terminal for now,,one step at a time.Im sure it will be very helpfull to me one day when I have better knowledge of the terminal.

 Thanks again guys!!

  Tommy:guitar:

---

### Post by Bucky Ball on 2012-11-13
> **577 Jersey said:**
> Thank you guys for the super info,,
 I will check out Xubunbtu,,and keep my eye out for those kernel updates.

You can try out the DE very easily. Just install xfce4, log out, choose that from 'Sessions' at the login window and you will be using Xfce instead of Unity. To revert back to Unity, do the same thing but choose Unity from the Sessions pop-up. ;)

---

### Post by 577 Jersey on 2012-11-13
> **Bucky Ball said:**
> You can try out the DE very easily. Just install xfce4, log out, choose that from 'Sessions' at the login window and you will be using Xfce instead of Unity. To revert back to Unity, do the same thing but choose Unity from the Sessions pop-up. ;)Oh my goodness,,really,,ok I will give it a try,,if its easy ,,its for me:)

---

### Post by monkeybrain2012 on 2012-11-13
> **Bucky Ball said:**
> 

To delete, find the kernel number you want to delete, open Synaptic Package Manager or Software Centre and look for it. Delete all instances.

@OP

Just to add that if for some reasons the new kernel has some bugs, boot into an earlier kernel (you can choose which one to boot into from the boot screen if you have multiple kernels installed) and delete the new one from synaptic there are usually three files to delete, the kernel image and two kernel headers. For this reason you shouldn't delete your previous kernel right the way after you update. You should keep one previous version until you are satisfied that the new one is ok.

---

### Post by deadflowr on 2012-11-13
> **Bucky Ball said:**
> You can try out the DE very easily. Just install xfce4, log out, choose that from 'Sessions' at the login window and you will be using Xfce instead of Unity. To revert back to Unity, do the same thing but choose Unity from the Sessions pop-up. ;)

If when you log out, and the login screen looks the same as always, click the ubuntu logo in the box where your login name and password are.(it'll be in the top right corner of that box).

I say this because I believe that when you add other DEs the login screen stays the Unity-greeter/lightdm of Ubuntu, unless you change it.

---

### Post by 577 Jersey on 2012-11-13
> **monkeybrain2012 said:**
> @OP

Just to add that if for some reasons the new kernel has some bugs, boot into an earlier kernel (you can choose which one to boot into from the boot screen if you have multiple kernels installed) and delete the new one from synaptic there are usually three files to delete, the kernel image and two kernel headers. For this reason you shouldn't delete your previous kernel right the way after you update. You should keep one previous version until you are satisfied that the new one is ok.
So I could just delete them all from synaptic,,do they all have the same # after them,,I was there looking under Linux and found so many different things that looked like they could be part of the kernel?

 Thanks Tom

---

### Post by Bucky Ball on 2012-11-13
> **monkeybrain2012 said:**
> @OP

Just to add that if for some reasons the new kernel has some bugs, boot into an earlier kernel (you can choose which one to boot into from the boot screen if you have multiple kernels installed) and delete the new one from synaptic there are usually three files to delete, the kernel image and two kernel headers. For this reason you shouldn't delete your previous kernel right the way after you update. You should keep one previous version until you are satisfied that the new one is ok.

And just one to add to that, I wouldn't delete the kernels. Just don't use them and use a stable one then boot into the newer one now and then and get updates and see if it's fixed yet ... ;)

---

### Post by monkeybrain2012 on 2012-11-13
> **Bucky Ball said:**
> And just one to add to that, I wouldn't delete the kernels. Just don't use them and use a stable one then boot into the newer one now and then and get updates and see if it's fixed yet ... ;)

If there is update you can install it from the stable kernel too and you will end up using the uodated one, so the buggy one will be deleted anyway, so why keep it around? ;)

---

### Post by Bucky Ball on 2012-11-13
> **monkeybrain2012 said:**
> If there is update you can install it from the stable kernel too and you will end up using the uodated one, so the buggy one will be deleted anyway, so why keep it around? ;)

Message recieved and understood. You might get some dependency issues, though, as you aren't updating from the latest kernel. Perhaps ...

Incidentally, love the nic! I spend a lot of my time looking at how similar our brains are to a monkey's, tracing human musicality mostly but generally otherwise, too! There is no disputing the fact that yes, monkeybrains we have, just with a further degree of sophistication and some alterations through genetics and evolution (not the email client but that wouldn't exist unless we'd moved on ... if only slightly!). ;)

Fascinating and off topic. Sorry all. ;)

---

### Post by 577 Jersey on 2012-11-14
No derail here,,
 Let the ball roll,,I enjoy reading all this info that you guys have absorbed over the years.

 Thanks

 Tom:guitar:

---

