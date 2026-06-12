---
title: "Ubuntu 8.04 will not install"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by juanfran27 on 2008-09-06
Hello all,

A few months ago I intalled Ubuntu 7.10 in a partition, In the other one I have Windows Vista. Now I want to delete the Vista partition to only have Ubuntu on my Dell. I thought I could do it by reinstalling a fresh copy of Ubuntu, so I downloaded the latest version. When I tried to install it, nothing happened, the computer screen was just blank. Then I tried doing it with the previous version (the one I had) but the CD would not load, the computer showed the "choose your OS" option - luckily nothing happend to what I had. 

I want to get rid of Vista (which I'm not happy with) and use linux. For programs requiring Windows I plan to use Virtualbox with Windows XP.

Thanks In advance for your help. 

Happy Saturday.

---

### Post by wolfen69 on 2008-09-06
basic question. is your pc set to boot from cd first?

---

### Post by juanfran27 on 2008-09-06
Yes. I pressed F12 to boot from CD.

---

### Post by Bucky Ball on 2008-09-06
Did you burn it as an iso at 8x or lower and then check the integrity of the burn? If it isn't a bootable disk it will ignore your setting to boot from cd and just boot from the second boot device, not always but does this on my desktop. Silly question perhaps but gotta ask. ;)

---

### Post by juanfran27 on 2008-09-06
> **Bucky Ball said:**
> Did you burn it as an iso at 8x or lower and then check the integrity of the burn? Silly question perhaps but gotta ask. ;)

I did burn it as an ISO, but I didn't see what speed I chose. The CD launches when I want it to. It is when I choose the install option when the screen goes black.

---

### Post by Bucky Ball on 2008-09-06
You have gone into the BIOS at boot, set first boot device to CD, inserted the cd, hit f10 to save changes and exit and the computer has restarted, thus *booting up from the cd*? Not talking about trying to boot it from inside an OS? :-k

---

### Post by kansasnoob on 2008-09-06
Vista's SP1 s^it will do that to you!

First of all, if you have Ubuntu running just like you like it there's no need to remove it all, other than updating from 7.10 (Gutsy) to 8.04 (Hardy).

Can you even boot and run the live CD by choosing "run Ubuntu without changes"?

---

### Post by Zzl1xndd on 2008-09-06
Have you tried the Alternate CD, I find when I have these kinds of issues it normally works without any trouble.

---

### Post by juanfran27 on 2008-09-06
> **Bucky Ball said:**
> You have gone into the BIOS at boot, set first boot device to CD, inserted the cd, hit f10 to save changes and exit and the computer has restarted, thus *booting up from the cd*? Not talking about trying to boot it from inside an OS? :-k

No, i'm not booting from the OS. I restarted the PC. When the Dell screen appeared, I pressed f12 (indicated in top right corner) to go to boot options. I chose the CD/DVD drive, with the CD in. The "Start screen" for the Ubuntu CD was shown, I had several options, such as trying with Live CD and installing the OS. I chose to Install the OS. The Kernel loaded and then the screen went blank. I let it sit there for a while but nothing would happen.

---

### Post by juanfran27 on 2008-09-06
> **tweakedenigma said:**
> Have you tried the Alternate CD, I find when I have these kinds of issues it normally works without any trouble.

The alternate CD? You mean the 7.10 CD? I did, but the CD screen does not load.

---

### Post by Zzl1xndd on 2008-09-06
When you download Ubuntu there is normally a check box that says download Alternate CD, It uses a Text installer instead of the normal one. For me 9 times out of 10 it works when you have issues like this.

---

### Post by juanfran27 on 2008-09-06
> **tweakedenigma said:**
> When you download Ubuntu there is normally a check box that says download Alternate CD, It uses a Text installer instead of the normal one. For me 9 times out of 10 it works when you have issues like this.

Text based Installer? Sounds scary for a linux noob like myself.

---

### Post by Zzl1xndd on 2008-09-06
I wouldn't worry too much about it, its much like the Windows installer for XP so if you can handle that you can handle this.

---

### Post by kansasnoob on 2008-09-06
> Text based Installer? Sounds scary for a linux noob like myself.

Can you boot and run the live CD environment?

---

### Post by deb_untu on 2008-09-06
> **juanfran27 said:**
> No, i'm not booting from the OS. I restarted the PC. When the Dell screen appeared, I pressed f12 (indicated in top right corner) to go to boot options. I chose the CD/DVD drive, with the CD in. The "Start screen" for the Ubuntu CD was shown, I had several options, such as trying with Live CD and installing the OS. I chose to Install the OS. The Kernel loaded and then the screen went blank. I let it sit there for a while but nothing would happen.

could you see the cursor blinking ?

---

### Post by kansasnoob on 2008-09-06
> When the Dell screen appeared, I pressed f12 (indicated in top right corner) to go to boot options. I chose the CD/DVD drive, with the CD in. The "Start screen" for the Ubuntu CD was shown, I had several options, such as trying with Live CD and installing the OS.

Have you tried "trying with Live CD"?

Honestly you're making it impossible to help you!

---

### Post by Bucky Ball on 2008-09-06
As was mentioned, the alternate install cd is easy if you can install windows. Same as the Ubuntu Live or desktop version, just without the disco colours! \\:D/

---

### Post by juanfran27 on 2008-09-06
> **kansasnoob said:**
> Can you boot and run the live CD environment?

No.

> **deb_untu said:**
> could you see the cursor blinking ?

Yes.

> **kansasnoob said:**
> Have you tried "trying with Live CD"?

Honestly you're making it impossible to help you!

Yes, and it won't load. 
Sorry, it is not my intention.

> **Bucky Ball said:**
> As was mentioned, the alternate install cd is easy if you can install windows. Same as the Ubuntu Live or desktop version, just without the disco colours! \\:D/

I will try it. I just downloaded the alternate install.

---

### Post by deb_untu on 2008-09-08
> **juanfran27 said:**
> No.



Yes.



Yes, and it won't load. 
Sorry, it is not my intention.



I will try it. I just downloaded the alternate install.

Try this:
press F6 key on install screen and add [COLOR="Red"]_vga=771 or 773_[/COLOR] as additional option.


I had this problem,so it might work for you too.

---

### Post by technotitclan on 2008-09-08
how old is the sys, your cd drive could be dieing. try a windows install cd and see if it does the same thing

---

### Post by juanfran27 on 2008-09-08
SOLVED. For reasons I do not know, the image was not burned correctly on the CD. I repeated it at x8 and it worked. I'm runnning Hardy since last night.

---

### Post by Bucky Ball on 2008-09-08
Excellent news, juanfran27. Thought it must be something like that, or as mentioned in a previous post, a hardware issue. Could you go to 'Thread Tools' and mark this thread as solved so others may reference it.

Enjoy! And don't forget to post if you have anymore probs. \\:D/

---

