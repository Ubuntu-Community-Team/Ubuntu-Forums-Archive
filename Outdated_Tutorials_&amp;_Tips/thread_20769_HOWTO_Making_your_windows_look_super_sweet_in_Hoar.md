---
title: "HOWTO: Making your windows look super sweet in Hoary (compositing)"
date: 2005-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by arnoct on 2005-03-18
(NOTE: THIS ONLY WORKS IN HOARY, DOES NOT WORK IN WARTY. Also, since I use an nvidia card, I'm not sure how well this will work in ATI. I've put in some ATI instructions that I've read but I'm not 100% sure if they'd work.)

I've spent the last day and a half trying to get compositing working in ubuntu. This is actually an amalgamation of a bunch of guides I've found; I shouldn't be given full credit for this.

The first thing you need to do is install xcompmgr and transset. These are found in the hoary universe repositories, if you havent already done so, enable the universe repo in your /etc/apt/sources.list. Its not very hard to do this, search the forums for how to do it :p

```

sudo apt-get install xcompmgr transset

```

xcompmgr is the composite manager (the program/extension that makes things look pretty) and transset sets windows transparencies.

Now, the next thing you have to do is actually *enable* compositing. This is done via a simple edit of your /etc/X11/xorg.conf

```

sudo gedit /etc/X11/xorg.conf

```

Add the following section after the "module" section:

```

Section "Extensions"
	Option 	"Composite" "Enable"
EndSection

```

This tells xorg to enable compositing. Now, just so you know, unless you have a good video card, compositing most likely slow down xorg. Apparantly nvidia cards fare better than ati cards, since you can enable acceleration (which we'll do later) which'll actually make x use your video card for rendering. 

As I said earlier, if you have an nvidia card it'll run better. I'm assuming you've already installed the nvidia binary drivers and such, if you haven't then do so. Add the following lines to the "device" section:

```

	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 

```

"RenderAccel" is actually an option you should already have if you're running an nvidia card, but I've included it incase you haven't put it in yet. I'm pretty sure this only works on nvidia cards; can someone tell me if there's an equivelant for ati?

"AllowGLXWithComposite" is a command that allows you to use OpenGL while compositing is running. Apparantly it can be buggy, though, so if you have problems you might want to disable compositing in your xorg.conf whenever you want to use opengl (just comment out the compositing option with #)

Now, if you have an ati card, add these lines instead:

```

        Option          "backingstore"              "true"
	Option 		"AllowGLXWithComposite" "true" 

```

According to a cached google page, backingstore is "used to enable the server's support for backing store, a mechanism by which pixel data for occluded window regions is remembered by the server thereby alleviating the need to send expose events to X clients when the data needs to be redisplayed."

(Since I don't own an ati card, I apologize if any of my facts are incorrect. If someone with an ati card can correct me, I'll make sure to update this.)

OK, now for the really fun part. We're going to actually set it so compositing is enabled when you start GNOME. Go to system -> preference -> sessions. Go to startup programs, and click "add."

Now, before I continue, I'm going to explain a few of xcompmgr's options:

-c : enable shadows
-s : enable simple shadows
-fF : enable fadeins/fadeouts

You can mix-and-match those commands. For example, if you want just shadows, use xcompmgr -c. If you want simple shadows, use xcompmgr -s. If you want to enable shadows and fadeins, use xcompmgr -cfF. I wouldn't recommend using -cs; that'll probably break the program.

So, where it asks you for the command, enter xcompmgr and then the argument. For example, if you'd like to enable shadows and fadeins/fadeouts, you'd enter:

```

xcompmgr -cfF

```

Finally, in the order, change it to 0. This'll make sure it's the first thing that GNOME runs. Apparantly things run much better this way.

Alright! Now you can restart X (ctrl+alt+backspace), log back in, and you should have compositing running!

**Using Transset**

This is just an extra little command. If you want to set certain windows as transparent, then run the command "transset" in the console. Your mouse will turn into a crosshair; simply click on the window you want to set as transparent. The transparency value can be anywhere from 0 (completely transparent) to 1 (opaque.) It defaults to .75, and back to 1 if the window is already transparent.

For example, if you want to make a window half-transparent:

```

transset 0.5

```

Have fun!

(By the way, I'm running xcompmgr and transset half-decently on a 32mb nvidia card, but I'm only using fadein/fadeout. Your mileage may vary.)

---

### Post by flange on 2005-03-18
Thanks, arnoct.

The HOWTO worked perfectly on my system.  Performance is fine with GNOME; it's definitely useable.

One problem so far:  xcompmgr died on me for some reason a few minutes ago.  It went away gracefully; I just noticed that I was no longer getting drop shadows, so it wasn't a big deal.

Anyway, my system specs, just in case any of you are wondering about performance:

Athlon XP 2500
512MB
60GB 7200RPM 
Nvidia GF FX 5600
2.6.10-k7 kernel
nvidia 1.0.6629 driver package from apt-get

Once again, thanks for the HOWTO.  I've been anxious to try this for quite awhile.

--Sorry, I should have mentioned that I'm using "xcompmgr -cfF".  I might ditch the fading, as I wish it were a little quicker.  I don't know if this is a performance issue or a configuration issue.  I'm thinking it's the latter for me.

---

### Post by HungSquirrel on 2005-03-18
Is there a way not to make xcompmgr's shadows apply to gdesklets?  Is there a way not to make xcompmgr maximize every window over the gnome-panel?

---

### Post by dude2425 on 2005-03-18
[QUOTE=HungSquirrel]Is there a way not to make xcompmgr's shadows apply to gdesklets?  Is there a way not to make xcompmgr maximize every window over the gnome-panel?[/QUOTE]

IIRC, gdesklets has a transluecency option to use your own transparency. I don't remember, and I havent even tried it yet, but it's worth a shot maybe.

Just do a quick "killall gnome-panel" to reload the gnome panels. It should work just fine after that. Also, if you're having trouble with your terminal window not responding after you did that, then open a new one and type "killall `whatever terminal you use`"

I hope this helps a little.

---

### Post by TravisNewman on 2005-03-18
if you have xcompmgr start up at gnome login you won't have that problem.

---

### Post by arnoct on 2005-03-18
Yeah, it's a known bug that xcompmgr makes windows overlap the gnome panel, afaik the only way to fix it is to make sure it's the first thing loaded (order 0)

[edit] Oh, also, just FYI you don't need a "boss" system to run compositing: I had a few issues with shadows, but fading is working fine using the following specs:

Celeron 667
~480mb ram
4gb hdd
nVidia GeForce2 32mb
Latest 386 kernel
Latest nvidia drivers in the universe repo

---

### Post by azelter on 2005-03-19
Come on then, lets see some screen shots!

---

### Post by HungSquirrel on 2005-03-19
Pardon my ignorance: how does one load xcompmgr before the rest of Gnome?

---

### Post by Julius on 2005-03-19
[QUOTE=HungSquirrel]Pardon my ignorance: how does one load xcompmgr before the rest of Gnome?[/QUOTE]
 Order "0" will make xcompmgr load first.

This HOWTO works perfectly :P Too bad my computer is so old that I can't use those shadows, everything gets slower.

---

### Post by kingofhell on 2005-03-19
it just didnt work for me 
help pls
```
root@ubuntu:/home/tianbo # apt-get install xcompmgr transset
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transset: Depends: libxcomposite1 but it is not installable
            Depends: libxdamage1 but it is not installable
            Depends: libxfixes3 but it is not installable
  xcompmgr: Depends: libxcomposite1 but it is not installable
            Depends: libxdamage1 but it is not installable
            Depends: libxfixes3 but it is not installable
E: Broken packages
```

---

### Post by Buffalo Soldier on 2005-03-19
First, I think you have forgotten sudo and the command should be:```
**sudo** apt-get install xcompmgr transset
```

Second, have you checked your repository list? But I don't think this is related to that because all the components are in the main repository. And that is enabled by default.

Anyway, thanks arnoct. It works but I kinda don't like the look... maybe too used without shadow :p

---

### Post by kingofhell on 2005-03-19
[QUOTE=Buffalo Soldier]First, I think you have forgotten sudo and the command should be:```
**sudo** apt-get install xcompmgr transset
```

Second, have you checked your repository list? But I don't think this is related to that because all the components are in the main repository. And that is enabled by default.

Anyway, thanks arnoct. It works but I kinda don't like the look... maybe too used without shadow :p[/QUOTE]
 i did use type sudo and here's my repo list
 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe multiverse restricted 
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main universe multiverse restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 
deb-src [http://dijkstra.csh.rit.edu/~mdz/debian/](http://dijkstra.csh.rit.edu/~mdz/debian/) unstable mythtv 

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by arnoct on 2005-03-19
It's because you're running warty, you have to be running hoary for this to work.

---

### Post by Buffalo Soldier on 2005-03-19
I don't mean to alarm you, but I don't think it's a good idea to mix warty, backports and hoary repositories.

Anyway, this howto was written with Hoary in mind. Not sure whether it would work in Warty.

[quote=arnoct]NOTE: THIS ONLY WORKS IN HOARY, DOES NOT WORK IN WARTY. Also, since I use an nvidia card, I'm not sure how well this will work in ATI. I've put in some ATI instructions that I've read but I'm not 100% sure if they'd work.[/quote]

---

### Post by kingofhell on 2005-03-19
i did upgrade my dist with sudo apt-get dist-upgrade
is there any way to check whether my os is warty or hoary

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=kingofhell]i did upgrade my dist with sudo apt-get dist-upgrade
is there any way to check whether my os is warty or hoary[/QUOTE]
 If you're running Hoary, what you should see at the top panel (or taskbar as MS Windows users like to call it)=>** Applications Places System**.

And click at **System -> About Ubuntu**. It should pop up a window saying *"Welcome to Ubuntu Linux 5.04 : The Hoary Hedgehog Release."*

Guys, any other better ways for him to check this? I'm not sure this way is the best. There could be exceptions to this scenerio.

King, just out of curiosity. What made the mixed up of hoary, warty and backports in your repository list?

---

### Post by Dromio on 2005-03-19
I've been using this for about a week and it looks beautiful.  However, I've found that I cannot log out while xcompmgr is running (if I have it run as part of my session).  I have to manually kill it before logging out.

Does anyone have a way to automatically kill the process on logout?

---

### Post by arnoct on 2005-03-19
hmm, that's strange. I haven't had too many problems with logging out. All I can suggest is that you killall xcompmgr, or restart x using ctrl+alt+backspace. It's still pretty buggy, so you're bound to hit problems.

---

### Post by flange on 2005-03-19
I've had freeze ups on logging out a couple times too.  Restarting X saves it, but it's still weird.  Guess it's not quite ready for prime time.

One other thing I've noticed:  it does some funny things when used in combination with 3ddesktop.  It hasn't caused either one to crash or slow down, but you can tell neither were designed with the other program in mind.  It's a minor thing, and I'm sure things like that will be corrected over time.

---

### Post by HungSquirrel on 2005-03-19
Next question: how does one make xcompmgr not crash when xscreensaver starts?  Happens every time for me.

---

### Post by arnoct on 2005-03-19
I had that problem too. If you did the AllowGLXWithCompositing thing, then all I can suggest is that you disable xscreensaver or pick one that doesn't use OpenGL. I had many problems with XScreensaver and OGL, and the best thing I could think of was just setting it to be a blank screen.

I should probably put a note somewhere, reminding people that this is still very very early in development and probably won't work very well :p

---

### Post by bman08 on 2005-03-19
Man!  That's about a million times cooler than I thought it would be.  Thanks!

---

### Post by mayco on 2005-03-19
[QUOTE=Dromio]I've been using this for about a week and it looks beautiful.  However, I've found that I cannot log out while xcompmgr is running (if I have it run as part of my session).  I have to manually kill it before logging out.

Does anyone have a way to automatically kill the process on logout?[/QUOTE]
Just press enter after you clicked logout, the dialog is just hidden, but it is focused :)

---

### Post by ACK!! on 2005-03-19
[QUOTE=mayco]Just press enter after you clicked logout, the dialog is just hidden, but it is focused :)[/QUOTE]


Eeeew that is annoying I turned off the default xcompmgr -c because of this.  

The fade stuff was cool but made my box seem slow as heck and the simple option just kind of looked fugly.  

Anyone got any idea how long before this handles logout dialog boxes?  Or performs the cool tricks without a huge drag on the ui?

I am running this on a fairly slick laptop with like 512MB.  Frankly, gnome running with that much memory is as faster if not faster than XP on the same box.  I am getting too used to the good performance to give it up.  

Btw, looking forward to the memory optimizations in gnome 2.12.  Gnome seems very memory dependant in relation to its performance/speed feel.

---

### Post by panabar on 2005-03-19
Thank you for this howto
I'm using only shadows with my laptop with ati mobility 7500 and they work great and they are great. :)

Fade in/fade out seems to use a lot of cpu power (I can see cpu scaling up while fade in and fade out of gnome menus) so I disabled them.

---

### Post by blinksilver on 2005-03-20
how do you set it to 0

---

### Post by arnoct on 2005-03-20
If it's laggy, guys, it's probably a misconfiguration with your video card. I'm running on a celeron 667 with no lag at all. Make sure acceleration is on, and like I said, it might not work well with ATI cards.

---

### Post by jdodson on 2005-03-20
after i installed it it worked and all.  however my glxgears performance took a 300fps hit.  i really don't want that kind of overhead when i play a game.  it was pretty cool though.

---

### Post by digby on 2005-03-20
So I've run into a small hitch trying to get this to work.  I'm on a clean install of Hoary, and I installed the nVidia 7167 driver according to the instructions in [this]("http://www.ubuntuforums.org/showthread.php?t=21111") HowTo.  

I made sure that I followed the instructions to the letter.  (I used -cfF for shadows and fading.)  When I restarded X, the Gnome splash screen came up and had a lovely shadow.  The background turned grey (from the usual brown) and the splash started to fade away.  Before it finished fading it just stopped.  My mouse cursor would still move, but nothing else would respond.  

I couldn't kill X with Ctrl+Alt+Backspace, and I couldn't switch to a virtual terminal with Ctrl+Alt+F1.  I had to do a hard reset and decided to try it one more time.  This time the splash faded away completely, but it then locked up the same as before.

That's the only user account I have, so I can't log into Gnome at all.  Any ideas?

XP 2500+
nVidia GF4 Ti4600
nVidia driver version 7167
Ubuntu Hoary 5.04 / Gnome 2.10 - still all default settings except for the new kernal for the glx driver (2.6.10)

---

### Post by Cybermagellan on 2005-03-21
[QUOTE=digby]So I've run into a small hitch trying to get this to work.  I'm on a clean install of Hoary, and I installed the nVidia 7167 driver according to the instructions in [this]("http://www.ubuntuforums.org/showthread.php?t=21111") HowTo.  

I made sure that I followed the instructions to the letter.  (I used -cfF for shadows and fading.)  When I restarded X, the Gnome splash screen came up and had a lovely shadow.  The background turned grey (from the usual brown) and the splash started to fade away.  Before it finished fading it just stopped.  My mouse cursor would still move, but nothing else would respond.  

I couldn't kill X with Ctrl+Alt+Backspace, and I couldn't switch to a virtual terminal with Ctrl+Alt+F1.  I had to do a hard reset and decided to try it one more time.  This time the splash faded away completely, but it then locked up the same as before.

That's the only user account I have, so I can't log into Gnome at all.  Any ideas?

XP 2500+
nVidia GF4 Ti4600
nVidia driver version 7167
Ubuntu Hoary 5.04 / Gnome 2.10 - still all default settings except for the new kernal for the glx driver (2.6.10)[/QUOTE]
 I ran across the same thing and the one thing that I found fixed it was going into Failsafe GNOME from the GUI Loader and doing a apt-get dist-upgrade after that it worked. However that was before I tried the instructions here but the same symptoms. I do have to say while it is cool. Until I can get my Nvidia card to work I am going to just wait. I had already tried it and worked like a charm however was slow on my onboard.

---

### Post by digby on 2005-03-21
How do I access the GUI loader to use the failsafe?

Edit:  Never mind.  Found it.

---

### Post by lerio on 2005-03-21
anibody tried this howto on a S3 card?

---

### Post by fackamato on 2005-03-21
I guess you guys never play any games, eh?

Since there are severe bugs with composite and opengl, games etc. I was playing around with it, sometimes x crashed, sometimes the computer hardlocked.

---

### Post by digby on 2005-03-21
So here is what I've discovered:

If I start xcompmgr from a terminal inside Gnome, it works fine with shadows ( -c ), and I can use transset to transparify (is that a word?) everything.  However, as soon as I tried to use fading ( -fF) with or without shadowing all my windows and pannels faded away and the computer locked.

Oh, I did have that rather annoying problem of my windows covering the top and bottom pannels, but I believe I saw a reference to that happening when xcompmgr wasn't the first thing started when Gnome was loading.

Unless anyone has ideas, I shall have to get my fix for eye candy another way.

---

### Post by xodeus on 2005-03-22
Somebody wanted screenshots. I've only one but it's the default ubuntu gnome with all this stuff enabled. It's so pretty.

---

### Post by zukeft on 2005-03-22
[QUOTE=xodeus]Somebody wanted screenshots. I've only one but it's the default ubuntu gnome with all this stuff enabled. It's so pretty.[/QUOTE]
 Looks pretty, um... normal. ^^'

---

### Post by ChaperonNoir on 2005-03-22
I followed the guide.

But i don't see any transparency ! Damn !

Why ?

The command transset works but .... I don't see the transparency after.

Yes my drivers work ^^

---

### Post by StacyWebb on 2005-03-22
ok it works with Gnome, but does it work with KDE? 

Plus I am getting the following error:
"No damage extension"

Any Ideas?

---

### Post by beeldings on 2005-03-22
I decided to try this out of curiosity, not really thinking it would work on my dinosaur of a computer. Well, let me tell you something, when I restarted X and once GNOME loaded, the first words out of my mouth were, "Whoa! Holy sh*t!"

I am really impressed with how this works on my system, although it does run a little slow as I am on a PII 400 MHz with 128 MB SDRAM. I'm not sure how much memory my video card has, but I do know that it is an on-board card manufactured by NVIDIA/SGS Thomson (according to the Device Manager). The model of the card is a Riva 128 and the OEM is Gateway 2000 (as this is an older Gateway PC) and the OEM product information is STB Velocity 128.

I didn't download any NVIDIA drivers, because I figured with the card being autodetected and configured by Ubuntu and all, I really wouldn't need them. If anyone can verify that by using the NVIDIA drivers, my performance would increase, let me know and I'll fetch 'em immediately.

Anyway, thanks for an awesome how-to.

---

### Post by digby on 2005-03-22
[QUOTE=ChaperonNoir]I followed the guide.

But i don't see any transparency ! Damn !

Why ?

The command transset works but .... I don't see the transparency after.

Yes my drivers work ^^[/QUOTE]
 Xcompmgr has to be running before you use transset.  After that, the procedure that I used was to open a terminal, enter the transset command, and then click on the window that you wanted to be transparent.

---

### Post by Kev0r on 2005-03-22
[QUOTE=digby]Xcompmgr has to be running before you use transset.  After that, the procedure that I used was to open a terminal, enter the transset command, and then click on the window that you wanted to be transparent.[/QUOTE]
 So we need more screenshot on how this looks!!! Can't believe you think the screenshot of xodeus was nice.. (The screenshot was nice but windows look like crap on the inside)

Any word on how this will work on Warty? :P

---

### Post by digby on 2005-03-22
[QUOTE=Kev0r]So we need more screenshot on how this looks!!! Can't believe you think the screenshot of xodeus was nice.. (The screenshot was nice but windows look like crap on the inside)

Any word on how this will work on Warty? :P[/QUOTE]

I'll don't have anywhere to host screenshots, so I can't help you there.

This won't work on Warty at all.  All these eye-candy additions are features of X.org.  Warty uses XFree86.

---

### Post by eljo on 2005-03-22
A screenshot of my desktop is available at [http://f-lips.de/images/Screenshot.png](http://f-lips.de/images/Screenshot.png) 

Funny thing is, with xcompmgr moving windows takes almost no CPU at all and acts _very_ smooth, even with all the eye candy. Still very buggy though - but that's kinda to be expected, what with the time it had to mature and stuff ;).

> Any word on how this will work on Warty? :P

It won't :). Not with stock warty, anyway, as you need xorg. Maybe if you install xorg from hoary or elsewhere, get xcompmgr and get recent nvidia stuff. Might as well just upgrade the rest too, when you're at it ;)

---

### Post by arnoct on 2005-03-22
I've been testing xcompmgr with various WMs, they all work with it but some run better than others. For example:

xfce - has a major bug where if certain windows are resized to be bigger, it won't redraw the new part of the window until the window is moved. This bug is also present in GNOME.
fluxbox - seems to work OK, although I'm having problems with fluxbox being stupid :p
openbox - Works very well when xcompmgr is on, but has a major bug where, after it turns on (or off,) apps don't come back as visible--you have to kill them through a console. This is using the verison in the hoary universe repository, I think it's out of date though
icewm - didn't have alot of time to look at it, but it seems to work OK.

So far, I'd recommend openbox (with fbpanel) except for the horrible "windows will disappear" bug.

---

### Post by xodeus on 2005-03-23
[QUOTE=zukeft]Looks pretty, um... normal. ^^'[/QUOTE]
If you look at the picture you can then see some shadows. :D
I havn't yet configured my desktop in other ways so it isn't so visible.

//XoDeus

---

### Post by Yamakazi on 2005-03-23
Hello,

I tried this yesterday and it works wonderfull.

I got myself the nVidia drivers from the repository.
Than i ran sudo nvidia-glx-config enable

Now i got nVidia working and i installed transset and xcompmgr as described in the tut.

Hitted Ctrl-alt-backspace.

And eveything camu up fine.

The ugly windows is transset, Some don't become completly transparant.  And have strange block in them.  the fade in and fade out work ok and look amazing.  Drop shadown also works.  Only real problem i have is i can't shutdown.  The box doesn't appear.  So i shutdown with: sudo shutdown -h now

Thx for the great tut.

---

### Post by Brian McConnell on 2005-03-24
After further use, I have edited my original post.

This works poorly with  ATI Radeon Pro 9800 on Mac G5 dual 1.8ghz 2gb ram

Use of transparency severely slows things down. Use of shadowing and/or fade/ins fade/outs causes problem with logout. What happens is after selecting logout from the system menu the system will hang. No logout/restart menu will appear. CPU usage skyrockets. ctrl+option+backspace will kill X and bring you back to a graphical login when the system hangs. 

It's a shame really, because these are some very nice effects. I think it's great someone took the time to share this info ;)

