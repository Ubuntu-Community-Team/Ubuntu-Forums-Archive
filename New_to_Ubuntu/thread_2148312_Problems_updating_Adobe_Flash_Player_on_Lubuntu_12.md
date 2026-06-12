---
title: "Problems updating Adobe Flash Player on Lubuntu 12.04"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by Florio on 2013-05-24
My young son regularly plays a particular online game for children. Today when he logged on, he was told he had to update the Adobe Flash Player. I've tried updating it but evidently without sucess as he continues to receive the same message. Could someone kindly walk me through the installation process here? (I'm an experienced Windows user but know next to nothing about Linux). For example, which of the four options given for Linux on the Adobe site should I choose? Once I've downloaded the update, where do I go to retrieve, open and install it?

Thanks to whoever can be bothered taking the time to reply.

P.S., I've tried using the terminal and typing in** sudo apt-get update** followed by **sudo apt-get install flashplugin-installer**, but this seems to have created problems, and I've received the following messages:

W: Failed to fetch cdrom:// Lubuntu 12.04_Precise Pangolin_Release i386  (2012043)/dists/precise/main/binary - i386/Packages  Please use apt -  cdrom to make this CD-ROM recognized by APT. apt-get update cannot be  used to add new CD-ROMs.

W: Failed to fetch cdrom:// Lubuntu 12.04_Precise Pangolin_Release i386  (2012043)/dists/precise/multiverse/binary - i386/Packages  Please use apt -  cdrom to make this CD-ROM recognized by APT. apt-get update cannot be  used to add new CD-ROMs.

W: Failed to fetch cdrom:// Lubuntu 12.04_Precise Pangolin_Release i386 (2012043)/dists/precise/restricted/binary - i386/Packages  Please use apt - cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs.

W: Failed to fetch cdrom:// Lubuntu 12.04_Precise Pangolin_Release i386  (2012043)/dists/precise/universe/binary - i386/Packages  Please use apt -  cdrom to make this CD-ROM recognized by APT. apt-get update cannot be  used to add new CD-ROMs.

