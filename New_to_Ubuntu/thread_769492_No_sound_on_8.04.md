---
title: "No sound on 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-04-26
I have had 8.04 since it has been released and I have had sound, but recently it has been going in and out and then I have to restart to get sound back then after awhile it goes away. I have an old dell with the dell speakers if that helps to know. What should I do to get sound working?

---

### Post by TimTim on 2008-04-28
You are luckier than me. I have no sound at all since I installed 8.04 on my desktop. It's not my hardware problem, because my desktop has three OS (Ubuntu 8.04, Ubuntu 7.10 & WinXP). Sound works on both of 7.10 & WinXP. Any idea?

---

### Post by Rodhill on 2008-04-28
Same here, I had sound in 7.04 but not in 8.04. My sound card says in the sound menu 'not connected':confused: Anyone any ideas?

Rod

---

### Post by Raistlinbuntu on 2008-04-28
> **TimTim said:**
> You are luckier than me. I have no sound at all since I installed 8.04 on my desktop. It's not my hardware problem, because my desktop has three OS (Ubuntu 8.04, Ubuntu 7.10 & WinXP). Sound works on both of 7.10 & WinXP. Any idea?

I tell you more: on the login, the splash sound works. After that, nothing... (I upgraded from 7.10 to 8.04)
I try to reboot with both the kernels but nothing changes.

---

### Post by Eisenwinter on 2008-04-28
All of you open up terminal.
```
asoundconf list
```
Type that, post output here.

---

### Post by Rodhill on 2008-04-28
Hi This is what I got:-

rod@rod-desktop:~$ asoundconf list
Names of available sound cards:
Live
rod@rod-desktop:~$ 


Rod

P.S. In my sound card menu in preferences it says my VIA8237 is 'not connected'.

---

### Post by Raistlinbuntu on 2008-04-28
> **Eisenwinter said:**
> All of you open up terminal.
```
asoundconf list
```
Type that, post output here.

asoundconf list
Names of available sound cards:
ICH6

---

### Post by Eisenwinter on 2008-04-28
Go to System -> Preferences -> Sound.

On each of the drop down boxes, select ALSA - Advanced Linux Sound Architecture, and click on the "Test" button.

If no sound is heard, something may be wrong with ALSA.

In that case, I advise installing ALSA from source.
____________________________