I wonder why ATI Radeon Pro 9800 with 256mb ddr ram and 8 pipelines would have these issues on a dual 1.8ghz G5 processor with 2gb ddr ram.

---

### Post by synmnky on 2005-03-25
[QUOTE=Kev0r]So we need more screenshot on how this looks!!! Can't believe you think the screenshot of xodeus was nice.. (The screenshot was nice but windows look like crap on the inside)
[/QUOTE]
Here's another screenshot -
I'm using a lot more customised GNOME settings (theme, background, icons and the rest)
Shadows around window edges are turned on
Transparency of Firefox window with Ubuntu page is set to 0.6 - can see some of the desktop background through it

---

### Post by dolson on 2005-03-26
Well, thanks for the tutorial. This is a lot of work for the average home user though. I hope that once the bugs are worked out, that this will become an option in the System menu.

Also, I have dual displays, so following the tutorial gave me one desktop nice, the other crap. I worked around it though.

It's alright, but it's no Luminocity... :(


For some reason, the -C option does NOT work for me properly... Argh.


EDIT: ARRRGGGHHHH. This plays havoc with BMP. Artifacts everywhere when dragging, and don't even try to expand the playlist. Grr. Oh well, it was pretty cool while it lasted.

Bring on the Luminocity.

---

### Post by teumima on 2005-03-26
Hi

ATI Radeon 9200

Shadows works great. The fade in doesn't. I get the fading, however its slow and it hear my hard disk reading everytime I move down the menu.

However, just the shadows is a nice change. Thanks.

If anyone knows how I can speed up the fading, would be greatly appreciated. ATI Radeon 9200 is pretty new.

---

### Post by grendelkhan on 2005-03-26
I ended up with all GLX completly horked, running Quake3 would crash X completely.  Disabled it all and now I am eye-candyless.

Total bummer.

---

### Post by hamiltjr on 2005-03-26
Funny, same thing happened with me in Quake 3, although all of my other GL apps work.. and the xcompmgr runs great!

---

### Post by out of the blue on 2005-03-26
Alias' Maya has problems with it. Titlebars are invisible, windows disappear. Even with just compositing enabled (nevermind running xcompmgr) problems like disappearing windows and window contents disappearing happens.

Just a warning to anyone who uses Maya. :)

---

### Post by LichiMan on 2005-03-27
[QUOTE=out of the blue]Alias' Maya has problems with it. Titlebars are invisible, windows disappear. Even with just compositing enabled (nevermind running xcompmgr) problems like disappearing windows and window contents disappearing happens.

Just a warning to anyone who uses Maya. :)[/QUOTE]

Yes, I have the same problem :)

---

### Post by rjr1049 on 2005-03-27
Doesn't work well for me.  The gnome panel log out buttons are completely disabled if I run xcompmgr.  Too bad - its looks slick.

---

### Post by martijntje on 2005-03-27
It's sweet alright!

There are only a few things bugging me with this:
- When i minimize a program, it starts to fade out, however, it also moves to the taskbar. Can i disable the moving? I think it would be better if it simply fades out.
- Is there a possibility to automatically fade a window to half transparancy when it loses focus, and set it back to full opacity when it gets focus? That would be even nicer, since it makes your screen look less cluttered.

---

### Post by dafrabbit on 2005-03-27
Just wondering, as I've been seeing conflicting reports about this, but has anybody gotten fglrx and composite working together? And also, has anybody gotten good solid performance using the ati (open source) and composite? Mine is slow as heck and I have a 9700pro. 

It looked awesome while it lasted though.  :grin:

---

### Post by Benny on 2005-03-27
[QUOTE=teumima]Hi

ATI Radeon 9200

Shadows works great. The fade in doesn't. I get the fading, however its slow and it hear my hard disk reading everytime I move down the menu.

However, just the shadows is a nice change. Thanks.

If anyone knows how I can speed up the fading, would be greatly appreciated. ATI Radeon 9200 is pretty new.[/QUOTE]

Hi!

How did you get it work. I have Ati Radeon 9600pro and tried but nothing happens. And the transset wont work.. 

Anyone??

---

### Post by stateq2 on 2005-03-27
it is pretty cool....still very slow though, almost unusable....although I do have a rather old laptop

p3 850mhz
575mb ram
ati rage mobility (mach64)

---

### Post by fackamato on 2005-03-27
I don't understand all the commotion, it's totally unusable at normal uses. If you use composite with glx (3D hardware acceleration) you're quite fucked, since it most certainly will crash your X or otherwise behave unstable. And it's the buggiest thing ever. It's not near ready, anywhere. :)

But when it's finished, it will be great.

---

### Post by Reb on 2005-03-27
```
xcompmgr -cCfF -r7 -o.65 -l-10 -t-8 -D7 &
```Very nice xcompmgr settings courtesy of gladiac.

---

### Post by dolson on 2005-03-28
[QUOTE=fackamato]I don't understand all the commotion, it's totally unusable at normal uses. If you use composite with glx (3D hardware acceleration) you're quite fucked, since it most certainly will crash your X or otherwise behave unstable. And it's the buggiest thing ever. It's not near ready, anywhere. :)

But when it's finished, it will be great.[/QUOTE]

Totally agree. I ran with it for a day or two, and disabled it now. It constantly stopped working and my desktop was slow as a turtle.

It was nice, but I just want Luminocity already!

---

### Post by teumima on 2005-03-28
Fading was too slow, shadow was great.

Note for ATI users. It's either composite or 3d accl, not both.

---

### Post by ba5e on 2005-03-28
I have a problem that when i enable xcompmgr -cfF as described, selecting the System - Log Out i dont get the log out screen up - its functional (ie i can press return and it will log out, go down and shutdown..etc etc) but its really bugging me! whats goin on? 

Regards, Will

---

### Post by Randabis on 2005-03-28
[QUOTE=ba5e]I have a problem that when i enable xcompmgr -cfF as described, selecting the System - Log Out i dont get the log out screen up - its functional (ie i can press return and it will log out, go down and shutdown..etc etc) but its really bugging me! whats goin on? 

Regards, Will[/QUOTE]
 xcompmgr is buggy...that's about the best answer you'll get for now.

In fact I'm kind of relucant to even use it now that I've had it completely crash the xserver on me 3 times. When it is working right the effects are quite sweet though.

