---
title: "HOWTO: Screenlets for Feisty or Edgy"
date: 2007-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by sorcererx84 on 2007-05-15
**The author of Screenlets is _RYX aka Rico Pfaus_**
Screenlets are small owner-drawn applications (written in Python, a very simple object-oriented programming-language) that can be described as "the virtual representation of things lying/standing around on your desk". You van read more about them at  This Howto will help to install Screenlets in Ubuntu Edgy or Feisty the easy way.

[IMG]http://compiz.org/images/thumb/e/e1/Zerofour.png/750px-Zerofour.png[/IMG]

**_Step 1: Add the Ubuntu repository to your sources (if you are using Edgy, replace feisty with edgy everywhere)_**

Make yourself root with
```
sudo -s
```
and run the following command
```
echo "deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets" >> /etc/apt/sources.list
```

**_Step 2: Add the repository signing key to your trusted APT keys_**

Run:
```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add -
```

**_Step 3: Update package listings and install the packages_**

Update package listings with:
```
sudo apt-get update
```
Then you can install all packages with:
```
sudo apt-get install screenlets screenlets-core screenlets-extra screenlets-utils
```

There should now be a item under Menu>Accessories. Use that to start screenlets. Then you can access the  Control panel from the tray icon. To start screenlets automatically when you log in, add ```
screenlets-tray
``` to your session's startup programs.

To uninstall, just run:
```
sudo apt-get remove --purge screenlets screenlets-core screenlets-extra screenlets-utils
```

_**Links:**_
[The "official" home of screenlets]("http://forum.compiz.org/viewtopic.php?t=358")
[Third-party sreenlets site]("http://hendrik.kaju.pri.ee/screenlets")
[Ubuntu repository]("http://hendrik.kaju.pri.ee/ubuntu")

---

### Post by FunnyLookinHat on 2007-05-16
The repositories listed above aren't quite correct...  there are instructions on the actual page here:
[http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/)

---

### Post by hexo1125 on 2007-05-17
I use this in lieu of adesklets...
I find the widgets/screenlets still lacking, but I can really see potential in this.

Thanks!!

---

### Post by sorcererx84 on 2007-05-17
The screenlets repository is located at [http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/)
The 'all' component includes packages from all repositories, not only screenlets.

---

### Post by kayef on 2007-05-18
i cant install it, it says the package screenlets is invalid

how come?

---

### Post by sorcererx84 on 2007-05-19
Sorry, there was a typo in a command. Try simply 'sudo apt-get install screenlets'

---

### Post by B3rs on 2007-05-22
Thank you for your efforts! Can you also add an unistallation method to the first post?

---

### Post by foureight84 on 2007-05-23
oo nice

---

### Post by foureight84 on 2007-05-23
i can't find instructions on how to hide the widgets.

---

### Post by glennric on 2007-05-23
> **FunnyLookinHat said:**
> The repositories listed above aren't quite correct...  there are instructions on the actual page here:
[http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/all/)

sorcererx84:  You should edit your initial post to fix this.  It is not the 'all' that is the problem.  It is the lack of the '/ubuntu' in the address that is the problem.   The correct apt source line is
```
deb http://hendrik.kaju.pri.ee/ubuntu feisty all
```
or
```
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```

---

### Post by sorcererx84 on 2007-05-23
Updated the repository address and added uninstall instructions. Please update your sources.list!

---

### Post by DARKGuy on 2007-09-23
screenlets-tray doesn't seem to be working... when I run "screenletsd start" all I get is:

Screenletsd isn't used for starting screenlets anymore. Please use the new 'screenlets-manager' or start each Screenlet individually from now on.

And when I run screenlets-manager, it says there's an error about the daemon not being initialized and that some widgets may not work or be started, so I get no screenlets at all.

Any help? distro is Ubuntu 7.04 x64

---

### Post by benhur99ph on 2007-09-28
Okay. So I had a problem installing screenlets using the repo:

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

There is always an error saying no GPG found or something. 

I found an easier way. To all those having problems with the said repo, try this: (Ubuntu Feisty)