Since I assume you guys are absolute beginners (otherwise you wouldn't be posting in this section of the forums ;)) I'll make a small guide for you.

**Section one - Getting the ALSA drivers and libraries**
Open up terminal.
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2
```

Note: the terminal will only let you download one file at a time, so please be patient.

Don't close the terminal, we'll need it.

**Section two - Extracting files from our downloaded archives**
```
tar -xvf /home/<username>/alsa-driver-1.0.16.tar.bz2
tar -xvf /home/<username>/alsa-lib-1.0.16.tar.bz2
tar -xvf /home/username/alsa-firmware-1.0.16.tar.bz2
tar -xvf /home/username/alsa-utils-1.0.16.tar.bz2
```

This will create four different folders in your home folder.
Also, this can be performed through the graphical user interface as well, my intention here is to just teach you how to uncompress basic archives.

**Section three - Installing ALSA**

In this section, we are going to compile configure and compile ALSA according to **_our_** devices.
This is what's so great about it, it compiles specifically to OUR machines :).

Open up the terminal.
We will now use the CD command to get into each of the directories.
But first...
```
sudo apt-get install build-essential
```
Install the build-essential package, it installs tools required for compiling and installing software from source.

After build-essential is downloaded, get into each of the directories. First - ALSA-driver.
```
cd /home/username/alsa-driver-1.0.16
```

**Raistlinbuntu:**
You type now:
```
./configure --with-cards=ICH6
make
make install
```

Do this with all other packages, except for the ALSA-utils package.

**Rodhill:**
You do the same, but with "Live" as the parameter.

If you get an error saying "No such driver", you can take a look [Here]("http://www.alsa-project.org/main/index.php/Matrix:Main") to see if ALSA supports your soundcard.

---

### Post by DezSP on 2008-04-28
Good post, but just in case mythical beings from the future using Google find this, 1.0.16 might not be the latest ALSA version, so you might need to find that out and change it before following what Eisen suggested. :)

---

### Post by martrn on 2008-04-28
why not use module-assistant to make / build / compile

open up a terminal and type :

```
sudo apt-get install build-essential
module-assistant
```

Start and Use [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") as a guide and when you get to the stage -- Using alsa-source * then note that .... ".. Open up a shell: (note: module-assistant is optional, it will compile the package for you) ..."....
means type module-assistant as this is not really optional as it will compile, build and install the module for you. If you do not want to compile, build and install just run this and the (optional part) will complete the compile build and install process for you.

You will need the alsa driver notes from:
[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")
This guide works.

---

### Post by Rodhill on 2008-04-28
Hi Eisenwinter,
Everything went fine up to this point:-
rod@rod-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rod@rod-desktop:~$ cd /home/username/alsa-driver-1.0.16
bash: cd: /home/username/alsa-driver-1.0.16: No such file or directory
rod@rod-desktop:~$ 

Any suggestions?

Rod

---

### Post by martrn on 2008-04-28
you didn't type this did ya ?
```

cd /home/username/alsa-driver-1.0.16
```

I think the idea was to cd /home/rod/alsa-driver-1.0.16
ie replace username with your username...

---

### Post by Rodhill on 2008-04-28
Hi re-did it and got this:-

rod@rod-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rod@rod-desktop:~$ cd /home/rod/alsa-driver-1.0.16
bash: cd: /home/rod/alsa-driver-1.0.16: No such file or directory
rod@rod-desktop:~$ 

not sure what to do next?

Rod

---

### Post by martrn on 2008-04-28
I do not build my drivers that way, I 

type at a terminal
```
sudo apt-get build essential
sudo module-assistant
```

and build it that way.
The official guide is at : 
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") when you get to .....".....Open up a shell: (note: module-assistant is optional, it will compile the package for you) .....".....

means you can make / configre / compile / install them yourself or

```
sudo module-assistant
```

and step through it.  I do it that way as I find it easier.

---

### Post by rajaram_s on 2008-04-28
I get sounds for all my songs and videos, but the login log out sounds alone seems to be disabled since my upgrade to 8.04. When I test audio, sound comes. When I click on the system sounds in sounds menu, it says install package gnome-audio. What does this mean?

---

### Post by martrn on 2008-04-28
> **rajaram_s said:**
> .... it says install package gnome-audio. What does this mean?

This means open a terminal and type :-
```
sudo apt-get install gnome-audio
```

---

### Post by Raistlinbuntu on 2008-04-28
> **Eisenwinter said:**
> 

If you get an error saying "No such driver", you can take a look [Here]("http://www.alsa-project.org/main/index.php/Matrix:Main") to see if ALSA supports your soundcard.

I got an error like this:

checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for which soundcards to compile driver for... configure: error: Unknown soundcard ICH6

lspci said:
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

On [ALSA]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel") I see that ICH6 family is compatible.

Any idea?

---

### Post by almabeck on 2008-04-28
I have the same sound problems and am following Eisenwinter's suggestions. All went well (I'm substituting "Intel" in the appropriate spot) until this point:

alma@dell:~/alsa-lib-1.0.16$ ./configure make
configure: WARNING: you should use --build, --host, --target
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed

---

### Post by Raistlinbuntu on 2008-04-28
> **almabeck said:**
> I have the same sound problems and am following Eisenwinter's suggestions. All went well (I'm substituting "Intel" in the appropriate spot) until this point:

alma@dell:~/alsa-lib-1.0.16$ ./configure make
configure: WARNING: you should use --build, --host, --target
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash ./config.sub make failed

"configure ...", "make" and "make install" are 3 different commands.

First you lauch the configure utility, than the "make" and than the "make install".

---

### Post by almabeck on 2008-04-28
> **Raistlinbuntu said:**
> "configure ...", "make" and "make install" are 3 different commands.

First you lauch the configure utility, than the "make" and than the "make install".

Thanks. I went back and tried that. "make" worked, but when I try "make install" I get this error:

alma@dell:~/alsa-driver-1.0.16$ make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/alma/alsa-driver-1.0.16/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
install: cannot change owner and permissions of `/usr/include/sound': No such file or directory
install: cannot create regular file `/usr/include/sound': Permission denied

[lots more repeats of above line--have deleted to save space here.] 

make: *** [install-headers] Error 1
alma@dell:~/alsa-driver-1.0.16$

---

### Post by Rodhill on 2008-04-28
I'm still stuck with no sound:confused:In the sound section my card is listed as a SB Live 5.1 (alsa mixer). I can't see it in any of the above categories in 'sound preferences'.I've tried all suggestions even going into "Getting the ALSA drivers from a *fresh* kernel" Using this I had to re-install my Gnome desktop but nothing has changed in the sound.
I went into the alsa drivers menu and mine is 'sb8'(a Creative Labs).
I've inputed all the suggestions in this thread but to no avail.Please has anyone any further suggestions?

thanks so far everyone

Rod

---

### Post by hooper on 2008-04-28
This just outright sucks.

Everytime I upgrade Ubuntu, I have to spend hours searching the damn forums trying to fix sound. Same problem with some progs in 7.10. I'm about fed up with it, they can either get their head out of the rear end or I'm going back to debian or slackware. The whole point of Ubuntu is that is is supposed to just work. Sound is supposed to work. If I wanted to compile my system, I wouldn't be using ubuntu in the first place.

I have the same issues, login and logout sounds do not work, pulseaudio is a piece of ****. I guess the Ubuntu devs believes that no one is going to install anything outside of the regular packaging ideas. This stinks. Not that you have to install a third party app TO CLEARLY SEE THAT THERE ARE ISSUES. 

All the testing, all the releases, all the time envolved and they cannot even check a damn login logout sound. I've about had it with ubuntu. Next revision gives me grief after I get this going and I'll never use it again.

Still doesn't work. Nor many third party apps. This is over a year now. Two revisions. 7.10 and 8.04. Both do not work.

ls |grep ubuntu dev dumbasses

No wonder walmart pulled the linux boxes with ubuntu off the shelves.

I could install debian 4 or slackware 12 and sound just works. You use ubuntu to save time, it ends up costing you more time and energy than compiling your system from sources. Just makes me sick.

The person above this post is using a SB Live 5.1 card. Now how long has this hardware been out there? How long? My card is a 1010LT 12 channel mixing card from m-audio. It works super and has been supported for over 4 years in linux. This is the **** I'm talking about. It's not Linux or debian that is the issue, it's UBUNTU.

Hooper

---

### Post by Rodhill on 2008-04-29
> **hooper said:**
> This just outright sucks.

Everytime I upgrade Ubuntu, I have to spend hours searching the damn forums trying to fix sound. Same problem with some progs in 7.10. I'm about fed up with it, they can either get their head out of the rear end or I'm going back to debian or slackware. The whole point of Ubuntu is that is is supposed to just work. Sound is supposed to work. If I wanted to compile my system, I wouldn't be using ubuntu in the first place.

I have the same issues, login and logout sounds do not work, pulseaudio is a piece of ****. I guess the Ubuntu devs believes that no one is going to install anything outside of the regular packaging ideas. This stinks. Not that you have to install a third party app TO CLEARLY SEE THAT THERE ARE ISSUE

All the testing, all the releases, all the time envolved and they cannot even check a damn login logout sound. I've about had it with ubuntu. Next revision gives me grief after I get this going and I'll never use it again.

Still doesn't work. Nor many third party apps. This is over a year now. Two revisions. 7.10 and 8.04. Both do not work.

ls |grep ubuntu dev dumbasses

No wonder walmart pulled the linux boxes with ubuntu off the shelves.

I could install debian 4 or slackware 12 and sound just works. You use ubuntu to save time, it ends up costing you more time and energy than compiling your system from sources. Just makes me sick.

The person above this post is using a SB Live 5.1 card. Now how long has this hardware been out there? How long? My card is a 1010LT 12 channel mixing card from m-audio. It works super and has been supported for over 4 years in linux. This is the **** I'm talking about. It's not Linux or debian that is the issue, it's UBUNTU.

Hooper

I can't think why I had sound in 7.10 and an upgrade makes it so difficult to have it working again. I spent the whole day yesterday trawling through 'do this''do that' and it still isn't working.I'm going to try a bit more and hope someone can help - please anyone:confused:

Rod

---

### Post by Raistlinbuntu on 2008-04-29
> **Rodhill said:**
> I can't think why I had sound in 7.10 and an upgrade makes it so difficult to have it working again. I spent the whole day yesterday trawling through 'do this''do that' and it still isn't working.I'm going to try a bit more and hope someone can help - please anyone:confused:

Rod

Hi everybody!
IT WORKS!

In my case was a problem in the alsamixer configuration. Not a problem with the kernel, not with the driver.
When you upgrade from 7.10 to 8.04, it switchs on almost every channel in the mixer.
I turned off every channel except: Master, Headphones, PCM, Line, CD, Mic

After that you reload the alsa and than it works!

The command are:
```
alsamixer
alsa reload
```

I hope you'll find my solution useful.

---

### Post by Rodhill on 2008-04-29
> **Raistlinbuntu said:**
> Hi everybody!
IT WORKS!

In my case was a problem in the alsamixer configuration. Not a problem with the kernel, not with the driver.
When you upgrade from 7.10 to 8.04, it switchs on almost every channel in the mixer.
I turned off every channel except: Master, Headphones, PCM, Line, CD, Mic

After that you reload the alsa and than it works!

The command are:
```
alsamixer
alsa reload
```

I hope you'll find my solution useful.

I'll give that a go tonight! many thanks. I'll let you know:)

Rod

---

### Post by marquee moon on 2008-04-29
On my Toshiba Satellite laptop, I had sound in 7.04. Then when I upgraded to 7.10, the sound stopped working & hasnt come back with 8.04. 

To be fair, the integrated sound cards on laptops in general arent too hot anyway. So I bought an [imic ](http://search.ebay.co.uk/search/search.dll?from=R40&_trksid=m37&satitle=imic)(external USB soundcard) from ebay for less than £20 delivered. That sorted out the problem straight off. Plug it in & get better sound than your built in sound card (no electrical interferance from motherboard & hardrive activity, so no annoying clicks & hums). 
Ubuntu recognises it straight off with no problems. 

Better sound quality & no problems with configering internal sound cards- I recommend this as a possible way forward.

---

### Post by mormor on 2008-04-29
This did the trick for my acer travelmate 6291. worth a try?


>  Originally Posted by Joshua Netterfield  View Post
The best way I have found to fix this problem is just to run alsaconf. Ubuntu doesn't include it, because it has a way cooler system which always works except for when it doesn't. Nice. We will need to install it ourselves.

1. Open up a terminal. (Applications->Accessories->Terminal)
2. Type "gedit ./alsaconf.sh" (without the quotes)
3. Go to [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf), select everything (ctrl+a) and copy it (ctrl+c)
4. Go to the gedit window. Paste what you copied (ctrl+v)
5. Save it.
6. Go back to the terminal and run:
Code:

chmod +x ./alsaconf.sh
sudo ./alsaconf.sh

7. Follow the instructions
8. It should work. But it still might not...


"Chmod +x" makes the program runnable, and "sudo ./alsaconf.sh" runs it.
The script detects the sound cards that you have and gets them ready for use.

Good luck!

Edit: Oh ya. Source is [http://www.ubuntux.org/sound-card-not-detected](http://www.ubuntux.org/sound-card-not-detected) . You should thank them if it works (;

---

### Post by msmollin on 2008-04-29
> **mormor said:**
> This did the trick for my acer travelmate 6291. worth a try?

BRILLIANT! That resurrected my sound. Looking thru the script, it appears to redo the entire ALSA sound stack and driver set up. Basically like killing a fly with a sledgehammer, although seems to be the only way to get ALSA back into working shape.

I gotta say, so far this 8.04 upgrade has been the suck. I've had to reinstall the nvidia drivers which it claimed it updated to the match the kernel modules but didn't, so X wouldn't load, then firefox would crash going to staples.com and other big name sites so that got reinstalled, and then the sound wouldn't load. LTS edition whateveredition. I hope their helpdesk is swamped.

Thanks again for the linkage!

---

### Post by mormor on 2008-04-29
: ) no problem. Not my solution, but happy to pass it on.

Hope some more peeps find it too- Glad it worked

---

### Post by Rodhill on 2008-04-29
> **Raistlinbuntu said:**
> Hi everybody!
IT WORKS!

In my case was a problem in the alsamixer configuration. Not a problem with the kernel, not with the driver.
When you upgrade from 7.10 to 8.04, it switchs on almost every channel in the mixer.
I turned off every channel except: Master, Headphones, PCM, Line, CD, Mic

After that you reload the alsa and than it works!

The command are:
```
alsamixer
alsa reload
```

I hope you'll find my solution useful.

Nope still no sound:confused:In the alsamixer it shows my sound card correctly.
When I try to save the settings you did it says this:-
rod@rod-desktop:~$ alsamixer

rod@rod-desktop:~$ alsa reload
/sbin/alsa: Warning: Processes using sound devices: 6879(mixer_applet2). 
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-emu10k1-synth snd-emux-synth snd-seq-virmidi snd-seq-midi-emul snd-emu10k1 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-util-mem snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
rod@rod-desktop:~$ 

So still nothing working!

Cheers

Rod

---

### Post by Rodhill on 2008-04-29
> **mormor said:**
> This did the trick for my acer travelmate 6291. worth a try?
Hi Mormor,
I tried this too but still no sound. Everything was ok in 7.10. My card is correctly detected and it doesn't matter what I do now can't get sound. Thanks though for your help.

Rod

---

### Post by Eisenwinter on 2008-04-29
Rodhill: in preferneces -> sounds, you select ALSA (Advanced Linux Sound Architecture) to test it.

I see "ICH6" wasn't working for you.

Get into the ALSA driver dir (/home/<username>/alsa-driver-1.0.16 most likely - remember to replace <username> with your login name).

use the terminal cd command to do it.

now try, ./configure --with-cards=sb8
make
make install
if this works, install the rest of the packages (alsa lib, alsa utils, and alsa firmware).

report back results, I may not be here to answer immediately, I have work in 2 and a half hours.

---

### Post by martrn on 2008-04-29
> **Rodhill said:**
> Hi Mormor,
I tried this too but still no sound. Everything was ok in 7.10. My card is correctly detected and **[SIZE="4"]it doesn't matter what I do now can't get sound[/SIZE]**. Thanks though for your help.Rod

So you have tried everything....
Including rebuilding your drivers from the source ????

From:- 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Follow it through then when you get to 
Using alsa-source

type at a terminal
```
sudo apt-get build essential
sudo module-assistant
```

and build it that way.

note *-** when you get to .....".....Open up a shell: (note: module-assistant is optional, it will compile the package for you) .....".....

means you can make / configre / compile / install them yourself or
do the opitionbit (as it is easier)....


```
sudo module-assistant
```
get the source
build asla module
select you correct sound card from
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
and install using module-assistant

and step through it. I do it that way as I find it easier.

Have you tried this ????

---

### Post by martrn on 2008-04-29
> **Eisenwinter said:**
> 

now try, ./configure --with-cards=sb8



I recommend to use module-assistant and let it do the hard-work for you....

---

### Post by Rodhill on 2008-04-30
> **Eisenwinter said:**
> Rodhill: in preferneces -> sounds, you select ALSA (Advanced Linux Sound Architecture) to test it.

I see "ICH6" wasn't working for you.

Get into the ALSA driver dir (/home/<username>/alsa-driver-1.0.16 most likely - remember to replace <username> with your login name).

use the terminal cd command to do it.

now try, ./configure --with-cards=sb8
make
make install
if this works, install the rest of the packages (alsa lib, alsa utils, and alsa firmware).

report back results, I may not be here to answer immediately, I have work in 2 and a half hours.

When you say get into the ALSA directory are you saying I do this in the terminal - as I have typed in what you said but nothing happened.I got this:-

rod@rod-desktop:~$ /home/rod/alsa-driver-1.0.16
bash: /home/rod/alsa-driver-1.0.16: No such file or directory
rod@rod-desktop:~$ 

 Can you give me the exact cd terminal 'command line' to do this. Sorry but I'm very new to all this:)

Rod

---

### Post by christianxxx on 2008-04-30
This might not be very constructive, but this thread reminds me of my upgrade Feisty->Gutsy. 
The upgrade broke sound, and I could never find a solution.
I can fully understand the frustrations, but all I could ever do to fix it was a clean installation. 

For those wanting to keep settings and files it might not be the best of solutions, but I strongly recommend it. 
I have actually put of Hardy-upgrade because I don't want these problems again, and now is a bad time to do a fresh install.

I really hope you'll find a fix, but you might consider doing a fresh install. Best of luck!

Also, Rodhill, you might consider using Tab-key for auto completing directories and filenames, it makes it so much easier if you have trouble finding the correct names. Just type a few characters and TAB, if it completes just continue, if not, the few characters might be wrong. Remember linux is case-sensitive...

---

### Post by almabeck on 2008-04-30
> **Eisenwinter said:**
> Rodhill: in preferneces -> sounds, you select ALSA (Advanced Linux Sound Architecture) to test it.

I see "ICH6" wasn't working for you.

Get into the ALSA driver dir (/home/<username>/alsa-driver-1.0.16 most likely - remember to replace <username> with your login name).

use the terminal cd command to do it.

now try, ./configure --with-cards=sb8
make
make install
if this works, install the rest of the packages (alsa lib, alsa utils, and alsa firmware).

report back results, I may not be here to answer immediately, I have work in 2 and a half hours.

I have the same problem (Dell Inspiron 1420, with Intel card). When I try this, I have success up until  "make install". Then I get this error message:


alma@dell:~/alsa-driver-1.0.16$ make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/alma/alsa-driver-1.0.16/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
install: cannot change owner and permissions of `/usr/include/sound': No such file or directory
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1

---

### Post by Thormick on 2008-04-30
I thought my sound was broken, but it turned out that that the volume level that I had used in 7.10 was almost silent in 8.04. As soon as I'd turned up the "Master" and "PCM" volume levels from 50% to just above 90%, everything was okay. It might just be my built in Intel sound card, and changes in it's driver though.

---

### Post by Rodhill on 2008-05-01
> **Rodhill said:**
> When you say get into the ALSA directory are you saying I do this in the terminal - as I have typed in what you said but nothing happened.I got this:-

rod@rod-desktop:~$ /home/rod/alsa-driver-1.0.16
bash: /home/rod/alsa-driver-1.0.16: No such file or directory
rod@rod-desktop:~$ 

 Can you give me the exact cd terminal 'command line' to do this. Sorry but I'm very new to all this:)

Rod

Can anyone help with this please...

Rod

---

### Post by martrn on 2008-05-01
find ././ -name "alsa-driver*"
then cd whatever it spews out....

you are not a fraction of the way through this yet.....

Sorry you didn't try this :
(in a terminal)
```
sudo apt-get build-essential
sudo apt-get module-assistant
sudo module-assistant
```

select update
select prepare
select alsa
select your soundcard
build / compile / install through a menu.

I unsubscribe from this thred to stop bothering you, and you are intent on doing it the hard way.

---

### Post by martrn on 2008-05-01
OK, If anyone knows how to unsubscribe from a thred that got themselves into contributing to please let me know how.

---

### Post by almabeck on 2008-05-01
> **Eisenwinter said:**
> Go to System -> Preferences -> Sound.

On each of the drop down boxes, select ALSA - Advanced Linux Sound Architecture, and click on the "Test" button.

If no sound is heard, something may be wrong with ALSA.

In that case, I advise installing ALSA from source.
____________________________

Since I assume you guys are absolute beginners (otherwise you wouldn't be posting in this section of the forums ;)) I'll make a small guide for you.

**Section one - Getting the ALSA drivers and libraries**
Open up terminal.
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2
```

Note: the terminal will only let you download one file at a time, so please be patient.

Don't close the terminal, we'll need it.

**Section two - Extracting files from our downloaded archives**
```
tar -xvf /home/<username>/alsa-driver-1.0.16.tar.bz2
tar -xvf /home/<username>/alsa-lib-1.0.16.tar.bz2
tar -xvf /home/username/alsa-firmware-1.0.16.tar.bz2
tar -xvf /home/username/alsa-utils-1.0.16.tar.bz2
```

This will create four different folders in your home folder.
Also, this can be performed through the graphical user interface as well, my intention here is to just teach you how to uncompress basic archives.

**Section three - Installing ALSA**

In this section, we are going to compile configure and compile ALSA according to **_our_** devices.
This is what's so great about it, it compiles specifically to OUR machines :).

Open up the terminal.
We will now use the CD command to get into each of the directories.
But first...
```
sudo apt-get install build-essential
```
Install the build-essential package, it installs tools required for compiling and installing software from source.

After build-essential is downloaded, get into each of the directories. First - ALSA-driver.
```
cd /home/username/alsa-driver-1.0.16
```

**Raistlinbuntu:**
You type now:
```
./configure --with-cards=ICH6
make
make install
```

Do this with all other packages, except for the ALSA-utils package.

**Rodhill:**
You do the same, but with "Live" as the parameter.

If you get an error saying "No such driver", you can take a look [Here]("http://www.alsa-project.org/main/index.php/Matrix:Main") to see if ALSA supports your soundcard.

All goes well until I try "make install" Then, I get the error message:
alma@dell:~/alsa-driver-1.0.16$ make install
if [ -L /usr/include/sound ]; then \
rm -f /usr/include/sound; \
ln -sf /home/alma/alsa-driver-1.0.16/include/sound /usr/include/sound; \
else \
rm -rf /usr/include/sound; \
install -d -m 755 -g root -o root /usr/include/sound; \
for f in include/sound/*.h; do \
install -m 644 -g root -o root $f /usr/include/sound; \
done \
fi
install: cannot change owner and permissions of `/usr/include/sound': No such file or directory
install: cannot create regular file `/usr/include/sound': Permission denied


Now what can I try? I'd be grateful for any assistance.

---

### Post by martrn on 2008-05-01
```
./configure --with-cards=hda-intel --with-sequencer=yes --read-the-manual=always
make
make install
```

try
```
configure --help
```

I don't think this will work but read the documentation / manual usualy helps with your configure options ?

---

### Post by almabeck on 2008-05-01
> **martrn said:**
> ```
./configure --with-cards=hda-intel --with-sequencer=yes --read-the-manual=always
make
make install
```

Thanks. When I try it I get the message:

alma@dell:~/alsa-driver-1.0.16$ ./configure --with-cards=hda-intel --with-sequencer=yes  --read-the-manual=always
configure: error: unrecognized option: --read-the-manual=always
Try `./configure --help' for more information.


I also tried doing it without the "read-the-manual" part and got the same error message I originally got.

Anything else I can try?

---

### Post by almabeck on 2008-05-01
> **martrn said:**
> ```
./configure --with-cards=hda-intel --with-sequencer=yes --read-the-manual=always
make
make install
```

try
```
configure --help
```

I don't think this will work but read the documentation / manual usualy helps with your configure options ?

Got my hopes up--after doing the "configure --help" code, the "make" took lots longer. However, "make install" gave me the same error code. 

Where can I find the documentation/manual? I'm doubting I can understand it (I'm REALLY new and ignorant), but I'll sure try.

---

### Post by martrn on 2008-05-01
> Where can I find the documentation/manual? I'm doubting I can understand it (I'm REALLY new and ignorant), but I'll sure try.

