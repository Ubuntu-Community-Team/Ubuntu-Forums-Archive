---
title: "[SOLVED] Ok, I've have VirtualBox runnin XP.... now what?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by surelock22 on 2008-11-03
Ok, after 4 days of Ubuntu, I got VirtualBox to run my XP disc install lickity split.

Looks like crap and none of the drivers are up and running.

I need Win XP to AT LEAST connect to the internet, so I tried turning on the network adapter in VirtualBox and I can't get it to connect to the net.

I would also like it to at least look nice too. Do I have to run the same Nvidia Drivers I had on there before when it was windows only?

Tips people, I'm looking for some tips.

Thanks in advance. I'll check back tomorrow.  

Night.

---

### Post by nhasian on 2008-11-03
install the guest additions.  that should get your network working, video and mouse working better.

---

### Post by stinger30au on 2008-11-04
in your config for virtual box set the ethernet connection to NAT and it will connect to the net

---

### Post by SunnyRabbiera on 2008-11-04
Just dont expect many miracles as VBox doesnt deliver compositing that much, its a limitation on how a VM works

---

### Post by ewinslow on 2008-11-04
I found this [article]("http://www.linux.com/feature/148194") very helpful for using VirtualBox.

Those guest additions work great.

---

### Post by surelock22 on 2008-11-04
I now have the network working...

I also have sound...

(and due to both, I can now LISTEN TO MY FAVORITE MORNING RADIO SHOW'S STREAM!!!)

It still looks like poop though. For instance, I have a Vizio 32" WS LCD HDTV as my monitor, and I cannot get my resolution correct through Windows' display properties.

Do I need to install Nvidia drivers or did I read it correctly that VB does not allow for drivers other than what's on the VM's list of devices?

I'm happy I have the radio show for now, BUT I WANT MORE!!! MWAHAHAHAHA!!!

(ok, i'm done, and again, thank you for giving me the previous advice)

---

### Post by surelock22 on 2008-11-04
> **SunnyRabbiera said:**
> Just dont expect many miracles as VBox doesnt deliver compositing that much, its a limitation on how a VM works

What would you consider a "miracle" anyways?

I want to be able to game with my GeForce 6800 XT enabled PC, and Window obviously has the most games. I assumed that VM would allow for this. I also wanted to be able to run IE for sites that ABSOLUTELY NEED IE TO RUN IT (with my experience, it's been alot of radio station's streams. even when i was all windows, when running FireFox I would have to set it to IE mode to get the pages to work). I also want to have the ability to run FL Studio and my kitchen design software - 20 / 20 Kitchen Design.

Are any of these things miracles?

I've seen video of people doing exactly the

---

### Post by phr0ze on 2008-11-04
Gaming would be a miracle. Virtual Box is not a way to game unless you love minesweeper. Right now you have 3 options to game: Wine, Dual Boot, or Linux games.

All the other stuff is perfect with virtual box. I use virtual box to run Lightroom and Visual Studio.

You can not install nvidia drivers in virtual box. A virtual machine has virtual hardware, it's not even an nvidia card to that windows. Go into device manager and look at the type of card that it sees.

It still looks like crap? I'm not sure what you mean here, it should be pixel for pixel the same unless you streached the window or something. To make the virual box window bigger, don't streach it, right click on the windows desktop and change the resolution. A higher resolution will make the window bigger. Also make sure you have those guest additions in.

---

### Post by tomcheng76 on 2008-11-04
You just need to install the Guest additions.
Do not install nvidia driver. It is not required. It may even hurt your guest OS system.
After installing the Guest additions, the resolution of the guest XP will be updated if you resize the VM window, of coz you may try seamless mode or fullscreen mode.

---