E: Some index files failed to download. They have been ignored, or old ones used instead.

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/precise/partner](http://archive.canonical.com/ubuntu/precise/partner) i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precised partner binary_i386 Packages)

W: You may want to run apt-get update to correct these problems.

E: Unable to locate package flashplayer-installer

---

### Post by lethall1 on 2013-05-24
```
sudo nano /etc/apt/sources.list
comment with '#' all lines with "cdrom" word
sudo apt-get update
sudo apt-get install -f 
sudo apt-get install flash...
```
By the way chrome or chromium works just fine with there own flash plugin. And there is custom flash player for mozilla, which can be installed from addons by keyword "flash linux"

---

### Post by Florio on 2013-05-25
Thanks  a lot for your reply, lethall1, but I don't really understand what I have to do. I've tried to locate the custom flash player for mozilla, but the keyword "flash linux" produces no result.
Could you give me some more precise instructions? (Please bear with me; as I've explained I know next to nothing about Linux!!:()



> **lethall1 said:**
> ```
sudo nano /etc/apt/sources.list
comment with '#' all lines with "cdrom" word
sudo apt-get update
sudo apt-get install -f 
sudo apt-get install flash...
```
By the way chrome or chromium works just fine with there own flash plugin. And there is custom flash player for mozilla, which can be installed from addons by keyword "flash linux"

---

### Post by lethall1 on 2013-05-25
There is no problem )
```
sudo nano /etc/apt/sourses.list
```
this command opens terminal text editor "nano", with input file sourses.list, where are list of sources described. 
List of sources is just a link for appropriate programs for your OS, and if you have installed OS from DVD image, you are able to install packages from this disk, becouse DVD image contains not just OS image, but some packages too.
And you had ejected you installation disk, thats why you see this warning:
> [COLOR=#000000]W: Failed to fetch cdrom:// Lubuntu 12.04_Precise Pangolin_Release i386 (2012043)/dists/precise/main/binary - i386/Packages Please use apt - cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs.[/COLOR]
Thats why you need to comment cdrom in sources.
```
sudo apt-get update
```
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)
sorry, but wiki better describes than me.

about mozilla... Yea i can't see that addon now, but i was using it for a while, long ago )
i think you must install not flash installer, but plugin himself
```
sudo apt-get install adobe-flashplugin
```

---

### Post by Impavidus on 2013-05-25
> **Florio said:**
> 
P.S., I've tried using the terminal and typing in** sudo apt-get update** followed by **sudo apt-get install [COLOR=#ff0000]flashplugin-installer[/COLOR]**, but this seems to have created problems, and I've received the following messages:
(...)

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/precise/partner](http://archive.canonical.com/ubuntu/precise/partner) i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precised partner binary_i386 Packages)
(...)

E: Unable to locate package [COLOR=#ff0000]flashplayer-installer[/COLOR]
There is a duplicate source too, so while you're at it you can remove that one too.

You said you gave the command to install **flashplugin-installer**, but apt-get complains it can't find **flashplayer-installer**. **flashplayer-installer** doesn't exist as far as I know, **flashplugin-installer** should work. There are different roads to Rome (is that expression known in English?) and installing **adobe-flashplugin** should work too.

---

### Post by Florio on 2013-05-25
Thanks Impavidus (and lethall1). I originally installed Lubuntu via a USB memory stick, and so the references to the CD-ROM messages must refer to the USB.

How do I remove the duplicate source?

I tried the command **sudo apt-get install adobe-flashplugin** and it seems to have installed the plugin (removing the adobe flashplayer installer). I was advised to run apt-get update again. I did this, but once again got all the messages about the CD-ROM and the duplicate. 

When my son tries to play his online game, he's still told to update the adobe flash player!!

Don't know where to go from here.](*,)






> **Impavidus said:**
> There is a duplicate source too, so while you're at it you can remove that one too.

You said you gave the command to install **flashplugin-installer**, but apt-get complains it can't find **flashplayer-installer**. **flashplayer-installer** doesn't exist as far as I know, **flashplugin-installer** should work. There are different roads to Rome (is that expression known in English?) and installing **adobe-flashplugin** should work too.

---

### Post by lethall1 on 2013-05-25
paste here 
```
sudo cat /etc/apt/sourses.list
sudo apt-cache search flashplayer
```
Why dont you want install chrome or chromium? It uses his own flash, and there is no problems whith it.
```
sudo apt-get install chromium-browser
```
or go to 
[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
download and run .dep package, or from terminal run
```
sudo dpkg -i /path/to/downloaded/package.deb (by default is ~/Downloads/google-chromeXXX.deb)
```

---

### Post by Florio on 2013-05-25
Thanks a lot, lethall1.

I'll try what you've suggested and see how it goes. I'll get back to you and let you know...;)




> **lethall1 said:**
> paste here 
```
sudo cat /etc/apt/sourses.list
sudo apt-cache search flashplayer
```
Why dont you want install chrome or chromium? It uses his own flash, and there is no problems whith it.
```
sudo apt-get install chromium-browser
```
or go to 
[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
download and run .dep package, or from terminal run
```
sudo dpkg -i /path/to/downloaded/package.deb (by default is ~/Downloads/google-chromeXXX.deb)
```

---

### Post by newb85 on 2013-05-25
I'd just like to throw out there the thought that instructing someone in Absolute Beginners to edit a file using a curses-style editor is perhaps not the most helpful.

```
sudo leafpad /etc/apt/sources.list
```

would probably make life easier.  ;)

@Florio - installing Chrome will address the flash player issue, but not the package management issue, which you should definitely try to fix.

Run ^that command^ and add a # symbol at the beginning of each line that begins with "cdrom://".  Save the file and exit the editor.

---

### Post by Florio on 2013-05-25
Thanks newb85. Forgive my apparent ignorance, but what do exactly do you mean by ^that commandì^? Linux really is a mystery for those of us weaned on Windows!!
Just another thing...  How do I save the file (I presume you mean the the terminal commands)?


> **newb85 said:**
> I'd just like to throw out there the thought that instructing someone in Absolute Beginners to edit a file using a curses-style editor is perhaps not the most helpful.

```
sudo leafpad /etc/apt/sources.list
```

would probably make life easier.  ;)

@Florio - installing Chrome will address the flash player issue, but not the package management issue, which you should definitely try to fix.

Run ^that command^ and add a # symbol at the beginning of each line that begins with "cdrom://".  Save the file and exit the editor.

---

### Post by lethall1 on 2013-05-25
> [COLOR=#000000]I'd just like to throw out there the thought that instructing someone in Absolute Beginners to edit a file using a curses-style editor is perhaps not the most helpful.[/COLOR]
Ok sorry, i'll take your advice. I thought that nano is very simple than vi, but i forgot about graphical editors.

---

### Post by newb85 on 2013-05-25
> **Florio said:**
> ...what do exactly do you mean by ^that commandì^?

The command
```
sudo leafpad /etc/apt/sources.list
```
will open a graphical text editor with the file sources.list.  I'm not familiar with leafpad (regular Ubuntu uses gedit), but I'm sure once you're there, you'll be able to figure out how to save the file.

---

### Post by Florio on 2013-05-25
I'm installing Chromium. Up until now I've had Mozilla Firefox as my browser. What's the command for deleting it? I'd prefer to have just the one browser due to limited disk space.

---

### Post by Florio on 2013-05-25
Hi newb85,
I've followed your instructions. The only problem is that there are no lines beginning with "cdrom://". Should I have first run sudo apt-get update?

---

### Post by lethall1 on 2013-05-25
```
sudo apt-get autoremove firefox
```
> [COLOR=#000000]The only problem is that there are no lines beginning with "cdrom://".[/COLOR]
paste please output of sources file
```
sudo cat /etc/apt/sources.list
```

---

### Post by Florio on 2013-05-25
Update. Even with Chromium installed, I still get the message telling me that I need to install the latest version of adobe flash player.

Since I'm using two different computers -- my own laptop with Windows, and my son's netbook with Lubuntu -- I've had to save the file to a USB memory stick and upload to my computer. Hope you can make sense of it:
```

deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```

---

### Post by lethall1 on 2013-05-25
comment the fiest line in this file
> [COLOR=#000000]deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe[/COLOR]

> #[COLOR=#000000]deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe[/COLOR]

Then paste in terminal
```
sudo apt-get update && sudo apt-get upgrade
```

that command will install all new packages, perhaps flash would update too.
and if that would not help(do not forget to reopen browser) try to install it

```
sudo apt-get install flashplugin-installer 
```

if installation procces complete whithout errors test flash in both browsers (if you are still able).

---

### Post by monkeybrain2012 on 2013-05-25
> **Florio said:**
> I'm installing Chromium. Up until now I've had Mozilla Firefox as my browser. What's the command for deleting it? I'd prefer to have just the one browser due to limited disk space.
I am not sure why lethall1 told you to install Chromium if your issue is flash version not sufficiently updated. Chromium and Firefox uses the same flash plugin!

If you need pepper flash you have to install Chrome the real thing, not Chromium which is an outdated and crippled version of Chrome and with less than half the features of Firefox so you get the worst of all worlds. Just head to Google, grab the .deb installer for Chrome that matches your architecture (32 or 64 bit), right click to install and that's it. :)

---

### Post by newb85 on 2013-05-25
I'm not sure where all the hate for Chromium comes from.  No, it doesn't run Pepper Flash by default (a commonly missed fact), but aside from that, I'm not sure why it gets poo-pooed so much.  I used it for quite a while with no complaints.  I recently switched to Chrome, and to be honest, I still haven't discovered anything that I've gained by the switch.

Also interesting,
[http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

---

### Post by monkeybrain2012 on 2013-05-25
> **newb85 said:**
> I'm not sure where all the hate for Chromium comes from.  No, it doesn't run Pepper Flash by default (a commonly missed fact), but aside from that, I'm not sure why it gets poo-pooed 

Well pepper flash is what would solve OP's problem since the site he visits appears to require up to date flash, if Chromium doesn't have it then it is not the solution, if it has nothing to do with the problem why recommend it?

```

Also interesting,
[http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

```

But why would you want to go through the hoop to install pepper flash on Chromium while you can just get Chrome the real thing?  It seems even more pointless as you have to download Chrome in the first place in order to extract pepper flash and put it in Chromium.

---

### Post by Impavidus on 2013-05-26
The latest Adobe flash player available for Linux is version 11.2. Adobe will not provide any later versions, only backports of security patches. Flash for Windows or Mac supports version 11.7, as does pepper flash. Apparently the site you visit insists on a flash player > 11.2.

---

### Post by Florio on 2013-05-26
Thanks to everyone who has contributed to this post. Quite frankly, I'm now very confused. Lubuntu was working perfectly until a few days ago, and I would not have touched it if the game that my son plays (Club Penguin) hadn't insisted upon upgrading adobe flash player. As things currently stand, I have removed Firefox and substituted it with Chromium, but to no avail since the adobe flash player apparently still needs to be updated.

If I understand correctly, at this stage I should replace Chromium with Chrome, which includes Pepper Flash. As for removing duplicate files, I ought to follow lethall1's advice.

Please correct me if I am wrong. I'll wait for further instructions before doing anything else!!:confused:

---

### Post by newb85 on 2013-05-26
Yes, at this point you should probably either install Chrome or follow the instructions [here]("http://www.webupd8.org/2012/09/how-t...sh-player.html") to have Chromium use Pepper Flash.  I'm guessing Chrome will be easier.

---

### Post by Florio on 2013-05-26
I appear to have successfully installed Chrome and removed Chromium, and my son's game now seems to be working, so the necessary flash player upgrade has worked.
However I am unable to carry out lethall1's other instructions. I cannot 'comment' that line in the terminal. Is there some particular procedure for typing in the terminal once you've run a command?
I think there is a larger problem there, but don't know what it is nor how to deal with it.

---

### Post by monkeybrain2012 on 2013-05-26
> **Florio said:**
> I appear to have successfully installed Chrome and removed Chromium, and my son's game now seems to be working, so the necessary flash player upgrade has worked.
However I am unable to carry out lethall1's other instructions. I cannot 'comment' that line in the terminal. Is there some particular procedure for typing in the terminal once you've run a command?
I think there is a larger problem there, but don't know what it is nor how to deal with it.

Well the easiest way is to just use the synaptic package manager to manage your sources list, it comes with lubuntu (look under Administration or System, forgot which) Open Synaptic, go to system > Repositories and then you can uncheck the box with cdrom. After that, close the "Repositories" window and click "Reload" on the upper left hand corner on Synaptic and that's it. 

Alternatively, you can use leafpad to edit the sources list (which open up in the text editor after running the command "sudo leafpad /etc/apt/sources.list") as new85 said, "comment out" means putting the # in front of the targeted line. The instruction to use nano just makes things unnecessarily cryptic and complicated for new users.


BTW, you don't need to remove Firefox, It may not have the most up to date flash but I think it is a better browser overall. Also, many non flash media content plays only in Firefox because those Linux media plugins don't work in Chrome or Chromium. I have both FF and Chrome but use FF as my main browser, Chrome mainly only when a site needs up to date flash. Also if you have two version of flash installed (one from flash-plugin in system,one from Chrome) Chrome may get confused. Open Chrome, type about:plugins in the url bar, then click "Details" and look up Adobe Flash, there are two entries, disable the one that says version 11.2.

---

### Post by Florio on 2013-05-26
Thanks for all your help, monkeybrain2012. I've unchecked the cdrom box as you suggested. 

I thought I'd removed Firefox, but it turns out that it is still on the computer. I also prefer it to Chrome and Internet Explorer, but this particular netbook has very little disc space and memory, and so I thought it might have been better to have just the one browser.

Thanks again,

Florio






> **monkeybrain2012 said:**
> Well the easiest way is to just use the synaptic package manager to manage your sources list, it comes with lubuntu (look under Administration or System, forgot which) Open Synaptic, go to system > Repositories and then you can uncheck the box with cdrom. After that, close the "Repositories" window and click "Reload" on the upper left hand corner on Synaptic and that's it. 

Alternatively, you can use leafpad to edit the sources list (which open up in the text editor after running the command "sudo leafpad /etc/apt/sources.list") as new85 said, "comment out" means putting the # in front of the targeted line. The instruction to use nano just makes things unnecessarily cryptic and complicated for new users.


BTW, you don't need to remove Firefox, It may not have the most up to date flash but I think it is a better browser overall. Also, many non flash media content plays only in Firefox because those Linux media plugins don't work in Chrome or Chromium. I have both FF and Chrome but use FF as my main browser, Chrome mainly only when a site needs up to date flash. Also if you have two version of flash installed (one from flash-plugin in system,one from Chrome) Chrome may get confused. Open Chrome, type about:plugins in the url bar, then click "Details" and look up Adobe Flash, there are two entries, disable the one that says version 11.2.

---

### Post by syntaxerror74 on 2013-10-03
Greetings!  I've run into this problem as well (Lubuntu 13.10 beta 2 for the record) and I've decided to publish a solution for it. 
This problem mainly exists on **old Athlon XP** CPUs. I don't know what CPU the OP has, but this might as well be an Athlon XP box (like mine). These machines do not have the **SSE2** hardware extension, and 11.2.202.* were all built with that extension active! And it's binary-only, so you cannot make any changed nor look inside. Basically it's a CPU-related issue.  

Since I got aware that an early version of a Google Chrome v19 flash plugin worked perfectly with non-SSE2-capable CPUs, I've decided to do the following:  

- used adobe-flashplugin_11.2.202.228-0maverick1_i386.deb as a basis 
- modified this package so that it installs 11.2.202.236 instead (Non-SSE2 build packaged with earlier Google Chrome v19.x) 
- rebuilt the .deb package 

 This should avoid all fiddling once and for all, especially for new users who might rather ruin something vital on their systems if they try the other "solutions" provided.

The package can be downloaded here:

  [http://www65.zippyshare.com/v/78802631/file.html](http://www65.zippyshare.com/v/78802631/file.html)  

Don't use aptitude here, but install with

```

$ sudo dpkg -i adobe-flashplugin_11.2.202.236-no-sse2.deb

```

NOTE: You might have to remove other conflicting installations first, but dpkg will complain when you have to do so.
**Please DO NOT force installation ****under any circumstances ** (by setting an option to dpkg, meant for *highly experienced* users who know what they're doing). When dpkg complains, it's for your own good. :)

Not only am I honored to do something for this great community, I'm also happy to use the zippyshare service for something fully legal for a change.
Please tell me if there are any problems. I've removed and installed it twice, and it worked a treat.

---