[http://lau.linuxaudio.org/Sound-HOWTO.html]("http://lau.linuxaudio.org/Sound-HOWTO.html")
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

---

### Post by TimTim on 2008-05-06
> **Eisenwinter said:**
> All of you open up terminal.
```
asoundconf list
```
Type that, post output here.

Here is mine:

timtim@E16:~$ asoundconf list
Names of available sound cards:
V8237
timtim@E16:~$

---

### Post by TopFan on 2008-05-06
Being an absolute beginner, I have no intention of getting involved with terminal, or searching the net for stuff that should have 'just worked'.

Having upgraded to 8.04, I now have a very quiet laptop. When will this problem be resloved via Software Update? Or am I compelled to live in silence unitl 8.10?

---

### Post by evozniak on 2008-05-06
in my acer laptop the problem is fixed doing..

Right clicl in sound icon placed in top panel > preferences > master source **surround**

try this after all other tricks.

---

### Post by Periswell on 2008-05-06
my sound on my computer just gave up one day, my solution, buy a new computer. its what i did.

---

### Post by TopFan on 2008-05-06
Thanks fot that. Unfortunately, it doesn't work on my Dell 1525. I can't get the preferences panel up. I click on 'Preferences' and nothing happens.

Anyone else got any non-terminal ideas?

Modified to add: I like the idea of buying a new computer, but that seems an expensive way of dealing with upgrades! My hardware is fine - it worked yesterday under 7.10. It's Hardly Hero that's broken.

---

### Post by TimTim on 2008-05-06
i guess the problem is due to the change of the sound server at 8.04. unlike those previous version, 8.04 uses PulseAudio as the default sound server. maybe there are some problem between ALSA & PulseAudio.

i will try to re-compile ALSA from the source. if it still doesn't work, i have to switch back to 7.10 for a while...:(:(:(

---

### Post by TimTim on 2008-05-06
when i "make install" in the alsa-driver-1.0.16 directory, i got this warning:
cp ac97_bus.ko /lib/modules/2.6.24-16-generic/kernel/sound/misc
make[1]: Leaving directory `/home/timtim/local/alsa-driver-1.0.16/misc'
/sbin/depmod -a 2.6.24-16-generic 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

root@E16:/home/timtim/local/alsa-driver-1.0.16#

any idea?

---

### Post by Declanthedork on 2008-12-04
> **Eisenwinter said:**
> All of you open up terminal.
```
asoundconf list
```
Type that, post output here.

Names of available sound cards:
CA0106

---

### Post by Xacarith on 2008-12-13
Just something to try that has worked for another and for me when having some sound issues.  Has any one tried to install 'esound'?  Hope this helps some one

---

### Post by cirr on 2009-01-20
I did the following:
$ asoundconf list
Names of available sound cards:
Intel
CMI8738

Then everything you suggested (wget, tar etc) then

 ./configure --with-cards=Intel

It was all looking very promising until:
checking for which soundcards to compile driver for... configure: error: Unknown soundcard Intel

Is the answer just to go and buy one of the sound cards suggested by the ALSA SoundCard Matrix?

---

### Post by asuastrophysics on 2009-04-05
> **Eisenwinter said:**
> Go to System -> Preferences -> Sound.

On each of the drop down boxes, select ALSA - Advanced Linux Sound Architecture, and click on the "Test" button.

If no sound is heard, something may be wrong with ALSA.

In that case, I advise installing ALSA from source.
____________________________

Since I assume you guys are absolute beginners (otherwise you wouldn't be posting in this section of the forums ;)) I'll make a small guide for you.

**Section one - Getting the ALSA drivers and libraries**
Open up terminal.
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2
```

Note: the terminal will only let you download one file at a time, so please be patient.

Don't close the terminal, we'll need it.

**Section two - Extracting files from our downloaded archives**
```
tar -xvf /home/<username>/alsa-driver-1.0.16.tar.bz2
tar -xvf /home/<username>/alsa-lib-1.0.16.tar.bz2
tar -xvf /home/username/alsa-firmware-1.0.16.tar.bz2
tar -xvf /home/username/alsa-utils-1.0.16.tar.bz2
```

This will create four different folders in your home folder.
Also, this can be performed through the graphical user interface as well, my intention here is to just teach you how to uncompress basic archives.

**Section three - Installing ALSA**

In this section, we are going to compile configure and compile ALSA according to **_our_** devices.
This is what's so great about it, it compiles specifically to OUR machines :).

Open up the terminal.
We will now use the CD command to get into each of the directories.
But first...
```
sudo apt-get install build-essential
```
Install the build-essential package, it installs tools required for compiling and installing software from source.

After build-essential is downloaded, get into each of the directories. First - ALSA-driver.
```
cd /home/username/alsa-driver-1.0.16
```

**Raistlinbuntu:**
You type now:
```
./configure --with-cards=ICH6
make
make install
```

Do this with all other packages, except for the ALSA-utils package.

**Rodhill:**
You do the same, but with "Live" as the parameter.

If you get an error saying "No such driver", you can take a look [Here]("http://www.alsa-project.org/main/index.php/Matrix:Main") to see if ALSA supports your soundcard.


after "make", i get this: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/girdy/alsa-driver-1.0.16/acore/hwdep.o
In file included from /home/girdy/alsa-driver-1.0.16/include/adriver.h:940,
                 from /home/girdy/alsa-driver-1.0.16/acore/hwdep.c:1:
include/linux/pci.h:627: error: expected identifier or ‘(’ before numeric constant
In file included from include/asm/pci.h:4,
                 from include/linux/pci.h:989,
                 from /home/girdy/alsa-driver-1.0.16/include/adriver.h:940,
                 from /home/girdy/alsa-driver-1.0.16/acore/hwdep.c:1:
include/linux/mm.h:261: error: conflicting types for ‘snd_compat_vmalloc_to_page’
/home/girdy/alsa-driver-1.0.16/include/adriver.h:744: error: previous declaration of ‘snd_compat_vmalloc_to_page’ was here
In file included from /home/girdy/alsa-driver-1.0.16/acore/hwdep.c:1:
/home/girdy/alsa-driver-1.0.16/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/girdy/alsa-driver-1.0.16/include/adriver.h:1182: error: too many arguments to function ‘pci_save_state’
/home/girdy/alsa-driver-1.0.16/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/girdy/alsa-driver-1.0.16/include/adriver.h:1186: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/girdy/alsa-driver-1.0.16/acore/hwdep.o] Error 1
make[2]: *** [/home/girdy/alsa-driver-1.0.16/acore] Error 2
make[1]: *** [_module_/home/girdy/alsa-driver-1.0.16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [compile] Error 2

this is really annoying. i've spent the past hour and a half trying to fix this. why can't the sound just work??? ](*,)](*,)](*,)](*,)](*,)

