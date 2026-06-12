---
title: "[SOLVED] a media player to listen to the bbc"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by lyni on 2008-06-24
hi I'm very much a newbie. I installed ubuntu 8.04 yesterday. I am just getting myself used to it.
I usually listen to the bbc online either thru realplayer or media player. I have been trying to listen on ubuntu but I can't seem to listen thru either of those players and I am having trouble downloading them. can anyone help me please with a player that will let me listen to the bbc? thank you.
lyni

---

### Post by timcredible on 2008-06-24
i've read you need realplayer.  do a search on realplayer and bbc and you should find a good how-to.

---

### Post by munkyboy on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=782774](http://ubuntuforums.org/showthread.php?t=782774)

That thread has details on how to install real player

---

### Post by HereInOz on 2008-06-24
You could try helix player, or if you go to the Real Player site, there is a linux version there.

[http://www.real.com/linux](http://www.real.com/linux)

Download it and save it to your desktop.

You will need to install it using the terminal.  Open a terminal and type:

cd Desktop  (note, the Linux command line is Case Sensitive)

then type:

sudo ./name_of_file_you_downloaded

That should run the install process.

See how you go installing it, and if you need more help post back here.

---

### Post by the_doc on 2008-06-24
I lifted this from another site and it worked ok for me.

> 1. Download the RealPlayer11GOLD from [http://www.real.com/linux](http://www.real.com/linux) to your home directory.
2. Open Terminal (from this point on, you must have admin rights).
3. Type sudo chmod +x RealPlayer11GOLD.bin
4. Type sudo "./RealPlayer11GOLD.bin"
5. Follow prompts. It'll start the installer. Do as it instructs and hit Enter.
6. It'll ask for the install path. Default is fine and hit enter.
7. It'll ask for a confirmation of install path. Press F to Finish the install.
8. It copies files, installs icons, etc. When you get the prompt, it's done.

Congrats! You have just installed RealPlayer 11 on Ubuntu. Easy, huh? ;)
To launch the app, go to Applications > Sound & Video > RealPlayer 11.

---

### Post by munkyboy on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=782774](http://ubuntuforums.org/showthread.php?t=782774)

That thread has details on how to install real player

---

### Post by vambo on 2008-06-24
I can heartily recommend mplayer, with restricted codecs installed (win32 or 64codec depending on your installation). With this there is just about nothing mplayer can't handle.

---

### Post by lyni on 2008-06-24
thank you all for your quick responses. I don't understand what a terminal is and how I'm to open it to install the linux version of real player. I have downloaded it to my desktop but I don't understand what to do from there. any step by step instructions would be very much appreciated. thank again.
lyni

---

### Post by philinux on 2008-06-24
To be honest you're better following this really good guide.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by the_doc on 2008-06-24
> **lyni said:**
> thank you all for your quick responses. I don't understand what a terminal is and how I'm to open it to install the linux version of real player. I have downloaded it to my desktop but I don't understand what to do from there. any step by step instructions would be very much appreciated. thank again.
lyni

[B]In gnome:

Applications > Accessories > Terminal

cd ~/Dektop[/B]

Continue from step 3 of my previous post.

---

### Post by lyni on 2008-06-24
thanks again everybody. thanks for those links as well. I'm going to have to really try to understand them before I try any of those commands. I didn't realise it was going to be so difficult to install something. 
lyni

---

### Post by the_doc on 2008-06-24
With the steps I posted I installed it in under one minute!

---

### Post by drifter2502 on 2008-06-25
I get all BBC both live and listen again with mplayer and ghecko. When installed click on `Listen Live´in BBC I player. Each channel sits on my desktop ready to load when needed. Works for me very well.

---

### Post by lyni on 2008-06-26
thanks again everyone for all your help. I finally succeeded in getting onto the bbc with mplayer. (I'm a bit slow) but hopefully I will get used to how ubuntu works.
I'm sure this won't be the last question I ask.
thanks
lyni

---

### Post by WRDN on 2008-06-26
You should also try out [VLC]("http://www.videolan.org/vlc/"), which in my opinion, is the best media player ever created.

---

