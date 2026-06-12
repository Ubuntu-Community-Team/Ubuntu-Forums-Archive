---
title: "[SOLVED] Automatic startup of 'Firestarter' upon booting up"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Yumpin_Yimminie on 2008-09-24
I've installed the firewall software 'Firestarter.'  I was wondering if it is possible to have it start automatically upon booting up my computer.  My computer is a sole machine connected to the internet via a cable modem.  

I've started the 'Firestarter' installation wizard numerous times but haven't seen an option for having 'Firestarter' start automatically.  

Thanks much.

Have a Great Day,
Jim

---

### Post by handydan918 on 2008-09-24
Firestarter is not exactly a firewall application. It is a graphical user interface for manipulating iptables, which is the program that actually does the firewalling. 
IOW, your firewall is already running at boot. Firestarter is only there for making changes to iptables.

If you want to see why frontends like firstarter are created, open a console and do  ```
man iptables
```

That should fry your brain....

---

### Post by Yumpin_Yimminie on 2008-09-24
[SIZE="2"][FONT="Arial"]Wow ... WOW with a headache attached.  Wow my brain went blank when I opened the terminal and typed in 'man iptables'.  

So what does a guy do who doesn't want to go back and earn a Phd in computer science to do if he wants a firewall to protect things when using Ubuntu or any other Linux flavor package?  

Whoever wrote IPTABLES should probably get a congressional medal of computing and a 5 page letter of thanks from anyone who uses it.  But to a neophyte it's pretty deep, very deep, way over the head deep.  It looks like a person would have to be very well versed in internet connections and packets and whatever.  

Can anyone suggest a firewall package for Ubuntu users like myself.  A package that is pretty much pre-configured.  Just a guy with a sole computer connected to the internet via a cable modem, who wants protection from the mean old world.  My computer is a dual boot system.  I worry about some nasty person coming in from the internet (however they do that) and planting some mean old nasty thing on my multipartitioned hard drive, that finds it's way to Windows XP files and does whatever.  

Or is Ubuntu just going to end up being plaything to most people that have extra hard drive space?[/FONT][/SIZE]

---

### Post by crazypenguin2008 on 2008-09-24
linux and ubuntu are far better at avoiding viruses. windows on the other hand makes a damn good virus finder lol 

id say you are safe on ubuntu juts the way it is in my opinion.

---

### Post by nkri on 2008-09-24
_[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)_

This is a link to getting it to run on boot.  I highly recommend Firestarter to you because you don't really *need* to understand how iptables and stuff like that works.  If you run the Firestarter wizard (which pops up when you run it the first time) and use the default settings for whatever you're not sure about, your computer won't explode.  Besides, you could always go back and change the settings or uninstall later.  I've been using it for about a month knowing nothing about iptables and it has blocked all unwanted connections, leaving the wanted ones open.

Good luck!
-nkri

---

### Post by ByteJuggler on 2008-09-24
Just to be clear:
[LIST]
[*]You don't need the firestarter icon to be visible in order for the firewall to be active.
[*]The firewall in linux (iptables) is always running.  It is part of the kernel.
[*]You use the Firestarter UI to a) change the firwewall settings, and b) monitor the firewall activity in real time via a GUI (avoiding the command line.)  But, the firewall still works even if the Firestarter GUI/icon is not running.
[/LIST]

---

### Post by Mad_Max_1412 on 2008-09-25
> **ByteJuggler said:**
> Just to be clear:
[LIST]
[*]You don't need the firestarter icon to be visible in order for the firewall to be active.
[*]The firewall in linux (iptables) is always running.  It is part of the kernel.
[*]You use the Firestarter UI to a) change the firwewall settings, and b) monitor the firewall activity in real time via a GUI (avoiding the command line.)  But, the firewall still works even if the Firestarter GUI/icon is not running.
[/LIST]

Hi,

I read, in a popular computing magazine in Australia, the following regarding Firestarter:

> Every machine connected to the net should have a firewall, and while the Linux kernel comes with everything you need to do this, it's not enabled by default. Firestarter will do this for you, and with a handy wizard to boot. To install it, run apt-get install firestarter and then launch it from Applications -> Internet. If not already running, launch the wizard using Firewall -> 'Run Wizard'. You can also tailor Firestarter's options from Edit -> Preferences. If you'd like to minimise Firestarter to the tray when closed, tick both 'Enable tray icon' and 'Minimize to tray on close'. Note that even if you close the Firestarter GUI, the firewall is still running as a service and will automatically run at bootup for you. The GUI is handy for tailoring preferences or 'watching' what's happening on the firewall.