1.) On the terminal, type  sudo gedit /etc/apt/sources.list
2.) Add this line: deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) feisty screenlets
3.) Save and exit sources.list
4.) On the terminal, type: sudo apt-get update
5.) Then type: sudo apt-get install screenlets
6.) Then when its done go to System>Preferences>Screenlets
7.) Choose your desired screenlets

If you want to hide your screenlets use the "Widget Layer" in compiz and right-click on a screenlet and select "window" then choose "widget". Now the screenlets will hide and only show when you activate the "Widget Layer" (F9).

Hope this helps.

---

### Post by elcasey on 2007-10-01
Is that some really old version of screenlets from the TuxFamily repo? There was a seriously curtailed list of themes for the Clock screenlet and no Weather screenlet at all. What gives?

---

### Post by Whise on 2007-10-01
heres some more 
[http://gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=165](http://gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=165)

---

### Post by skattman83 on 2007-10-02
> **benhur99ph said:**
> Okay. So I had a problem installing screenlets using the repo:

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

There is always an error saying no GPG found or something. 

I found an easier way. To all those having problems with the said repo, try this: (Ubuntu Feisty)

1.) On the terminal, type  sudo gedit /etc/apt/sources.list
2.) Add this line: deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) feisty screenlets
3.) Save and exit sources.list
4.) On the terminal, type: sudo apt-get update
5.) Then type: sudo apt-get install screenlets
6.) Then when its done go to System>Preferences>Screenlets
7.) Choose your desired screenlets

If you want to hide your screenlets use the "Widget Layer" in compiz and right-click on a screenlet and select "window" then choose "widget". Now the screenlets will hide and only show when you activate the "Widget Layer" (F9).

Hope this helps.

I followed this, but when I log in, the screenlets crash compiz.  I installed compiz-extra to provide the widget layer functionality.  When the computer starts, the widgets come up with a black border, but if i disable/re-enable desktop effects, the widgets disappear and they only reappear if I press F9.  Is anyone else experiencing this problem?

---

### Post by rmfought on 2007-10-14
> **benhur99ph said:**
> Okay. So I had a problem installing screenlets using the repo:

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

There is always an error saying no GPG found or something. 

I found an easier way. To all those having problems with the said repo, try this: (Ubuntu Feisty)

1.) On the terminal, type  sudo gedit /etc/apt/sources.list
2.) Add this line: deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) feisty screenlets
3.) Save and exit sources.list
4.) On the terminal, type: sudo apt-get update
5.) Then type: sudo apt-get install screenlets
6.) Then when its done go to System>Preferences>Screenlets
7.) Choose your desired screenlets

If you want to hide your screenlets use the "Widget Layer" in compiz and right-click on a screenlet and select "window" then choose "widget". Now the screenlets will hide and only show when you activate the "Widget Layer" (F9).

Hope this helps.

MIght want to add the GPG key download command to this list:

    wget [http://download.tuxfamily.org/screenlets/hendrikkaju.gpg](http://download.tuxfamily.org/screenlets/hendrikkaju.gpg) -O- | sudo apt-key add -

I get an error on startup, "Unable to connect or launch daemon. Some values may be displayed incorrectly."  The clock doesn't work for me, just blank.  The picture frame image load screen does not show jpgs, and hangs when I try to select an image.  So far, works great!  LOL

---

### Post by lunamystry on 2007-10-21
Uhm... How do I solve this? 

> Fetched 41.1kB in 7s (5693B/s)                                                 
Reading package lists... Done
W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
lunamystry@michelle:~$ 

I added this: deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets 
 
to my source list and then tried t get the key wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

I then tried to install screenlets but nothing. So I downloaded the tar and used make install but i don't know how to launch it if it is installed.

---

### Post by Naikei on 2007-10-22
[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users]("http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users")
The above link to instructions worked fine for me... Seems the official website is useful! Who would have thought?

---

### Post by yizuman on 2008-02-10
Seems someone needs to rewrite the whole instruction on page one as none of it on this thread works.

---

