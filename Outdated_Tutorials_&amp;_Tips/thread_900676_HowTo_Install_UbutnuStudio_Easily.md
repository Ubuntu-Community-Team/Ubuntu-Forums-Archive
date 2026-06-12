---
title: "HowTo: Install UbutnuStudio Easily"
date: 2008-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Thelasko on 2008-08-25
UbuntuStudio can be challenging to install for new users.  I have found that quite a few users have trouble installing UbuntuStudio from [the DVD]("http://ubuntustudio.org/downloads").  This is how to do an alternate installation.

**[SIZE="3"]Things you will need:[/SIZE]**
[LIST=1]
[*]Ubuntu Installation CD ([from here]("http://www.ubuntu.com/getubuntu/download"))
[*]Internet connection (wired broadband preferred)
[*]A computer
[/LIST]

**[SIZE="3"]Instructions[/SIZE]**
[LIST=1]
[*][Install Ubuntu]("https://help.ubuntu.com/community/GraphicalInstall") the normal way.  If that doesn't work, use the [alternate install method.]("https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD")
[*]Once you have finished installing Ubuntu, make sure your machine works properly.  Reboot the machine to make sure you can login, check your [screen resolution]("https://help.ubuntu.com/community/Video"), and most importantly **make sure your [network card]("https://help.ubuntu.com/community/NetworkDevices") works, and that you can connect to the internet.**  You are using the standard version of Ubuntu, so all of the standard documentation applies.
[*]Once your machine is configured properly, you can begin installing Ubuntu Studio.  To do this in Hardy Heron, open the terminal (applications>accessories>terminal) and enter:
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```
Ubuntu will begin downloading all of the packages for UbuntuStudio.  This will take quite a bit of time even on a high speed connection.  Once the packages are downloaded, they will be installed automatically.  For instructions on other versions of Ubuntu [look here]("https://help.ubuntu.com/community/UbuntuStudio/Installation").
[*]Reboot your machine and your installation should be complete.
[/LIST]

This same method can be used for installing UbuntuStudio 64-bit.  However, in step 1 you should install the 64-bit version of Ubuntu.

If you think UbuntuStudio should be easier to install, vote for [my idea on Ubuntu Brainstorm.]("http://brainstorm.ubuntu.com/idea/11864/")

---

### Post by Mariane on 2008-10-16
You shouldn't have to reboot. That a windish thing. 

Mariane

---

### Post by snowpine on 2008-10-16
> **Mariane said:**
> You shouldn't have to reboot. That a windish thing. 

Mariane

How do you switch kernels without rebooting?

Thanks for the tutorial Thelasko!

---

### Post by MWSTX on 2008-10-17
I just upgraded an ubuntu installation from hardy to intrepid (beta).  If I now follow your install sequence will I end up with ubustu intrepid beta or will it still pull hardy off the repository?  I need intrepid to make my usb modem work.

---

### Post by Thelasko on 2008-10-17
> **MWSTX said:**
> I just upgraded an ubuntu installation from hardy to intrepid (beta).  If I now follow your install sequence will I end up with ubustu intrepid beta or will it still pull hardy off the repository?  I need intrepid to make my usb modem work.
All of the necessary packages appear to be in the repositories for Intrepid, so I can't see any reason why it won't work.  You can search the repositories yourself from [here.]("http://packages.ubuntu.com/")

---

### Post by camoanimal on 2008-10-24
WOW, this is a great idea.  I wanted to install UbuntuStudio, but I don't have a DVD burner, or external HDD, so this would allow me to install it after all!  YAY!

---

### Post by Th3Professor on 2008-11-22
One exception to using the real time kernel could be if running either a quad-core cpu and/or a RAID-type set-up. I forget which (or if both, either, etc.)... though I just heard that through word of mouth via the 64 Studio crowd.

So far, I've had no bad luck with running generic kernel under ubustu (64-bit). I do get the silly message when opening Rosegarden or similar apps, though thus far the gen kern makes no difference in performance. (Running a fairly fast 64-bit quad-core with 4gb ram, raid5+lvm (storage drives) and more stuff, I forget, but that's a basic idea.)

edit:
no noticeable difference with gen kern.

---

### Post by Thelasko on 2008-11-24
> **Th3Professor said:**
> One exception to using the real time kernel could be if running either a quad-core cpu and/or a RAID-type set-up. I forget which (or if both, either, etc.)... though I just heard that through word of mouth via the 64 Studio crowd.

So far, I've had no bad luck with running generic kernel under ubustu (64-bit). I do get the silly message when opening Rosegarden or similar apps, though thus far the gen kern makes no difference in performance. (Running a fairly fast 64-bit quad-core with 4gb ram, raid5+lvm (storage drives) and more stuff, I forget, but that's a basic idea.)

edit:
no noticeable difference with gen kern.
Yes, with this method, you don't have to install the real time kernel "Linux-rt" unless you want to.  I don't think the real time kernel will make a big difference for most people with modern machines.  On older machines there may be a difference.  I've heard stories of people having a keyboard and mouse lag on older machines with the real time kernel, because of the real time kernel's different ways of prioritizing input/output.

---

### Post by Th3Professor on 2008-11-25
> **Thelasko said:**
> Yes, with this method, you don't have to install the real time kernel "Linux-rt" unless you want to.  I don't think the real time kernel will make a big difference for most people with modern machines.  On older machines there may be a difference.  I've heard stories of people having a keyboard and mouse lag on older machines with the real time kernel, because of the real time kernel's different ways of prioritizing input/output.

Wow! That's interesting. :) Lagging mouse and keyboard... nuts. :)

---

### Post by Thelasko on 2008-11-26
> **Th3Professor said:**
> Wow! That's interesting. :) Lagging mouse and keyboard... nuts. :)

This is what I hear.  It's not all too common though.

---

### Post by Fstop on 2008-12-07
Excellent guide. I had to do this for my roommate's computer tonight. The ubustu alternate install cd seems to often have trouble. I was getting lockups when choosing the default language, so we just went with straight Ubuntu and installed the packages. :)

---

### Post by crazyness003 on 2008-12-07
I first installed ubustu gutsy using the alternate dvd. Then i found out you can do it in a regular install then just add the packages. Now I always use regular installs with upgrading to ubustu packages.
The -rt kernel is not that cool (only if you use lots of midi authoring ans synthesizing). I had much problems bavk in the day when i coulnt get my rieless to work (the -rt development is a step behind the -generic one).

Now, i think Ubustu Intrepid ships with the -generic kernel anyway. Not sure tho.

---

### Post by gogitosbanditos on 2009-02-21
```