Although it mentions at the end that the services are running in the background whether or not the GUI is running, it does seem to imply that Ubuntu doesn't come with the firewall enabled until Firestarter is run for the first time.

Is that how you interpret the magazine article, and is this wrong?

---

### Post by Primefalcon on 2008-09-25
Actual by default Ubuntu doesn't listen to any ports, you install firestarter as a gui method to loosen up protocols so you can do stuff, you don't need to have firestarter running to be safe.

Ubuntu is different from windows apps, Ubuntu has a lot of these safe protocols such as iptables already in place, firestarter is just a gui front end to manage them easily

---

### Post by jakupl on 2008-09-25
So if you don't really know what you are doing, then Firestarter can only make your computer more unsafe.

---

### Post by Primefalcon on 2008-09-25
to read up on it type in your terminal

```
man firestarter
```

---

### Post by ByteJuggler on 2008-09-25
> **Mad_Max_1412 said:**
> Although it mentions at the end that the services are running in the background whether or not the GUI is running, it does seem to imply that Ubuntu doesn't come with the firewall enabled until Firestarter is run for the first time.

Is that how you interpret the magazine article, and is this wrong?

No.  I think perhaps "enabled" was a poor choice of words which is what gives rise to the confusion.  What they probably meant by that is, that without having installed Firestarter, Ubuntu's iptables rules will be at their defaults (which is true), which however is pretty secure by itself (even if it is relatively permissive for *outgoing* connections and services), and so *firestarter's ruleset* will by definition not be "enabled".  Nevertheless, the "firewall", such as it is, is always running.  Whatever ruleset is defined for iptables, is always in force whenever linux runs, whether the (any) GUI program that wrote those rules are (still) running or not.  So, while you need to install Firestarter, and run it to set up your firewalling preferences at least once (so they get written to the iptables config), after that firestarter is not needed to "enable" the settings.  They'll get loaded automatically on boot from the iptables config, where firestarter wrote the rules to the previous time you ran it.  I hope that clarifies things - ask again if you have further questions. 

Edit:  You can check this by using "iptables -L" before and after you've done your firewall config (or run Firestarter once), you'll see the ruleset change.  Then reboot and don't start Firestarter, and check your ruleset again with "iptables -L".  You'll see (as long as the network is up again) that the new ruleset is still being used, in orther words, the "firewall" is running.

---

### Post by Orange_and_Green on 2008-09-25
Good morning everybody :)

I [was told]("http://ubuntuforums.org/showthread.php?t=922163") that firestarter is a discontinued project, so I tried out ufw (which I found was already installed by default) and downloaded its gui gufw from here:

[http://gufw.tuxfamily.org/index.html]("http://gufw.tuxfamily.org/index.html")

as unfortunately it is not on the repositories (yet?). I must say I'm very satisfied. If you like eye-candy, it even comes with an option to display permanently in your taskbar (altough, as the previous posters mentioned, iptables is always running, regardless of whether the gui of the configuration tool is).

Just wanted to share. Have a nice day everyone.

---

### Post by ByteJuggler on 2008-09-25
> **Orange_and_Green said:**
> so I tried out ufw (which I found was already installed by default) and downloaded its gui gufw from here:


Thanks for pointing that out - knew about ufw, but didn't know about gufw.  Learn something new here every day! :)

---

### Post by Pelham123 on 2008-09-25
You can also try...

```

sudo iptables -L

```

and this will display current iptable rules in place...an empty table and therefore no firewall, will look like this...

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by adult swim on 2008-09-25
ufw is easy and is definitely worth learning. to start it [(use ufw to edit your firewall) even though your firewall, iptables is already on by default] you can sudo ufw enable.  then if you want to open a port for torrents or something, you can enter sudo ufw allow portnumber (where portnumber is the port you want open.)  if you want to close the port you have opened you can, sudo delete allow portnumber.  ufw is great, dont let the CLI scare you!

---

### Post by Vishal Agarwal on 2008-09-25
> **Yumpin_Yimminie said:**
> I've installed the firewall software 'Firestarter.'  I was wondering if it is possible to have it start automatically upon booting up my computer.  My computer is a sole machine connected to the internet via a cable modem.  

I've started the 'Firestarter' installation wizard numerous times but haven't seen an option for having 'Firestarter' start automatically.  

Thanks much.

Have a Great Day,
Jim

Just go to the system > administration > preferences > session.

There you can add the firestarter to start automatically.

---

### Post by Yumpin_Yimminie on 2008-09-25
Many thanks for taking the time to address my concerns.

Have a Great Day,
Jim

---