---

### Post by aavaliani on 2009-08-27
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)  I followed this documentation, and it was very helpful.

---

### Post by lkraemer on 2009-08-27
Shouldn't the typical commands be:
```

./configure --with-cards=ICH6
make
sudo make install

```

The last command is the same I use when I compile my madwifi drivers.

lkraemer

---

### Post by PeterVR on 2009-09-07
Thanks aavaliani

I followed some three hundred howto's trying to get a single bleep out of a Dell Latitude D830. Your link was the only one with a positive result.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) !

---

### Post by dognose2 on 2009-09-09
> **hooper said:**
> This just outright sucks.

Everytime I upgrade Ubuntu, I have to spend hours searching the damn forums trying to fix sound. Same problem with some progs in 7.10. I'm about fed up with it, they can either get their head out of the rear end or I'm going back to debian or slackware. The whole point of Ubuntu is that is is supposed to just work. Sound is supposed to work. If I wanted to compile my system, I wouldn't be using ubuntu in the first place.

Hooper

Tell me about it.   I've been trying for a week to get sound and tty working.. no one here helping.  docs and posts are all over the map with advice, but doesn't seem like anyone here even know how it all fits together.    I've been a linux user for years, but I'll have to say, I get more problems than ever with it.  

~d

---

### Post by shamimkhaliq on 2009-09-19
> **hooper said:**
> This just outright sucks.

