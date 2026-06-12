---
title: "Eee PC: Light stays on after shutdown"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Sii on 2008-08-22
Hi, my first post here!  [img]http://Si6776.www.idnet.com/smileys/red-face.gif[/img]

Just bought an Asus Eee PC, but the Xantros software wouldn't connect to the network using WPA, so I was advised to install Ubuntu.  Connection is now fine, and I'm slowly finding my way round, but I have a couple of questions:

1. When I shut the machine down, a little green light with what looks like a light bulb above it, stays on, and the only way to get rid of it seems to be to remove the battery.  This didn't happen with the Xantros installation, so I'm, assuming this is something to do with the shutdown process?  The unit also stays quite warm underneath while the light is still on after shutdown.

2. I would like to use the SeaMonkey browser suite, and found it in Synoptics Package Manager, but the version there is 1.1.9, and the latest version on the [**Mozilla Website**]("http://www.seamonkey-project.org/") is 1.1.11.  Is there a way to update the package?

3. I get a password request each time a network connection is started.  As I am the only user, this is quite annoying.  Is there any way to switch this off?

Many thanks!

Simon.  :)

---

### Post by forger on 2008-08-22
1. Just checking, are you sure you're using System > Quit > **Shut down**?
(Don't use hibernate or suspend)
2. If there's no security or very very very big functionality improvement, you probably won't find it updated (maybe in 8.04.2?)
There's an update package in the intrepid release (still in development) - [http://packages.ubuntu.com/intrepid/seamonkey](http://packages.ubuntu.com/intrepid/seamonkey) (you click on the link just under the **architecture column**)

---

### Post by Sii on 2008-08-22
> **forger said:**
> 1. Just checking, are you sure you're using System > Quit > **Shut down**?
(Don't use hibernate or suspend)

Umm... I click the little man in the lower right hand corner, and choose Shut Down.  Shouldn't that do it?  [img]http://Si6776.www.idnet.com/smileys/dunno.gif[/img]

> 2. If there's no security or very very very big functionality improvement, you probably won't find it updated (maybe in 8.04.2?)
There's an update package in the intrepid release (still in development) - [http://packages.ubuntu.com/intrepid/seamonkey](http://packages.ubuntu.com/intrepid/seamonkey) (you click on the link just under the **architecture column**)

Thanks, but I'm only 2 days into this, so I'm still very much feeling my way, and I wouldn't know what to do with that.

---

### Post by forger on 2008-08-22
About 3, System > Administration > Network > Unlock, then Wireless connection > Properties > uncheck roaming mode and enter your network details

---

### Post by Sii on 2008-08-22
Thanks.  That won't stop me being able to connect to a wi-fi spot away from home, will it?

---

### Post by forger on 2008-08-22
> **Sii said:**
> Umm... I click the little man in the lower right hand corner, and choose Shut Down.  Shouldn't that do it?
I don't have a running man here on my Ubuntu, but do you select "shut down" afterwards? If it goes down directly, try doing it the way I said, maybe that man is a hibernation shortcut or something :)

> **Sii said:**
> Thanks, but I'm only 2 days into this, so I'm still very much feeling my way, and I wouldn't know what to do with that. 
Ah, then you better stick around with what you have, you can play in the dirt after you get the feeling :)

---

### Post by Sii on 2008-08-22
Oh, and going back to Sea Monkey, where's the profile located?  I want to import my bookmarks, saved cookies and passwords from my Windows machine.  Is it just a case of over writing the existing files, as I would usually do?  I did notice that this didn't seem to be possible in the 'built in' Firefox profile.

---

### Post by Sii on 2008-08-22
> **forger said:**
> I don't have a running man here on my Ubuntu, but do you select "shut down" afterwards? If it goes down directly, try doing it the way I said, maybe that man is a hibernation shortcut or something :)

The running man or the power button both bring up the window of options, with hibernate, suspend, restart and shutdown options.  I select the shutdown option, but I'll try it your way.  :)

---

### Post by forger on 2008-08-22
> **Sii said:**
> Thanks.  That won't stop me being able to connect to a wi-fi spot away from home, will it?

Hmm if you're always connecting to various wi-fi spots, I think there's a way to create "profiles" (?)
Try installing the package wifi-radar, execute this command in Applications > Accessories > Terminal:
```
sudo apt-get install wifi-radar
```

(The app is in Applications > Internet > Wifi-Radar)
I don't have a wifi here, but I think that if you create a "new" profile there you can use multiple wifi access points

Also, make sure you **check roaming mode** in the Network (a.k.a. undo what I mentioned before)

---

### Post by forger on 2008-08-22
> **Sii said:**
> Oh, and going back to Sea Monkey, where's the profile located?  I want to import my bookmarks, saved cookies and passwords from my Windows machine.  Is it just a case of over writing the existing files, as I would usually do?  I did notice that this didn't seem to be possible in the 'built in' Firefox profile.

I think these will be helpful:
[http://www.ehow.com/how_2033289_import-bookmarks-seamonkey.html](http://www.ehow.com/how_2033289_import-bookmarks-seamonkey.html)
[http://kb.mozillazine.org/Import_bookmarks](http://kb.mozillazine.org/Import_bookmarks)

I also believe that you are able to simply copy over your windows account, execute this in Terminal:
```
nautilus $HOME/.mozilla/firefox/
```
[COLOR="Red"]**Warning! Could break stuff!**[/COLOR]
First off, close firefox
It will open up the firefox configuration folder, delete the folder you see there and profiles.ini and copy over the folder and profiles.ini from your Windows "application data" folder (more info [here]("http://kb.mozillazine.org/Profile_folder_-_Firefox"))

There must be a similar folder for seamonkey, but I don't know it :)

---

### Post by Sii on 2008-08-22
OK, thanks for your help.  Unticking Roaming Mode, and setting up the network, actually lost the connection, so I'm not sure what happened there, but I've gone back to how it was.  The password dialogue box I was referring to, is something about a 'keyring', and needs the system password, not the WPA key, in case there was any confusion.  :)

---

### Post by forger on 2008-08-22
Hm.. keyrings are set up in Applications > Accessories > Passwords and Encrypted keys
I think this could help, Edit > Preferences > PGP passphrases > "always remember passphrases when logged in" and uncheck the "ask me before using a cached passphrase"
Close seahorse (the "Passwords and Encrypted keys" window), log out and log in again, it should work fine now I think

---

### Post by Sii on 2008-08-22
OK, thanks, I'll try that.

Main problem at the moment is it not powering down properly.  I used the Stystem > Quit method, and the light still stays on, further to which, I have just discovered, it won't boot up again while in this state, until I remove and replace the battery, which is a pain, to say the least!

---

### Post by forger on 2008-08-22
You could search your problem on google:
[http://www.google.com/search?q=asus%20eeepc%20ubuntu%20shut%20down%20properly](http://www.google.com/search?q=asus%20eeepc%20ubuntu%20shut%20down%20properly)
:)

> The EeePC does not turn off when set to shutdown. This is due to a module not being removed and the sound subsystem remaining active (Bug #126140). 
[https://help.ubuntu.com/community/EeePC/Fixes#Shutdown](https://help.ubuntu.com/community/EeePC/Fixes#Shutdown)
[https://help.ubuntu.com/community/EeePC/TODO](https://help.ubuntu.com/community/EeePC/TODO)

[http://www.nerdlogger.com/2008/05/asus-eeepc-installing-ubuntu-804.html](http://www.nerdlogger.com/2008/05/asus-eeepc-installing-ubuntu-804.html)
> # Note that ubuntu does not shut down the Eee properly. Shutting down your Eee will make the screen go entirely blank, but does not cut the power, and you will have to force it to fully shutdown by holding the power button.


---

### Post by Sii on 2008-08-22
Honestly, this is so frustrating!!

I found this on eeewiki:

> Some users have reported that when they shutdown Ubuntu, the screen goes blank, but the power light remains on. If you are having this problem, then try the following:
Open a Console window using Ctrl-Alt-T
edit the file /etc/default/halt:
sudo vi /etc/default/halt
Add the following line at the end of the file:
rmmod snd-hda-intel
save the file (:wq in vi) and reboot.

OK, so how do you edit the file?  I can't get the cursor to move past the 't' in halt and all this fiddling about on a tiny screen, is driving me nuts!!  ](*,)

---

### Post by Sii on 2008-08-22
Ah, sorry, didn't see your post above.  Will try it that way.

---

### Post by lswest on 2008-08-22
for information, I advise you to use nano as you're a beginner, vi always seems to be less intuitive.  To insert (or edit) the file, hit "I", then when you're done, hit esc, then type ":w" then ":q" (without the quotes) (this is for vi) or else in nano just edit, and ctrl + x to exit.

---

### Post by Sii on 2008-08-22
What astonishes me is how (and why!) anyone learns all these different commands.  It's like a foreign language to me, and compared to Windows, in which you just click and install stuff, it seems ridiculously complicated.  

Thanks for the help, guys, it now does power off fully.  I'll give it a few more days, but I can see me not having the patience for Linux, and installing Windows XP on it before long.  :)

---

### Post by lswest on 2008-08-22
> **Sii said:**
> What astonishes me is how (and why!) anyone learns all these different commands.  It's like a foreign language to me, and compared to Windows, in which you just click and install stuff, it seems ridiculously complicated.  

Thanks for the help, guys, it now does power off fully.  I'll give it a few more days, but I can see me not having the patience for Linux, and installing Windows XP on it before long.  :)

You don't have to do it using commands, most things can be done with a GUI, however, in the case of giving help, commands are universal, whereas GUIs can change.  Makes it easier for those offering help.  It's up to you what you use though.  Glad we could help.

---

### Post by forger on 2008-08-22
Some of these commands look pretty frustrating at the beginning, but don't let that make you quit. If you don't want to learn anything new, then you probably should stick with Windows, Ubuntu is based on GNU/Linux which is in a lot of ways different :)
You just need to "get the hang of it", just like when you ride your bike the first time - tweaking tweaking and before you know it, you're racing with no hands ;)
The console is really powerful if you care enough to read the manual or even ask someone how to do something, or even search for it, the internet is the learning place for everyone!

An off-topic example:
 Imagine you want to get an updated list of all the servers for the [Undernet IRC Network]("http://www.undernet.org") in order to be able to update your IRC server list, otherwise you're stuck with ol' rusty non-working servers.
 I use **curl**, **pcregrep** and **sed** and here's where **[regular expressions]("http://www.regular-expressions.info/")** come along.
The plan:
1) get the site with the servers, which is [http://www.undernet.org/servers.php](http://www.undernet.org/servers.php) and we'll use the **curl** command
2) grab the sites, using **pcregrep** command
3) output them the way you want them, using **sed** command

Regex or regexp (short for regular expressions) allow you to make a complex text string with which you can search with precision what you need.

Now the commands; either **man command** or **command --help** (or -h) will eventually show you a way to use the command.

> 
sed --help
  -e script, --expression=script
                 add the script to the commands to be executed


Knowing my regex and how to use the commands, I eventually came up with this:
```
curl -s http://www.undernet.org/servers.php | pcregrep -i "\.(?:\w\w)\.undernet\.org" | sed -e 's/<[^>]*>//g' -e 's/\s*//g'
```

And the output:
> Vancouver.BC.CA.Undernet.org
bucharest.ro.eu.undernet.org
Diemen.NL.EU.Undernet.Org
Ede.NL.EU.UnderNet.Org
Elsene.Be.Eu.undernet.org
graz.at.Eu.UnderNet.org
Helsinki.FI.EU.Undernet.org
Lelystad.NL.EU.UnderNet.Org
oslo.no.eu.undernet.org
trondheim.no.eu.undernet.org
Zagreb.Hr.EU.UnderNet.org
Dallas.TX.US.Undernet.org
mesa.az.us.undernet.org
mesa2.az.us.undernet.org
newyork.ny.us.undernet.org
SantaAna.CA.US.Undernet.org
Tampa.FL.US.Undernet.org

---

### Post by Sii on 2008-08-22
The trouble for me is, and I don't want to sound as though I'm making excuses, but there's only 24 hours in a day.  I work daytimes, and I am also a sole parent for a lad with special needs, so he takes up the rest of my time, apart from trying to grab a few hours sleep each night.  I do love my computer though, and gadgets in general.  I help to run two internet forums, one being basic PC help, the other being a specific ISP support forum, but in more of a 'host' capacity, as I don't class myself as being particularly technically adept.  

My 'day job' is driving kids to school on a contract for the local education authority, and in between the school runs, I drive a taxi.  I have been keeping track of the two forums via WAP on my phone, but the interface is limited, to say the least, so I thought that the Eee PC would be something I could take to work with me, and fiddle with while I sat in the car waiting for my next fare, also making it easier to keep track of the forums.  Whilst I knew Linux would be 'different', I was expecting some sort of intuitive interface in which to work, not to have to spend weeks learning all sorts of command codes (although, I take on board what was said earlier).

A good example of how frustrating it can be, happened just now.  I decided to install the Epiphany browser, just to try, as Firefox seemed to be having problems with flash animations on websites (yes, I have the Adobe plug-in), so I went to Synoptics Package Manager, found what I wanted, ticked the box to install, clicked Apply, it all happened, but where the heck do I now find it?  I want a desktop icon, one click and it's there, not to have to learn some sort of command code.  I want to launch a simple web browser, not a NASA space shuttle!  :biggrin:  Do you see what I'm getting at?  Nothing is intuitive, *nothing* is simple! 

I'm sure, given enough time, I would start to get the hang of it, but having time to learn even the basics, is something I don't have.  Hell, I can't even work out how to turn the sound volume down, so I'm not blasted out with that start music every time I turn the thing on!  

Anyway, thanks for letting me have a moan, and thanks for the help you've given me so far.  I'm sure I'll be back for more, just as soon as I can summon up the patience to dive into it again.

[img]http://Si6776.www.idnet.com/smileys/01-cheers-sig.gif[/img]

---

### Post by anjilslaire on 2008-08-22
You can find the new applications in the menus at the top bar of the screen. I'm using Kubuntu, so I don't recall the Gnome menu name, but its listed in there with all of the other applications. 

It should be simple enough to create a desktopn shortcut, however.

---

### Post by Sii on 2008-08-22
> **anjilslaire said:**
> You can find the new applications in the menus at the top bar of the screen. I'm using Kubuntu, so I don't recall the Gnome menu name, but its listed in there with all of the other applications. 

Was just about to come back and say, it appeared in the Applications list when I rebooted.

> It should be simple enough to create a desktop shortcut, however.

It is - providing you can find the program in the first place!  :biggrin:

---

### Post by lswest on 2008-08-23
About the system sound, you can go to system-->administration-->login window and under one of the tabs (can't recall which one right this second) you can disable the sound.  I know what you mean with being assaulted by it :P

If memory serves, there's another one under administration (or maybe preferences) that's system sounds, where you can disable the sound that occurs when you log in.  (the above one is for the sound when the login screen is ready).

Sorry I can't be more precise, it's been a while since I used GNOME (using openbox on my laptop these days).  Also, if you don't have time to learn, I'd suggest using whatever your comfortable with.  Who knows, maybe you'll find time later and decide to come back?

Also - my hat's off to you for being able to juggle all that on a daily basis!

---

### Post by Sii on 2008-08-23
> **lswest said:**
> About the system sound, you can go to system-->administration-->login window and under one of the tabs (can't recall which one right this second) you can disable the sound.  I know what you mean with being assaulted by it :P

Thanks.  I'm leaving it alone today, but will have another play tomorrow, when I have more time.

> If memory serves, there's another one under administration (or maybe preferences) that's system sounds, where you can disable the sound that occurs when you log in.  (the above one is for the sound when the login screen is ready).

I think I found that, but couldn't work out which bit did what, and as it happened, they all seemed to be off.

> Sorry I can't be more precise, it's been a while since I used GNOME (using openbox on my laptop these days).  Also, if you don't have time to learn, I'd suggest using whatever your comfortable with.  Who knows, maybe you'll find time later and decide to come back?

Sorry to sound negative.  It's not that I don't want to learn new things, it's just frustrating when everything you try to do seems like an obstacle course, compared to Windows.  I will pursue it, in dribs and drabs, until I get it working how I want it to, then will probably leave it at that.

> Also - my hat's off to you for being able to juggle all that on a daily basis!

Thanks.  It's not always easy, but it's how it is.  :)

---

### Post by dnns123 on 2008-08-23
Hi! I'm not sure if you've fixed your shutdown problem (didnt read the whole thing), but I'll give the step by step.

1. In the command line, type "sudo gedit /etc/default/halt"
2. Type your password (A notepad-like text editor will show up; hurray for GUI)
3. Add the following line at the end of the file: "rmmod snd-hda-intel"
4. Save the file (ctrl+s)
Thats it; from what I can read in the quote anyway.

> 
Some users have reported that when they shutdown Ubuntu, the screen goes blank, but the power light remains on. If you are having this problem, then try the following:
Open a Console window using Ctrl-Alt-T
edit the file /etc/default/halt:
sudo vi /etc/default/halt
Add the following line at the end of the file:
rmmod snd-hda-intel
save the file (:wq in vi) and reboot.

edit: Oops! Didn't read that you've fixed it. Even I dont know how to use vi :P

---

### Post by Sii on 2008-08-23
Thanks, yes I did manage to do it yesterday, but doesn't this show, once again, how difficult this can be to understand?  Already, there have been three different suggested commands (vi, nano and gedit), which achieve the same thing, only in more or less intuitive ways!  How the heck anyone learns this stuff is beyond me, but all credit to you guys who have, as if it wasn't for you helping numpties like me, my Eee PC would have gone in a passing dustcart by now.  :)

---

### Post by philinux on 2008-08-23
For basic text file editing gedit is my choice.

If you look back at the windows world, only if I have to he says, of commercial,freeware and shareware dont you find that there's more than one free firewall or virus checker etc etc. Same thing with linux text editors and other apps.

---

### Post by Sii on 2008-08-23
> **philinux said:**
> For basic text file editing gedit is my choice.

If you look back at the windows world, only if I have to he says, of commercial,freeware and shareware dont you find that there's more than one free firewall or virus checker etc etc. Same thing with linux text editors and other apps.

Well, yes there is, but you don't have to know all sorts of different commands to try them.  You just install and uninstall in a couple of clicks, and you don't *need* to know all the technical stuff.

That said, I have to admit, the Synopsis Package Manager is quite easy to use, and having everything under one roof, so to speak, does have it's advantages, and presumably, if you stick to the Ubuntu approved stuff, you know it's safe, and it's going to work, unlike some Windows utilities.

---

### Post by philinux on 2008-08-23
True. Mind you I think the problems you've had affect only a minority of hardware configurations. Mine worked out the box with no editing of config files.

Also remember that windows mainly comes preinstalled on hardware known to work with it. Installing an OS from scratch on unknown hardware is occasionally going to need tweaking.

---

### Post by lswest on 2008-08-24
Also, I don't find you're being negative.  I completely understand your thoughts on the matter.

One comment on the commands though, they are (usually) just the name of the program.  So if, for example, you installed a program called nvidia-settings, to launch it you could go to system-->administration-->Nvidia Settings, or just type "nvidia-settings" in the terminal.

And, in case you want to know, below are a few useful commands listed that come pre-installed.

*sudo* - stands for Super User DO, meaning running a command with this preceeding it will run it with root permission (e.g. full control, giving you access to all the files on the eeePC).  Graphical version is gksudo (for GNOME).

*man* - stands for MANual, and gives you a manpage (text document with information on using a command).  Usage is: man *program name*

*iwconfig* - text-based configuration for wireless, and ifconfig is for wired connectiong/hardware information.

*lshw* - lists hardware information (very useful if you need help with hardware-specific problems)

*ls* - stands for list, and lists the content of a) the directory you're in if there is no argument given or b) the directory given as an argument.

*rm* - command to ReMove files or folders.

*cat* - outputs the content of a file to the terminal without actually opening the file.

*grep* - program that can search through inputted data and display only information that contains the argument supplied.

These are just a few small ones I use almost every day.  Before running any of these commands please run man *command* for a better understanding of what it does, to prevent you from causing yourself any problems.  (yes, even man man works :P)

If you don't feel you need or want this info, you can just ignore it.

All the best,
Lswest

---

### Post by Sii on 2008-08-24
Thanks, that will be useful to refer to.  [img]http://Si6776.www.idnet.com/smileys/thumb.gif[/img]

---

### Post by philinux on 2008-08-24
Don't forget that the main strength of Ubuntu is this forum/community.

---

### Post by lswest on 2008-08-24
Thanks for all the thanks Sii, and I agree with philinux, this community is great.  I hope it all goes well for you, and don't hesitate to ask any more questions you might have!

---

### Post by Sii on 2008-08-24
Yes, it does seem a nice community here.  There's nothing worse than going to a new forum, and being told to 'use the search button', if you dare to ask a question that someone else might have asked thousands of posts earlier.  I don't tend to visit those.  :)

---

### Post by Fredk on 2008-08-29
I have the same problem on my new EeePC. I am booting ubuntu from a memory card. But it fails to shut down propoerly - leaving the power light on. Only by cold start (if that what you call using the  end of a paper clip) or by removing and replacing the battery can i get it to reboot.  If I remove my memory card I can still boot and close down using the original Linux OS.
I am a complete newbie with ubuntu - but any help would be appreciated.

---

### Post by Sii on 2008-08-29
Hi Fred,

The solution I posted earlier in the thread worked for me, with a little help from some friends here.  ;)

