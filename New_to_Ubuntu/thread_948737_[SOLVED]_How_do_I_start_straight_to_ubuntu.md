---
title: "[SOLVED] How do I start straight to ubuntu?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by CJ Master on 2008-10-15
Hello, =]

I was wondering if there was any way to boot straight to ubuntu without uninstalling windows? Because I love ubuntu, but I need to keep windows installed for various reasons.

Currently when I turn on the computer, it'll show a menu on what operating systems I have, and if I don't select one It'll automatically boot to windows in 10 seconds.

So is there any way to make it boot straight to ubuntu without that screen?

**PLEASE NOTE: If you show me a way to do this, please also show me a way to get that selection screen back, not much use having windows installed if i can't get to it!!**

---

### Post by SunnyRabbiera on 2008-10-15
Not a good idea, you are better off with your current boot menu as short cutting around this sort of thing can mess your system up.

---

### Post by Duck2006 on 2008-10-15
You could try startup-manager for your repo's to manage your boot order.

---

### Post by LowSky on 2008-10-15
+1 I totally agree with SunnyRabbiera, don't mess with it.

but ther is a way to change it with a program caled Start-up manager. It can change the timer, change the default boot, and a few other things, JUST BE CAREFUL

---

### Post by Bufke on 2008-10-15
If you're using grub and not the windows boot loader that gets used in wubi do this.

Just make that timer smaller so it's less annoying.  In a console type
```
sudo nano /boot/menu/grub.lst
```

Look for where it says timeout 10 and set it to a lower number.

---

### Post by drs305 on 2008-10-15
> **CJ Master said:**
> Hello, =]

I was wondering if there was any way to boot straight to ubuntu without uninstalling windows? Because I love ubuntu, but I need to keep windows installed for various reasons.

Currently when I turn on the computer, it'll show a menu on what operating systems I have, and if I don't select one It'll automatically boot to windows in 10 seconds.

So is there any way to make it boot straight to ubuntu without that screen?

**PLEASE NOTE: If you show me a way to do this, please also show me a way to get that selection screen back, not much use having windows installed if i can't get to it!!**

Yes, you can do this. The easiest way to do it without having to manually edit grub's menu.lst is to install and use StartUp-Manager, a gui based app.

Install StartUp-Manager:
```
sudo apt-get install startupmanager
```
Start it:
Systems, Administration, StartUp-Manager.

At this point, on the Boot Options tab, you can set the Default Operating System to your ubuntu kernel. In the 'Timeout' window, you can set the time to something other than '10' (the default). Here I will agree with SunnyRabbiera in that you may not want to boot directly into Ubuntu. Rather, I would suggest setting the timeout to 1 or 2 seconds.

Having made these changes, the grub menu will display for a very brief time and then continue to boot to ubuntu. You probably would not even notice the menu unless you were looking.

The reason to display it for a second or two is if you want to get into Windows or Recovery Mode. When the menu displays, hit ESC to pause the menu and allow you to make a different selection.

You *can* set the timeout to 0 and still gain access if you need to, your timing just needs to be a bit better. If there is no display, wait until you here your computer's BIOS beep during boot. Immediately afterward, start hitting the ESC key until the grub menu appears. Then make your selection.

StartUp-Manager can tweak a lot of boot settings. See the link in my signature line for a tutorial on it.

---

### Post by jerome1232 on 2008-10-15
edit: Beaten to it :)

Yes you definitly can, you just need to edit menu.lst properly or use startup manger to change it for you. You can select which OS it defualts to and you can make it have a quicker time out, or make it to where it boots in 3 seconds to Ubuntu unless you press escape etc...

Just be careful with what changes you make and ask quetions if you are unsure.

```
sudo apt-get install startupmanager
```

---

### Post by haydnc on 2008-10-15
Edit: Wow - so totally beaten to it - by so many people. There's your answer then. Startup Manager if you used Wubi to install or edit Grub if you used Ubuntu to install.

It would probably depend on how you installed Ubuntu.

If you installed Ubuntu it would have installed Grub to give you the boot menu with the choices of Ubuntu or Windows to chose from. It's easy enough to edit the Grub boot menu to select a different OS as the default one to load.

On the other hand, if you installed Ubuntu from inside Windows using Wubi you'll need to edit the bootloader that setup uses instead. I do have a copy of Ubuntu installed this way, but unfortunately I've never looked into how to alter the boot order.

If you could let us know how you installed Ubuntu in the first place and we'll see if someone here can post instructions for editing your boot order so Ubuntu comes first.

---

### Post by CJ Master on 2008-10-15
Hi,

Wow, thanks for all the replies! One question, out of all of these which one do I choose to start up as?

Ubuntu Intrepid (development branch) kernal 2.6.27-7-generic
Ubuntu Intrepid (development branch) kernal 2.6.27-7-generic (recovery mode)
Ubuntu Intrepid (development branch) kernal 2.6.24-19-generic
Ubuntu Intrepid (development branch) kernal 2.6.24-19-generic (recovery mode)
Ubuntu Intrepid (development branch) memtest 86+

Edit: Btw I'm beta testing the new version, and I'm using 64-bit ubuntu incase you needed to know.

---

### Post by jerome1232 on 2008-10-15
> **CJ Master said:**
> Hi,

Wow, thanks for all the replies! One question, out of all of these which one do I choose to start up as?

[COLOR="Red"]Ubuntu Intrepid (development branch) kernal 2.6.27-7-generic[/COLOR]
Ubuntu Intrepid (development branch) kernal 2.6.27-7-generic (recovery mode)
Ubuntu Intrepid (development branch) kernal 2.6.24-19-generic
Ubuntu Intrepid (development branch) kernal 2.6.24-19-generic (recovery mode)
Ubuntu Intrepid (development branch) memtest 86+