Everytime I upgrade Ubuntu, I have to spend hours searching the damn forums trying to fix sound. Same problem with some progs in 7.10. I'm about fed up with it, they can either get their head out of the rear end or I'm going back to debian or slackware. The whole point of Ubuntu is that is is supposed to just work. Sound is supposed to work. If I wanted to compile my system, I wouldn't be using ubuntu in the first place...

I've about had it with ubuntu. Next revision gives me grief after I get this going and I'll never use it again.

Still doesn't work. Nor many third party apps. This is over a year now. Two revisions. 7.10 and 8.04. Both do not work...

No wonder walmart pulled the linux boxes with ubuntu off the shelves.

I could install debian 4 or slackware 12 and sound just works. You use ubuntu to save time, it ends up costing you more time and energy than compiling your system from sources. Just makes me sick.

The person above this post is using a SB Live 5.1 card. Now how long has this hardware been out there? How long? My card is a 1010LT 12 channel mixing card from m-audio. It works super and has been supported for over 4 years in linux. This is the **** I'm talking about. It's not Linux or debian that is the issue, it's UBUNTU.

Hooper

SAME HERE. ubuntu needs a "linux restore" function so i can use the old version from 5 years ago that worked, or 1 year ago when it worked too, or even a few months back when it worked. when it works again remind me to switch off the update option.

