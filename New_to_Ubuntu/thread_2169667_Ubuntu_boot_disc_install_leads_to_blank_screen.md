---
title: "Ubuntu boot disc install leads to blank screen"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by JarekErvin on 2013-08-23
Hey all,

I'm having what looks like a fairly common problem, but the roadblocks I've encountered are making me wonder if my problem is a bit different from others.

I'm trying to install Ubuntu from a usb stick to a Asus laptop, and have constantly arrived at a blank black screen before I'm able to launch the application. I'm using an Asus K55N-SA80403V 15.6" Laptop with an AMD A8-4500M Quad-Core 1.9Ghz processor, 4GB ram, AMD Radeon Mobility HD 7640G, and a HD LED backlit display.

I've tried a number of different boot disks, including 12.04, 13.04, and 12.04 alternate, all of which have arrived at the same problem. Each time I boot from the disk, I'm taken to the GNU GRUB menu which offers a number of options. No matter which one I choose ("Try Ubuntu," "Install Ubuntu," etc.), the screen instantly goes blank. Note: unlike other users, my screen does not simply dim or show a blinking or solid dash; it simply goes completely black and remains there as long as I've waited (up to 20 min).

In searching through previous forum posts, I've come across a number of solutions. Many suggest editing the startup options within the boot menu, most often adding the term “nomodeset” somewhere in the chain. I've done this a number of times, each time to no avail. One thing that seems important about this is that when many of the commands people suggesting one might add it to do not appear when I attempt to edit the commands before booting (I've linked a picture of what I see at the bottom). Many other solutions suggest editing or downloading files using the sudo command, but the command-line in my grub menu doesn't recognize the *sudo* command.

Sorry if this overlaps with other posts, but so far, I've had no luck with any other proposed suggestion. I would greatly appreciate anyone offering a suggestion, or pointing me to another post in the event that I *have* missed something relevant.

Thanks in advance!

J

[IMG]http://i44.tinypic.com/70hp20.jpg[/IMG]

---

### Post by su:bhatta on 2013-08-23
Ok, I will try and give you two ways, you have to follow 1 and if it does not work try the other and see where you end up! Please post the results too. I am Using AMD A4, with Radeon 6760, hence I guess this will work out!

**1)** In the screenshot you have uploaded, the 3rd line from top reads like this**:" iet splash --"**, take the cursor there beside** "--"** use the arrow keys to do that, and **delete those two "--"** or hyphens using "backspace" & add the word "**nomodeset**" without quotes, and hit F10 or "enter" to boot!

**This is the second way**:
On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen:

1)At that screen you hit **Enter**...
it gives you a next screen where by default you will get a list of languages with English selected as default..

2)on that screen select English/or what you want---> hit enter... It will get you the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen you will see options underneath F1 F2 F3 etc.. ... **Hit F6** on that screen.. 
You will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 

Also, You might as well try with 13.04, which is the latest stable Ubuntu available !

BTW, All 'nomodeset' does is, it stops installing the video drivers at the beginning...
Since you r using AMD, you may have to download proprietary drivers(Once  installed) to get the right screen resolution & all.... 

Best of Luck, and do let know how it turns up!

---

### Post by JarekErvin on 2013-08-24
Bhatta,

Many thanks for the reply!

 I had tried the solution you suggested for the USB stick. But using a DVD did the trick. I'm glad the problem is fixed, but it turned out to be more simple than I thought.

Thanks again!

Jarek

---

### Post by su:bhatta on 2013-08-24
Glad it worked out, no problem Ervin! Welcome to Ubuntu!

---