Get:281 http://ru.archive.ubuntu.com intrepid/universe vgrabbj 0.9.6-3 [55.2kB]                                                                           
Get:282 http://ru.archive.ubuntu.com intrepid/universe csound-gui 1:5.08.0.dfsg2-8 [277kB]                                                                   
Get:283 http://ru.archive.ubuntu.com intrepid/universe csound-utils 1:5.08.0.dfsg2-8 [38.8kB]                                                                
99% [Working]                                                                                                                                                
99% [Working]
99% [Working]
99% [Working]
99% [Working]
99% [Working]
99% [Working]

```

That's what I have now...

Is it a bug or anything?

Can I close the terminal window?
Will it fix automatically?

:(:(:(

I am really worried help please

---

### Post by gogitosbanditos on 2009-02-21
I closed terminal and entered it again.
Everything's fixed now.

Don't worry.

---

### Post by crazyness003 on 2009-02-21
> **gogitosbanditos said:**
> I closed terminal and entered it again.
Everything's fixed now.

Don't worry.
thats good.

---

### Post by gogitosbanditos on 2009-02-21
But... What difference does -rt kernel make?

Can you work with MIDI on generic one? Or it is no possibility to work with it on generic at all? What is better to use - new or old?
[i][b]
note:
I have an Acer Extensa 5220 laptop , if it helps ;)
[/i][/b]

---

### Post by crazyness003 on 2009-02-22
to be honest, I dont think there's any benefit to using -rt. -generic will work with midis.
-rt was supposed to do memory interrupts in a fashion that would give cycle-critical code better resource management. But nowa days, processors (esp. multi-core)  do that automatically. SO the only reason why you'd want the -rt is to support it. Otherwise, there's no difference, except the release schedule.

your call

---

### Post by xyppy on 2009-11-05
This method worked in 9.10.  I just installed UbuStu with no problems.

---

### Post by Thelasko on 2009-11-08
> **xyppy said:**
> This method worked in 9.10.  I just installed UbuStu with no problems.

Good to know, Thanks!

---