[http://img17.exs.cx/my.php?loc=img17&image=snapshot55vk.jpg](http://img17.exs.cx/my.php?loc=img17&image=snapshot55vk.jpg)

---

### Post by dolson on 2005-03-28
[QUOTE=ba5e]I have a problem that when i enable xcompmgr -cfF as described, selecting the System - Log Out i dont get the log out screen up - its functional (ie i can press return and it will log out, go down and shutdown..etc etc) but its really bugging me! whats goin on? 

Regards, Will[/QUOTE]

Umm, did you read this thread? I am pretty sure it was already mentioned.

---

### Post by ions on 2005-03-29
Definately looks alright although it slowed my box down considerably using the recommended -cfF.  Trying transset left my machine unusable.  I clicked to close the transparent window and waited a good 25 seconds until the window did close and my system became usable again.  Gonna just go with the shadows for now I think.  I thought my machine would have been more capable with this stuff considering the specs others have mentioned.  Barton 3200 and a nvidia 5200 with a gig of ram.  Oh well.

Oh, and chalk up another user that has the log out dialogue window problem.  Kinda a pain.

---

### Post by Whiffle on 2005-03-29
Compositing works great over here...for one screen. A few bugs here and there but its not perfect yet.  When I set it up to do twinview I get all kinds of interference on the screen.  Did it in  gentoo too, not sure what causes it :(  Pentium 4 1.6 ghz geforce4 ti4200 128mb video ram, 256 mb system ram

---

### Post by Happy on 2005-03-31
Well. I made my windows look super sweet.
Unfortunately X windows crashed shortly after
but that could have been because I installed and was running skippy

---

### Post by Gandalf on 2005-04-04
hello,
my video card is
```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

``` do i take the risk and try this, or it will be maybe too risky?

---

### Post by keffo on 2005-04-04
Oh well, just followed this guide.. (nice guide)

BUT, this is way to unstable n buggy.. atleast for me, I do have
a Radeon 9800pro   - And it was major buggy and really fuxed up.

So.. if theres anyone around with a similar card running this
composite thingies nicly, please tell..


Cheers

---

### Post by df-sean on 2005-04-04
I've tried it several times -- went over every detail.  But no matter what I do, when I type "xcompmgr -cfF", it simply says "No composite extension".  How can I get past this?

(Kubuntu Hoary, xcompmgr, transet, nvidia -- all installed.  xorg.conf modified with extensions section as described at the top of this thread)

---

### Post by graabein on 2005-04-04
[QUOTE=xodeus]Somebody wanted screenshots. I've only one but it's the default ubuntu gnome with all this stuff enabled. It's so pretty.[/QUOTE]
Got a link to the desktop wallpaper you were using there? I like brown ones that fit in with the default brown color theme.

---

### Post by Bo Rosén on 2005-04-04
Those drop shadows are really nice and the only thing I managed to get to work somewhat on my system - and then only from a terminal before the system froze solid ;-) 

It'll be very cool when things are more stable.

AMD Athlon 1 gig and Nvidia Geforce 440 mx

---

### Post by ions on 2005-04-04
This is what I've done with it:

[Clean](http://home.cogeco.ca/~ionsvw/images/04.05clean.jpg) 
[Dirty](http://home.cogeco.ca/~ionsvw/images/04.05dirty.jpg) 

Just running the drop shadows cause anything else is too much.

---

### Post by unforgivendown on 2005-04-06
[QUOTE=df-sean]I've tried it several times -- went over every detail.  But no matter what I do, when I type "xcompmgr -cfF", it simply says "No composite extension".  How can I get past this?

(Kubuntu Hoary, xcompmgr, transet, nvidia -- all installed.  xorg.conf modified with extensions section as described at the top of this thread)[/QUOTE]
Do you have an ATi card?

---

### Post by df-sean on 2005-04-07
>>  Do you have an ATi card?
Nope, it's an nVidia GForce MX-something (32MB).  nVidia drivers are running correctly (I get the nVidia bootsplash too).

---

### Post by bektom on 2005-04-07
Hi everyone,

I am struggling with a problem for the last couple of days, but I didnot find the solution in any forums, so I think (of course I am not sure) this is the best place to ask it:

I would like to change the profile of the terminal windows from the command prompt, and not in the terminal menu's change profile option. However, I have not really found any files, or env. values which would specify this. I have checked the gnome-terminal command, but it only specifies how to start a new terminal with a different profile.

gnome-terminal --widow-with-profile=PROFILENAME

but as I said, it creates a new terminal with the specified porfile. So does anyone has an idea or a link to a HOWTO on this?

Thank you in advance

Thomas

---

### Post by brehloi on 2005-04-08
wow, this is sexy! =P~ 

good work! nice guide

althougth it crashed my pc completely with normal gnome login.
managed to get it working by using a failsafe session en manually starting it.

it is really really nice, seeing forward to a more stable version.

had to remove it for now,  :cry:

---

### Post by angrykeyboarder on 2005-04-09
[QUOTE=teumima]Hi

ATI Radeon 9200

Shadows works great. The fade in doesn't. I get the fading, however its slow and it hear my hard disk reading everytime I move down the menu.

However, just the shadows is a nice change. Thanks.

If anyone knows how I can speed up the fading, would be greatly appreciated. ATI Radeon 9200 is pretty new.[/QUOTE]

I've got an nVidia GeForce 6800 GT with 256 MB of RAM and the fading is still damn slow. I can only imagine what it would be on an older card with 64 or 128 MB of RAM......

---

### Post by heimo on 2005-04-09
[QUOTE=angrykeyboarder]I've got an nVidia GeForce 6800 GT with 256 MB of RAM and the fading is still damn slow. I can only imagine what it would be on an older card with 64 or 128 MB of RAM......[/QUOTE]

Works very well on my Nvidia FX 5200 128MB card. Fading is smooth and in no way I'd describe it slow. And opening menus or programs is not considerably slower / doesn't cause more hard disk activity than before. Is your hardware 3d-acceleration working correctly? I guess your 6800GT should be flying compared to my 5200, if there's no bugs or problems with configuration.

---

### Post by udha on 2005-04-09
it seems that it does work pretty well for alot of people, I would say those it doesn't work well for would be due to their video driver module and their xorg config, I had very percular results when I tried all this out.

I got the shadows, but they would keep resetting things, such as the contents of a window or sections of the gnome panels. Also the entire background was all grey except for the immediate area around the icons. my sig should say what i'm running so I won't go into that.

In short I couldn't use it.

---

### Post by MetalMusicAddict on 2005-04-09
Is there a FAQ or a guide to exlpain the arguments you can use to change options/appearances?

Like this:
"xcompmgr -cCfF -r7 -o.65 -l-10 -t-8 -D7 &"

---

### Post by RastaMahata on 2005-04-09
Ack, ubuntu just didnt want to load after the xcompmgr thing.. I had to uninstall them :(

---

### Post by Arbiter on 2005-04-09
I tried to do this whole compositiing thing, but with limited success (or conditional failure, depending if you're a glass-half-empy type person).

Initially, I followed the directions, and all seemed well until I actually tried to log into Ubuntu at the GDM login screen.  The GNOME startup splash loaded, and then the machine hung at that screen with the only thing working being my mouse, which I was somehow able to still move.

After this I decided to play with my X.org settings.  I set RendAccel = "true" to RendAccel = "false" and then after a quick restart, I was able to get to my GNOME desktop.

But wait!  There's more!

The animation was extremely slow (as compared with non-existant last time), and when I tried to open FireFox, the X Server crashed and I was dropped to a terminal prompt.

Here's my hardware setup if anyone's got any ideas.  I liked the way it all looked, but I wish it would work properly...

CPU - Athlon XP 2600+
Motherboard - Biostar M7NCD NForce 2
RAM - 256MB PC2100 DDR
Video - Nvidia GeForce 4 Ti4200
Sound - Sound Blaster Live! 5.1

Also, I am using the nvidia-glx driver that is provided from an Ubuntu APT repository.  And yes, I am using Ubuntu 5.04 Hoary.

---

### Post by poofyhairguy on 2005-04-10
Ok. I've read every post, and tried to fiddle with it myself. I think I got this thing figured out. 

Everyone with ATI cards on this thread says that the shadows work well, but fading doesn't. On my desktop ( A P4 2.6GZ with a 128mb 9600 pro ATI card) this is exactly the case. Drop shadows work fine, but fading slows everything to a crawl.

On my girlfriend's laptop (a celeron 1.7 GHz with a 16MB or 32MB Nvidia Geforce 420 Go) I have the nvidia drivers working and fading works great (it hard to describe, but its the best eyecandy I've ever seen. It removes my biggest complaint of Gnome with this Nvidia card- how ugly windows look when minimized. With this, on her laptop, they look great. Yet shadows won't work on hers. My guess is (based on the other people with Nvidia cards that have posted problems with this feature) that pre-directx9 cards- anything before the 5xxx FX series- won't do it. But thats just a guess.

I'll know soon, tonight I will buy an Nvidia card. Goodby ATI, hello fading. Changed my life this howto did...

---

### Post by MetalMusicAddict on 2005-04-10
Im having a weird problem. When I add the lines needed to the xorg.conf. I loose local FAT and NTFS drived being mounted in "Computer". If I remove the lines, they're back. Weird.

---

### Post by RastaMahata on 2005-04-10
[QUOTE=MetalMusicAddict]Im having a weird problem. When I add the lines needed to the xorg.conf. I loose local FAT and NTFS drived being mounted in "Computer". If I remove the lines, they're back. Weird.[/QUOTE]
 what lines would those be? Please tell me

---

### Post by MetalMusicAddict on 2005-04-10
These 2:
> 
Add the following section after the "module" section:
```

Section "Extensions"
	Option 	"Composite" "Enable"
EndSection

```
Add the following lines to the "device" section:
```

	Option 		"AllowGLXWithComposite" "true" 

```

If I add 'em I loose local FAT and NTFS drives being mounted the in "Computer". They're in "/media/WHATEVER", I can get to 'em. Just not displayed in "Computer". 

"RenderAccel" is added in this FAQ also but I already had that in the conf.

---

### Post by RastaMahata on 2005-04-10
[QUOTE=MetalMusicAddict]These 2:

If I add 'em I loose local FAT and NTFS drives being mounted the in "Computer". They're in "/media/WHATEVER", I can get to 'em. Just not displayed in "Computer". 

"RenderAccel" is added in this FAQ also but I already had that in the conf.[/QUOTE]
 weird, I dont have those lines, and I cant see my drives in computer or places :(
"sudo /etc/init.d/dbus-1 restart" fixes the problem, but takes out the names... I think this has something to do with xorg and dbus... hrm

---

### Post by Thorongil on 2005-04-10
[QUOTE=digby]So I've run into a small hitch trying to get this to work.  I'm on a clean install of Hoary, and I installed the nVidia 7167 driver according to the instructions in [this]("http://www.ubuntuforums.org/showthread.php?t=21111") HowTo.  

I made sure that I followed the instructions to the letter.  (I used -cfF for shadows and fading.)  When I restarded X, the Gnome splash screen came up and had a lovely shadow.  The background turned grey (from the usual brown) and the splash started to fade away.  Before it finished fading it just stopped.  My mouse cursor would still move, but nothing else would respond.  

I couldn't kill X with Ctrl+Alt+Backspace, and I couldn't switch to a virtual terminal with Ctrl+Alt+F1.  I had to do a hard reset and decided to try it one more time.  This time the splash faded away completely, but it then locked up the same as before.

That's the only user account I have, so I can't log into Gnome at all.  Any ideas?

XP 2500+
nVidia GF4 Ti4600
nVidia driver version 7167
Ubuntu Hoary 5.04 / Gnome 2.10 - still all default settings except for the new kernal for the glx driver (2.6.10)[/QUOTE]
 Same here, X-Server not reacting to break signal, and even not possible to escape to a terminal screen via Ctrl-Alt-n

---

### Post by Arbiter on 2005-04-10
Is it a problem using the nvidia-glx driver from the Ubuntu repository or do you have to download nvidia's latest driver and install it?

---

### Post by digby on 2005-04-10
I've tried it both with installing the driver from nvidia's site (before 7167 was in the apt repository) and with the newer driver from apt.  Same result both ways.

---

### Post by Arbiter on 2005-04-10
[QUOTE=digby]I've tried it both with installing the driver from nvidia's site (before 7167 was in the apt repository) and with the newer driver from apt.  Same result both ways.[/QUOTE]

Ah, ok.  I've been using the newer apt driver and I still really can't get past the GNOME splashscreen before the system hangs.  After disabling the RenderAccel value in my x.org config file I was able to login successfully, but the animations onscreen were far too slow and X crashed after a few minutes.

I'm using an Nvidia GeForce 4 Ti4200 - I should have more than enough horsepower in that thing to do this...not sure why it doesn't like the RenderAccel value being enabled.

To make a long story short, I don't know what's going wrong.  Any help would be greatly appreciated, cuz this is a REALLY nice thingy.

---

### Post by Thorongil on 2005-04-10
[QUOTE=Arbiter]Ah, ok.  I've been using the newer apt driver and I still really can't get past the GNOME splashscreen before the system hangs.  After disabling the RenderAccel value in my x.org config file I was able to login successfully, but the animations onscreen were far too slow and X crashed after a few minutes.

I'm using an Nvidia GeForce 4 Ti4200 - I should have more than enough horsepower in that thing to do this...not sure why it doesn't like the RenderAccel value being enabled.

To make a long story short, I don't know what's going wrong.  Any help would be greatly appreciated, cuz this is a REALLY nice thingy.[/QUOTE]
 Ti 4200 here, too!

---

### Post by Arbiter on 2005-04-10
[QUOTE=Thorongil]Ti 4200 here, too![/QUOTE]

Maybe we've stumbled on something here.  What company made your Ti4200?  Mine was manufactured by Gainward.

---

### Post by spacemonkey on 2005-04-10
I'm running a Nvidia XFX Geforce FX 5600 and everything works great, except I've discovered xcompmgr quits working after the monitor is put into standby.  Any suggestions on how to solve this?

---

### Post by Thorongil on 2005-04-10
[QUOTE=Arbiter]Maybe we've stumbled on something here.  What company made your Ti4200?  Mine was manufactured by Gainward.[/QUOTE]
 Leadtek WinFast 250 LE TDH here ;-)

The one with the all-aluminium cooler round the card....noisy bastard of a fan after 2 years of operation :(

---

### Post by Arbiter on 2005-04-10
[QUOTE=Thorongil]Leadtek WinFast 250 LE TDH here ;-)

The one with the all-aluminium cooler round the card....noisy bastard of a fan after 2 years of operation :([/QUOTE]

Mine's of similar construction...the round aluminum cooler and such.  It sounds almost identical.

Hmmm...somehow it seems that the compositing feature really has it out for the GeForce4 Ti series of cards...anyone have any luck with the GeForce4 Ti's?

---

### Post by Thorongil on 2005-04-10
[QUOTE=Arbiter]Mine's of similar construction...the round aluminum cooler and such.  It sounds almost identical.

Hmmm...somehow it seems that the compositing feature really has it out for the GeForce4 Ti series of cards...anyone have any luck with the GeForce4 Ti's?[/QUOTE]
 Original Poster claimed to run on a Ti4600 - identical chipset, only different chip/memory clock....

---

### Post by poofyhairguy on 2005-04-10
[QUOTE=Arbiter]
I'm using an Nvidia GeForce 4 Ti4200 - I should have more than enough horsepower in that thing to do this...not sure why it doesn't like the RenderAccel value being enabled.

To make a long story short, I don't know what's going wrong.  Any help would be greatly appreciated, cuz this is a REALLY nice thingy.[/QUOTE]


Experiance has shown me that Nvidia cards without Directx 9 capabilites can't do drop shawdows. Thats why everyone on here with Geforce FX cards doesn't have any problems, but everyone here with Directx 8 cards (Geforce 4 or older) is having problems. On my girlfriend's computer (a geforce 4) fading works great- I really like that- but drop shadows bork everything. I suggest if you have a Geforce 4 or earlier sticking to fading. On my desktop, ( a P4) I use the Mesa driver (damn ATI card's official drivers have worse 2d then Mesa) and that card (which is a 9600 pro) does shadows with no problem but fading slows everything to a crawl (its obviously not hardware accerated). 

This morning I bought a cheap 64mb 5200 FX card (lowest price Directx 9 card that exists) and I will post how well it works. For me, fading is worth what I plan to pay for it (30$) but drop shadows are over rated. On my girlfriend's laptop I just have fading  going, and it makes me wanna cry.

Time will tell if it works, but I think it will. I mean, the prettiest OS on the planet- OSX- runs well on a 32mb!!! Directx 9 card-

[http://www.apple.com/macmini/](http://www.apple.com/macmini/)

---

### Post by dabeej on 2005-04-10
It's best to stay away from this. Reasons why is that first it does weird things to applications. Look at gnome-theme-manager after enabling it. Yes games you will have issues. Window drawing will have issues to. It's nice to look at, you decide if it's worth it.

---

### Post by Chromance on 2005-04-11
Has anyone tried this with the ATI card yet?

---

### Post by poofyhairguy on 2005-04-11
[QUOTE=Chromance]Has anyone tried this with the ATI card yet?[/QUOTE]


I did. Shadows work ok, fading is slow compared to an Nvidia card.

---

### Post by Thorongil on 2005-04-11
[QUOTE=poofyhairguy]I did. Shadows work ok, fading is slow compared to an Nvidia card.[/QUOTE]
 Well, I think as Gnome gets a new 3D-enabled, powerful Window Manager, this can only be considered as an "intermediate hack", do a search on the web for "wobbly windows", you wil see some really great stuff in the works ;-)

---

### Post by mgor on 2005-04-11
great howto!

works like a charm on my geforce fx 5200.
[http://joshua.haninge.kth.se/~mgoransson/composite.png](http://joshua.haninge.kth.se/~mgoransson/composite.png)

---

### Post by poofyhairguy on 2005-04-11
[QUOTE=Thorongil]Well, I think as Gnome gets a new 3D-enabled, powerful Window Manager, this can only be considered as an "intermediate hack", do a search on the web for "wobbly windows", you wil see some really great stuff in the works ;-)[/QUOTE]


Its just that....I can't wait...  I NEED EYECANDY NOW!!!

Its either a Nvidia card or a Mac. I'll get the damn card......

---

### Post by Thorongil on 2005-04-12
[QUOTE=mgor]great howto!

works like a charm on my geforce fx 5200.
[http://joshua.haninge.kth.se/~mgoransson/composite.png](http://joshua.haninge.kth.se/~mgoransson/composite.png)[/QUOTE]

Na, OK, after seeing the Screenshot, I will not investigate this any further for me. THe gnome-panel should definitively be in the BACKGROUND and not casting shadows over  Windows  :-# 

As long as gnome is not really prepared for this eycandy, I think you will always encounter such problems....

---

### Post by poofyhairguy on 2005-04-12
[QUOTE=Thorongil]Na, OK, after seeing the Screenshot, I will not investigate this any further for me. THe gnome-panel should definitively be in the BACKGROUND and not casting shadows over  Windows  :-# 

As long as gnome is not really prepared for this eycandy, I think you will always encounter such problems....[/QUOTE]


If you have an Nvidia card try the shading. Its only like 1000 times better than drop shawdows (but won't show up in a screenshot).

---

### Post by poofyhairguy on 2005-04-14
I want to post a followup:

Today I got my 64mb 5200FX NVIDIA card. My suspicions were correct, this card (though technically a lot weaker than other people's 4200s) support a high enough version of opengl to do every trick. Drop shadows and fading work like a charm. 

The eyecandy was well worth the $30 I paid for the card on ebay, and would have been worth the $55 it costs on newegg. I recommend that any ATI owner that likes eyecandy but doesn't actually play (many)  high end 3D games on their Linux machine buy one of these cards.

EDIT: thanks for the howto.

---

### Post by Stormy Eyes on 2005-04-14
Guys, you don't *have* to have drop-shadows with xcompmgr. Just run **xcompmgr -fF** instead of **xcompmgr -cfF** and you'll have creamy compositing goodness without annoying shadows.

---

### Post by RastaMahata on 2005-04-14
[QUOTE=Stormy Eyes]Guys, you don't *have* to have drop-shadows with xcompmgr. Just run **xcompmgr -fF** instead of **xcompmgr -cfF** and you'll have creamy compositing goodness without annoying shadows.[/QUOTE]
 well, this worked for me, as my pre directx9 geforce4mx doesnt support shadows! :(

---

### Post by Shuddertrix on 2005-04-14
Finally restarted X after putting this on a few days ago, and I have to say that the fade-in/out is probably the best part of it. The slow feeling of the fade-in/out is well appreciated. I use -sFf personally, as the simple shadows don't slow it down but look OK to me (if you love eye-candy, you aren't going to like the simple shadows, that's for sure.)

transset looks AWESOME, especially with 'transset 0.25' on gnome-panel. Since I perfer using a transparent menubar/taskbar on all my other computers, transset is quite nice for it. 

Fading in and out with maximize/minimize in Gnome is sometimes a little flaky with Firefox, as it will sometimes fade in just the WM, firefox, or both. Otherwise, smooth and silky on this box.

---

### Post by neilius on 2005-04-14
This is really good stuff, I also recommend people use this with just the -a switch which gives you a sexy accellerated desktop but without any eye candy, it really speeds things up especially dragging windows over Firefox, which normally leave nasty ugly trails. I'm using -fF because I too have a GeForce 4 MX which makes X crash when I try to use shadows but I'd like to some day use shadows with this card if possible. Still, with the fades, things are pretty damn nice!!! Thanks!

Regards,

Neil.   :smile:

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=neilius]This is really good stuff, I also recommend people use this with just the -a switch which gives you a sexy accellerated desktop but without any eye candy, it really speeds things up especially dragging windows over Firefox, which normally leave nasty ugly trails. I'm using -fF because I too have a GeForce 4 MX which makes X crash when I try to use shadows but I'd like to some day use shadows with this card if possible. Still, with the fades, things are pretty damn nice!!! Thanks!

Regards,

Neil.   :smile:[/QUOTE]

so add the -a to the -fF and -c, or does it do that already with the others?

---

### Post by zeus on 2005-04-15
[QUOTE=poofyhairguy]so add the -a to the -fF and -c, or does it do that already with the others?[/QUOTE]
 xcompmgr -a 
speed up window draging and menu poping in my Tecra 8200 notebook.
Shadow and fading is too much to handle by my P III 750 128 RAM :p

It's a neat app, i wonder when xorg add this stuff.

---

### Post by cyrix^ on 2005-04-15
Does anyone have a solution, when using the shadowing, and RenderAccel options with the nvidia driver ?

It keeps crashing... This topic is well known, but nothing I have tried seems to fix the problem.

Will another version of the nvidia driver maybe do the trick ?

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=cyrix^]Does anyone have a solution, when using the shadowing, and RenderAccel options with the nvidia driver ?

It keeps crashing... This topic is well known, but nothing I have tried seems to fix the problem.

Will another version of the nvidia driver maybe do the trick ?[/QUOTE]

What card do you have? If it is not a FX card or higher (anything Geforce 4 or less isn't) then it does not currently support drop shadows. It requires newer opengl support. It no big deal, drop the -c (just use -fF) and get the better effect, the fading effect. This works GREAT on my girlfriend's 16mb Nvidia card so I know that most of them can do it.


The fading effect is worth buying an nvidia card...

---

### Post by cyrix^ on 2005-04-15
Ok. I will try that out. 
It is a GF4 mx440 card.

edit:
nice. It worked. Though without shadows. Anyway, it aint my computer, so I guess I will try it when I come home, on my own computer.

---

### Post by anopenscroll on 2005-04-15
There's still the problem of **not being able to use the logout box** with this thing going. I have an FX 5200 128 mb card. Any ideas? (yes, I know shutdown -h works but that's so blech  \\:D/ )

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=anopenscroll]There's still the problem of **not being able to use the logout box** with this thing going. I have an FX 5200 128 mb card. Any ideas? (yes, I know shutdown -h works but that's so blech  \\:D/ )[/QUOTE]

I personally press

ctrl-atl-backspace

at the same time to logout. This problem won't get fixed  til (AT THE EARLIEST) after the next Gnome release. Currently Gnome doesn't supprot all of this jazz, that creates the problem.

If the current way it works in Gnome irks you:

A. Use KDE. 3.4 does have xcompmgr support.

B. Turn it off. Its just eyecandy.

---

### Post by Dromio on 2005-04-15
[QUOTE=anopenscroll]There's still the problem of **not being able to use the logout box** with this thing going. I have an FX 5200 128 mb card. Any ideas? (yes, I know shutdown -h works but that's so blech  \\:D/ )[/QUOTE]

As mentioned earlier in the thread, the shutdown dialog box is hidden when logging out while xcompmgr is running.   Just wait a half a second, then press Enter on your keyboard to dismiss the dialog.  Then it will log out normally.

---

### Post by idn on 2005-04-15
I have also noticed that VLC does not start up properly. If you minimize and restore it fixes the problem,

---

### Post by anopenscroll on 2005-04-15
[QUOTE=poofyhairguy]I personally press

ctrl-atl-backspace

at the same time to logout. This problem won't get fixed  til (AT THE EARLIEST) after the next Gnome release. Currently Gnome doesn't supprot all of this jazz, that creates the problem.

If the current way it works in Gnome irks you:

A. Use KDE. 3.4 does have xcompmgr support.

B. Turn it off. Its just eyecandy.[/QUOTE]
 Thanks for the replies. I guess I'll just wait for the next release of gnome :| before turning this back on.

---

### Post by neutron on 2005-04-16
I've followed every step in the first post in this thread, yet xcompmgr refuses to work properly. The funniest thing is that I actually GOT IT working on my first Hoary install  :???:  (I reinstalled Hoary yesterday). 

I've a geforce2 gts and I'm using the official nvidia driver. I don't know what the relevant parts from my xorg.conf exactly are, but maybe this gives an indication:

```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection
``` 
```
Section "Device"
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
	Option		"NoLogo"	"true"
EndSection
``` 
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
	DisplaySize	270	203	# 1024x768 96dpi
EndSection
``` 
```
Section "Extensions"
	Option 	"Composite" "Enable"
EndSection
``` 

It doesn't matter it I'm typing xcompmgr -c in the CLI whithin Gnome or add it to my session (order=0). In both cases, my computer completely locks. When I add it to my session and login from gdm I get a nice splashsceen WITH shadow and then an empty desktop with one panel. And suddenly I can't do anything, no CTRL+ALT+Backspace, no CTRL+ALT+Fkey, I can't add anything to the panel and it has no buttons. 

I've a picture attached (made with my digicam) so you can see how it looks like. [[IMG]http://img87.echo.cx/img87/3423/xcompmgr1rx.th.jpg[/IMG]](http://img87.echo.cx/my.php?image=xcompmgr1rx.jpg)

Oh yeah, and I've changed the font rendering from autohint to 'subpixel rendering' (although that shouldn't matter)

Anyone got a clue what's going on? Thnx!

---

### Post by cyrix^ on 2005-04-16
Neutron, I guess you have the same problem as I had.. You can't use the shadow effects with such an old graphic card..

See these two:
My question:
[http://ubuntuforums.org/showpost.php?p=133236&postcount=117](http://ubuntuforums.org/showpost.php?p=133236&postcount=117)
The answer:
[http://ubuntuforums.org/showpost.php?p=133236&postcount=118](http://ubuntuforums.org/showpost.php?p=133236&postcount=118)

It works perfectly at home with a Geforce PCX 5900 ...

Another solution is to disable the RenderAccel, but then it will run god damn slow..

---

### Post by mgor on 2005-04-16
[QUOTE=anopenscroll]There's still the problem of **not being able to use the logout box** with this thing going. I have an FX 5200 128 mb card. Any ideas? (yes, I know shutdown -h works but that's so blech  \\:D/ )[/QUOTE]

i have the same problem. though it works for me if i got like beep-media-player open, logout, and i'll get a dialogue saying that the beep-media-player window dosen't support "save state" something, just close it and i'm logged out.

---

### Post by neutron on 2005-04-16
[QUOTE=cyrix^]Neutron, I guess you have the same problem as I had.. You can't use the shadow effects with such an old graphic card..

Another solution is to disable the RenderAccel, but then it will run god damn slow..[/QUOTE]

Cyrix, thanks for your answer. As I stated it actually worked pretty good the first time I installed Hoary  :) . But since the 2nd time (reinstalled Hoary yesterday) it doesn't work anymore. I'll disable RenderAccel, and see if it helps. 

/edit
Just disabled RenderAccel and it seems to work! Unfortunately it's dogslow now  ;-), but it works! Thanks m8!

---

### Post by zer on 2005-04-16
Is it possible to use xcompmgr with the binary ATI drivers?!

```

zer@ubuntu:~$ xcompmgr
No damage extension

```

I have an ATI Radeon 9800 Pro. With the driver "ati", it works (but it is slooooow (on a 3 Ghz Machine, 1000MB RAM)

Any ideas or hints?

---

### Post by yoshic on 2005-04-16
hi, well, i can't use shadows because i'm using a gforce4 mx,  and, as i've read it's because the new opengl drivers, and this is the big cuestion, what problems  will i get if i install an old nvidia drivers on hoary???? :-|

---

### Post by raid517 on 2005-04-16
Well I followed all the advice I could find - and I still can't get this to work properly. I get something as in a desktop where everything is transparent - including the desktop itself. Also I don't get dropshadows, so much as 'seeing double.' That is to say that I simply see my text in duplicate with a dark version of my text appaering to sit on top of an only slightly lighter version.

In other words my desktop is a complete mess.

Can anyone offer any advice, or see anything in my xorg.conf file that I might be doing wrong?

[xorg.conf](http://www.justlinux.com/forum/attachment.php?s=&postid=810019) 

GJ

---

### Post by QCompson on 2005-04-16
Just wanted to add my experiences with the Nvidia driver, Render Accel, and eye-candy.

With a FX5900, I had apt-installed nvidia driver, renderaccel, and drop-shadowy goodness all cooperating well, but glx didn't work.

WIth a ti4200 in the same system, I manually installed the nvidia driver, which allowed me to get glx working, but renderaccel leads to periodic freezes (everything freezes, mouse moves).

Ti4200's don't seem to like Render Accel.  Hoary's nvidia drivers don't seem to like glx.  I spend more time messing around with nvidia drivers than anything else on my linux installs.    ](*,)

---

### Post by raid517 on 2005-04-16
Pah... it aint all it's cracked up to be. I think this is a fetaure that still needs a lot of work.

GJ

---

### Post by mgor on 2005-04-17
[QUOTE=Stormy Eyes]Guys, you don't *have* to have drop-shadows with xcompmgr. Just run **xcompmgr -fF** instead of **xcompmgr -cfF** and you'll have creamy compositing goodness without annoying shadows.[/QUOTE]

or you'll just run xcompmgr -cCfF:

[QUOTE="man xcompmgr"]-C     When -c is specified, attempts to avoid painting shadows on panels and docks.[/QUOTE]

updated screenshot: [http://joshua.haninge.kth.se/~mgoransson/composite.png](http://joshua.haninge.kth.se/~mgoransson/composite.png)

---

### Post by poofyhairguy on 2005-04-17
[QUOTE=QCompson]
With a FX5900, I had apt-installed nvidia driver, renderaccel, and drop-shadowy goodness all cooperating well, but glx didn't work.
[/QUOTE]

I think that glx won't work on any Linux system with xcompmgr.

---

### Post by mgor on 2005-04-20
hm, every time i right click and chose "save target as" in firefox, xcompmgr dies with the message "Segmentation fault". that's a weird bug.

---

### Post by faqpete on 2005-04-20
[QUOTE=QCompson]Just wanted to add my experiences with the Nvidia driver, Render Accel, and eye-candy.

With a FX5900, I had apt-installed nvidia driver, renderaccel, and drop-shadowy goodness all cooperating well, but glx didn't work.

WIth a ti4200 in the same system, I manually installed the nvidia driver, which allowed me to get glx working, but renderaccel leads to periodic freezes (everything freezes, mouse moves).

Ti4200's don't seem to like Render Accel.  Hoary's nvidia drivers don't seem to like glx.  I spend more time messing around with nvidia drivers than anything else on my linux installs.    ](*,)[/QUOTE]
 Hoary's nvidia driver like glx!
Just open /etc/X11/xorg.conf (with sudo!), take a look @ Section "Device" and add there following line: Option "AllowGLXWithComposite" "true"
That should work
Hope this helps

faqpete

---

### Post by hamster2k3 on 2005-04-21
mmm there must be a way to make it work nicely with ATI. Otherwise it sucks! :(

Under a MAC these effects works perfectly with an ATI card.
But I know you will probably say its not the same  OS and not the same X server (right?) and not even the same tools.

But do they have the same drivers as us ? Or is it something developped by apple ?

Also, anyone here who's using a Mac and Ubuntu maybe and who tried this ?
Do you have the same problem ? Basically you should... but just to make sure! ;)

---

### Post by goldfish on 2005-04-21
Sweet how-to, i have had no trouble with it so far, using it a while now.

Here is my current desktop

[http://www.redbrick.dcu.ie/~goldfish/Screenshot-3.png](http://www.redbrick.dcu.ie/~goldfish/Screenshot-3.png)

thanks for the info :grin:

---

### Post by poofyhairguy on 2005-04-21
[QUOTE=hamster2k3]mmm there must be a way to make it work nicely with ATI. Otherwise it sucks! :([/QUOTE]

No, its still pretty cool. Drop shadows worked with my ATI card.

[QUOTE=hamster2k3]Under a MAC these effects works perfectly with an ATI card.
But I know you will probably say its not the same  OS and not the same X server (right?) and not even the same tools.

But do they have the same drivers as us ? Or is it something developped by apple ?

Also, anyone here who's using a Mac and Ubuntu maybe and who tried this ?
Do you have the same problem ? Basically you should... but just to make sure! ;)[/QUOTE]

OSX has better ATI drivers thatn Linux.

---

### Post by tlepes on 2005-04-21
**I am having no luck with the ATI card using the latest ATI drivers in Ubuntu/Hoary repositories.**  I have an ATI Radeon 9800 Pro with 128Mb video SDRAM.  My system is an MSI K8N Neo2 Platinum (nForce 350 chipset) with an AMD Athalon 64 3000+ running 32-bit Hoary 5.04.

```
$ uname --all
Linux alembic 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
```

The xcompmgr reports version 1.1.1.

Now the compositing works (using the word loosely).  Problem is that it is painfully slow, and very buggy.  It misses big chunks.  It has problems updating elements.  Like, for instance, if I open Firefox and use the transset command to make it 50% transparent it will SEEM to work at first.  But if you scroll the page, the new parts stay opaque.  Also, as you mouse over widgets, they goof up.  It also has problems with one window getting the image of another (overlain) window stuck on it.  This is far from workable.

HOWEVER, I think it may have something to do with this...  When I enable the compositing, it seems that my 3D acceleration and all goes out the window.  I am back to MESA.  I don't have a clip of that for you, but on the OpenGL lines of fglrxinfo output I get MESA.  With the compositing disabled, I get this...

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)
```

Now the only difference in my configuration is whether I enable the Compositing Extensions or not.

```
$ diff xorg.conf xorg.conf~
57,59c57,59
< Section "Extensions"
<       Option "Composite" "Enable"
< EndSection
---
> #Section "Extensions"
> #     Option "Composite" "Enable"
> #EndSection
```

Things that make ya go #!$#@^%$#...

For what it's worth, I found in the Xorg.0.log file that the following is not understood by the ATI fglrx driver (it gives messages to that effect)...

```

	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true"
```

But this one seems to be recognized okay...

```

	Option		"BackingStore"		"true"
```

I would really like to have the compositing.  I am certain that my machine is physically capable of handling it just fine.  I guess I'll have to ride this out until it gets developed a little further along.

- Tim

---

### Post by Jesus Franco on 2005-04-22
According to those using the nVidia driver, the app works perfectly fine. And in a beefy system it runs at full speed.

 So to my understanding its the ati drivers. Not the xorg compositing thing. I also have a Ati video card. A AIW 9800 Pro. I have used these settings and run into the same problems as stated above :(

ATI plz fix it.

Are there any alternatives to the ati fglrx drivers? For example on windows theres the official ATI ones, the Omega ones and a few others. Are there any FGLRX alternatives for linux?  :roll:

---

### Post by ConstableRoark on 2005-04-22
Jesus Franco, those windows drivers you refer to are based off official ATi releases.

---

### Post by poofyhairguy on 2005-04-22
[QUOTE=tlepes]
I would really like to have the compositing.[/QUOTE]

How much do you want it? I found it worth it to toss my 9600 pro in a drawer and buy a cheap Nvidia card. It is the only solution as of now.

[QUOTE=tlepes]I am certain that my machine is physically capable of handling it just fine.  I guess I'll have to ride this out until it gets developed a little further along.

- Tim[/QUOTE]

You might ride for a few years and get nothing. After A LOT of complaining ATI has finally started to improve the 3D of their drivers a little. At the rate they went, it will take a long time before the company adds composite (2D) support I imagine.

---

### Post by poofyhairguy on 2005-04-22
[QUOTE=Jesus Franco]
Are there any alternatives to the ati fglrx drivers? For example on windows theres the official ATI ones, the Omega ones and a few others. Are there any FGLRX alternatives for linux?  :roll:[/QUOTE]

Well, the MESA drivers will do the drop shadows. But if you want compositing, its buy a Nvidia card or bust.

---

### Post by msgyrd on 2005-04-22
Just reporting my mileage with this.
Running a 1.4ghz AMD, with a GeForce2 PCI 64 mb card with 256 mb system mem, also running Hoary/Gnome and everything is updated.
The howto worked flawlessly for me, but my system couldn't handle the fade in/fade out effects very well.  They rendered fine, but framerate/refresh rate seemed to drop to about 15fps and was very choppy (but the effect did look cool).  I have shadows enabled still and don't notice them affecting anything (I don't use screensavers and havn't ran any opengl applications yet, so nothing to report there).

This summer when I install Ubuntu on my better system, I'll try this on my (much newer) ATI card.

---

### Post by Tobi Vollebregt on 2005-04-22
I tried it too; it looks super-ultra sweet and the HOWTO is just perfect. Unfortunately this composite manager freezes my system at random if I enable shadows. I'm now testing how it performs with only translucent windows. I'm looking forward to the moment this thing is perfectly stable.

The performance is really good for me (even with everything enabled, bad thing that it freezes even before logon is finished) - might be because my videocard is kinda oversized for my system: Amd Duron 800 Mhz, 384 Mb RAM, nVidia Geforce 4 Ti 4200  :wink: 

glxgears even seems to gain 50-100 fps (3000 ==> 3050-3100) from it (just translucency).

---

### Post by echoz on 2005-04-22
True for the dx9 card issue.

Mine dies on shadows.

2.4c p4
1gb ddr ram
gf4ti4800se

---

### Post by Tobi Vollebregt on 2005-04-23
I've disabled it: xcompmgr without arguments (ie. only translucency) sometimes randomly restarts X and that's quite frustrating if you have lots of windows open.

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=echoz]True for the dx9 card issue.

Mine dies on shadows.

2.4c p4
1gb ddr ram
gf4ti4800se[/QUOTE]

All the evidence supports it.

---

### Post by shof2k on 2005-04-25
[QUOTE=Gandalf]hello,
my video card is
```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

``` do i take the risk and try this, or it will be maybe too risky?[/QUOTE]
 Tried it on the above board, and shadows are useable.  However if you switch on fading or transparency then X.org takes a large amount of cpu (15-30%) making the desktop too slow for my liking.

---

### Post by okenobu on 2005-04-26
Hi all,

I have a crappy GeForce 4 MX 440 card with 128 MB ram made by some asian crap company and have had hard lockups every time i tried using the -c or -s options to xcompmgr. So by now i stick to using -fF which looks cool enough.

But i have a special scenario here. I have my computer and then my gf has a pretty crappy p-166 box that connects to my X server via XDM, so she actually uses her desktop in my machine and her comp only works as a dumb terminal. That box has a really ancient 4mb pci card or so, and i'm wondering what will happen if i turn xcompmgr on for her session too. Since i don't really understand how the X protocol works and etc, i don't know how this compositing thing is done, and would like know if her box will crash when trying to display the fadings.

Thanks!

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=okenobu]
But i have a special scenario here. I have my computer and then my gf has a pretty crappy p-166 box that connects to my X server via XDM, so she actually uses her desktop in my machine and her comp only works as a dumb terminal. That box has a really ancient 4mb pci card or so, and i'm wondering what will happen if i turn xcompmgr on for her session too. Since i don't really understand how the X protocol works and etc, i don't know how this compositing thing is done, and would like know if her box will crash when trying to display the fadings.

Thanks![/QUOTE]


The fading needs a semimodern Nvidia card to work well. Nothing else does the trick.

---

### Post by bored2k on 2005-04-29
Why is it that when I enable xcompmgr, the gnome panel is not always on top anymore? It's quite annoying. It gets solved with killall , so its no biggie.

---

### Post by colours on 2005-04-30
To ATI owners out there who hadn't realized: composite, or at least damage, doesn't work with fglrx. You'll get a "No damage extension" error if you try. If you want to use xcompmgr you'll need to use the open source, default ATI driver that also happens to be painfully slow.

So the transparency and shadow effects look really, really cool but also make everything really, *really* unusable.

Here's hoping ATI keep up their Linux driver development momentum. 8.12.10 made UT2004 playable, after all, and that was an enormous improvement!

---

### Post by Atfa on 2005-05-04
I have a Radeon 9550

I'm really frustrated because fglrx drivers are the only ones that works "fine" in linux with direct rendering, but on the other hand, are the only drivers that just doesn't work with composite.

I really want to make composite work, but I don't want to  lose Direct Rendering so anyone here knows how to contact the fglrx team so we can explain our problem and maybe one day, they release a version with composite support?

Thanks

---

### Post by Atfa on 2005-05-04
sorry,  I didn't know before that fglrx drivers was the official ATI drivers, so it will be impossible to contact the development team......
:( :(

---

### Post by imwithstupid on 2005-05-09
AMD 64 (3200+??)running 32 bit version of ubuntu with two monitors...one crt one lcd.  128mb 5200geforece FX with two vga outs.  1 gig ram.

verdict: works for the most part.  I have the fade in fade out off and it all seems to work fine for me.  I think it might be causing a crash when I open multiple documents in openoffice though.  I'm going to have to look at the logs for that one (it kills x completely...just like a ctrl+alt+bksp).

I set up to little things on the dockbar that do .7, .5 and 1 so i can have eye candy at my fingertips.  

I wish we had it like they have in enlightenment (I think?) that applies transparency to only the innactive windows
[[IMG]http://img239.echo.cx/img239/3163/transpoint5and75ih.th.png[/IMG]](http://img239.echo.cx/my.php?image=transpoint5and75ih.png)

---

### Post by Daz on 2005-05-10
Hi,

I've been trying to get this working on my machine too - but have been having a bit of a 'mare!  ](*,) I hope someone can help me out!  :wink: 

I have an AMD64 3200+ running 32-bit Hoary, 128Mb GeForce FX5200 card, 1Gb ram etc. - should be more than enough...

Whenever I try to start xcompmgr though, the screen just get's totally screwed - the mouse cursor dissaprears, the screens turn off and switch back on with loads of random shapes and patterns, and nothing works... umm, help!

I tried running xcompmgr -fF from a terminal and I got the following messages after I killed it (Ctrl+C):

```
error 9 request 158 minor 4 serial 1653
error 9 request 158 minor 4 serial 1660
error 9 request 158 minor 4 serial 1667
error 9 request 158 minor 4 serial 1674
error 9 request 158 minor 4 serial 1681
error 9 request 158 minor 4 serial 1688
error 9 request 158 minor 4 serial 1695
error 9 request 158 minor 4 serial 1702

```

Oh, and i'm on dual monitors if this makes any difference.

Anybody any ideas on this one?

Thanks in advance!

---

### Post by giorg on 2005-05-11
Alright guys am I the only one with nvidia problems? It crashes as soon as I run xcompmgr if I keep RenderAccel option enabled... the mouse is moving, I can still hear music, but nothing else's there. Any suggestion?
Thx

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=imwithstupid]AMD 64 (3200+??)running 32 bit version of ubuntu with two monitors...one crt one lcd.  128mb 5200geforece FX with two vga outs.  1 gig ram.

verdict: works for the most part.  I have the fade in fade out off and it all seems to work fine for me.  I think it might be causing a crash when I open multiple documents in openoffice though.  I'm going to have to look at the logs for that one (it kills x completely...just like a ctrl+alt+bksp).[/QUOTE]

Yeah. Its pretty unstable. I turn it off if I want to download or move files during the night. If I don't I wake up to the Ubuntu login screen.

Hopefully stablility will improve of the year!

> I wish we had it like they have in enlightenment (I think?) that applies transparency to only the innactive windows


KDE has that....

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=giorg]Alright guys am I the only one with nvidia problems? It crashes as soon as I run xcompmgr if I keep RenderAccel option enabled... the mouse is moving, I can still hear music, but nothing else's there. Any suggestion?
Thx[/QUOTE]


Drop shadows don't work with a pre FX card....

Just use fading...

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=Daz]
Anybody any ideas on this one?
[/QUOTE]

Sure. Mine works with that card. Compare the Xorgs and get yours to work!

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"NoLogo"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"NEC LCD1712"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"NEC LCD1712"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option 	"Composite" "Enable"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by giorg on 2005-05-12
[QUOTE=poofyhairguy]Drop shadows don't work with a pre FX card....

Just use fading...[/QUOTE]

Thx a lot, only with fading it works. I tried also transset and I found it beautiful, and I asked myself if is there any why to definitely apply transset to a program (let's say gnome-terminal). It is annoying every time to call it and point with the mouse... 
Thank you again

---

### Post by Daz on 2005-05-12
[QUOTE=poofyhairguy]Sure. Mine works with that card. Compare the Xorgs and get yours to work![/QUOTE]

Hi poofyhairguy!

Thanks for that, i've found out what the problem was... Xinerama!!! I was using xinerama to run my dual display set-up, but when I changed back to a single monitor everything worked (even gDesklets - which i've been having troubles with), so i've now switched to using Nvidia twinview to run the dual monitors, and everything works great!

Cheers!

Daz

---

### Post by SqdnGuns on 2005-05-15
[QUOTE=MetalMusicAddict]Is there a FAQ or a guide to exlpain the arguments you can use to change options/appearances?

Like this:
"xcompmgr -cCfF -r7 -o.65 -l-10 -t-8 -D7 &"[/QUOTE]


Options
-d display Specifies which display should be managed.
-r radius Specifies the blur radius for client-side shadows. (default 12)
-o opacity Specifies the translucency for client-side shadows. (default .75)
-l left-offset Specifies the left offset for client-side shadows. (default -15)
-t top-offset Specifies the top offset for clinet-side shadows. (default -15)
-I fade-in-step Specifies the opacity change between steps while fading in. (default 0.028)
-O fade-out-step Specifies the opacity change between steps while fading out. (default 0.03)
-D fade-delta-time Specifies the time between steps in a fade in milliseconds. (default 10)
-a Use automatic server-side compositing. Faster, but no special effects.
-c Draw client-side shadows with fuzzy edges.
-C Avoid drawing shadows on dock/panel windows.
-f Fade windows in/out when opening/closing.
-F Fade windows during opacity changes.
-n Normal client-side compositing with transparency support
-s Draw server-side shadows with sharp edges.
-S Enable synchronous operation (for debugging).

---

### Post by stubby on 2005-05-16
That's beautiful mate... appriciate the HOWTO. Worked great.

---

### Post by jldugger on 2005-05-17
Just a note to NVIDIA users: this technically isn't supported by the nvidia driver. The readme for the drivers says so, but also tells you the option to try anyways (its taken care of in the HOWTO).  Theoretically this isn't stable, try running glxinfo after turning it on for a quick demonstration. For me at least, running glxgears and the ut2004 demo didn't bring up any problems, although I hear the openGL screensavers can bone things up nicely.

---

### Post by joplass on 2005-05-21
I got myself in trouble.  After following the "how to" I can not start my laptop anymore.
I get a blue screen like the one I hate from windows with this message:
"I cannot start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the probem?

Yes                            No

ubuntunotebook login:"

Can someone please help???

Thanks,

---

### Post by RastaMahata on 2005-05-22
[QUOTE=joplass]I got myself in trouble.  After following the "how to" I can not start my laptop anymore.
I get a blue screen like the one I hate from windows with this message:
"I cannot start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the probem?

Yes                            No

ubuntunotebook login:"

Can someone please help???

Thanks,[/QUOTE]
 sudo apt-get remove xcompmgr transset
sudo gdm

then restore your xorg.conf backup... If you dont have a backup, then create a new xorg.conf file with:
sudo dpkg-reconfigure xserver-xorg
and follow the steps :)

Good luck

---

### Post by joplass on 2005-05-22
sudo dpkg-reconfigure xserver-xorg
Result: sxerver not installed

sudo apt-get install xserver-xorg
Result: couldn't find package xserver-org
I also tried cd /cdrom
and sudo apt-get install xserver-org with the same result.

Any help will be appreciated.

---

### Post by joplass on 2005-05-22
Ok I fixed my problem but of course I will go back to xcmpmgr again  :razz:  :razz:  :razz: has to work for me as well!

---

### Post by robtotheb on 2005-05-24
Wow looks great!  Running on my new computer - AMD3500, Nvidia Geforce 6800 GT etc...  Gnome takes a little longer to load up but its worth it.  Crashes now and then but there is great potential with this.   Next stop [Luminocity](http://www.gnome.org/~seth/blog/xshots) baby!!!!


BTW  Any way to get UT2004 to work while its running?

---

### Post by GoLo on 2005-05-25
Bored typing "transet x"....

I've written a simple transset gui in java. It's in early development but it works. Don't know if i'm gonna make a new version... so I give the sources.

To use it just download the .jar from [here.](http://capitangolo.net/transparencias/transparencias.jar) 

type:
 java -jar transparencias.jar &
and again:
 java -jar transparencias.jar

The first time it loads a server listener and a hidden window.
Second and next, it shows the window :D.

If it works and u like it... add the command at startup and a launcher in desktop ;) no more typing to get transparency.

source code is available [here.](http://capitangolo.net/transparencias/src.tar.gz) 

Note: I tried to get GTKLookAndFeel for the program... but i couldn't. If some one could compile it with it 4 me would be wow...

---

### Post by Spelley on 2005-05-29
Geforce 4 TI cards DO support drop shadows, and I would suggest the same goes for earlier models. I'm not sure what all this "pre-directx 9" stuff has to do with it. If you can enable drop shadows and see them for even a limited time (before a crash) then obviously drop shadows are supported. Unfortunately, the current nvidia drive and xorg revisions (at least on Ubuntu) seem to be causing instability for certain cards (including my Geforce4 Ti4200). I had compositing (drop shadows) running stably on Fedora Core when it was first released back in the fall. As the programmers have fixed parts of their code, other things have gotten broken along the way. Hence, experimental.

---

### Post by Spelley on 2005-05-29
So I have long suspected that I lost dropshadow/compositing stability because of subsequent NVidia releases. That seems to be the case. I've been running drivers 6629 all day with shadows and fading without a crash (normally, X had been crashing within a few minutes). This is with a Geforce4 TI4200.

So anyone with a Geforce4 card (or even earlier) may want to downgrade to earlier drivers if they want the sweet eye candy...
I don't play games or run 3D or twinview/Xinerama, so I can't say how earlier drivers affect that. 

All I did to install the earlier drivers is download the NVIDIA-Linux-x86-1.0-6629-pkg1.run package from the archives on their website:

[http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html)

I removed the NVIDIA-GLX-7174 package using Synaptic (leaving Nvidia-settings & Kernel-nvidia-common installed) and then installed GCC and LINUX-HEADERS for my kernel. I dropped out of X to a console and installed the nvidia package:

sudo sh /.NVIDIA-Linux-x86-1.0-6629-pkg1.run

That was it. I recommend it to anyone with an NVIDIA card experiencing crashing with drop shadows.


SIDE NOTE: 

I disabled the option "AllowGLXwithComposite". It was preventing me from booting into GDM.

---

### Post by pdk001 on 2005-06-01
i've successfully done, and huge lag

---

### Post by banditti on 2005-06-04
say I added those commands to gnome boot and now I can't get back into x.  How do I get them out?

---

### Post by geearf on 2005-06-05
Hello,

i've follow this with kubuntu, and my gf4 ti 4200, like others it just crashed, but it works fine with only the fading.

But then, when i try a glxgears, it seems i have a loss of 50% which is a bit high i think.

I am not quite sur i will let it this way long enough ;(

(Last drivers in apt).

---

### Post by geearf on 2005-06-05
Well in fact, with this i had artifacts in kplayer, and it could hang, so i stopped this fading :(

---

### Post by Paulus on 2005-06-05
Greetings!

GLX works fine for me when xcompmgr is running!!!   Ut2004, glxgears... the lot.   I think it's because i am running **k**ubuntu, because with gnome i had the same crashing problems as described here.   You GF4 users should give the new nvidia drivers a go, xcompmgr seems faster since the upgrade!

---

### Post by lizardking on 2005-06-06
I installed Compositing on my ubuntu hoary folowing the HOWTO but when I go to start xcompmgr** all gnome desktop Envoriment goes away: panel- icons- gdesk - applications and remains only the desktopbackground**. I can move the mouse but not click because I dont have nothing to click and **If I press Ctrl + Alt + Del the X serve does not restart**. Some help??

---

### Post by jonny on 2005-06-06
Don't know what's gone wrong for you, but one possible rescue sequence would be like this:

<ctrl>+<alt>+<F1>

This will give you a full-screen terminal session.  Login, then enter

killall xcompmgr
killall gnome-panel

<ctrl>+<alt>+<F7>

This will return you to Gnome.

---

### Post by lizardking on 2005-06-06
[QUOTE=jonny]Don't know what's gone wrong for you, but one possible rescue sequence would be like this:

<ctrl>+<alt>+<F1>

This will give you a full-screen terminal session.  Login, then enter

killall xcompmgr
killall gnome-panel

<ctrl>+<alt>+<F7>

This will return you to Gnome.[/QUOTE]
**seem to NOT work...** ](*,)

---

### Post by geearf on 2005-06-06
boot in the rescue mode in grub, not the normal mode, log in as root, and do what you need to clean the mess.

(i had to do this :) )

---

### Post by minimidgy on 2005-06-06
I don't think I like it, and it's slowing down my computer. How should I go about uninstalling this?

---

### Post by lizardking on 2005-06-06
What is the mess? Sorry for my English... ( Mess ?=? Problem )
[QUOTE=geearf] what you need to clean the mess.[/QUOTE]



I have already apt-get remove Xcmrmgr so the problem goes away.
[B]But if I want to run Xcmprmgr I can't?  :? 
What is the cause of the problem?[/B]

---

### Post by geearf on 2005-06-06
oh if you already uninstalled it then it's good IMO. :)

---

### Post by frodon on 2005-06-07
Just for information, xcompmgr can generate these problems : 

with Close Session window  => will freeze Gnome. You must kill xcompmgr before using this window. 
And also I needed to disable screensaver because screensaver can generate conflicts with xcompmgr. In my case, each time the screensaver start I was log out of my session (really boring when using amule or bittorrent !).

I hope it's helpful

---

### Post by lizardking on 2005-06-07
**My problem is just bigger**...some help?
> I installed Compositing on my ubuntu hoary folowing the HOWTO but when I go to start xcompmgr all gnome desktop Envoriment goes away: panel- icons- gdesk - applications and remains only the desktopbackground. I can move the mouse but not click because I dont have nothing to click and If I press Ctrl + Alt + Del the X serve does not restart. Some help??

---

### Post by aladdin89 on 2005-06-12
[QUOTE=panickedthumb]if you have xcompmgr start up at gnome login you won't have that problem.[/QUOTE]

Ever notice though, that if you have xcompmgr start up at gnome login, and you set windows to fade in/out, the windows (not menus) fade IN but not OUT?

By the way, I've created a shell script to stop/start transparency -- You can put this on your GNOME panel to quickly kill xcompmgr before you log out, in case you're interested:

```
#!/bin/bash

if [ "$(pidof xcompmgr)" ]
then
        killall xcompmgr
else
        xcompmgr -c -f
fi


```

This script checks to see if xcompmgr is running -- if it is, it kills it, and if it isn't, it starts it up (you can modify "xcompmgr -c -f" with any arguments you like).

---

### Post by Antipop on 2005-06-14
I've got a little problem with xcompmgr, it totally halts my desktop upon starting it. When starting xcompmgr all the action on the desktop comes very slow and moving opened windows leave a "ghost picture" of the window in the former place. 
I'm using fluxbox as my window manager on an ATI -videocard system. Composition is enabled in xorg.conf and everything else is working great. I just can't get any system monitoring software to use transparency (so far I've tried gdesklets and SuperKaramba) and they look pretty ugly with a black box surrounding the meters.  

Could anyone help me with this issue? So far I've had no luck following howto's and other common tips&tricks.

---

### Post by burki on 2005-06-15
i would like to make my terminal look always transparent. But always. How?

---

### Post by frodon on 2005-06-15
[QUOTE=Antipop]I've got a little problem with xcompmgr, it totally halts my desktop upon starting it. When starting xcompmgr all the action on the desktop comes very slow and moving opened windows leave a "ghost picture" of the window in the former place. 
I'm using fluxbox as my window manager on an ATI -videocard system. Composition is enabled in xorg.conf and everything else is working great. I just can't get any system monitoring software to use transparency (so far I've tried gdesklets and SuperKaramba) and they look pretty ugly with a black box surrounding the meters.  

Could anyone help me with this issue? So far I've had no luck following howto's and other common tips&tricks.[/QUOTE]


xcompmgr works well on my computer, i have an AMD athlon 700MHz and a Nvidia FX 5200 graphic card, i try to install it on a friend's computer last week, he has 1.4GHz pentium + ATI graphics card and i have this kind of problem, all become really too slow !!!!!
My conclusion is that xcompmgr work bad (too slow) with ATI cards. Maybe someone use ATI graphic card and run xcompmgr well ? but i nerver met such person

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=frodon]
My conclusion is that xcompmgr work bad (too slow) with ATI cards. Maybe someone use ATI graphic card and run xcompmgr well ? but i nerver met such person[/QUOTE]


Kinda. ATI cards can do the drop shawdows-

the -cC option

But nothing but an Nvidia card can do fading correctly-

the -fF option, my fav.

I bought an Nvidia card to clear up the second problem.

---

### Post by Efwis on 2005-06-15
I tried to run this little thing, and Gnome failed to start completely, once I got past the login screen it just froze up, so I had to remove all aspects of this. Oh well. I will survive, if I wanted shadowing that badly I would stay with windows

---

### Post by ratl3 on 2005-06-24
[QUOTE=burki]i would like to make my terminal look always transparent. But always. How?[/QUOTE]
Well, i wanted the same thing, and here's how i did it.

First, i compiled and installed the patched version of transset, transset-df. This program allows you to set a programs transparency by the window id instead of a click. You can get this program at:
[http://www.forchheimer.se/transset-df/](http://www.forchheimer.se/transset-df/)

Ok, now i need to figure out how to get the window ids for the program i want. I came up with this script (trans-gnometerm) to do that:
```
#/bin/bash
for i in `xwininfo -all -root | grep '      0x........"Terminal' | grep -o '0x.......'`; 
do
	command=`transset-df -i $i 0.8`;
done
```

Now that i've got that worked out, i just run this script when a new bash shell starts. Look in /home/user/.bashrc for the xterm case and add trans-gnometerm somewhere in there.

(my first ubuntu forums post)

EDIT:
Oh, i forgot to say that you need to change the gnome-terminal settings so that it only displays Terminal as the default window title.

---

### Post by vladuz976 on 2005-07-19
[QUOTE=ratl3]Well, i wanted the same thing, and here's how i did it.

First, i compiled and installed the patched version of transset, transset-df. This program allows you to set a programs transparency by the window id instead of a click. You can get this program at:
[http://www.forchheimer.se/transset-df/](http://www.forchheimer.se/transset-df/)

Ok, now i need to figure out how to get the window ids for the program i want. I came up with this script (trans-gnometerm) to do that:
```
#/bin/bash
for i in `xwininfo -all -root | grep '      0x........"Terminal' | grep -o '0x.......'`; 
do
	command=`transset-df -i $i 0.8`;
done
```

Now that i've got that worked out, i just run this script when a new bash shell starts. Look in /home/user/.bashrc for the xterm case and add trans-gnometerm somewhere in there.

(my first ubuntu forums post)

EDIT:
Oh, i forgot to say that you need to change the gnome-terminal settings so that it only displays Terminal as the default window title.[/QUOTE]
 hi following the howto
i get stuck in with the splash screen
i have a nvidia fx440

only way to log in is to comment out the suggested additons to xorg.conf

any ideas?

thanks

---

### Post by frodon on 2005-08-01
Due to some xcompmgr problems (with logout window for exemple) and because sometimes I want to swich off xcompmgr (to play games for exemple) I wrote a small bash script in order to toggle on/off xcompmgr.
1) create a file called toggle_xcompmgr.bash (or what you want) and move it to /usr/bin : ```
sudo mv toggle_xcompmgr.bash /usr/bin/
```
2) edit the file like that (choose the option you want for xcompmgr, I use -fF) : ```
#!/bin/bash
a=`ps -aef | grep -i xcompmgr | awk ' {if ($8 == "xcompmgr"){printf "2"}} '`
if  [[ $a = "" ]]
then
	xcompmgr -fF &
	killall gnome-panel
else
	kill -9 `ps -aef | grep -i xcomp | awk ' {if ($8 == "xcompmgr"){printf $2}} '`
	killall gnome-panel
fi
```
3) make the script executable : ```
sudo chmod +x /usr/bin/toggle_xcompmgr.bash
```
4) right click on gnome panel and add a shortcut, choose custom shortcut in the menu and add /usr/bin/toggle_xcompmgr.bash in the command field.

Now each time you click on the icon xcompmgr is toggled on/off.

---

### Post by pomalin on 2005-08-01
really cool frodon, nice script, thank you.

---

### Post by ishtvan222 on 2005-08-01
That is a very nice script for turning it on and off. Thanks alot. For people who want to have shadows after using the script they will need to edit that script so it starts xcompmgr with the shadow option. There is a problem with this script and gdesklets though. I think it has something to do with gdesklets using its own transparency or that of composite, switching between the 2 causes problems. Thanks for the script.

---

### Post by frodon on 2005-08-02
If you use gdesklet I think the problem come from the killall gnome-panel lines, because the gdesklets icon is on gnome panel and when you kill the panel ... it kill also gdesklet (or gaim for me).
So if you want to solve that, you can remove the killall gnome-panel lines in the script, it will work but when you will maximize a window it will be above gnome-panel (it's why I always do a killall gnome-panel in my script). Maybe it's a better solution for your use ... up to you (otherwise you will have to restart gdesklet after using this script, it's what I do for gaim .. it takes 2 sec to click on the icon  ;-) ).

---

### Post by Sushi on 2005-08-02
Partially off-topic: I find it surprising how many people want to make their terminals transparent. And some want everything to be transparents. I for one can't understand this, since it would make the contents of the windows a lot harder to read. Transparent windows would be perfect for out-of-focus windows, but it shouldn't IMO be used everywhere.

---

### Post by ishtvan222 on 2005-08-02
Thanks alot frodon. I kind of like my maximized windows over the panel since i barely ever use them maximized.

---

### Post by simonjardine on 2005-08-02
Thought i would add a screenshot of my Gnome Desktop, although i use Xfce4 as my default desktop.

Thanks to you guys, i have added transset to some of my windows. Love it works great. Toshiba laptop M30, 528mb, Centrino 1800, 64mb Nvidia.

Love Linux. \\:D/

---

### Post by Aeneas_117 on 2005-08-02
here's my screenshot

---

### Post by simonjardine on 2005-08-04
[QUOTE=kingofhell]it just didnt work for me 
help pls
```
root@ubuntu:/home/tianbo # apt-get install xcompmgr transset
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transset: Depends: libxcomposite1 but it is not installable
            Depends: libxdamage1 but it is not installable
            Depends: libxfixes3 but it is not installable
  xcompmgr: Depends: libxcomposite1 but it is not installable
            Depends: libxdamage1 but it is not installable
            Depends: libxfixes3 but it is not installable
E: Broken packages
```[/QUOTE]
 It works for me, amazing, except i had to stop loading it, as my system will not shut down, any thought on this?
 Help!!
Coz i love it...

---

### Post by simonjardine on 2005-08-05
It Works, very very well! I like it alot.
here is a screenshot using Gnome, I also use Xfce which runs even better, although i would love to know how to start xcompmgr  automaticaly? I have to open a terminal and run xcompmgr -sfF everytime within xfce?? Any help here? \\:D/  :grin:

---

### Post by frodon on 2005-08-05
The answer of this question is in the thread ... add your xcompmgr command in System > Preferences > Session with the wanted option(s), and give the number 0 for this line in order to be sure that xcompmgr is the first application to be launched (important).
I gave also a script (previous page i think) which allow you to toggle on/off xcompmgr with a simple icon.

xcompmgr is so great !!!!!!

---

### Post by catolh on 2005-08-06
For some reason when im using xcompmgr everything gets all screwy.
Screenshot:
[http://home.no.net/catolh/Screenshot.png](http://home.no.net/catolh/Screenshot.png)

In fact, everything is messed up.. :\

I have an ATI card, using the latest fglrx drivers.

Im currently using gdesklets and i need to use xcompmgr to make them transparent..

Help.. :(

---

### Post by simonjardine on 2005-08-06
[QUOTE=catolh]For some reason when im using xcompmgr everything gets all screwy.
Screenshot:
[http://home.no.net/catolh/Screenshot.png](http://home.no.net/catolh/Screenshot.png)

In fact, everything is messed up.. :\

I have an ATI card, using the latest fglrx drivers.

Im currently using gdesklets and i need to use xcompmgr to make them transparent..

Help.. :([/QUOTE]
 I know how to start it up in gnome, I would like to know how to start it automatically in Xfce, any  
ideas? 
 At the moment i use (alt f2) then run xcompmgr -cfF. Thanks.

---

### Post by ishtvan222 on 2005-08-06
To make gdesklets use their xcompmgr for their transparency right click on the gdesklets icon and go to Configuration. Put a check in the box under Xcomposite support. Hope this helps.

To start in XFCE i think you may need to put xcompmgr in your .xfwmrc file.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=catolh]

I have an ATI card, using the latest fglrx drivers.
[/QUOTE]

ATI + xcompmgr = not good time.

---

### Post by orev on 2005-08-07
I tried this with a ASUS (A7VBX-LA) motherboard with integrated graphics (VIA), and it killed x for kubuntu.

---

### Post by Trojan1313 on 2005-08-07
I followed through the whole tutorial and then rebooted. WhenI tried to log in again it stopped (or took to long time for me to wait) when it loaded update-notifier.

This is strange, why did this happend?

Atleast I got the renderaccl-thingie, didn't have that before. :)
Things seem to run smoother now, haven't put it to a lot of stress yet though. :)

---

### Post by Synner on 2005-08-08
It worked perfectly for me, and I've been wanting to get transparencies set for a while.  Thanks!

---

### Post by Trojan1313 on 2005-08-08
The shadows work, but my computer freezes on the fade in/out. I followed the tutorial precisly. GeForce 4 Ti4200.

What's left to do?

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=Trojan1313]The shadows work, but my computer freezes on the fade in/out. I followed the tutorial precisly. GeForce 4 Ti4200.

What's left to do?[/QUOTE]

Nothing. No Nvidia card before the FX series supports shadows. I think its lacks the needed Open GL (which is hardwired into card). Use fading, or Enlightened Gnome's (E17) fake shadows:

[http://www.ubuntuforums.org/showthread.php?t=54476&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=54476&page=1&pp=10)

---

### Post by manicka on 2005-08-08
[QUOTE=poofyhairguy]Nothing. No Nvidia card before the FX series supports shadows. [/QUOTE]
 Will I have issues with a GeForce2 mx400?

---

### Post by Trojan1313 on 2005-08-08
[QUOTE=poofyhairguy]Nothing. No Nvidia card before the FX series supports shadows. I think its lacks the needed Open GL (which is hardwired into card). Use fading, or Enlightened Gnome's (E17) fake shadows:

[http://www.ubuntuforums.org/showthread.php?t=54476&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=54476&page=1&pp=10)[/QUOTE]
Oh shoot. =/


manicka: lol :p

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=manicka]Will I have issues with a GeForce2 mx400?[/QUOTE]

Well....fading should work nicely with official drivers.

Drop shadows won't work on any card older than a 5200FX with official drivers.

(thats why I bought a 5200FX chap on the internet. And I liked it SOO much I sold that and bought a 6600 GT. Full blown eye candy is cool.)

---

### Post by manicka on 2005-08-09
[QUOTE=Trojan1313]Oh shoot. =/


manicka: lol :p[/QUOTE]
 It was a serious question, I know very little about graphics cards as I'm not really into gaming etc. 

If nothing else your reply made me go to the nvidia site and check things out, as I didn't get what was so funny.

:)

---

### Post by Drain on 2005-08-09
[QUOTE=orev]I tried this with a ASUS (A7VBX-LA) motherboard with integrated graphics (VIA), and it killed x for kubuntu.[/QUOTE]

I think I have the same motherboard, but I've got a nvidia card in there as well (5200FX, if I remember right). I'm running Hoary Kubuntu, and XFCE - under XFCE, transparencies and shadows work great, but with KDE, X ends up rebooting on me when I try and run xcompmgr. I didn't catch any error messages when I checked the logs. Freaky. 

I did a quick search of the forums and googled a bit, but didn't see anything that helped. Any suggestions?

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=Drain]I think I have the same motherboard, but I've got a nvidia card in there as well (5200FX, if I remember right). I'm running Hoary Kubuntu, and XFCE - under XFCE, transparencies and shadows work great, but with KDE, X ends up rebooting on me when I try and run xcompmgr. I didn't catch any error messages when I checked the logs. Freaky. 

I did a quick search of the forums and googled a bit, but didn't see anything that helped. Any suggestions?[/QUOTE]

Don't use xcompmgr in KDE. It has a fork of it built in- kompmgr. Its actually a little more stable. Do all of the Xorg stuff in this guide, reboot and then look through the KDe options (the one you need is called "transparancies."

---

### Post by arnoct on 2005-08-10
Whoa, I just wanted to post to say that I haven't used Ubuntu since about a month after I originally posted this but I'm amazed it's still around  :D Finally gone back to it, though.

---

### Post by GoA on 2005-08-14
I also tried the compositing in kubuntu and I managed to get it work. However it was so slooooow that I had to remove it. Maybe because of my Matrox g400 that lacks of performance (but has a nice 2d image quality). :D

---

### Post by Rob2687 on 2005-08-15
[QUOTE=GoA]I also tried the compositing in kubuntu and I managed to get it work. However it was so slooooow that I had to remove it. Maybe because of my Matrox g400 that lacks of performance (but has a nice 2d image quality). :D[/QUOTE]
 The one in the universe is label cvs2004 blah blah...is there a newer version. has anyone tried it?

---

### Post by akutz on 2005-08-21
FYI, I noticed that xcompmgr screws up rdesktop (tsclient).  This is a known bug and this link has a workaround.

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=140511](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=140511)

---

### Post by thebluesgnr on 2005-08-29
I use the following solution for the gnome-logout problem:

Applications -> System -> Configuration Editor

Disable the key:
apps/gnome-session/options/logout_prompt

Now I have to use gdm to reboot/shutdown, but at least everything works easily for the other people in my family who use this computer.

Btw, it works great with my FX5200, hoary system configured as per the instructions. Thank you. :)

---

### Post by thebluesgnr on 2005-08-29
Anyone tried it on breezy yet?

---

### Post by Rinnan on 2005-08-30
You know, I gave up on this method and instead am working on DirectFB -- which on my Nehemiah M12000, is many many times faster and smoother.

---

### Post by the_purulent on 2005-09-01
[QUOTE=brehloi]wow, this is sexy! =P~ 

good work! nice guide

althougth it crashed my pc completely with normal gnome login.
managed to get it working by using a failsafe session en manually starting it.

it is really really nice, seeing forward to a more stable version.

had to remove it for now,  :cry:[/QUOTE]

How do you do this failsafe session thing? I have he same problem, hangs while loading gnome over a grey background and I cannot do anything except move my mouse around :(

---

### Post by frodon on 2005-09-01
[QUOTE=the_purulent]How do you do this failsafe session thing? I have he same problem, hangs while loading gnome over a grey background and I cannot do anything except move my mouse around :([/QUOTE]Personally I kill xcompmgr before logout. I use an icon which run a script to toggle on/off xcompmgr, see previous pages if you want to get this script.
I also saw a thread in this forum which give a way to configure something which make the logout window working with xcompmgr, but it's not a perfect solution.

---

### Post by usergentoo on 2005-09-01
I have the Geforce2Go in my laptop when i add just the line renderaccel true it will not let me login justs locksup and hangs looses keyboard function so i have to hold the power button down till it restarts mouse still moves though.When I remove that line everything is back to normal. Any ideas.

---

### Post by gn0me on 2005-09-02
Tried it with ATI drivers.. if I add the compositing extension (along with all the other config additions.. or even without) it doesn't load the fglrx drivers.. but without the extension it works.  :-\

---

### Post by kamstrup on 2005-09-06
I just discovered that the Fluxbox window manager can utilise transparency! See this thread: [http://www.ubuntuforums.org/showthread.php?t=62834](http://www.ubuntuforums.org/showthread.php?t=62834)

Cheers!

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=usergentoo]I have the Geforce2Go in my laptop when i add just the line renderaccel true it will not let me login justs locksup and hangs looses keyboard function so i have to hold the power button down till it restarts mouse still moves though.When I remove that line everything is back to normal. Any ideas.[/QUOTE]

So....just editing hte xorg file messes it up!?

---

### Post by martijntje on 2005-09-06
[QUOTE=kamstrup]I just discovered that the Fluxbox window manager can utilise transparency! See this thread: [http://www.ubuntuforums.org/showthread.php?t=62834]("http://www.ubuntuforums.org/showthread.php?t=62834")

Cheers![/QUOTE]That IS a nice feature. Unfortunately it's about the only thing i like about fluxbox :( .

I really think a function like that should be added to GNOME.

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=martijntje]
I really think a function like that should be added to GNOME.[/QUOTE]

[http://www.ubuntuforums.org/showpost.php?p=335331&postcount=42](http://www.ubuntuforums.org/showpost.php?p=335331&postcount=42)

---

### Post by | MM | on 2005-09-06
I'm sad.

I can manually launch it from the terminal, but when i try to add the command to the programme list in the Session manager, after i click close and reopen it, its been removed.

Like i said i can launch xcompmgr -fF and it runs all nice and dandy ... but i cant get it to auto-launch from a session :(

I'm using the generic 64bit Hoary ...


Any thoughts

---

### Post by born_confused on 2005-09-06
[QUOTE=| MM |]I'm sad.

I can manually launch it from the terminal, but when i try to add the command to the programme list in the Session manager, after i click close and reopen it, its been removed.

Like i said i can launch xcompmgr -fF and it runs all nice and dandy ... but i cant get it to auto-launch from a session :(

I'm using the generic 64bit Hoary ...


Any thoughts[/QUOTE]
 For me, with an ati card, it doesnt work at all. Just enabling composite in xorg.conf makes the screen garble when starting gdm. I dont know if its the same, but I ran a trial with Linspire five-0 and blimey the shadows were nice.

---

### Post by vayu on 2005-09-10
This is so yum.  I don't think I can do without it.  I'm using -cfF, and it looks so cool.  I'm just starting with Linux and Ubuntu so I havn't finished getting my system set up enough to say how well it works with various applications, but it works really well with just nautilus, Firefox, Terminal and simple apps.  Playing a DVD fullscreen with Xine had a problem with the control continually bleeding through the video.  I easily solved it by closing the control.  For this, I'll sacrifice having to pull the control up manually when I need it.

I hope I don't discover some serious problem with it it because I don't want to give it up.  This effect is so groovy I can easily live with the logoff problem.  All you have to do is press enter, then you come to the login screen and shutdown there, or go to a terminal and "sudo shutdown -h now", if you want to do it in one step.

It is the perfect eye candy.  Not gaudy or flashy just smooth and elegant.  I have only seen OS X being used once, and I thought the window animations were cool, but I could never have them on my system, they were over the top, but these are right on.

---

### Post by bierpullen on 2005-09-10
Thought i would add a screenshot of my Gnome Desktop.
Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.


[http://www.antarctica-rbak.nl/ubuntu/index.php](http://www.antarctica-rbak.nl/ubuntu/index.php)


 :razz:

---

### Post by vvlist on 2005-09-11
Someone mentioned a screenshot being ugly, here's mine :)

---

### Post by gcblig on 2005-09-14
[QUOTE=arnoct](NOTE: THIS ONLY WORKS IN HOARY, DOES NOT WORK IN WARTY. Also, since I use an nvidia card, I'm not sure how well this will work in ATI. I've put in some ATI instructions that I've read but I'm not 100% sure if they'd work.)

I've spent the last day and a half trying to get compositing working in ubuntu. This is actually an amalgamation of a bunch of guides I've found; I shouldn't be given full credit for this.

The first thing you need to do is install xcompmgr and transset. These are found in the hoary universe repositories, if you havent already done so, enable the universe repo in your /etc/apt/sources.list. Its not very hard to do this, search the forums for how to do it :p

```

sudo apt-get install xcompmgr transset

```

xcompmgr is the composite manager (the program/extension that makes things look pretty) and transset sets windows transparencies.

Now, the next thing you have to do is actually *enable* compositing. This is done via a simple edit of your /etc/X11/xorg.conf

```

sudo gedit /etc/X11/xorg.conf

```

Add the following section after the "module" section:

```

Section "Extensions"
	Option 	"Composite" "Enable"
EndSection

```

This tells xorg to enable compositing. Now, just so you know, unless you have a good video card, compositing most likely slow down xorg. Apparantly nvidia cards fare better than ati cards, since you can enable acceleration (which we'll do later) which'll actually make x use your video card for rendering. 

As I said earlier, if you have an nvidia card it'll run better. I'm assuming you've already installed the nvidia binary drivers and such, if you haven't then do so. Add the following lines to the "device" section:

```

	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 

```

"RenderAccel" is actually an option you should already have if you're running an nvidia card, but I've included it incase you haven't put it in yet. I'm pretty sure this only works on nvidia cards; can someone tell me if there's an equivelant for ati?

"AllowGLXWithComposite" is a command that allows you to use OpenGL while compositing is running. Apparantly it can be buggy, though, so if you have problems you might want to disable compositing in your xorg.conf whenever you want to use opengl (just comment out the compositing option with #)

Now, if you have an ati card, add these lines instead:

```

        Option          "backingstore"              "true"
	Option 		"AllowGLXWithComposite" "true" 

```

According to a cached google page, backingstore is "used to enable the server's support for backing store, a mechanism by which pixel data for occluded window regions is remembered by the server thereby alleviating the need to send expose events to X clients when the data needs to be redisplayed."

(Since I don't own an ati card, I apologize if any of my facts are incorrect. If someone with an ati card can correct me, I'll make sure to update this.)

OK, now for the really fun part. We're going to actually set it so compositing is enabled when you start GNOME. Go to system -> preference -> sessions. Go to startup programs, and click "add."

Now, before I continue, I'm going to explain a few of xcompmgr's options:

-c : enable shadows
-s : enable simple shadows
-fF : enable fadeins/fadeouts

You can mix-and-match those commands. For example, if you want just shadows, use xcompmgr -c. If you want simple shadows, use xcompmgr -s. If you want to enable shadows and fadeins, use xcompmgr -cfF. I wouldn't recommend using -cs; that'll probably break the program.

So, where it asks you for the command, enter xcompmgr and then the argument. For example, if you'd like to enable shadows and fadeins/fadeouts, you'd enter:

```

xcompmgr -cfF

```

Finally, in the order, change it to 0. This'll make sure it's the first thing that GNOME runs. Apparantly things run much better this way.

Alright! Now you can restart X (ctrl+alt+backspace), log back in, and you should have compositing running!

**Using Transset**

This is just an extra little command. If you want to set certain windows as transparent, then run the command "transset" in the console. Your mouse will turn into a crosshair; simply click on the window you want to set as transparent. The transparency value can be anywhere from 0 (completely transparent) to 1 (opaque.) It defaults to .75, and back to 1 if the window is already transparent.

For example, if you want to make a window half-transparent:

```

transset 0.5

```

Have fun!

(By the way, I'm running xcompmgr and transset half-decently on a 32mb nvidia card, but I'm only using fadein/fadeout. Your mileage may vary.)[/QUOTE]
 :In Monty Burns words-Excellent! Works well enough for me, and the How To was well written.

---

### Post by TiD on 2005-09-28
Ok, this has crashed my GUI, i can't even login.  It'll show the nvidia splash, crash, show the nvidia splash, crash again then show the nvidia splash once again, then get a blue screen error.

I boot into ubuntu command line and have put a "#" infront of everything i've added in the xorg.conf.  No go.

I think it's crashing when it tries to load the "xcompmgr -cfF" i added to that sessions thing.  Any idea of how to disable it through the command line?

Any suggestions would be much appreciated.

---

### Post by kamstrup on 2005-09-28
Log in to a failsafe session (Choose Session-Failsafe on the login screen). Then run gnome-session-properties (or something like that) from the command line. Remove the xcompmgr startup entry.

Good luck

---

### Post by TiD on 2005-09-28
Thanks for the quick reply.

I can't login to anything the login screen doesn't even show up.  I can only get to "recovery mode" through grub.

---

### Post by hjelm on 2005-10-01
I got same problem as TiD.
I installed, rebooted but now it dosn't start gnome. It says something problem in line 48 so I tried to edit xorg.conf and remove all changes what I have made but Iam total noob about those command-line things so it dosnt save my changes.
I tried run "gnome-session-properties" but it dosn't work and give me warning & error.
:confused:

e// meh, problem solved. for TiD read this thread: [http://www.ubuntuforums.org/showthread.php?t=63820](http://www.ubuntuforums.org/showthread.php?t=63820)

---

### Post by elgx on 2005-10-02
anyone who can say how to use this in kde 3.4?
know it is not the right place to ask but i think most people read this thread, even if they used kde.
so, if you have got a solution...
thanks aniway for the GREAT how-to!
in GNOME it works perfectly!

(the fact is.. i'm totally switchink to Kubuntu now...)

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=elgx]anyone who can say how to use this in kde 3.4?
[/QUOTE]


Do all of the xorg.conf stuff, then open the KDE control panel.

look for the "windows decoration" thing. The last tap will be "transparancies." Turn them on and restart KDE.

---

### Post by Iandefor on 2005-10-02
This is friggin' awesome. Since my computer's older than Methuselah (64 megabytes of ram, 700 megahertz AMD) I didn't really think this would work at all well. Surprise! I'm running it with shadows enabled and transparency on firefox, and it's just as slow as before I added compositing.

---

### Post by elgx on 2005-10-03
[QUOTE=poofyhairguy]Do all of the xorg.conf stuff, then open the KDE control panel.
look for the "windows decoration" thing. The last tap will be "transparancies." Turn them on and restart KDE.[/QUOTE]

well but if i go to the window decoration thing i cannot see that tag ("transparencies")!
here you are:
[IMG]http://img251.imageshack.us/img251/9339/windec6ja.png[/IMG]
is there something wrong in here?  °_°''

---

### Post by razor7 on 2005-10-03
any chance to get this to werk automatically on KDE?

Thanks...

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=elgx]well but if i go to the window decoration thing i cannot see that tag ("transparencies")!
here you are:
[IMG]http://img251.imageshack.us/img251/9339/windec6ja.png[/IMG]
is there something wrong in here?  °_°''[/QUOTE]


If you lack the transparacies tab, then that means you did not set up your Xorg file correctly. Do that part of the how to.

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=poofyhairguy]If you lack the transparacies tab, then that means you did not set up your Xorg file correctly. Do that part of the how to.[/QUOTE]


And looking at it, you are in the wrong place. That why I kinda don't use KDE, its GUIS are confusing.

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=razor7]any chance to get this to werk automatically on KDE?
[/QUOTE]

Like "out of the box?" I don't lead the Kubuntu team, but that will never happen. Why?

1. Its not stable. Not even clsoe. Randomly with both the KDE version and xcompmgr the xserver will crash. No way around it. 

2. You need an Nvidia card AND its closed drivers to work well. A no-no is OSS land.

3. In the future, a better method will be used to have eye candy so this stuff will be obsolete soon. Xcompmgr and its KDE cousin are toys. Simple toys. They are not the future. Xcompmgr has not been worked on since 2004.

4. Did I mention that no compositor in any of the environments are stable? Good. I pick Gnome and xcompmgr over using KDE's or XFCE's built in ones because at some level they all suck, but in Gnome with the script found in this thread its easy to turn off and on xcompmgr.

---

### Post by bryan986 on 2005-10-03
When I add the

```

Section "Extensions"
	Option	"Composite"	"Enable"
End Section

```

to my xorg.conf and restart x, kde will not start at all, just leaves me at a console until I remove that section, any idea why?

---

### Post by poofyhairguy on 2005-10-03
[QUOTE=bryan986]When I add the
```

Section "Extensions"
Option	"Composite"	"Enable"
End Section

```
to my xorg.conf and restart x, kde will not start at all, just leaves me at a console until I remove that section, any idea why?[/QUOTE]

Did you do the "glx with composite" part doo in the device section?

---

### Post by bryan986 on 2005-10-03
[QUOTE=poofyhairguy]Did you do the "glx with composite" part doo in the device section?[/QUOTE]

Thanks for the ultra quick reply, but I got it to work now by doing something esle. I commented out the "GLCore" part in the modules section and it is working great!!

---

### Post by lusepuster on 2005-10-04
#10: 

Have you enabled Universe and Multiverse package repositories? You need to do that. 

By the way: It also works for me fine on the Breezy Preview Release, except that when I try to logout from a session with xcompmgr running, the system would freeze end I'd have to force it down by using the Power button. 

Any idea what should be done?

---

### Post by bryan986 on 2005-10-04
[QUOTE=poofyhairguy]If you lack the transparacies tab, then that means you did not set up your Xorg file correctly. Do that part of the how to.[/QUOTE]

It is in System Settings -> Desktop -> Window Behavior

you can also get to it if you right click on any window title bar and click "Configure Window Behavior" and then select "Transparency"

these settings will apply for all windows

---

### Post by elgx on 2005-10-04
[QUOTE=bryan986]It is in System Settings -> Desktop -> Window Behavior
[/QUOTE]

yeah... here it is.
Thank you very much.
[[IMG]http://img249.imageshack.us/img249/8562/transp18vt.th.jpg[/IMG]](http://img249.imageshack.us/my.php?image=transp18vt.jpg)

---

### Post by luxactor on 2005-10-11
It won't work for me. I have color stripees on my screen, and GNOME freeze on splash-screen. I'm using Breezy and ubuntu nvidia drivers. Can someone help me please?

btw: sorry, if the the answer for my question is allready in the thread

---

### Post by poofyhairguy on 2005-10-11
[QUOTE=luxactor]It won't work for me. I have color stripees on my screen, and GNOME freeze on splash-screen. I'm using Breezy and ubuntu nvidia drivers. Can someone help me please?

btw: sorry, if the the answer for my question is allready in the thread[/QUOTE]

It won't work in Breezy like in Hoary. You must get into Gnome using the failsafe version, and put xcompmgr further back than 0 in the sessions tool. I use position 49.

---

### Post by Fyrzen on 2005-10-25
I've been following this topic for a while now. So far i've managed to get by on my own but now i've hit a snag. Here's my story:

I'm running a Duron 933mhz, 256mb, ti4200. Like everyone else i couldn't get full shadow support with the latest drivers(I used 7667). Fading and simple shadows worked, log out crashes all the same but that's not an issue thanks to aladdin89's shell script. Thanks to Spelley's suspicion I downgraded to 6629. Whaddaya know, it works, shadows look and work great. This was when i started gnome after installing the driver.

But after a reboot X failed to load the Nvidia kernel module. I've been down this road before, install other driver, edit xorg.conf yada yada yada... I opted for a solution instead, luckaly this particular problem is mentioned in the [6629 readme](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6629/README.txt), "(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!".

A simple workaround is to log in at the console and type "sudo modprobe nvidia", then restart gdm. It works this way, i just don't understand why it won't load the module by default. I'm out of ideas. The xorg.conf file is fine, the X log file says it's using xorg.conf. Nothing i change in the configuration has any effect, not even disabling "EnableGLXwithcomp...". Solutions mentioned in the readme don't work either. 

Is there a simple way i could just have the system run these two commands without me typing them and the password?

---

### Post by kamstrup on 2005-10-27
Fyrzen:

[http://www.ubuntuforums.org/showpost.php?p=89594&postcount=18](http://www.ubuntuforums.org/showpost.php?p=89594&postcount=18)

---

### Post by Fyrzen on 2005-10-27
Works like a charm! Thanks! :smile:

---

### Post by Xealot on 2006-01-13
[QUOTE=arnoct]I've been testing xcompmgr with various WMs, they all work with it but some run better than others. For example:

xfce - has a major bug where if certain windows are resized to be bigger, it won't redraw the new part of the window until the window is moved. This bug is also present in GNOME.
fluxbox - seems to work OK, although I'm having problems with fluxbox being stupid :p
openbox - Works very well when xcompmgr is on, but has a major bug where, after it turns on (or off,) apps don't come back as visible--you have to kill them through a console. This is using the verison in the hoary universe repository, I think it's out of date though
icewm - didn't have alot of time to look at it, but it seems to work OK.

So far, I'd recommend openbox (with fbpanel) except for the horrible "windows will disappear" bug.[/QUOTE]


As far as i can tell, the window-will-disappear bug in openbox only affects windows
present on the current workspace, which means if you onlu have ONE terminal open on say workspace 4, and you enable xcompmgr in that terminal, it will disappear and you have to kill it.. But the rest of the windows on the other workspaces will be fine..

Also, just a small notice.. im using a Dell latitude D505 laptop model with the graphics card: (onboard)
```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Devi$        Driver          "i810"
```

and all of the xcompmgr effects seems to slow it down alot..
Oh, and the laptop got a 1500 MHz cpu.

If i can get it to work better, il re-post here later on.

---

### Post by bogoliubov on 2006-01-16
Hmm, I wasn't gonna post anything here since most things have been said at least one time already. But I was looking for a way to use transset automatically on all windows; so if I open, say, a terminal it'll automatically have 0.9 (for instance) in opacity. Does anyone know if this is possible?

In general it works ok. But I can't put xcompgr in the startup for my account. If I do, I get a gray background and a splash screen when logging in, nothing more.
Other have written about this problem when using xcompmgr, but I couldn't find any solution here..., Any ideas?

And, my main question: Does anyone know if/when this will be "naturally" implemented in Gnome, so that you can set this up in systems-prefs-windows (or something similar)?

---

### Post by giannisapatis on 2006-02-22
very nice how to but i dont see any diffirence in my windows?????
does any1 may  know why?

---