as a linux newbie (i confess to returning to windows when i get frustrated) i've just had problems finding anything as easy to install as ubuntu, even if it doesn't work 80% of the time it's an easy install. i'll try debian and slackware again (thanks for the info) as soon as i can get my burner to work to burn off documents. ubuntu has plagued me with on/off no sound and ruining DVD disks for years.

---

### Post by vmonsanto on 2009-09-26
I updated from 7.10 to 8.04 and I got the crossed circle of dead over my volumen control icon. After weeks reading tons of sugestion and explanations (that I hardly understand) about how to fix it, I just restore my computer to factory setings lossing everything. That was almos a year ago. 

Stupid me, that try once more to upgrade to 8.04, thinking that maybe by this time it would work.

I have a dell inspiron 1525. A DELL!!!! COME ON!!! If I had a ChuriChurinFunFlay computer made in some unknow country, maybe I could understand why my sound card doesn't work. BUT I HAVE A DELL!!! A DELL, FOR GOD SAKE!!! Who made a computer program that won't work on dell? 

I know anyone can made a mistake. But this is a year long mistake.

---

### Post by dognose2 on 2009-10-25
Yeah, a DELL.. and to top it off, a Dell with Ubuntu Linux pre installed.  so, it should be all compatible.  geez.

---

### Post by gareththomasnz on 2009-10-27
Quote Eisenwinter:

