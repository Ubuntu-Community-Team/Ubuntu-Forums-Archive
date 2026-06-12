---
title: "HOWTO: E17 using the repository provbied by Elive"
date: 2005-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by SFN on 2005-08-31
[COLOR=Red]OK. This HOWTO does some things that some people consider dangerous to your Ubuntu installation. The only reason to do this is if you are one of the "e17 Crackheads"(TM). I can tell you that I have done everything shown here on both a fresh install and an existing one and it works. That doesn't mean it will work for you. It probably will but it may not. If you don't have any intention of dealing with your install getting farked, you shouldn't do this.

I would.

But I wouldn't recommend that you do.

But I would.
[/COLOR]

In theory, this HOWTO is complete but in reality, it's a work in progress.

First, I wish to thank Smoon for all the work that he did on the Ubuntu repository for e17. With his departure, many have been looking for other ways to get e17 installed and working. This is an attempt to document a setup that works as easily as using Smoon's repo. Because the process is so similar, I used the Smoon HOWTO written by Tab to avoid extra typing. Only a few items have changed but I thought a separate thread would be helpful.

A new version of Elive was released on August 30, 2005. While checking it out, I noticed that they had also added a repo that "works also for debian or ubuntu". So I tried it out. It works like a charm, with a few tweaks.

There are apt sources for x86, AMD64 and PPC. This HOWTO only deals with x86 but should work for all three. Here's the scoop.