Edit: Btw I'm beta testing the new version, and I'm using 64-bit ubuntu incase you needed to know.

The one in red, btw it's kernel ;) not kernal

---

### Post by CJ Master on 2008-10-15
Ahaha. whoops. *blush*

Well thanks! I'm going to try it right now. =]

---

### Post by CJ Master on 2008-10-15
Well um.

Well first off I guess I won half of the battle. There's no longer that annoying "Press ESC to go back to the menu..."

But when I first tried it, it made me go to this command prompt. I had no idea how to do any of that stuff, so I rebooted the computer and tried again, and I guess it works now.

HOWEVER!

It still automatically highlights windows on the screen, and it won't boot straight into ubuntu.

---

### Post by Therion on 2008-10-15
Using Startup Manager, click the box for "Use Timeout in Bootloader Menu".
Set the "Timeout in Seconds" box to whatever you want.
Set "Default Operating System" from the dropdown menu to Ubuntu.

Free Bonus:  [Explanatory Screenshots!!!](http://tombuntu.com/index.php/2007/07/18/configure-grub-and-usplash-with-startup-manager/)

---

### Post by drs305 on 2008-10-15
> **CJ Master said:**
> HOWEVER!

It still automatically highlights windows on the screen, and it won't boot straight into ubuntu.

You have to change the default operating system to the correct kernel in the Boot Options tab of StartUp-Manager.

---

### Post by jerome1232 on 2008-10-15
This is a screenshot of my configuration in startupmanger and Mine is set to not display that list, and boot straight into Ubuntu. Of course since you are using interpid your kernels will be listed with different numbers and etc...

---

### Post by crjackson on 2008-10-15
> **CJ Master said:**
> Well um.

Well first off I guess I won half of the battle. There's no longer that annoying "Press ESC to go back to the menu..."

But when I first tried it, it made me go to this command prompt. I had no idea how to do any of that stuff, so I rebooted the computer and tried again, and I guess it works now.

HOWEVER!

It still automatically highlights windows on the screen, and it won't boot straight into ubuntu.

Did you make the modification using start-up manager as suggested? That is what you need. If yes then look through the tabs and options. You will find an option with a drop down box that lets you select your default booting OS. You can make the desired changes there.

If you didn't install start-up manager, go to your software soruces (look in your admin menu) and enable the multiverse and universe repositories. Once it's done reloading, close that and open up synaptic package manager (look in your admin menu). Do a search for startup manager. Install it and make the desired changes.

---

### Post by Commander_Keen on 2008-10-15
> **CJ Master said:**
> Hello, =]

I was wondering if there was any way to boot straight to ubuntu without uninstalling windows? Because I love ubuntu, but I need to keep windows installed for various reasons.

]
Question:
  Why couldn't the user edit Grub to do the following; Ie revers the lines in Grub, so it would say something like 

Line one :  Boot into Ubunto
Line two :  Boot into XP
Line 3: Time limit 5

---

### Post by jerome1232 on 2008-10-15
He could, it's just easier to use startupmanager.

---

### Post by drs305 on 2008-10-15
> **Commander_Keen said:**
> Question:
  Why couldn't the user edit Grub to do the following; Ie revers the lines in Grub, so it would say something like 

Line one :  Boot into Ubunto
Line two :  Boot into XP
Line 3: Time limit 5

He could, but there are other settings in menu.lst that would come into play. For instance, the first line isn't necessarily the one that is the default. If you start counting titles, of course, you have to start with 0 instead of 1 to determine what goes on the "default 0" line. 

If you say he could just put the desired system at the same relative position as the current choice, that may not work either as another grub setting may be set to use the last system booted (saved).

There is nothing wrong with manually editing menu.lst and for those who do it regularly it is easy and maybe even a bit faster. However, for a new user, my opinion is to let him/her either use StartUp-Manager on his own or post the menu.lst to allow more experienced users take a look at all the settings.

There are lots of ways to do things. Sometimes for helping one way is just easier to explain than others.

---

### Post by CJ Master on 2008-10-15
I looked all over, is there anything here I didn't set up right?

Ok picture works now.

---

### Post by drs305 on 2008-10-15
Tick the "show bootloader menu" and you should be all set - seeing the menu for 3 seconds before continuing. Even without this ticked, it should have booted to your ubuntu kernel.

---

### Post by CJ Master on 2008-10-15
I tried it... didn't work. =[

Oh I just remembered, I installed ubuntu from inside windows if that makes a diffrence.

---

### Post by jerome1232 on 2008-10-15
It does :)  wubi doesn't use grub 

It is actually using the windows boot manager and that's a very different process. Give me a moment to find it in the wubi wiki.

AND here it is [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?)

---

### Post by peterthecyclist on 2008-10-15
> **CJ Master said:**
> Hello, =]

I was wondering if there was any way to boot straight to ubuntu without uninstalling windows? Because I love ubuntu, but I need to keep windows installed for various reasons.

Currently when I turn on the computer, it'll show a menu on what operating systems I have, and if I don't select one It'll automatically boot to windows in 10 seconds.

So is there any way to make it boot straight to ubuntu without that screen?

**PLEASE NOTE: If you show me a way to do this, please also show me a way to get that selection screen back, not much use having windows installed if i can't get to it!!**

I tried Ubuntu,on a partitioned disk, win XP became unavailable.        a bit frustrated, but backed up. I now have two drives, Ubuntu second. I have a boot menu now that defaults to Ubuntu ,
 or XP by choice

---

### Post by mwalimu54 on 2008-10-15
Hey, welcome to the forums, Peterthecyclist.  You'll find this a great place to get help and kill time.

---

### Post by CJ Master on 2008-10-15
Thank you very much jerome!! That completely solved my problem. =]

---