Go to System -> Preferences -> Sound.

On each of the drop down boxes, select ALSA - Advanced Linux Sound Architecture, and click on the "Test" button.

If no sound is heard, something may be wrong with ALSA.

In that case, I advise installing ALSA from source.

This has saved my *** more than once - thanks

---

### Post by Spoooolin on 2009-11-28
> **gareththomasnz said:**
> Quote Eisenwinter:

Go to System -> Preferences -> Sound.

On each of the drop down boxes, select ALSA - Advanced Linux Sound Architecture, and click on the "Test" button.

If no sound is heard, something may be wrong with ALSA.

In that case, I advise installing ALSA from source.

This has saved my *** more than once - thanks


How exactly, do I install it from source?  Total n00b here, as I am sure you figured out by my question.

---

### Post by Crossbow on 2009-11-28
> **dognose2 said:**
> Yeah, a DELL.. and to top it off, a Dell with Ubuntu Linux pre installed.  so, it should be all compatible.  geez.

Me too. A Dell 530, preinstalled with Ubuntu. And my sound works for a while but then when I'm away it shuts off. I've spent HOURS trying all the suggestions to fix it, and no luck. I've given up. It's my one big problem with Ubuntu.

---

### Post by Spoooolin on 2009-11-28
Anyone know where I can get a Windows Torrent that works, since my New laptop did not come with the reboot cd's?