Open a Console window using Ctrl-Alt-T

edit the file /etc/default/halt:
```
sudo nano /etc/default/halt
```
Add the following line at the end of the file:
```
rmmod snd-hda-intel
```
save the file and reboot.

Hope that helps, if not, someone else will along soon, I'm sure.  :)

---

### Post by Fredk on 2008-08-29
I have a new EeePC and have Ubuntu on a memory card, whildt keeing the ordinal Xandros OS on the hard drive.
Ubunto opens and accesses wireless etc.  but refuses to shut completely down - leaving th the little power light still on. It then refuses to boot up until I do a cold start (if that's what you call poking the end of a paper clip in the apprpriate hole!)  or else removing and replacing the battery.  The original OS closes down O.K. but not Ubunto.  I am still a raw newbie when it comes to Linux - so can anyone advise?

---

### Post by wolfen69 on 2008-08-29
> **Fredk said:**
> I have a new EeePC and have Ubuntu on a memory card, whildt keeing the ordinal Xandros OS on the hard drive.
Ubunto opens and accesses wireless etc.  but refuses to shut completely down - leaving th the little power light still on. It then refuses to boot up until I do a cold start (if that's what you call poking the end of a paper clip in the apprpriate hole!)  or else removing and replacing the battery.  The original OS closes down O.K. but not Ubunto.  I am still a raw newbie when it comes to Linux - so can anyone advise?

the answer is right above your post. i will repost it changing one thing. (thanks sii, you're already giving back!)
open a terminal, and:

edit the file /etc/default/halt: by


```
gksudo gedit /etc/default/halt
```

Add the following line at the end of the file:


rmmod snd-hda-intel

save the file and reboot.

---

### Post by Fredk on 2008-08-29
Thanks again = it did the trick  - after i had worked out how tro open aconsole window - since control - alt - t didn't seem to work.
I said I was a complete newbie to Liunux !!!

---

### Post by Sii on 2008-08-29
Actually, Ctrl+Alt+T doesn't work for me either,  I have a Terminal shortcut on my desktop to make it easier.

I have to be honest, guys, I think I'm going to admit defeat with this, and load XP onto the Eee PC.  It's one thing learning a new OS, but having to keep resizing stuff so I can read it, and half the time, finding the bit I need is off the bottom of the screen, doesn't make things any easier.  I do have an old Windows PC, which is currently sitting idle, but still has stuff on it to be recovered.  When I get round to doing that, I may well give this another go, as I think it would be easier to learn on a 'proper' machine.

---

