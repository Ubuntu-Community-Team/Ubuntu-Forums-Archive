---
title: "How do I change the bootsplash/login screen?"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by tkabir11 on 2012-01-20
For a while I've been getting tired of the same Kubuntu screen and login screen that comes up during log-in; so I was looking for ways to change/customize it. So far I've only managed to get and install a splash screen (which is basically an animated wallpaper- the screen that shows up just after I put log-in details) using the splash screen manager in Kubuntu. But when I try to do the same thing using the Login manager- I get nothing. I choose a login theme- install it- but it never shows up in the list of login themes in the manager. :confused:
For changing the bootsplash- I tried to follow _[THIS]("http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml")_ guide- but I couldn't find *libusplash-dev* anywhere; I still downloaded and installed Startup manager- but it only lets me change the resolution of the bootsplash screen- nothing else. 
So can anyone give me a basic how-to or point me to a guide showing how I can change/customize the bootsplash/login screen on Kubuntu 11.10? Thanks

---

### Post by Matt__ on 2012-01-20
have you tried [Ksplash](http://linux.softpedia.com/get/Desktop-Environment/Tools/KSplasherX-41167.shtml)?

---

### Post by tkabir11 on 2012-01-20
> **Matt__ said:**
> have you tried [Ksplash](http://linux.softpedia.com/get/Desktop-Environment/Tools/KSplasherX-41167.shtml)?

Cool- I'm gonna try that out :) Thanks
I also come across _[Grub Customizer]("https://launchpad.net/grub-customizer")_ so i'll be trying that too.

---

### Post by Matt__ on 2012-01-20
Grub customiser is great for cleaning up the text entries you see and organising what boots by default, I don't think it has any graphical tweaks.

For a quick and easy (Ubuntu) splash screen change I usually use [Ubuntu Tweak](http://ubuntu-tweak.com/).

---

### Post by tkabir11 on 2012-01-20
OK- apologies. I really haven't made things clear on my original post. I've tried Ksplash- but it's not really what I'm looking for. Although using it I can make my own splash screens flawlessly :)
What I really need is a way to customize the ''bootsplash''...and by that I mean the screen that comes up at the very beginning after switching the PC on- which by default contains ***a blue background with the kubuntu text, logo and dotted progress bar.*** <<< that's what I wanna change. 
Usplash, as I mentioned earlier, used to be the best and probably the only way to do this- but not anymore; since the libusplash-dev package has been removed from ubuntu. So, to rephrase my title question- all I need to know is- is there currently an alternative to Usplash??

---

### Post by kazztan0325 on 2012-01-20
[FONT=Verdana][SIZE=1]I usually use **'**[/SIZE][/FONT][FONT=Verdana][SIZE=1]**Plymouth Manager'** to change plymouth.

Please refer this web page to install it.
[/SIZE][/FONT][https://launchpad.net/~mefrio-g/+archive/plymouthmanager]("https://launchpad.net/%7Emefrio-g/+archive/plymouthmanager")
[FONT=Verdana][SIZE=1]
[/SIZE][/FONT]

---

### Post by tkabir11 on 2012-01-21
> **kazztan0325 said:**
> [FONT=Verdana][SIZE=1]I usually use **'**[/SIZE][/FONT][FONT=Verdana][SIZE=1]**Plymouth Manager'** to change plymouth.

Please refer this web page to install it.
[/SIZE][/FONT][https://launchpad.net/~mefrio-g/+archive/plymouthmanager]("https://launchpad.net/%7Emefrio-g/+archive/plymouthmanager")
[FONT=Verdana][SIZE=1]
[/SIZE][/FONT]

That's what I was looking for- but unfortunately it didn't work for me. Whatever bootsplash theme I installed, the manager wouldn't load it- instead it loaded this totally different and uglier kubuntu bootsplash theme everytime lol.
Luckily however I found *[Zorin splash screen manager]("http://zorin-os.webs.com/splashscreenmanager.htm")* while trying to solve my problem with the Plymouth manager. And that works like a charm :D Even the splashscreens that I installed from Plymouth manager are working now thru Zorin mngr :D Thanks for all your help anyways- much appreciated! There's always a way in Linux :D

---