I need sound.

---

### Post by mizami on 2010-03-23
i've tried the command given but it result no command available.. i've tried csound instead and download i don't know what it is. then i try again command asoundconsf ls stll the same.. n at the system>sound there is no ASDL..

---

### Post by Leo Simon on 2010-04-13
I have no sound on my Dell D630 running Hardy.  Never had any since the beginning, but I do have sound in windows.

The command
 cat /proc/asound/card0/codec#* | grep Codec
 returns
        Codec: SigmaTel STAC9205
        Codec: Conexant ID 2c06

I'm not sure of the relationship between this output and my sound card, which as far as I can tel is hda-intel

I followed Eisenwriter's instructions to the end, using ./configure --with-cards=hda-intel    
Configured, made and made install for all three directories, no errors, as far as I could tell.   Rebooted but still no sound.   The bottom line of my /etc/modprobe.d/alsa-base file has the line
options snd-hda-intel model=auto.    Tried various other model names as well, but nothing worked.    Any advice as to what I should do next?

---

### Post by lidex on 2010-04-13
> **Leo Simon said:**
> I have no sound on my Dell D630 running Hardy.  Never had any since the beginning, but I do have sound in windows.

The command
 cat /proc/asound/card0/codec#* | grep Codec
 returns
        Codec: SigmaTel STAC9205
        Codec: Conexant ID 2c06

I'm not sure of the relationship between this output and my sound card, which as far as I can tel is hda-intel

I followed Eisenwriter's instructions to the end, using ./configure --with-cards=hda-intel    
Configured, made and made install for all three directories, no errors, as far as I could tell.   Rebooted but still no sound.   The bottom line of my /etc/modprobe.d/alsa-base file has the line
options snd-hda-intel model=auto.    Tried various other model names as well, but nothing worked.    Any advice as to what I should do next?

Can you give me a little more info? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by rapelover on 2010-05-17
"Good post, but just in case mythical beings from the future using Google  find this, 1.0.16 might not be the latest ALSA version, so you might  need to find that out and change it before following what Eisen  suggested. :smile:"

I'm Einstein and still got no sound. I hear the starting sound but nothing since. I try to listen W.A.S.P. as loud as I can but the sound is still not coming out of the sockets. I had the same problem occasionally with Karmic Koala freak. What's wrong? Do I have to become regular in here to hear something?

---

### Post by rapelover on 2010-05-17
my laptop is general brand esystem, very cheap

navetta@navetta-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC662 rev1
Codec: Intel G45 DEVCTG

---