First, you are going to need some debs direct from Debian (this is the part that I would do but I wouldn't recommend that you do but I would do anyway). 

Get:

libc6 from [here](http://packages.debian.org/stable/base/libc6) 
libc6-dev from [here](http://packages.debian.org/stable/libdevel/libc6-dev) 
libc6-i686 from [here](http://packages.debian.org/stable/libs/libc6-i686) 
locales from [here](http://packages.debian.org/stable/base/locales) 
libvorbis0a from [here](http://packages.debian.org/stable/libs/libvorbis0a)
libextractor1 from [here](http://packages.debian.org/stable/libs/libextractor1)  

(Note: for all of the links above, scroll down to where it says "Download". There you will find versions for multiple architectures. Remember though, that this theoretically only works for x86, AMD64 and PPC. Maybe not even AMD64 and PPC.)

Then do 

sudo dpkg -i /location/of/libc6_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/libc6-dev_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/libc6-i686_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/locales_2.3.2.ds1-22_all.deb
sudo dpkg -i /location/of/libvorbis0a_1.1.0-1_i386.deb
sudo dpkg -i /location/of/libextractor1_0.4.2-2_i386.deb

Once you are done, you may want to reboot. (I know, I know, it's not necessary to reboot. You can just restart certain services. Alright, Uncle! I'll fess up - I have no idea which services I should restart. Do you? I don't even know if there is a point to restarting at this point. Do you? If you do, restart the services. If not, take two minutes out of your life and reboot.)

Now, add the Elive repository to your apt sources.list. Do:

```
sudo gedit /etc/apt/sources.list
``` 

At the bottom of the list, add:

> ## e17 repository from Elive
deb [http://www.vobcopy.org/mirror/elive/](http://www.vobcopy.org/mirror/elive/) elive main efl elive 


Next, create and open the apt preferences file:

```
sudo gedit /etc/apt/preferences
``` 

and add the following to it:

> Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999 

Update apt:

```
sudo apt-get update
``` 

and install e17

```
sudo apt-get install e17
``` 

Once that's done, you have e17 installed. Log out, log into E, and enjoy!

Optionally, you can also install extra programs and modules. To install all of them, do:

```
sudo apt-get install engage eclair elicit entice examine e-modules e-utils evidence
``` 

Here are the modules listed above:

e-modules - These add functionality and eye-candy to the Enlightenment desktop outside of those included in E.
engage - An OSX-style dock.
eclair - Media player.
elicit - Magnifier/color dropper.
entice - Image viewer.
examine - Configuration utility.
e-utils - Enlightenment utilities.
evidence - The Enlightenment fIle manager
eterm - The Enlightenment terminal

I've taken entrance (the Enlightenment login manager) out of this HOWTO for the time being. It would appear that entrace 1) causes gdm to be removed and 2) doesn't work. So you get no login manager. Not the end of the world but annoying.

The other piece that this does not provide that Smoon's repo did is the image viewer eclips. I'll see what I can find for getting that done easily.

To use engage, you need to enable it. Do:

```
enlightenment_remote -module-load engage
``` 

Then, click on the desktop, mouse over Configuration, mouse over Applications and mouse over Modules, then mouse over Engage. Then click Enabled.

You can edit the items on the engage bar two different ways. The first way I will detail in the following paragraph uses a program called entangle. entangle is still very buggy. You will see a number of complaints about it if you read this whole thread. You may want to use the second method I mention here. But first, entangle.

Click on the desktop, mouse over Configuration, mouse over Applications and click Menu Editor. In the new screen that opens up, click the button that says Engage. Drag programs from the bar on the left into the blank area under the buttons. When you have the programs you want, click the button marked Save, then click the button marked Quit. You might have to click Quit twice. That seems to happen on and off.

The second way to do this is to build an .eap file (basically a shortcut with an icon attached) for the the program you want to add to engage. From the e17 User Guide:

> 
Once you've opened an application you want to make an icon for, click the top left corner (but not the border!) [Note from SFN: Basically, this is the icon in the top left-hand corner ofg the broder - or where there would be one if one does nto exist] with the left mouse button and select "Create Icon". This menu can also be reached by right clicking the application name section of the window decorations. This starts e_util_eapp_edit, so you'll have to have e_utils and all its dependencies installed in order for it to work.

Add all the information you need, but ignore the "Window name" section. That needs to be left empty. Then select an icon file. It can be of any size - it will be resized with Imlib2. The bigger the file, the more memory it uses. Note that you don't have to have the full path for the executable - just the name of the program is ok too, assuming the program is in your path. The EFL GUI for selecting icons is a bit unstable currently and is under heavy development. It should work though, but it may sometimes ignore input for example. After the icon is made the original icon picture isn't needed anymore for the icon to work. It will be included in the created EAP file and is automatically moved to ~/.e/e/applications/all

Now you just need to edit the .order file for engage:

```
sudo nano ~/.e/e/applications/engage/.order
``` 

In the file that opens up, just add the name of the .eap file. Let's say you created one that runs "gksudo synaptic" and you called it "Synaptic.eap". You just need to add that .eap file on its own line. So the resulting file should look something like:

eterm.eap
xmms.eap
mozilla-firefox.eap
Synaptic.eap

Save and close that file and you're all done.

If you want to adjust the engage bar (like maybe center it on the bottom of the screen) right-click on it and choose Edit Mode at the bottom of the popup menu. You can then right-click on it again and you will have a whole bunch of options available to you. When you have it the way you want, right-click it again and choose End Edit Mode.

To change the command that engage executes when you click on a particular icon, right-click on the icon, Icon Options/Edit Icon.

Note: It has been reported that you may have to do 
```
sudo apt-get install engage-module
``` 
or perhaps even 
```
sudo apt-get install engage-module engage-manager
``` 
to get engage to work properly. Do so if you find that it';s not doing what it should.

A quick perusal of the repo at [http://www.vobcopy.org/mirror/elive/pool/elive/e/](http://www.vobcopy.org/mirror/elive/pool/elive/e/) revelaed some nifty treasures. These can be had via Synaptic by searching on the package name elive.

The coolest of these is e17genmenu. It adds in all of your menus from either Gnome or KDE. After installing it, do:

```
e17genmenu -g
``` for Gnome or

```
e17genmenu -k
``` for KDE

If you click on the desktop, you will see a menu item named Modules. Mouse over it and a menu will open with a number of modules, some of which are already on your desktop. There are other modules that don't show up on that menu. They are:

flame - shows glowing flames at the bottom of your desktop
snow - shows Christmas trees and falling snow on your desktop
notes - a desktop sticky notes module - (DOES NOT CURRENTLY WORK) 
monitor - A system monitor - tracks CPU, network and memory usage
weather - display the weather on your desktop *(buggy - see note bleow)

To load these modules, do:

```
enlightenment_remote -module-load *module*
``` 

Obviously, replace *module* with the actual name of the module.

**********
Currently, the weather module causes e17 to freeze up whenever I try to change the geographical location. Not living in or anywhere near Kirkenes Lufthavn, this is a bit of a problem for me. The problem appears to stem from the length of the menus that contain the continents, countries, states and cities.

I got it to work but the solution is just plain dumb. I edited /usr/lib/e_modules/weather/dir.xml so that only places I knew I was interested in (the town where I live, the town where I grew up, the location of my next vacation) were listed. Dumb but it works. YMMV
**********

If click the desktop again and go to Modules, you will see your newly loaded modules there. You can enable them by mousing over them and choosing Enable from the resulting menu.

For Enlightenment themes, backgrounds, modules and more visit [Get-e.org](http://get-e.org)  and the [Edevelop Forum](http://edevelop.org/forum) .

I hope this helps everyone wanting to use e17.

The Elive people have done some great work here. For those that only grabbed the repo, Elive is a live-cd designed to show off Enlightenment. It has both e16 and e17.

They definitely deserve some kudos for their work.

The site is [http://www.elivecd.org/](http://www.elivecd.org/)

This may be full of typos. And I'm OK with that.

---

### Post by rpgcyco on 2005-08-31
Cool, works OK. Though there are some packages mentioned as upgrades, which do not install because of dependency issues. I guess that's what you can expect from mixing repos. ;)

- Rpg Cyco

---

### Post by shanghaipi on 2005-08-31
This is what I got on the last step...


localbob@ubuntu:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17: Depends: efl-all (= cvs20050828) but it is not going to be installed
E: Broken packages

that smiley face is an 8 with a ).

---

### Post by SFN on 2005-08-31
Odd.

Go to Synaptic and do a seacrh on efl-all. Let me know what it shows for the latest version there.

When I do that it shows both the latest and  the installed version as cvs20050828. I did an apt-get update right before that.

---

### Post by shanghaipi on 2005-08-31
I found it on synaptic, but when applying, it conked out and gave me this:

efl-all:
 Depends: libxine-dev but it is not going to be installed
 Depends: libimlib2-dev but it is not going to be installed or
 	libimlib2-dev but it is not going to be installed

---

### Post by SFN on 2005-08-31
Do:

```
sudo apt-get -f install
```

That *may* take care of it.

---

### Post by SFN on 2005-09-01
Also, if that doesn't work, post the contents of /etc/apt/sources.list here.

---

### Post by shanghaipi on 2005-09-01
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## e17 repository from Elive
deb [http://www.vobcopy.org/mirror/elive/](http://www.vobcopy.org/mirror/elive/) elive main efl elive

---

### Post by SFN on 2005-09-01
Weird. I have the identical sources. (Well, I have the Skype repo as well but that shouldn't make a difference).

What do you get if you do

```
sudo apt-get install libxine-dev
``` 
?

---

### Post by shanghaipi on 2005-09-01
localbob@ubuntu:~$ sudo apt-get install libxine-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine-dev: Depends: libxine1 (= 1.0.1-1elive1) but it is not going to be installed
E: Broken packages

---

### Post by SFN on 2005-09-01
Hmm. And if you do 

```
sudo apt-get install libxine1
``` 
?

---

### Post by rpgcyco on 2005-09-01
They do not install because the version of libc6 in Ubuntu Hoary is older then the version required.

- Rpg Cyco

---

### Post by SFN on 2005-09-01
I'd say that too except I've got the Ubuntu versions installed and it worked for me.

---

### Post by shanghaipi on 2005-09-01
won't install either...

---

### Post by rpgcyco on 2005-09-01
Yeah, that's certainly odd. I've attached a screenshot of the error, just to confirm.

- Rpg Cyco

---

### Post by Weav on 2005-09-01
[QUOTE=shanghaipi]This is what I got on the last step...


localbob@ubuntu:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17: Depends: efl-all (= cvs20050828) but it is not going to be installed
E: Broken packages

that smiley face is an 8 with a ).[/QUOTE]

I have the same problem, i was able to install e17 but none of the "addons" work.

---

### Post by bam on 2005-09-01
[QUOTE=Weav]I have the same problem, i was able to install e17 but none of the "addons" work.[/QUOTE]
 nope....gives me the finger, cant find install(e17)

---

### Post by foxy123 on 2005-09-01
I've got the same problem. I guess it is common thing for all Debian repos, since the current version is built against newer libc6 library. I still do not understand why it is impossible to upgrade libc6 without breaking everything else. Why it does not have backward compatibility (or whatever it is called).

---

### Post by Ratur on 2005-09-01
That's work great for me, except eclair which won't install.

Thank you very much ! :)

---

### Post by Weav on 2005-09-01
[QUOTE=bam]nope....gives me the finger, cant find install(e17)[/QUOTE]
To install e17 i did not use Elive's repository instead i followed this long website building each lib at a time. It took a while but it worked.
[https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php)

---

### Post by SFN on 2005-09-01
[QUOTE=Ratur]That's work great for me, except eclair which won't install.

Thank you very much ! :)[/QUOTE]

Hmm. Me too (obviosuly, I guess). Makes me curious as to why it works for us and not others.

I had tried the "Bleeding Edge with update script" listed in another thread without success on this computer. I'm wondering if something I added there helped out.

Ratur, had you tried that or any other method to get e17 installed previously?

To those of you who had failures: had you tried any method(s) for instaling e17 previously?

---

### Post by mcduck on 2005-09-01
Nope, this didn't work for me either:

The following packages have unmet dependencies:
  e17: Depends: efl-all (= cvs20050828) but it is not going to be installed

I've tried the Smoon repo, and it worked. When I heard that it's discontinued I uninstalled E17+all related stuff  and removed his repo from my sources.

I haven't tried that 'Bleeding Edge Script', reading the thread I felt that it's not likely to work ;)

---

### Post by foxy123 on 2005-09-01
I also used Smoon's repo and it installed fine. Then yesterday I tried another repo, and it updated enlightenment and enlightenment-data, but I could not install anything else due to dependencies.

I have not tried any cvs script: too much headache and no gain. Though it's fun I guess.

---

### Post by SFN on 2005-09-01
This has me very intrigued. I'm going to try this from a fresh Ubuntu install and see what I get.

Something I'm going to try if it doesn't work is adding the packages listed as dependencies in the "bleeding edge" thread by opening the sources.list:

```
sudo nano /etc/apt/sources.live
``` 

and commenting out the Elive repo:

> 
## e17 repository from Elive
## deb [http://www.vobcopy.org/mirror/elive/](http://www.vobcopy.org/mirror/elive/) elive main efl elive
 

and updating:

```
sudo apt-get update
``` 

Then, deleting all versions of automake:

```
sudo apt-get remove --purge automake*
``` 

and adding in the packages:

```
sudo apt-get install autoconf autogen automake1.7 bison build-essential byacc cvs flex g3.4 gcc-3.4 gettext libbz2-dev libfreetype6-dev libgtk1.2-dev libjpeg62-dev libltdl3-dev libpng12-dev libpng3-dev libsqlite3-dev libssl-dev libtag1-dev libtagc0-dev libtiff4-dev libtool libungif4-dev libx11-dev libxine-dev libxml2-dev pkg-config xlibmesa-dev xlibmesa-gl-dev zlib1g-dev
``` 

Then, possibly:

```
sudo apt-get install giblib1 giblib-dev
``` 

That's all just to see what happens. It sounds like a real pain and I wouldn't recommend that any of you bother with it. Of course, if you want to try it.............


At any rate, I'll be sure and let you know what I find out.

---

### Post by SFN on 2005-09-01
Hey, while I'm doing that let me throw something else out to everyone.

The Elive people have done some great work here. For those that only grabbed the repo, Elive is a live-cd designed to show off Enlightenment. It has both e16 and e17.

They definitely deserve some kudos for their work.

The site is [http://www.elivecd.org/](http://www.elivecd.org/)

---

### Post by Ratur on 2005-09-01
[QUOTE=SFN]Hmm. Me too (obviosuly, I guess). Makes me curious as to why it works for us and not others.

I had tried the "Bleeding Edge with update script" listed in another thread without success on this computer. I'm wondering if something I added there helped out.

Ratur, had you tried that or any other method to get e17 installed previously?

To those of you who had failures: had you tried any method(s) for instaling e17 previously?[/QUOTE]

Yes, I tried the script "Bleeding Edge", but I had an error at the build of evas.

So I used this repository and it worked

---

### Post by SFN on 2005-09-01
Well, I just tried it on a fresh install and it failed. Same error

> 
e17: Depends: efl-all (= cvs20050828) but it is not going to be installed

Oh, how the smiley face mocks me.

It's starting to look like something in the bleeding edge script provides us with something that makes this install work. I'm going to see if I can find out what it is. My guess would be that it has something to do with libc6 as that is the ultimate hangup.

---

### Post by Weav on 2005-09-01
[QUOTE=SFN]Well, I just tried it on a fresh install and it failed. Same error


Oh, how the smiley face mocks me.

It's starting to look like something in the bleeding edge script provides us with something that makes this install work. I'm going to see if I can find out what it is. My guess would be that it has something to do with libc6 as that is the ultimate hangup.[/QUOTE]
Hhhhmmm its mocking all of us, i'll serach the web and try to see what i can get working.

Hopefuly we can come up with some sort of solution.

---

### Post by SFN on 2005-09-01
I think I've got an answer. It's the kind of answer that may get some people's panties in wads but it seems to work. I'll re-write the initial post with a big ol' disclaimer. 

Should be soon.

---

### Post by Weav on 2005-09-01
[QUOTE=SFN]I think I've got an answer. It's the kind of answer that may get some people's panties in wads but it seems to work. I'll re-write the initial post with a big ol' disclaimer. 

Should be soon.[/QUOTE]
haha ok sounds dangerous...I like it!

---

### Post by SFN on 2005-09-01
OK. I've rewritten the initial post to reflect a new method. 

Give it a whirl.

Hope it helps.

---

### Post by Weav on 2005-09-01
SFN just a quick question i already have e17 up and running and can install and log onto it and move around. However none of the modules nor the gnome menu work.

Would you adivse to follow your whole howto and install e17 again or rather just go to the modules parts?

Thanks, and i'll give this a whirl after calc class tonight

---

### Post by SFN on 2005-09-01
Hmmm. I'd certainly try just the modules first. If you can do it that way, life would certainly be easier. I'll be trying a couple of the modules tonight myself as I never got eterm or evidence working last night.

I'll be sure and post on that. In the meantime, if you try it and works be sure to post here.

---

### Post by SFN on 2005-09-01
Regarding the machine I installed last night that was the original test of this thread, after I added the debian packages I was able to install eterm and evidence.

Everything is going swimmingly on the fresh install from this afternoon.

Now it's just a matter of getting eclips. Not that eclips is that important. It's just a matter of being complete.

---

### Post by Weav on 2005-09-01
Ok i'm trying to do a completely fresh install on a friend's ubuntu computer and we are to the part where we install e17 but receive the following error:
```

steve@ubuntu:~$ sudo apt-get install e17
Reading package lists... Done
E: Invalid record in the preferences file, no Package header

```
Any ideas? Thanks

UPDATE: Alright the problem is with this code right here:
```

 Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999

```
If i take that out i am able to install programs but without it, I don't think it will compile e17 perfectly.

---

### Post by SFN on 2005-09-02
[QUOTE=Weav]
UPDATE: Alright the problem is with this code right here:
```

 Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999

```[/QUOTE]

It's the space at the beginning of the first line. Get rid of that space, do

```
sudo apt-get update
``` 

and you should be good to go.

---

### Post by Weav on 2005-09-02
Ugh that was a dumb mistake on my part.

Anyway i'm up and running in e17! Thanks for all the instructions and guidance!
Installed fine, only problems i'm having now are getting the gnome menu to work within it and engage.

I boot up the gnome menu and it says it configures everything but how do i actually get it to appear at the top of my screen? And then engage just shows up as a long black bar at the bottom of my screen and won't even load the module.

It's looking nice and the time for me to decide over gnome or e17 is comming soon....

---

### Post by SFN on 2005-09-02
[QUOTE=Weav]
Thanks for all the instructions and guidance!
[/QUOTE]

I'm glad it worked out for you. Just always remember to help out anybody when you can.

[QUOTE=Weav]
I boot up the gnome menu and it says it configures everything but how do i actually get it to appear at the top of my screen?
[/QUOTE]
You don't get the Gnome menu across the top of the screen anymore. e17genmenu adds your existing Gnome menus to the e17 menus. If you click on the desktop, you'll see Favorite Applications. Mouse over it and you'll see Gnome. Mouse over that and your Gnome menus will appear. You could also just right-click on the desktop and mouse over Gnome.

The new menu will be more or less categorized the same as they were in Gnome. If you want to modify that menu, click on the desktop, mouse over Configuration, mouse over Applications and click Menu Editor. In the new screen that opens up, click where it says Gnome. If you see a program you want moved within the menu, click on it, then right-click in the spot where you want it to appear. To remove an item from the menu, middle-click on it.

When the menu is the way you want it. Click the button marked Save. Then click the button marked Quit. (I've found that I have to click Quit twice sometimes.) 

[QUOTE=Weav]
And then engage just shows up as a long black bar at the bottom of my screen and won't even load the module.
[/QUOTE]

That's a new one on me. If somebody else knows about this, feel free to jump in. In the meantime, I'll look into it.

[QUOTE=Weav]
It's looking nice and the time for me to decide over gnome or e17 is comming soon....[/QUOTE]
I know the feeling. I made Enlightenment my default desktop but have kept Gnome, just in case.

---

### Post by SFN on 2005-09-02
[QUOTE=Weav]
And then engage just shows up as a long black bar at the bottom of my screen and won't even load the module.[/QUOTE]

[QUOTE=SFN]
That's a new one on me. If somebody else knows about this, feel free to jump in. In the meantime, I'll look into it.[/QUOTE]

Bah. I just realized that I don't use engage. I use the default thing. "Iconbar" or whatever it's called. Here's you answer, though.

First, you need to enable engage. Do:

```
enlightenment_remote -module-load engage
```

Then, click on the desktop, mouse over Configuration, mouse over Applications and mouse over Modules, then mouse over Engage. Then click Enabled.

Now, click on the desktop, mouse over Configuration, mouse over Applications and click Menu Editor. In the new screen that opens up, click the button that says Engage. Drag programs from the bar on the left into the blank area under the buttons. When you have the programs you want, click the button marked Save, then click the button marked Quit. Might have to click Quit twice.

If you want to adjust the engage bar (like maybe center it on the bottom of the screen) right-click on it and choose Edit Mode at the bottom of the popup menu. You can then right-click on it again and you will have a whole bunch of options available to you. When you have it the way you want, right-click it again and choose End Edit Mode.

Hope that helps.

---

### Post by mcduck on 2005-09-03
Now this worked nice for me, except some little problems:
E17 is running fine, but im missing Engage. It installed with no errors, but it's not in menus and running 'enlightenment_remote -module-load engage' pops up an error window saying:
```

Error loading Module

There was an error loading module named: engage
No module named engage/linux-gnu-i686/module.so could be found in the module search directories

```

Also I can't find the e17genmenu program. Should it be available with Synaptic?

edit: The module that Engage was missing wasn't even installed with packet 'engage', I had to install also packet 'engage-module' from synaptic..

---

### Post by foxy123 on 2005-09-03
aprat from eclair, which did not install, everything was fine. I have eclair from Smoon's repo anyway, and I am not sure if I will use it at all.

> Now, click on the desktop, mouse over Configuration, mouse over Applications and click Menu Editor. In the new screen that opens up, click the button that says Engage. 

I do not see any Engage button :( well, now I see it, it take time to appear...

pity, I cannot use amarok in E17

---

### Post by SFN on 2005-09-03
[QUOTE=mcduck]Now this worked nice for me, except some little problems:
E17 is running fine, but im missing Engage. It installed with no errors, but it's not in menus and running 'enlightenment_remote -module-load engage' pops up an error window saying:
```

Error loading Module

There was an error loading module named: engage
No module named engage/linux-gnu-i686/module.so could be found in the module search directories

```

Also I can't find the e17genmenu program. Should it be available with Synaptic?

edit: The module that Engage was missing wasn't even installed with packet 'engage', I had to install also packet 'engage-module' from synaptic..[/QUOTE]

Those both sound like it's not picking up the info in /etc/apt/preferences. Did you create that? Also, did you do "sudo apt-get update" after creating it?

Assuming you do have the /etc/apt/preferences file created correctly, do this:

```
sudo apt-get update
``` ```
sudo apt-get install engage
``` 

What does it say?

---

### Post by SFN on 2005-09-03
[QUOTE=foxy123]aprat from eclair, which did not install, everything was fine. I have eclair from Smoon's repo anyway, and I am not sure if I will use it at all.[/QUOTE]

I have it but I don't think I'll be using it. At least not right now. It's a bit bare compared to XMMS and Amarok.

---

### Post by UrbanSlayer on 2005-09-03
Im also having a problem with Engage not installing - 


```
urban@tiffany:~$ sudo apt-get install engage
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  engage: Depends: efl-all (= cvs20050828) but it is not going to be installed
E: Broken packages

```

I tried to install efl-all, but it then complained about libxine-dev which then complained about libxine1 and that it wanted the package from elive, but the ubuntu one was already there.  At this point I stopped as I didnt want to mess about to much with the current system (since it works).

---

### Post by SFN on 2005-09-03
[QUOTE=UrbanSlayer]Im also having a problem with Engage not installing - 


```
urban@tiffany:~$ sudo apt-get install engage
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  engage: Depends: efl-all (= cvs20050828) but it is not going to be installed
E: Broken packages

```

I tried to install efl-all, but it then complained about libxine-dev which then complained about libxine1 and that it wanted the package from elive, but the ubuntu one was already there.  At this point I stopped as I didnt want to mess about to much with the current system (since it works).[/QUOTE]


That's something I think we all had. This part fixed that:

> 
Get:

libc6 from here
libc6-dev from here
libc6-i686 from here
locales from here
libvorbis0a from here
libextractor1 from here

(Note: for all of the links above, scroll down to where it says "Download". There you will find versions for multiple architectures. Remember though, that this theoretically only works for x86, AMD64 and PPC. Maybe not even AMD64 and PPC.)

Then do

sudo dpkg -i /location/of/libc6_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/libc6-dev_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/libc6-i686_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/locales_2.3.2.ds1-22_all.deb
sudo dpkg -i /location/of/libvorbis0a_1.1.0-1_i386.deb
sudo dpkg -i /location/of/libextractor1_0.4.2-2_i386.deb


Did you do that?

---

### Post by UrbanSlayer on 2005-09-03
Thanks, that fixed it.  I wasnt sure if I needed that since I only wanted Engage (im using E16 within Gnome from the Enlightened Gnome thread).  It did install it, but Engage barely works and sends my cpu crazy etc.  Its probably because im running it on an Inspiron 6000 with only the onboard Intel GFX chipset.

I did then decide to try e17 itself, but came up against this somewhat large hurdle - 

```

The following NEW packages will be installed:
  e17
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/22.9MB of archives.
After unpacking 38.8MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  e17
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 107587 files and directories currently installed.)
Unpacking e17 (from .../e17_cvs20050828_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/e17_cvs20050828_i386.deb (--unpack):
 trying to overwrite `/usr/bin/enlightenment', which is also in package enlightenment
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/e17_cvs20050828_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I thought e16 and e17 would co-exist on the same system?  I'm guessing not from that.  Since e16 works at the moment, I guess I'll be sticking with that for now.

---

### Post by darkmatter on 2005-09-03
[QUOTE=UrbanSlayer]I thought e16 and e17 would co-exist on the same system?  I'm guessing not from that.  Since e16 works at the moment, I guess I'll be sticking with that for now.[/QUOTE]

They will coexist, but only if e16 is version 16.8 or higher, OR if you install e17 to a different path.

---

### Post by SFN on 2005-09-04
darkmatter,

Thanks for the input. I never would have known that.

Someday this whole e17 thing will be licked. It would be ince to have it in Breezy but I imagine that's beyond the scope of the project right now. Till then, we keep trying.

---

### Post by UrbanSlayer on 2005-09-04
I have e16.7 installed at the moment, but how would I install e17 to a different path via apt?  Ive had a google around and havent really found anything that says I can.

---

### Post by foxy123 on 2005-09-04
[QUOTE=SFN]I have it but I don't think I'll be using it. At least not right now. It's a bit bare compared to XMMS and Amarok.[/QUOTE]
how does one use amarok in E17?

---

### Post by SFN on 2005-09-04
[QUOTE=foxy123]how does one use amarok in E17?[/QUOTE]

If you already had Amarok installed before e17 and then installed and ran e17genmenu, it should have been added to your menu system.

If nothing else, you should be able to run it from the command line.

---

### Post by foxy123 on 2005-09-05
[QUOTE=SFN]If you already had Amarok installed before e17 and then installed and ran e17genmenu, it should have been added to your menu system.

If nothing else, you should be able to run it from the command line.[/QUOTE]
if I run it from console, I do not see it... it is running but not showing...

---

### Post by SFN on 2005-09-05
That's odd. I don't use Amarok so I just installed it. It ran right off the bat.

Let's try killing all of it, then seeing if there are any updates to be had, then run it again and check for errors.

```
sudo killall amarokapp
``` 
```
sudo apt-get update
```
```
sudo apt-get upgrade
``` 
```
amarok
``` 

Did you get any errors when running amarok?

---

### Post by foxy123 on 2005-09-05
[QUOTE=SFN]That's odd. I don't use Amarok so I just installed it. It ran right off the bat.

Let's try killing all of it, then seeing if there are any updates to be had, then run it again and check for errors.

```
sudo killall amarokapp
``` 
```
sudo apt-get update
```
```
sudo apt-get upgrade
``` 
```
amarok
``` 

Did you get any errors when running amarok?[/QUOTE]
let me try again tonight when I get to my Ubuntu laptop...

---

### Post by SFN on 2005-09-05
OK. I'll check back tonight.

---

### Post by foxy123 on 2005-09-05
the thing is that amarok launches ok, I can see its splash screen... I can see it running with middle-click, but I do not see it... actual application window does not exist.. it is wierd...

---

### Post by firecat53 on 2005-09-05
Looks awesome!!  

Some problems:

1. I keep getting a message saying that Enlightenment has segfaulted. I can't tell exactly when it happens yet. Seems to be associated with using Engage and/or Entangle (the menu editor).

2. There's always a green question mark labelled 'unmatched' in the engage toolbar that won't go away.

3. Entangle seems to be very slow and unstable....kept locking up hard!

4. Is there a way to change the command that engage executes when you click on a particular icon? I want to put Synaptic there, but it tells me that is needs to be run as root.

5. How do edit a note added with the notes module??? I can see it and delete it but I can't edit it!! It's driving me crazy!!

6. Whenever I install a new package, I get the following errors:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```
The package still gets installed, but it'd be nice to make the errors go away! Any thoughts? I followed the directions in this forum for installing e17.

Thanks a lot!!  
Scott

---

### Post by Karny on 2005-09-06
[QUOTE=firecat53]
3. Entangle seems to be very slow and unstable....kept locking up hard!
[/QUOTE]

I'm having this problem a lot too. Is there a config file I could edit rather than use Entangle?

PS. Thanks for the HOWTO, it's great to be running e17!!  \\:D//

---

### Post by foxy123 on 2005-09-06
[QUOTE=firecat53]Looks awesome!!  

Some problems:

4. Is there a way to change the command that engage executes when you click on a particular icon? I want to put Synaptic there, but it tells me that is needs to be run as root.

Scott[/QUOTE]
you should use 'gksudo synaptic' Right-click on the icon, Icon Options/Edit Icon...

---

### Post by SFN on 2005-09-06
[QUOTE=foxy123]the thing is that amarok launches ok, I can see its splash screen... I can see it running with middle-click, but I do not see it... actual application window does not exist.. it is wierd...[/QUOTE]

That is definitely weird. I've tried and cannot duplicate this at all. Do you have this problem with any other apps?

---

### Post by SFN on 2005-09-06
[QUOTE=firecat53]
2. There's always a green question mark labelled 'unmatched' in the engage toolbar that won't go away.[/QUOTE]

That's an app that you have running that Engage has no info on. See foxy's problem with Amarok. 

Does this happen right off the bat when you start e17?

[QUOTE=firecat53]
3. Entangle seems to be very slow and unstable....kept locking up hard![/QUOTE]

I've had that problem too. I guess we have to remember that it's all still alpha.

[QUOTE=firecat53]
5. How do edit a note added with the notes module??? I can see it and delete it but I can't edit it!! It's driving me crazy!![/QUOTE]

I haven't even tried the notes. I'll check it out when I get home tonight.

---

### Post by SFN on 2005-09-06
[QUOTE=foxy123]Right-click on the icon, Icon Options/Edit Icon...[/QUOTE]

Sweet. I hadn't noticed that. I'll add it to the instructions at the top tonight.

---

### Post by loon on 2005-09-06
Thanks for the tut.

I had Smoons previous e17 installed.  everything updated and installed correctly.

Thank you!! works like a charm! (except engage wont load with -module-load)

- loon



engaged fixed:

Went back a few pages....

sudo apt-get install engage-module

Add this to your list of things to install and then people can do the enlightnment_remote -module-load engage

---

### Post by SFN on 2005-09-06
[QUOTE=loon]sudo apt-get install engage-module

Add this to your list of things to install and then people can do the enlightnment_remote -module-load engage[/QUOTE]

Actually, you shouldn't need to do that.

[QUOTE=SFN]Optionally, you can also install extra programs and modules. To install all of them, do:

```
sudo apt-get install engage eclair elicit entice examine e-modules e-utils evidence
``` [/QUOTE]

That should have installed engage-manager and engage-modules.

Oddities everywhere.

---

### Post by loon on 2005-09-06
bummer, cause it didnt.
I had to manually do it, just like the other guy who posted the fix.

If anyone else has problems with engage, try it and see if it worked?

---

### Post by firecat53 on 2005-09-07
Anyone have any ideas about this locale problem? It started happening after I installed the locale library per this thread. 

Also when I typed man for an entry that didn't exist:

man: can't set the locale; make sure $LC_* and $LANG are correct

Whenever I install a new package, I get the following errors:

perl: warning: Setting locale failed. perl: warning: Please check that your locale settings: LANGUAGE = "en", LC_ALL = (unset), LANG = "en" are supported and installed on your system. perl: warning: Falling back to the standard locale ("C"). locale: Cannot set LC_CTYPE to default locale: No such file or directory locale: Cannot set LC_MESSAGES to default locale: No such file or directory locale: Cannot set LC_ALL to default locale: No such file or directory


The package still gets installed, but it'd be nice to make the errors go away! Any thoughts? I followed the directions in this forum for installing e17.

Thanks! Scott

---

### Post by foxy123 on 2005-09-07
[QUOTE=loon]bummer, cause it didnt.
I had to manually do it, just like the other guy who posted the fix.

If anyone else has problems with engage, try it and see if it worked?[/QUOTE]
yeah, I had to install it manually as well, following somebody's tip here....

Does anyone know a keyboard layout indicator, which works in E17? I use kkbswitch and it does ot show up...

---

### Post by SFN on 2005-09-07
[QUOTE=firecat53]Anyone have any ideas about this locale problem? It started happening after I installed the locale library per this thread. 

Also when I typed man for an entry that didn't exist:

man: can't set the locale; make sure $LC_* and $LANG are correct

Whenever I install a new package, I get the following errors:

perl: warning: Setting locale failed. perl: warning: Please check that your locale settings: LANGUAGE = "en", LC_ALL = (unset), LANG = "en" are supported and installed on your system. perl: warning: Falling back to the standard locale ("C"). locale: Cannot set LC_CTYPE to default locale: No such file or directory locale: Cannot set LC_MESSAGES to default locale: No such file or directory locale: Cannot set LC_ALL to default locale: No such file or directory


The package still gets installed, but it'd be nice to make the errors go away! Any thoughts? I followed the directions in this forum for installing e17.

Thanks! Scott[/QUOTE]

I don't have any idea on this one. Perhaps someone else knows something about this?

---

### Post by SFN on 2005-09-07
[QUOTE=foxy123]yeah, I had to install it manually as well, following somebody's tip here....[/QUOTE]

Not sure why that is but I did add it to the original directions after loon's post.

---

### Post by loon on 2005-09-07
[QUOTE=SFN]I don't have any idea on this one. Perhaps someone else knows something about this?[/QUOTE]



I get the same errors.

Possibly due to not running Ubuntu libs?

---

### Post by SFN on 2005-09-07
[QUOTE=foxy123]Does anyone know a keyboard layout indicator, which works in E17? I use kkbswitch and it does ot show up...[/QUOTE]
I've noticed a couple of references to KDE apps. Did you go to e17 from Ubuntu or Kubuntu?

---

### Post by SFN on 2005-09-07
[QUOTE=loon]I get the same errors.

Possibly due to not running Ubuntu libs?[/QUOTE]
Certainly makes sense. Based on the error it would seem to go straight back to the locales package.

Now this is all just a guess but since locales was already installed via Ubuntu and we replaced it with the package from Debian, it would indicate that the Ubuntu package had our locales set up for us whereas the Debian package sets up nothing.

Looking the page for the Debian loacles package, we find:

> This package contains the libc.mo i18n files, plus tools to generate locale definitions from source files (included in this package). It allows you to customize which definitions actually get generated.

which seems to support the notion that no locales have been generated. Looking at /usr/share/doc/locales/README we see:

> To compile the locale data files you simply have to decide which locale
(based on the location and the language) and which character set you
use.  E.g., French speaking Canadians would use the locale `fr_CA' and
the character set `ISO_8859-1,1987'.  Calling `localedef' to get the
desired data should happen like this:

	localedef -i fr_CA -f ISO-8859-1 fr_CA

Sounds like just the thing that would solve this problem --- or bork my whole system because I don't actually know what I'm doing. Personally, I'd live with the error since it doesn't seem to affect the ability to install packages. But that's just me.

---

### Post by SFN on 2005-09-07
[QUOTE=firecat53]
5. How do edit a note added with the notes module??? I can see it and delete it but I can't edit it!! It's driving me crazy!![/QUOTE]

[QUOTE=SFN]
I haven't even tried the notes. I'll check it out when I get home tonight.[/QUOTE]

Sorry. I forgot all about this. Just tried it and I have the same issue. 

So I checked out the [e17 User Guide](http://get-e.org/User_Guide/English/_pages/3.2.html) and found this:

> The following modules are included in the e_modules package:

    * notes (a deskto sticky notes module - DOES NOT CURRENTLY WORK)

Guess that answers that. I'll update the HOWTO.

---

### Post by SFN on 2005-09-07
[QUOTE=firecat53]4. Is there a way to change the command that engage executes when you click on a particular icon? I want to put Synaptic there, but it tells me that is needs to be run as root.[/QUOTE]
[QUOTE=foxy123]you should use 'gksudo synaptic' Right-click on the icon, Icon Options/Edit Icon...[/QUOTE]
I went ahead and put this in the HOWTO but I just tried it and I can't duplicate it. Are you right clicking on the icons in the engage bar or on the icons in the entangle dialog for the engage bar?

---

### Post by firecat53 on 2005-09-07
Thanks for the responses!  

Locales:  yeah, waiting until someone who REally knows tells us how sounds wise!

Notes:  Bummer! I love desktop sticky notes!

Engage: I've finally got it working. Right-click on the icon in the engage tool-bar. The trick is to pull your cursor down to the bottom of the screen to bring the rest of the menu into view. That took a while to see, since most of us are used to the MS menus which automatically keep themselves inside the viewable screen. Worth a note to the developers, probably!  I still have the green question mark that won't go away. It shows up right away on boot.

I have to move through mouse-click menus fairly slowly when scrolling through a large number of entries, or else I get an enlightenment segfault. Same with entangle...it worked as long as I didn't click on too many things in a row. I'm operating on a slower machine (PII 366), so I'm sure that's part of it!

Otherwise it looks great!  I wish the gant theme had a digital clock!

---

### Post by foxy123 on 2005-09-07
[QUOTE=SFN]I've noticed a couple of references to KDE apps. Did you go to e17 from Ubuntu or Kubuntu?[/QUOTE]
Ubuntu, but I am using XFCE now. 
> I went ahead and put this in the HOWTO but I just tried it and I can't duplicate it. Are you right clicking on the icons in the engage bar or on the icons in the entangle dialog for the engage bar? 
right-click on the icon in the engage bar and move the mouse down to reveal a whole pop-up menu (which actually does not pop ut at all), click on Edit Icon....
> I went ahead and put this in the HOWTO but I just tried it and I can't duplicate it. Are you right clicking on the icons in the engage bar or on the icons in the entangle dialog for the engage bar? 
yes, exactly like that...

regarding a green question mark, it is apparently a programme that loads at startup, which engage does not recognise...

---

### Post by SFN on 2005-09-07
[QUOTE=Karny]I'm having this problem a lot too. Is there a config file I could edit rather than use Entangle?[/QUOTE]

Sorry for the late response on this but the answer is "yes". This is actually a nice option for all of us who have been wrestling with engage and specifically, setting up engage through entangle. Here's the scoop.

First, you need to build an .eap file (basically a shortcut with an icon attached) for the the program you want to add to engage. From the e17 User Guide:

> 
Once you've opened an application you want to make an icon for, click the top left corner (but not the border!) [Note from SFN: Basically, this is the icon in the top left-hand corner ofg the broder - or where there would be one if one does nto exist] with the left mouse button and select "Create Icon". This menu can also be reached by right clicking the application name section of the window decorations. This starts e_util_eapp_edit, so you'll have to have e_utils and all its dependencies installed in order for it to work.

Add all the information you need, but ignore the "Window name" section. That needs to be left empty. Then select an icon file. It can be of any size - it will be resized with Imlib2. The bigger the file, the more memory it uses. Note that you don't have to have the full path for the executable - just the name of the program is ok too, assuming the program is in your path. The EFL GUI for selecting icons is a bit unstable currently and is under heavy development. It should work though, but it may sometimes ignore input for example. After the icon is made the original icon picture isn't needed anymore for the icon to work. It will be included in the created EAP file and is automatically moved to ~/.e/e/applications/all


Now you just need to edit the .order file for engage:

```
sudo nano ~/.e/e/applications/engage/.order
``` 

In the file that opens up, just add the name of the .eap file. Let's say you created one that runs "gksudo synaptic" and you called it "Synaptic.eap". You just need to add that .eap file on its own line. So the resulting file should look something like:

eterm.eap
xmms.eap
mozilla-firefox.eap
Synaptic.eap

Save and close that file and you're all done.

---

### Post by SFN on 2005-09-07
[QUOTE=foxy123]Ubuntu, but I am using XFCE now. [/QUOTE]

So no e17 now? Sorry to hear that but I do have to say that XFCE is very nice and a lot less hassle.
 
[QUOTE=foxy123]right-click on the icon in the engage bar and move the mouse down to reveal a whole pop-up menu (which actually does not pop ut at all), click on Edit Icon....[/QUOTE]

Here's a lovely bit of strangeness. On my laptop, the "Edit Icon" menu item does not appear at all. Here on my desktop, it does. So that's working now.

---

### Post by SFN on 2005-09-07
Added the instructions for editing engage's .order file to the original post.

Now if I could just figure out a way to make it so the name of this thread no longer says "provbied".

---

### Post by samjam on 2005-09-08
Any chance you could also make the deb-src av ailable so we can rebuild e17 according to your rules but against our current library versions to save installing from debian-stale^H^Hble and all the problems that was causing?

apt-get -b source e17
is not onerous

Thanks

Sam

---

### Post by SFN on 2005-09-08
[QUOTE=samjam]Any chance you could also make the deb-src av ailable so we can rebuild e17 according to your rules but against our current library versions to save installing from debian-stale^H^Hble and all the problems that was causing?

apt-get -b source e17
is not onerous

Thanks

Sam[/QUOTE]

Actually, you would need to speak to the Elive people about this. All I have done is point people in a direction that worked for me.

The Elive site is [http://elivecd.org/](http://elivecd.org/)

---

### Post by foxy123 on 2005-09-08
[QUOTE=SFN]So no e17 now? Sorry to hear that but I do have to say that XFCE is very nice and a lot less hassle.
 
well, I still keep E17. I love the look and feel, but it keep crashing and I miss some desklets I am using with xfce... I think I will keep it, configuring bit by bit and maybe make it my default DE enetually... but now I have the work to do and xfce is more or less configured for that...

if you come across a keyboad layout indicator which works with E17, please post here. I found a couple but they are for E16...

Here's a lovely bit of strangeness. On my laptop, the "Edit Icon" menu item does not appear at all. Here on my desktop, it does. So that's working now.[/QUOTE]
Have you installed E17 from the same source to you desktop and laptop? My installation is not pure because I initially used Smoon's repo and then a couple of others, Elive being the latest... Like amarok, which I do not see and you can...

---

### Post by SFN on 2005-09-08
The laptop is pure. On the desktop, I had tried the CVS Updater Script which failed on the first build. So that could easily explain the inconsistency between my laptop and desktop. However, on both I can see Amarok.

All of these things are odd but I do expect that they should all get ironed out when e17 becomes stable.

Yes, I giggle when I say that too.

---

### Post by foxy123 on 2005-09-08
[QUOTE=SFN]The laptop is pure. On the desktop, I had tried the CVS Updater Script which failed on the first build. So that could easily explain the inconsistency between my laptop and desktop. However, on both I can see Amarok.

All of these things are odd but I do expect that they should all get ironed out when e17 becomes stable.

Yes, I giggle when I say that too.[/QUOTE]
I've got a feeling that the guys behind E17 are perfectionists and maybe our grandchildren will see the final release while retired...

---

### Post by SFN on 2005-09-08
[QUOTE=foxy123]I've got a feeling that the guys behind E17 are perfectionists and maybe our grandchildren will see the final release while retired...[/QUOTE]
It definitely feels like perfectionism. On the one hand, we could say that perfectionsism has allowed them to put out a DE that is well ahead of anything that anybody is doing and relatively stable, considering it's still alpha. 

On the other hand, it's like painting or making music. At some point you need to back away from your work and say "I'm done", even if you still want to do more.

---

### Post by foxy123 on 2005-09-08
[QUOTE=SFN]It definitely feels like perfectionism. On the one hand, we could say that perfectionsism has allowed them to put out a DE that is well ahead of anything that anybody is doing and relatively stable, considering it's still alpha. 

On the other hand, it's like painting or making music. At some point you need to back away from your work and say "I'm done", even if you still want to do more.[/QUOTE]
I agree... I would prefer if they released a stable version now, even it is not perfect, and then continued working on its next release... On the other hand, they have stable E16...

---

### Post by samjam on 2005-09-08
[QUOTE=SFN]Actually, you would need to speak to the Elive people about this. All I have done is point people in a direction that worked for me.

The Elive site is [http://elivecd.org/](http://elivecd.org/)[/QUOTE]

Thanks, I have asked and will post back any response I get.

Sam

---

### Post by SFN on 2005-09-09
I can't imagine they'd be willing to do that as it could be percieved as taking away from their project but I'm certainly interested in hearing what they have to say.

You might want to try out their Live CD as it will give you a better idea of how it should run. Or at least their take on how it should run. I've tried it myself and it's quite solid.

---

### Post by SFN on 2005-09-09
Hmmm. New package for evidence just came available.

---

### Post by foxy123 on 2005-09-09
[QUOTE=SFN]Hmmm. New package for evidence just came available.[/QUOTE]
thanks... do you use it?

i also wonder why in the weather module they do not use the source which is used in all desklets? It provides the greater choice of locations. I do not use gnome and xfce weather applets for the same reason. I wish E17 used a different source for the weather forecast...

---

### Post by SFN on 2005-09-09
[QUOTE=foxy123]thanks... do you use it?[/QUOTE]

I fired it up and browsed through it a bit. That's about all I did with it before the update. To be honest, I don't really use Nautilus for browsing files in Gnome all that much. But for what little bit I did, evidence seems to be fine.

[QUOTE=foxy123]i also wonder why in the weather module they do not use the source which is used in all desklets? It provides the greater choice of locations. I do not use gnome and xfce weather applets for the same reason. I wish E17 used a different source for the weather forecast...[/QUOTE]

Yeah. The weather modules are starting to give me a PITA. Truth be told, I don't think I've ever used a weather module in anything (Karamba, gdesklets, gkrellm, anything in Windows) that I didn't end up shutting off because they started to annoy me. It would appear that I have an adversion to dekstop gadgetry.

That makes it seem odd that I'm drawn to e17 but I like e17 for it's style and speed. Toys get old quickly.

---

### Post by stevea1210 on 2005-09-09
> Get:

libc6 from here
libc6-dev from here
libc6-i686 from here
locales from here
libvorbis0a from here
libextractor1 from here

Packages.debian.org has been down for awhile.   :mad: I've been trying to get these pkgs so I can install e17

I downloaded elive today and loved it.  Unfortunately, I wasn't able to get it to recognize three wired nics on three pc's.  That put a little damper on it.  I then figured I'd install ndiswrapper to try my wireless. I also couldn't install that, since the kernel source wasn't included.

I love the look and feel of e17, so I decided to just go for it,  using the how to in this thread.  Then I start this how to and get roadblocked at step one, since packeges.debian.org is down  ](*,) .

Maybe I'm not meant to have e17 tonight.  I'll try again tommorow.

Thanks, Rant over.

---

### Post by foxy123 on 2005-09-10
I installed Breezy preview in my test drive on the desktop yesterday and tried to get E17 there. The problem was that efl-all refused to install because could not find xlibmesa-dev... This package does not exist in Debian repos as well. Sort of transitional or dummy stuff. Though it is pity that I can get E17 working there...

---

### Post by SFN on 2005-09-10
[QUOTE=stevea1210]Packages.debian.org has been down for awhile.[/QUOTE]

Strange. I was using it last night. It's definitely up as I'm typing this. See the next post.

---

### Post by SFN on 2005-09-10
[QUOTE=foxy123]The problem was that efl-all refused to install because could not find xlibmesa-dev... This package does not exist in Debian repos as well.[/QUOTE]

I'm wondering if this has to do with the post before yours. I see xlibmesa-dev [here](http://packages.debian.org/stable/oldlibs/xlibmesa-dev)

---

### Post by foxy123 on 2005-09-10
[QUOTE=SFN]I'm wondering if this has to do with the post before yours. I see xlibmesa-dev [here](http://packages.debian.org/stable/oldlibs/xlibmesa-dev)[/QUOTE]
Thanks, how did you find it? I tried search and only found a reference that it is not available.... I will try to set up E17 on Breezy today and let you know if successful...

---

### Post by foxy123 on 2005-09-10
Does E17 have a session manager? How can I get thigs like skype and gaim start in the beginning?

---

### Post by SFN on 2005-09-10
[QUOTE=foxy123]Thanks, how did you find it? I tried search and only found a reference that it is not available.... I will try to set up E17 on Breezy today and let you know if successful...[/QUOTE]

I went to [http://www.debian.org/distrib/packages#search_packages](http://www.debian.org/distrib/packages#search_packages)  and did a search for xlibmesa-dev. I'm just wondering if the downtime that the previous poster was talking about affected your search.

---

### Post by SFN on 2005-09-10
[QUOTE=foxy123]Does E17 have a session manager? How can I get thigs like skype and gaim start in the beginning?[/QUOTE]

Unfortunately, we're back to entangle which I think neither of us is big on. But you can do it there, supposedly.

When you open entangle up (click on desktop, Configuration, Applicatiosn, Menu Editor) you will see a button across the top that says Startup. Click that and then it's teh same process you sue for adding items to menus. 

I haven't actually tried this so let me know how it goes for you.

---

### Post by SFN on 2005-09-10
I'm just guessing but it looks like you can also do this by creating a .order file similar to the one I mention in the updated original post.

Look for the section there that starts out "The second way to do this is to build an .eap file" and change the reference to "~/.e/e/applications/engage/.order" to "~/.e/e/applications/startup/.order".

I have to say I found that to be a less crash-prone method for seting up engage.

---

### Post by foxy123 on 2005-09-10
thanks, I will try both methods...

Am I right to assume that E16 modules won't work in E17? I have found a keyboard layout indicator, though it is for E16 and I failed to compile it...

---

### Post by SFN on 2005-09-10
I couldn't give you an informed answer, there. I haven't used e16 since in a few years.

Perhaps someone with more experience could chime in on this one?

---

### Post by SFN on 2005-09-10
Oh, hey! I forgot all about this. 

In using e17genmenu I ended up with all of my Gnome menu items (and more, actually). In there, I see the Gnome keyboard manager. If that covers your needs, you can use that.

---

### Post by foxy123 on 2005-09-10
[QUOTE=SFN]Oh, hey! I forgot all about this. 

In using e17genmenu I ended up with all of my Gnome menu items (and more, actually). In there, I see the Gnome keyboard manager. If that covers your needs, you can use that.[/QUOTE]
I am afraid it does not a keyboard layout indicator... as I remember it uses some gnome panel applet to show it.... I doubt it will work with engage...

I found another indicator called xxkb, the problem is that I cannot place it properly on the desktop.  I want it borderless and small, but if I make it that way, I cannot move it with the mouse... If I try to place it where I want before making it borderless, I cannot put it in the exact location I want.... a bit annoying...

---

### Post by KageKeeper on 2005-09-12
[QUOTE=firecat53]Thanks for the responses!  

Locales:  yeah, waiting until someone who REally knows tells us how sounds wise![/QUOTE]

I had this exact same issue with the locales.

I posted about it and arnieboy was kind enough to help me out.

Here is the original [post.](http://www.ubuntuforums.org/showthread.php?t=60329) 

Hope this helps everyone!

Enjoy. :D

---

### Post by foxy123 on 2005-09-12
[QUOTE=SFN]The laptop is pure. On the desktop, I had tried the CVS Updater Script which failed on the first build. So that could easily explain the inconsistency between my laptop and desktop. However, on both I can see Amarok.

All of these things are odd but I do expect that they should all get ironed out when e17 becomes stable.

Yes, I giggle when I say that too.[/QUOTE]
btw, what version of amarok do you use... I am using 1.3, soi wonder if it is not compatible with E17...

---

### Post by SFN on 2005-09-12
[QUOTE=foxy123]btw, what version of amarok do you use... I am using 1.3, soi wonder if it is not compatible with E17...[/QUOTE]

That could be it. I've got the one that's available in Synaptic. If you check the version in amarok it says it's 1.2. If you look in Synaptic, it's 2:1.2.4-0ubuntu1~5.04ubp2.

It still works OK but I've got a couple of multimedia apps that are seg faulting right and left. Specifcally goobox and audacity. Goobox is no big deal but audacity is a deal breaker. I run a locally-broadcast net radio station and must have audacity for editing sound files. Audacity is even seg faulting whne I'm in Gnome.

If I can't get that issue resolved quickly, that's it for me and e17 on my desktop. I'll still be playing with it on the laptop just so I can keep testing it but It will be back to Gnome only on the desktop.

---

### Post by loon on 2005-09-12
SFN:

With a little reaseach, I have found out that the "perl: warning: Falling back to the standard locale ("C")" errors are coming from the upgrades we did at the beginning. I read some where that it is not pearl itself, but the locales and possibly the libc6 installs we did.  Have you tried installing e17 with having to do these upgrades?? If not, we might need to try it.  Smoon's repo info didn't need anything upgraded within Ubuntu itself.  Is this a elive thing?

Also,

has anyone been able to get rid of the green question mark in engage?? The one that wont go away, even though you select remove.  (/dev/null)

Thanks,

-loon

---

### Post by SFN on 2005-09-13
[QUOTE=loon]SFN:

With a little reaseach, I have found out that the "perl: warning: Falling back to the standard locale ("C")" errors are coming from the upgrades we did at the beginning. I read some where that it is not pearl itself, but the locales and possibly the libc6 installs we did.  Have you tried installing e17 with having to do these upgrades?? If not, we might need to try it.  Smoon's repo info didn't need anything upgraded within Ubuntu itself.  Is this a elive thing?[/QUOTE]

The only thing I can say for sure about that is that, at the time the original post was written, those files were needed to resolved the dependency issues that people were having with efl-all. I did try from a fresh install and installed and removed each of those packages one at a time before coming up with the necessary combo.

Now, as packages have changed since then, the requirements may have changed. The only way to tell for sure is to do a fresh install and leave the locales and libc6 packages out. I'd be happy to to do that but it will be a while before I can get to it. Leaving for a Caribbean Cruise this weekend.  \\:D/ 

If you want to try it out, be sure to post your findings here and I'll update the post when I get back. Otehrwise, I'll do a new install on the laptop when I get back and update everyone then.

Having said all of that, did you follow the link that KageKeeper posted above? Looks like that might also solve the problem.

[QUOTE=loon]Also,

has anyone been able to get rid of the green question mark in engage?? The one that wont go away, even though you select remove.  (/dev/null)[/QUOTE]

You know, that never happened to me but it did happen to a buddy of mine here. We fixed it by editing the .order file for engage. Not the one in ~/.e/e/applications/engage. There is a second one. I can't tell you for sure where it is now but if you do a
```
sudo find / -name ".order"
``` 
you should find it.

Hope that helps.

---

### Post by json684 on 2005-09-13
HELP! Okay, so I got E17 installed, and everything was good. Segfaults here and there, but I was expecting as much. Then things went bad. I was using the menu editor, I know its buggy but I was giving it a go. And then E crashed, hard. Finally I got it to reboot, almost had to do a hard reset, but now when X loads it is blank. I dont get the login screen anymore. It is just blank. I can still Alt-Ctrl-F* to other terminals but X always comes up blank. Any help?

---

### Post by SFN on 2005-09-14
My involvement in the forum is going to be pretty much nill for a bit. Besides the aforementioned vacation, the hard drive in my laptop decided to keel over on me. SONY's service plan? 7 to 14 days after they receive it.  :-x But I'll try to help out where I can.

First, was this a normal Ubuntu install before you put e17 on it? That is, it was running Gnome, not KDE or anything else and you didn't do much in the way of system tweaking?

Assuming all that is the case (and actually whether or not that is the case), can you post the contents - or really just the most recent and pertinent lines - of /var/log/Xorg.0.log?

---

### Post by foxy123 on 2005-09-14
Have a nice trip! Hopefully when you're back there will be some new development in E world...

---

### Post by SFN on 2005-09-14
[QUOTE=foxy123]Have a nice trip! Hopefully when you're back there will be some new development in E world...[/QUOTE]
Thanks for the well wishes!

---

### Post by firecat53 on 2005-09-14
The locale fix [here](http://www.ubuntuforums.org/showthread.php?t=60329) did fix the locale problems when using the terminal. However, synaptic still shows the errors in the output terminal window, so there is still a system-wide problem somewhere.

I couldn't find any other .order file for engage using the "sudo find / -name ".order"" command other than the one in ~/.e/e/applications/engage. There were other directories with .order files in ~/.e/e/applications (all,bar,favorites,startup,restart,trash), but none had any suspicious entries.

In case anyone is interested, I finally figured out how to automatically start xscreensaver so I could use the screen lock feature. I've heard rumors of a screen saver feature for E17, but haven't found it. I added the following two lines near the top of /etc/gdm/Xsession: ```
xscreensaver-command -exit
xscreensaver -nosplash &
``` Then I added a new icon to engage using the menu editor (entangle) and changed the 'Executable' block to```
 xscreensaver-command -lock

```

I'm sure that's easy to figure out for most of you, but I thought I'd write it down so someone else won't spend too many hours on it!! At least I learned a few things.

Scott

---

### Post by SFN on 2005-09-16
Someone pointed out to me that elive updated their packages.

```
sudo apt-get update
``` 
```
sudo apt-get upgrade
``` 

I haven't tested any of it and won't for a while. If anybody does, please be sure to post your results here.

---

### Post by foxy123 on 2005-09-16
[QUOTE=SFN]Someone pointed out to me that elive updated their packages.

```
sudo apt-get update
``` 
```
sudo apt-get upgrade
``` 

I haven't tested any of it and won't for a while. If anybody does, please be sure to post your results here.[/QUOTE]
thanks... apart from eterm and eclair everything updated fine. I guess eclair is my local problem because it is compiled against libtag 1.3 while I have 1.4 to get new amarok work. eterm requires a newer libc6.

---

### Post by loon on 2005-09-19
Anyone tested this elive repo without having to install the beginning files?

---

### Post by SFN on 2005-09-24
[QUOTE=loon]Anyone tested this elive repo without having to install the beginning files?[/QUOTE]

I'm going to do a fresh install some time tomorrow. I'll be sure and try this and let you know.

UPDATE: Looks like there's been another update to the elive repo, inlcuding ecalir, examine, evidence and e17 itself. So I'll be getting whatever is the latest elive stuff.

---

### Post by linkunderscore on 2005-09-26
well im trying this How-To....then im giving up on e17

i have tried them all with various retarded/arbitrary errors.

---

### Post by linkunderscore on 2005-09-26
OH HELL YEA!!!! 


THIS IS AWESOME! 

Well after 4 failed attempts, a fresh install of ubuntu, and one glitch later.....

I am truly enlightened :)

---

### Post by SFN on 2005-09-26
Don't worry. You'll find various retarded/arbitrary errors with this too.;-)  I think that has more to do with e17 not quite being there yet than it does any of the methods for installing it. I do still like this method, though.

I'll be trying the install without the added deb packages tonight. I was going to do it yesterday but without access to the forums, I had no access to the instructions.

---

### Post by linkunderscore on 2005-09-26
[QUOTE=SFN]Don't worry. You'll find various retarded/arbitrary errors with this too.;-)  I think that has more to do with e17 not quite being there yet than it does any of the methods for installing it. I do still like this method, though.

I'll be trying the install without the added deb packages tonight. I was going to do it yesterday but without access to the forums, I had no access to the instructions.[/QUOTE]


How can I edit the menu? 

I want to add all of these programs that I just installed to the menu. Also, how do I install themes?

Is there a file browser for E? 

And my final question....how to i install/run gtk themes in e17 and how do I get them to run on start up.  :)

---

### Post by SFN on 2005-09-26
It's all in the instructions.

[QUOTE=linkunderscore]How can I edit the menu?[/QUOTE]
First you want e17genmenu.
[QUOTE=SFN]A quick perusal of the repo at [http://www.vobcopy.org/mirror/elive/pool/elive/e/](http://www.vobcopy.org/mirror/elive/pool/elive/e/) revelaed some nifty treasures. These can be had via Synaptic by searching on the package name elive.

The coolest of these is e17genmenu. It adds in all of your menus from either Gnome or KDE. After installing it, do:

Code:

e17genmenu -g

for Gnome or

Code:

e17genmenu -k

for KDE[/QUOTE]

[QUOTE=linkunderscore]I want to add all of these programs that I just installed to the menu.[/QUOTE]
[QUOTE=SFN]To use engage, you need to enable it. Do:

Code:

enlightenment_remote -module-load engage



Then, click on the desktop, mouse over Configuration, mouse over Applications and mouse over Modules, then mouse over Engage. Then click Enabled.

You can edit the items on the engage bar two different ways. The first way I will detail in the following paragraph uses a program called entangle. entangle is still very buggy. You will see a number of complaints about it if you read this whole thread. You may want to use the second method I mention here. But first, entangle.

Click on the desktop, mouse over Configuration, mouse over Applications and click Menu Editor. In the new screen that opens up, click the button that says Engage. Drag programs from the bar on the left into the blank area under the buttons. When you have the programs you want, click the button marked Save, then click the button marked Quit. You might have to click Quit twice. That seems to happen on and off.

The second way to do this is to build an .eap file (basically a shortcut with an icon attached) for the the program you want to add to engage. From the e17 User Guide:

Quote:
Once you've opened an application you want to make an icon for, click the top left corner (but not the border!) [Note from SFN: Basically, this is the icon in the top left-hand corner ofg the broder - or where there would be one if one does nto exist] with the left mouse button and select "Create Icon". This menu can also be reached by right clicking the application name section of the window decorations. This starts e_util_eapp_edit, so you'll have to have e_utils and all its dependencies installed in order for it to work.

Add all the information you need, but ignore the "Window name" section. That needs to be left empty. Then select an icon file. It can be of any size - it will be resized with Imlib2. The bigger the file, the more memory it uses. Note that you don't have to have the full path for the executable - just the name of the program is ok too, assuming the program is in your path. The EFL GUI for selecting icons is a bit unstable currently and is under heavy development. It should work though, but it may sometimes ignore input for example. After the icon is made the original icon picture isn't needed anymore for the icon to work. It will be included in the created EAP file and is automatically moved to ~/.e/e/applications/all

Now you just need to edit the .order file for engage:

Code:

sudo nano ~/.e/e/applications/engage/.order



In the file that opens up, just add the name of the .eap file. Let's say you created one that runs "gksudo synaptic" and you called it "Synaptic.eap". You just need to add that .eap file on its own line. So the resulting file should look something like:

eterm.eap
xmms.eap
mozilla-firefox.eap
Synaptic.eap

Save and close that file and you're all done.[/QUOTE]
[QUOTE=linkunderscore]Also, how do I install themes?[/QUOTE]
Go to [http://get-e.org/Themes/E17/index.html]("http://get-e.org/Themes/E17/index.html"). Instructions for downloading and installing themes are there.

[QUOTE=linkunderscore]Is there a file browser for E?[/QUOTE]
Yep. It's called evidence and it's already installed if you used the instrucions from the beginning of this thread. It's coll but a tad buggy. 

Just type in evidence from a command prompt to see it.

[QUOTE=linkunderscore]And my final question....how to i install/run gtk themes in e17 and how do I get them to run on start up.  :)[/QUOTE]
Well, I haven't tried to do this only because e17 has it's own themes. I actually think they're a lot nicer than the gtk stuff. Once you've gotten the rest of your questions taken care of, see if you still want gtk themes. I've never wanted them in e17.

---

### Post by SFN on 2005-09-26
[QUOTE=loon]Anyone tested this elive repo without having to install the beginning files?[/QUOTE]

No dice. It still comes back with

> The following packages have unmet dependencies:
  e17: Depends: efl-all (= cvs20050921) but it is not going to be installed
E: Broken packages


and trying to install efl-all still gives

> The following packages have unmet dependencies:
  efl-all: Depends: libxine-dev but it is not going to be installed
           Depends: libimlib2-dev (>= 1.2.1.001-1) but it is not going to be installed or
                    libimlib2-dev but it is not going to be installed
E: Broken packages


Hopefully the lib stuff will get updated in Breezy. I actually thought about doing a Breezy install just to see how e17 would work but it doesn't look like e17 is going to be in Breezy anyway so I figured I'd just wait until Breezy was officially released (and thus stable) then just try to install e17 over that.

---

### Post by SFN on 2005-09-27
[QUOTE=SFN]Hopefully the lib stuff will get updated in Breezy. I actually thought about doing a Breezy install just to see how e17 would work but it doesn't look like e17 is going to be in Breezy anyway so I figured I'd just wait until Breezy was officially released (and thus stable) then just try to install e17 over that.[/QUOTE]

Um,

I just upgraded to Breezy. Guess I just can't help myself.

Once the upgrade was done, I treid doing the e17 install without the extra lib debs. Same errors as before. I guess that means they won't be upgrading those libs in Breezy.

*grumble grumble grumble*


EDIT: Scratch that. Maybe. I just realized that I did "apt-get upgrade" instead of "apt-get dist-upgrade". Doing "dist-upgrade" now. I'll update when it's done.

UPDATE: Oh, I just had to do it, didn't I? The upgrade wouldn't complete and now the system won't restart. Lovely. Well, the best advice I can offer is, don't do that.

---

### Post by foxy123 on 2005-09-28
I've got Breezy preview release on my test drive, and Elive repo does not work without installing additional Debian libs which is not a good thing. I am thinking about using a script from another topic. Anyway it won't happen anytime soon since I've just got no time to switch to Breezy as a primary distro.

---

### Post by Morm on 2005-09-29
Foxy123:

Everything worked perfectly for me, but I also ran into Amarok running even though I couldn't see it. I had resume on, so it would start playing and I would see the album cover pop up each time a new song played. Not being a real Linux expert, I replaced the Debian debs with Ubuntu ones and removed E17. Then back in Gnome, Amarok wasn't visible when I launched. Then I realized - d'oh.... It was minimized to the tray. lol :oops:

So I may turn resume off, disable the tray icon and try again.

I don't know if you goofed like I did, but just in case - you might want to check that out.

---

### Post by spindley on 2005-09-30
[QUOTE=foxy123]I've got Breezy preview release on my test drive, and Elive repo does not work without installing additional Debian libs which is not a good thing. I am thinking about using a script from another topic. Anyway it won't happen anytime soon since I've just got no time to switch to Breezy as a primary distro.[/QUOTE]
I've got e17 successfully built on breezy using cvs and compiling by hand.  Get-E.org has a section for ubuntu dependancies that need to be installed at the bottom of this page: [http://get-e.org/User_Guide/English/_pages/2.2.html]("http://get-e.org/User_Guide/English/_pages/2.2.html"), which includes automake-1.7 (after which, you have to change some sylinks or it tries to use 1.4).  After all this, E17 launches fine.  However, any app that I add to the menu or ibar freezes the desktop completely solid when I try to launch them.  So far I've tried evolution and gaim.  All the default apps in the ibar (firefox, xchat, xterm, gimp, etc.) all launch fine though.
Pretty annoying.
Mike

---

### Post by SamuliSuominen on 2005-10-02
Are you complete retard? Installing libc6, glibc that provides the base for all
programs from different distro?

PEOPLE! This will break your WHOLE system, including simple commands
like "ls" , "cd". 

Please remove this retard from forums.

---

### Post by foxy123 on 2005-10-02
[QUOTE=SamuliSuominen]Are you complete retard? Installing libc6, glibc that provides the base for all
programs from different distro?
PEOPLE! This will break your WHOLE system, including simple commands
like "ls" , "cd". 
Please remove this retard from forums.[/QUOTE]
it does not look like breaking anything in my system, even ls and cd...

---

### Post by SFN on 2005-10-02
[QUOTE=SamuliSuominen]This will break your WHOLE system, including simple commands like "ls" , "cd".[/QUOTE]

Hmm, yes. As evidenced by all of the people who have done this and ended up with broken systems.

---

### Post by localzuk on 2005-10-02
As he states at the beginning -  it is not meant for the faint of heart (which you obviously appear to be). It is for people who like bells, whistles and shineyness.

He stated it can be bad - so there was no need for such an aggressive post.

Personally, I use e17 from source rather than messing with various, possibly, incompatible repos - but then there are always those trying to improve the ease of installation (which this guy is doing).

Please post constructive comments rather than abusive ones.

Going back to the original post - does it allow the use of 'entrance'?

---

### Post by SFN on 2005-10-02
[QUOTE=localzuk]Going back to the original post - does it allow the use of 'entrance'?[/QUOTE]
I haven't tried it since the first time around. At the time, installing entrance caused gdm to be removed. Then entrance wouldn't start up so back out to the console login you went.
When I did that, it wasn't a gigantic problem to get back to gdm. It was an "apt-get remove --purge" for entrance and an "apt-get install" for gdm. Still, I was happy with gdm and wasn't into the headache of messing with it.
Looking at the repo, it does appear that a newer version of entrance is available so that may be fixed. I'll try it tomorrw (on a different machine) and post the results here.

---

### Post by SFN on 2005-10-03
OK. I installed entrance but I'm getting the same results. It doesn't work and gdm gets removed.
With Breezy coming out in just under two weeks, it seems to me that we should probably be looking for a Breezy repo. It just so happens that dvlspawn created one for us. Details are here:
[http://ubuntuforums.org/showthread.php?p=378692&highlight=breezy#post378692]("http://ubuntuforums.org/showthread.php?p=378692&highlight=breezy#post378692")
It works perfectly without updating the libc6 stuff. I just added his repo (and commented out the Elive stuff), then did
```
sudo apt-get install enlightenment
```
Just remember: Breezy only.
I haven't installed any of the extras yet. Also, it doesn't have all of the extras, but it's got the basics plus some other good stuff. It's very cool to have a good starting point. Plus it's just started so we may get some good stuff out of this. 
Many beers for dvlspawn.

---

### Post by foxy123 on 2005-10-06
Elive updated its repository... Now I cannot change desktop background, the utility crashes evry time I try to fire it. Does not matter though. Looking forward to switch to Breezy and use either the script or a new repo, mentioned here...

---

### Post by SFN on 2005-10-06
Yep. Once Breezy is released and Smoon's new repo is happening, I'd recommend that everyone abandon this method completely.

---

### Post by Spyderizer on 2005-10-12
I'm getting a similar problem to the first one mentioned with it not installing efl-all, but with different depedancies missing.

"efl-all:
 Depends: xlibmesa-dev  but it is not installable or
 	xlibmesa-gl-dev  but it is not installable or
 	libglu1-xorg-dev  but it is not installable"

I'm using a fresh Breezy installation.
I tried using those debs mentioned at the begining, although those were either present or older then ones that came with breezy, also their usage leads into why I have a fresh Breezy installation.

My sources:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu](http://nz.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## e17 repository from Elive
deb [http://www.vobcopy.org/mirror/elive/](http://www.vobcopy.org/mirror/elive/) elive main efl elive

---

### Post by Spyderizer on 2005-10-12
Nevermind, I was just doing something retarded. That'll teach me for not reading the end of the thread.

Yeah, that repo seems to work a treat...using E17 now infact.

---

### Post by shadoi on 2005-10-17
Hi, 

I'm the current Debian package maintainer for the Enlightenment project, I've created native Ubuntu 5.10 packages, found here:
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

This is the first draft of these packages.  So please give me feedback on their quality.

---

### Post by foxy123 on 2005-10-17
[QUOTE=shadoi]Hi, 

I'm the current Debian package maintainer for the Enlightenment project, I've created native Ubuntu 5.10 packages, found here:
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

This is the first draft of these packages.  So please give me feedback on their quality.[/QUOTE]
thanks a lot, Shadoi. I will try it as soon as I get Breezy installed on my laptop some time that week.

---

### Post by Spyderizer on 2005-10-18
Apparently I need libssl0.9.8. The latest one I can find in synaptic is 0.9.7. Which repo would I be missing?

---

### Post by foxy123 on 2005-10-18
[QUOTE=shadoi]Hi, 

I'm the current Debian package maintainer for the Enlightenment project, I've created native Ubuntu 5.10 packages, found here:
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

This is the first draft of these packages.  So please give me feedback on their quality.[/QUOTE]

Got that:
```
W: GPG error: http://soulmachine.net unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BC95B8B5CF6984C
W: You may want to run apt-get update to correct these problems

```

how to fix it?

---

### Post by sinkemlow on 2005-10-22
[Signed Repositories]("http://shadoi.soulmachine.net/2005/10/signed-repositories.html")

You've to run a couple of commands:

wget soulmachine.net/public.key && apt-key add public.key

Then your apt-get update should go well.

---

### Post by foxy123 on 2005-10-22
[QUOTE=sinkemlow][Signed Repositories]("http://shadoi.soulmachine.net/2005/10/signed-repositories.html")

You've to run a couple of commands:

wget soulmachine.net/public.key && apt-key add public.key

Then your apt-get update should go well.[/QUOTE]
yes, I have already figured it out, thanks to shadoi's instructions in his blog. Thanks a lot anyway.

---

### Post by totalshredder on 2005-10-26
Hey Guys,

  I plugged all the stuff into my sources.list and hit apt-get update and I got an error

[CODEW: GPG error: http://www.vobcopy.org elive Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1C79A27CD5E81909
W: You may want to run apt-get update to correct these problems][/CODE]

But, this is after I got the signed repositories. It also has a different "pubkey" than the last guy who had an error like this. Anybody have a clue? Thanks fellas.

---

### Post by Samuli on 2005-10-31
Doesn't replacing the libc6 (and all the other packages you need to replace) with debian versions break dependencies for just about everything in the repositories? :rolleyes: 

If so, I don't understand the "convenience" of this How-to over compiling it yourself. It really wasn't so hard anyways. Oh, and maybe there should be mention in the guide how to disable nautilus to draw the desktop (which draws over to E17 tools AND disables mouse menu). You can do this by switching off "show_desktop" @ applications/system tools/configuration editor/apps/nautilus/preferences/

PS. Thanks for the info how to integrate E17 in to gnome. _much_ appreciated :)

EDIT: nevermind for the last paragraph, I have way too many ubuntuforums windows open in my browser :)

---

### Post by Noahod on 2005-11-18
I was stupid enough to follow these instructions and install the libc packages, and now my system is borked, I can't even use apt to install or remove the packages. 

Anyone know how I can rescue my system? (breezy badger)

---

### Post by Benn on 2005-11-26
> 
I was stupid enough to follow these instructions and install the libc packages, and now my system is borked, I can't even use apt to install or remove the packages.

Anyone know how I can rescue my system? (breezy badger)


Exactly that happened to me, i solved it by using Synaptic, it re-upgraded  to libc6-ubuntu.

By the way, the repos doesn't worked for me:

> 
W: GPG error: [http://www.vobcopy.org](http://www.vobcopy.org) elive Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1C79A27CD5E81909
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas


And I can't find the Publick Key in order to add it with apt-key

see ya

---

### Post by Benn on 2005-12-03
Any ideas ?

:(

---

### Post by corefile on 2005-12-31
[QUOTE=shadoi]Hi, 

I'm the current Debian package maintainer for the Enlightenment project, I've created native Ubuntu 5.10 packages, found here:
deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

This is the first draft of these packages.  So please give me feedback on their quality.[/QUOTE]



These packages do work very well, the only problem is that this repository has not been updated in ages, if you really want to enjoy E17 just compile it from cvs, not hard, and enjoy E17 that is current

---

### Post by b0bby on 2006-06-21
i get this error when running apt-get update,
```
W: GPG error: [http://www.vobcopy.org](http://www.vobcopy.org) elive Release: 
The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY 1C79A27CD5E81909
```

and if a try to install e17 anyway i get
```
b0bby@laptop:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
e17: Depends: efl-all (= cvs2005082 but it is not going to be installed
E: Broken packages
```

and if i try to run sudo apt-get install elf-all i get
```
b0bby@laptop:~$ sudo apt-get install efl-all
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  efl-all: Depends: libglu1-xorg but it is not installable
           Depends: libimlib2-dev but it is not going to be installed
E: Broken packages
```

*sad puppy*:(
got any ideas how to fix the public key thing?

---

### Post by nwgray on 2006-06-22
Looks like the cvs repo is dead. Get these errors:

graynw@ubuntu7:~/cvs$ cvs -d:pserver:anonymous:@cvs.sourceforge.net:/cvsroot/enlightenment login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/enlightenment
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host
graynw@ubuntu7:~/cvs$ cvs -z3 -d:pserver:anonymous:@cvs.sourceforge.net:/cvsroot/enlightenment co e17 misc
cvs [checkout aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host


Bummer.

---

### Post by TLE on 2006-06-22
Is this HOWTO still valid for Dapper?
There have only been 2 posts in 2006

---

### Post by askyle on 2006-06-23
[QUOTE=nwgray]Looks like the cvs repo is dead. Get these errors:
graynw@ubuntu7:~/cvs$ cvs -d:pserver:anonymous:@cvs.sourceforge.net:/cvsroot/enlightenment login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/enlightenment
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host
[/QUOTE]

Replace cvs.sourceforge.net with enlightenment.cvs.sourceforge.net. Thus:

```
cvs -d:pserver:anonymous:@**enlightenment.**cvs.sourceforge.net:/cvsroot/enlightenment login
```

Similarly for other cvs commands. Hope this helps.

---

### Post by gavcos on 2006-06-23
The correct repository is:

:pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e

---

### Post by Feanor on 2006-07-22
> **b0bby said:**
> i get this error when running apt-get update,
```
W: GPG error: [http://www.vobcopy.org](http://www.vobcopy.org) elive Release: 
The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY 1C79A27CD5E81909
```

and if a try to install e17 anyway i get
```
b0bby@laptop:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
e17: Depends: efl-all (= cvs2005082 but it is not going to be installed
E: Broken packages
```

and if i try to run sudo apt-get install elf-all i get
```
b0bby@laptop:~$ sudo apt-get install efl-all
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  efl-all: Depends: libglu1-xorg but it is not installable
           Depends: libimlib2-dev but it is not going to be installed
E: Broken packages
```

*sad puppy*:(
got any ideas how to fix the public key thing?

I've got the same problem... Where can we find the public key to download the packages? :-k

---

### Post by ajmorris on 2007-01-22
i know this a very old thread but i was wondering if i can get some help on engage?

I want to configure it to put it on top of other windows and also i want to manually edit the eap entries that were automatically created because when i try to run one of the applications from the bar it says "/home/myuser/%u doesn't exist."


Any help is greatly appreciated.

---

### Post by hyg53 on 2007-05-19
> **totalshredder said:**
> Hey Guys,

  I plugged all the stuff into my sources.list and hit apt-get update and I got an error

```
W: GPG error: http://www.vobcopy.org elive Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1C79A27CD5E81909
W: You may want to run apt-get update to correct these problems]
```
It type it for the Debian users that may find this post and try to use the Elive repos: try this guys
```
sudo -s
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1C79A27CD5E81909
gpg --armor --export 1C79A27CD5E81909 | apt-key add -
apt-get update 
```

for the ubuntu users, you'd better use the edevelop ubuntu repositories

---

### Post by vanden12 on 2007-09-02
So by doing this...
Can I make ubuntu look like elive?

---

### Post by Nick_Jinn on 2010-07-28
Subscribes


It would be nice to get a remix of E17 based on Mint with all the codecs they added. Xfce or LXDE versions.

---

