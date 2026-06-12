---
title: "How To Install Ubuntu 7.10 (Gutsy) on Dell Inspiron 1520"
date: 2007-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by ctpaterson on 2007-10-16
Hey all,

I've seen bits and pieces about, but no thread that specifically talks about installing gutsy on an Inspiron 1520, so I thought I'd kick one off in the hopes it would help.

A few notes, I did this with the 32-bit final release.  I could not get my 1520 to boot from the 64-bit CD.  Corrections, additions, and comments are encouraged, especially since some people might have some different hardware than I.

Computer specs are:
[LIST]
[*] Intel Core 2 Duo T7300
[*] 2 GB RAM
[*] 1680x1050 display
[*] 256MB nVidial GeForce TM8600M GT video card
[*] High Definition audio 2.0
[*] Intel PRO/Wireless 3945abg
[*] Integrated webcam
[*] Dell wireless 355 bluetooth internal
[/LIST]

What's working...
[LIST]
[*] Sound from speakers + speaker cutoff when headphones plugged in
[*] High-res screen, w/ Compiz effects
[*] Plug-in microphone
[*] Internal microphone
[*] Wireless
[*] Bluetooth scans and finds other devices (haven't successfully connected yet)
[*] Webcam (tested with Ekiga using V4L2, and tested in Skype 2.0 beta)
[*] NFS (working after "sudo apt-get install nfs-common")
[*] Suspend (sort of).  It usually works...sometimes it doesn't.
[*] Memory card slot (tested with SD)
[/LIST]

What's not working...
[LIST]
[*] Suspend (sort of).  It usually works...sometimes it doesn't.
[*] Hibernate (got it to return once, but it took a while)
[*] Bluetooth connections (success has been reported by at least one user - not for me)
[/LIST]

What I haven't tested.
[LIST]
[*] Modem (there are some reported issues)
[/LIST]

The good news is that besides the audio, I've had to do very little in the way of post-installation system configuration.  Much less painful than feisty.  The bad news is that the audio was the main thing that was snarfed - the same problem is happening on several other models.

What I did...
[LIST=1]
[*] Boot from live CD; install
[*] Boot from hard drive
[*] Enable restricted nVidia drivers
[*] Install all Ubuntu updates
[*] Perform audio fix (as suggested by "alexander.forster"
[LIST]
[*] sudo apt-get install linux-backports-modules-generic
[/LIST]
[*] Reboot so all changes take effect; you should now have sound.
[*] You might want to do the following if you find the volume too low (courtesy from alfredska)
[LIST]
[*] Right click on speaker icon in system tray, and select "Open Volume Control"
[*] Go to Edit: Preferences
[*] Put a check next to Front. Hit OK
[*] Turn Front volume all the way up.
[*] Now the master volume control raises and lowers the volume between much greater extremes.
[/LIST]
[*] Amixer settings so the microphone plugging in to the side will work...
[LIST]
[*] amixer set Capture 15 cap
[*] amixer set Mux,0 3 cap
[/LIST]
[*] Settings so the digital mic will work
[LIST]
[*] Run "alsamixer", scroll to the right with the arrow keys until you've selected "Digital".
[*] If the Digital Input Source is "Analog Inputs", use the up/down arrows until it says "Digital Mic 1".
[*] Hit "Escape" to exit. 
[*] *(I believe switching the Digital back and forth from "Analog Inputs" to "Digital Mic 1" will cause a switch between the internal mic, and the mic plugged into the side -- but I have not tested this.)*
[*] amixer set Capture 15 cap
[*] amixer set Digital 120
[/LIST]
[/LIST]

Bonus step: "sudo apt-get install compizconfig-settings-manager" to choose from even more effects.

**Other Issues** (mentioned, resolved and otherwise)
[LIST]
[*] Aggressive power management seems to be beating up on some laptop hard drives.  My machine appears to be affected.  More details about the issue here; [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695), and there's an ubuntu discussion thread here; [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503).  I have employed a fix that I've posted here: [http://ubuntuforums.org/showthread.php?p=3778205#post3778205](http://ubuntuforums.org/showthread.php?p=3778205#post3778205).  I'll say again here what I said there; **do not blindly copy and paste my solution unless you're aware of, and accept the risks that come with giving a complete stranger control over how your hardware behaves.**  I strongly recommend you get familiar with the issue yourself and decide if the fix is right for you.  I present what I have done without reassurances that it's safe, but for informational purposes only.
[*] alfredska has cracked the nut of 64-bit and is playing well with Vista and MediaDirect here: [http://ubuntuforums.org/showpost.php?p=3855904&postcount=81](http://ubuntuforums.org/showpost.php?p=3855904&postcount=81)
[*] Or you can try working with XP and Media Direct: [http://ubuntuforums.org/showpost.php?p=4141488&postcount=153](http://ubuntuforums.org/showpost.php?p=4141488&postcount=153)
[*] some people have complained about a lot of noise coming out of their headphones.  A potential solution is here: [http://forum.notebookreview.com/showthread.php?t=197809](http://forum.notebookreview.com/showthread.php?t=197809)
[*] A possible solution for intermittent wireless connectivity issues: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)
[*] A possible solution for suspend (haven't tried it myself): [http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/](http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/)
[*] Some have complained of incorrect titlebar fonts: [http://ubuntuforums.org/showpost.php?p=3592412&postcount=5](http://ubuntuforums.org/showpost.php?p=3592412&postcount=5)
[/LIST]

Thanks to many contributors throughout the thread for filling in a number of gaps and so forth.  I particularly wanted to thank alfredska who has become a key resource for a lot of people.

---

### Post by kirkquitar on 2007-10-16
I have a Dell 1720, the Intel PRO/Wireless 3945abg wasn't working for me with the 64bit RC. It could see the networks, but not connect. Also modem doesn't work. I could not get the sound to work, but I messed around enough that I'm going to start fresh and try some of the other fixes, I'll have a detailed update for what works/doesn't and what I did to fix it this weekend. I'm going to be trying this on 32 bit, just in case 64 bit was contributing to the sound problem.

---

### Post by ctpaterson on 2007-10-16
> **kirkquitar said:**
> I have a Dell 1720, the Intel PRO/Wireless 3945abg wasn't working for me with the 64bit RC. It could see the networks, but not connect. Also modem doesn't work. I could not get the sound to work, but I messed around enough that I'm going to start fresh and try some of the other fixes, I'll have a detailed update for what works/doesn't and what I did to fix it this weekend. I'm going to be trying this on 32 bit, just in case 64 bit was contributing to the sound problem.

The procedure I've used to fix the audio was originally recommended for a 1720 - so I would think it should work for your machine.  If it's a difference between a 32 and 64 bit release - that would be an interesting thing to note.

Cheers.

---

### Post by linux23dragon on 2007-10-18
Alsa-1.0.15  has lots of Intel HDA driver and codec fixes.  You might even have more PCM devices too :-)

I have written a [_*[COLOR="Blue"]howto[/COLOR]*_]("http://ubuntuforums.org/showthread.php?t=530374&highlight=1520+dell+alsa+hda+intel") if you want to check the new drivers out.  Just skip down to the "Installing the Alsa Sound System" section.  I'll be supporting Gusty LL kernels soon.

Enjoy :-)

---

### Post by alexander.forster on 2007-10-18
hey so i tried this method and it said this:



alexander@lappie-tron:~$  wget [ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2)
--12:55:48--  [ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2)
           => `drive....15rc1.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive....15rc1.tar.bz2 ... 
No such file `drive....15rc1.tar.bz2'.

any help would be greatly appreciated.
oh btw i am on a dell 1521 so i imagine the soundcard is the same. but it just seem to be having a problem getting the file...
thank you very much :)

---

### Post by alexander.forster on 2007-10-18
oh and when i click the link on the howto that you wrote, it d/l the file :S but i dont know what to do with it.

oh and sorry, but im a complete beginner

---

### Post by ctpaterson on 2007-10-18
> **alexander.forster said:**
> hey so i tried this method and it said this:



alexander@lappie-tron:~$  wget [ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2)
--12:55:48--  [ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....15rc1.tar.bz2)
           => `drive....15rc1.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive....15rc1.tar.bz2 ... 
No such file `drive....15rc1.tar.bz2'.

any help would be greatly appreciated.
oh btw i am on a dell 1521 so i imagine the soundcard is the same. but it just seem to be having a problem getting the file...
thank you very much :)

Sorry - you got screwed because the rendering shrunk the link (notice the ellipses in the middle of the URL).  Of course, clicking on it works.  ;>

If you can find the file, just move it into your home directory, cd to your home directory, and proceed down the steps.  Otherwise, go over them again.  I've changed the line so it doesn't resolve to a URL anymore, but I had to add a space between "ftp://" and "pub/".  You'll need to take it out after copying.

A suggestion, if you're feeling brave; the instructions use 1.0.15rc1 of the alsa drivers, but 1.0.15 is out.  If you felt like wgetting the 1.0.15 version instead of 1.0.15rc1 for us, and confirming all is still well - I'd appreciate it.

You can confirm that you have the same card as I by executing the commands at the "$" prompt - and seeing if you have the same results:

> 
paterson@bilbo:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
paterson@bilbo:~$ lspci -n | grep 1b
00:1b.0 0403: 8086:284b (rev 02)


1521 has the AMD processor and ATI graphics card, I believe.  You should be okay, but ignore the references to the nVidia.

Good luck

---

### Post by lefthand on 2007-10-18
I had some trouble with the audio fix as well. It wanted me to install binutils-dev instead of libc5-dev and  './configure --with-cards=hda-intel,emu10k1' didn't work.

But I found these instructions which did the trick for me...

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I found that here: [http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

---

### Post by alexander.forster on 2007-10-18
first off thanks to ctpaterson   for the quick resposnse and i used this to get it working

sudo apt-get install linux-backports-modules-generic

well im pretty darn sure thats the one i used. it works because it has alsa 1.0.15 built in or something :S

sorry im a total linux/ubuntu beginner so... but anyway, that method is nice and clean, and after a quick reboot i had sound :)

---

### Post by ctpaterson on 2007-10-18
Thanks for the feedback on alternative audio solutions, guys.  I'll update the procedures to mention them up front, and when I get a chance to do some tests with the final release (the servers are a tad busy now, and I figured I'll leave the bandwidth for more needy users), I'll pick the simplest/easiest to recommend.

---

### Post by sebald on 2007-10-18
As far as NFS goes, you might have to actually install NFS mounting capability, check for the appropriate packages in Synaptic. I had to install the samba mount separately on every Ubuntu install I've done!

---

### Post by muadnu on 2007-10-18
None of these solutions for the sound has worked in my Vostro 1400 (I'm running 64 bit Gutsy). Anyone got lucky?

---

### Post by ctpaterson on 2007-10-18
> **sebald said:**
> As far as NFS goes, you might have to actually install NFS mounting capability, check for the appropriate packages in Synaptic. I had to install the samba mount separately on every Ubuntu install I've done!

Samba I'm used to having to install - but not NFS.  Nonetheless, your comments prompted me to do some more googling, and "sudo apt-get install nfs-common" delivered me from evil.  Thanks **very** much.

---

### Post by linux23dragon on 2007-10-19
I've updated the Sound card howto to support Gusty.

Please help test [here]("http://ubuntuforums.org/showthread.php?t=530374&highlight=intel+hda")

---

### Post by DarthTibault on 2007-10-19
I can confirm that the linux-backports-modules-generic package works perfectly: installed it and rebooted, everything works now (yes it mutes the speakers when you plug in headphones). The volume does need a boost and to enable the microphones etc, you just have to enable all the tracks in volumecontrol (edit->preferences) and mess a little with the settings (I set "front" to max).

Am I the only one that gets huge letters in some places (eg: the login screen)???

---

### Post by odin1965 on 2007-10-19
> **lefthand said:**
> I had some trouble with the audio fix as well. It wanted me to install binutils-dev instead of libc5-dev and  './configure --with-cards=hda-intel,emu10k1' didn't work.

But I found these instructions which did the trick for me...

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

I found that here: [http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

I tried this method and I now have sound, but it doesn't mute when I insert the headphones. Any ideas?

---

### Post by muadnu on 2007-10-19
Anyone has it working with Gutsy 64 bit? I'm not sure it should make a difference, but nothing has worked for me...

---

### Post by mac-duff on 2007-10-19
Hi,
after I had installed Ubuntu 7.10 I installed the nvidia graphic driver via ENVY and activated the graphic acceleration. Since that I just have a screen resolution from 640x480 or so. How can I go back to 1680 x 1050 because this is really annoying.

thx


edit:
ok, the failure is that after ubuntu has not discovered the monitor. now I choosed a dell monitor with a size of 1600+1200, but i have 1680 x 1050... so, how do I do? :D

---

### Post by qbox on 2007-10-19
Hi to all. this is my first time to run ubuntu
I have Dell inspiron 1520
My sound card not work,
dell wireless 1505 wireless-n mini-card not working 
and I have no idea how to repearite.
Any help?
Thx to all
P.S. I looking for solution on google and didnt find nothing

---

### Post by OiPenguin on 2007-10-19
I'm on the look out for a not to expensive lap top. Would you recommend buying this machine? I'm a newbie determined to use Ubuntu but can't really determine the complexity of the described problems.

Yours,

Lars

---

### Post by JekiTheRogue on 2007-10-19
I tried all these steps, and still no sound.  I decided to start over, and did apt-get remove alsa.  It removed successfully, and then after a reboot my sound started working.  Odd, but thought I'd post this in case it might help anyone else.  I have a Dell 1721 with the Sigmatel 9205 chipset, which I think is the same used in the 152x/172x line.

---

### Post by linux23dragon on 2007-10-19
> **JekiTheRogue said:**
> I tried all these steps, and still no sound.  I decided to start over, and did apt-get remove alsa.  It removed successfully, and then after a reboot my sound started working.  Odd, but thought I'd post this in case it might help anyone else.  I have a Dell 1721 with the Sigmatel 9205 chipset, which I think is the same used in the 152x/172x line.

How does that work?

It must remove something but the driver itself. unless it defaults to oss drivers?

---

### Post by muadnu on 2007-10-20
I finally got the sound working! I tried many things and nothing worked. At the end I found this link [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330"), rebooted, and sound works fine now! I'm not sure if some of the things I did before were needed or not, but I hope this helps in any case...

---

### Post by qbox on 2007-10-20
YESS
I install sound card drivers finaly.

sudo apt-get install libncurses5-dev gettext libncursesw5-dev speex  libspeex-dev liba52-0.7.4-dev libsamplerate0-dev jackd jack-rack libjack0.100.0-dev checkinstall  build-essential linux-headers-$(uname -r)

apt-get remove alsa

but the sound is too low

---

### Post by sloter on 2007-10-21
Hi,

Just for information,
I just upgraded my 1505 from feisty to gutsy and the sound is not working.

Thanks,
sloter

---

### Post by sloter on 2007-10-21
Ok,

Since my inspiron 1505 is
```
lspci
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```
I went to [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

I did the **Method B: Manually build alsa-modules** but with 1.0.15-rc**[COLOR="Red"]3[/COLOR]** as suggested in the comment.

In order to compile properly I also had to install the kernel-headers package
```
sudo aptitude install kernel-headers-`uname -r`
```

Everything is working great!

Thanks,
sloter

---

### Post by Horrendus on 2007-10-21
Hello,

Sound works perfectly with the linux-backports-modules-generic package.

Can also confirm that Bluetooth is working out of the box.

Stefan

---

### Post by ankursmart on 2007-10-21
Hi

I upgraded from Feisty to Gutsy. I upgraded to new kernel 2.6.22 and installed latest ALSA packages (alsa-driver, alsa-lib, alsa-utils).

Though the sound is working, but I cannot get the internal microphone working.

Could anyone help on this?

Ankur

---

### Post by linux23dragon on 2007-10-21
I've included a simple check list to the [[COLOR="Blue"]*_HDA Howto_*[/COLOR]]("http://ubuntuforums.org/showthread.php?t=530374&highlight=intel+hda") post.  It might be a good idea if you follow that before you compile your own Alsa drivers.  Lots of cleanups as well is included.  

And I put a note on how to inform (or submit bug reports) to the Ubuntu developers, if you get the Sound card working.

Hope this helps

---

### Post by necross on 2007-10-21
Hey guys. I'm new and am a noob to ubuntu. I would really like to keep this os but am having a few problems on it. After installing Gusty my sound, wireless and bluetooth does not work. Though I somehow fixed the sound I really need to get the wireless and bluetooth working.

For my wireless I have the "Dell Wireless 1505 N" card, not the intel chipset. I called dell and confirmed this. 

My bluetooth recognizes my devices (mouse) but gives an error when it tries to connect. 

Can you guys please help me out? Keeping in mind that I'm completely new at this. Thanks alot.

- Necross

---

### Post by Jeffrey Magder on 2007-10-21
> **JekiTheRogue said:**
> I tried all these steps, and still no sound.  I decided to start over, and did apt-get remove alsa.  It removed successfully, and then after a reboot my sound started working.  Odd, but thought I'd post this in case it might help anyone else.  I have a Dell 1721 with the Sigmatel 9205 chipset, which I think is the same used in the 152x/172x line.
I am happy to confirm that the Dell Inspiron 1721's sound problems can be fixed by running:

 [FONT="Courier New"]sudo apt-get remove alsa[/FONT]

I think the problem is that the alsa package is mistakingly installing drivers for the 1720's chipset (Intel based), instead of the drivers for the 1721 chipset (ATI/AMD based).  

Running:

[FONT="Courier New"]lspci | grep Audio[/FONT]

now returns:

[FONT="Courier New"]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia[/FONT]

Note that if your audio sounds to quiet, you can still change the volumes by playing around with [FONT="Courier New"]alsamixer[/FONT].  Thanks for your post JekiTheRogue! :-)

---

### Post by necross on 2007-10-21
Can someone please help me out with my bluetooth and wireless problem plx? Thanks.

---

### Post by ctpaterson on 2007-10-21
> **necross said:**
> Can someone please help me out with my bluetooth and wireless problem plx? Thanks.


So, generally, it's not great form to ask again for help after two hours of waiting.  We're all doing this in our spare time.  No hard feelings, but if you're very new at this - then it's something you should be aware of.

I can't help you with the Bluetooth - I don't have it working either; it browses and finds other device, but I get cryptic errors when trying to connect.  If I ever find a solution, I'll post it.

As for your wireless; I did some googling for you, and came across this thread: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

It was first posted about feisty, but it may be helpful.  You should dig through it and see if anyone's talked about gutsy.  It's a long thread, so set yourself some time.

Good luck.

---

### Post by argux on 2007-10-21
w00t!

Module Assistant method worked perfectly on an Inspiron 1501. You can add that to the list.

Necross: You should create a new topic for that question.

---

### Post by mac-duff on 2007-10-22
Hi,
well, I have problems with my mic too. I remember by version 7.04 I had the same issue. At this time I just had to install the RC of ALSA driver but now I doesnt work, tried the RC and the final.
For testing the mic I also installed a audio record tool, but I forgot the same, guess it started with aud....

hope somebody can help me

---

### Post by badriThebig on 2007-10-22
thank you for those instructions , it was very **effective** and I've returned back my sound card driver which I was the cause of lost the sound driver.
and it set my microphone :guitar:

---

### Post by ctpaterson on 2007-10-22
> **mac-duff said:**
> Hi,
well, I have problems with my mic too. I remember by version 7.04 I had the same issue. At this time I just had to install the RC of ALSA driver but now I doesnt work, tried the RC and the final.
For testing the mic I also installed a audio record tool, but I forgot the same, guess it started with aud....

hope somebody can help me

Audacity?  That's what I used to test my mic.  Again; I'll say that the mic I used was one that plugged into the ministereo mic port on the side -- NOT the internal mic.

I would think that a particular incantation of amixer settings would do the trick - but no joy yet.

---

### Post by mac-duff on 2007-10-22
thx,
this was exactly the tool I was looking for. Now I just have to get work my mic


edit:
I just mentioned that the scroll function of my touchpad doesnt work. Also I have the feeling that its more sensitive then before. Can someone confirm it?

---

### Post by chess360 on 2007-10-24
Hi All! My laptop is Inspiron 1520 with sound card Sigmatel 9250 and display card nVidia 8600. 

I messed around for a few days and finally got them working. Now I have sound, can plug in the headphone to mute the speakers, and the mic is working (tested with "Application->Sound and Video->Sound Recorder"). 

Below are what I did. Hope this helps.

1. Install Gutsy with the Live CD. Pretty straight forward.

2. "System->Administration->Software Sources" for an update. Check everything under tab "Ubuntu Software". Click "Close". Many "how-to" articles did not mention this essential step. 

3. "System->Administration->Restricted Driver Manager". Enable nVidia driver. (Perform Step 2 beforehand is essential) After that Compiz could be installed and enabled.

4. Follow atpaterson's 1st method to install the alsa-driver. I used 1..15rc3 driver instead of atpaterson's rc1. I also typed the line "./configure --with-cards=hda-intel" without ",emu10k1".

5. Edit "/etc/modprobe.d/alsa-base" by adding a line "options snd-hda-intel model=3stack"

6. Use "Synaptic Package Manager" to install "irqbalance" (Step 2 beforehand is essential) and "alsa-oss". And remove "alsa-base". 

7. Reboot and good luck.

To Mac-duff: I also feel  the mouse is a little bit more sensitive than it is under Windows. I adjust it with "Sytem->Preference->Mouse". You may give it a go too.

---

### Post by mac-duff on 2007-10-24
Hi,
yes, with the sensitive I figured out too, but still the scroll function doesnt work.

And my sound.... yesterday I got my mic working, but just if I set it on digital and then I couldnt set the volume.

So, I tried your installation progress and now I have no sound... tried reinstall the driver like I did before, nothing change.....

I think thats are reason why Linux has not so much success. I mean sound is really not so new, but why is it so difficult to get to work it?

---

### Post by ctpaterson on 2007-10-24
> **mac-duff said:**
> Hi,
yes, with the sensitive I figured out too, but still the scroll function doesnt work.

And my sound.... yesterday I got my mic working, but just if I set it on digital and then I couldnt set the volume.

So, I tried your installation progress and now I have no sound... tried reinstall the driver like I did before, nothing change.....

I think thats are reason why Linux has not so much success. I mean sound is really not so new, but why is it so difficult to get to work it?

Hey mac-duff,

If you want to post your amixer settings, I can tell you if I recognize anything.

Cheers.

---

### Post by mac-duff on 2007-10-24
Hi,
there I am a newbie with Linux, u have to help me please, how can I quote my settings :)

---

### Post by ctpaterson on 2007-10-24
> **mac-duff said:**
> Hi,
there I am a newbie with Linux, u have to help me please, how can I quote my settings :)

On the command prompt (Applications -> Accessories -> Terminal) type "amixer" and copy/paste the output.

Cheers.

---

### Post by mac-duff on 2007-10-25
Hi, well, I think this is an easy one:
amixer
amixer: Mixer attach default error: No such device

---

### Post by nutrapi on 2007-10-25
To get sound working on the Sigmatel STAC9228 included with the new Inspirons, add the line:


```

options snd-hda-intel model=3stack

```
to the /etc/modprobe.d/alsa-base


I found this on another post and it worked great on my vostro 1400 in 7.10

---

### Post by chess360 on 2007-10-25
For the touchpad problem, under "System->Preferences->Mouse". Under tab "Touchpad", there are some settings to choose from.

---

### Post by ctpaterson on 2007-10-25
> **mac-duff said:**
> Hi, well, I think this is an easy one:
amixer
amixer: Mixer attach default error: No such device

Yeah, looks like the system has lost your device.  Try the following:

Execute "lspci | grep -i audio"  You should get a line something like:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Then try "lspci -n | grep 00:1b.0" (substitute whatever code came at the beginning of the line you got).

The response I had to the "lspci -n" line is:
00:1b.0 0403: 8086:284b (rev 02)

If you're seeing the same output - then you have the same audio card that I have, and I strongly recommend you follow the procedures I laid out without deviating.  If you have different data, post it, and we'll see if it's a card anyone else recognizes.

Cheers.

---

### Post by mac-duff on 2007-10-26
Hi,
sorry for my late delay, but after I tried to uninstall my audio driver, how its written on the alsa homepage, I couldnt login anymore. but now i am back in my system, but still without sound ;)
I have the same hardware as u and I already tried all kinds of installation. I guess I ****** a bit my system.... because now I can install what I want, nothing change

edit:
does it help:
root@stephan-laptop:/home/stephan# sudo sh /etc/init.d/alsa reload
sh: Can't open /etc/init.d/alsa
??

---

### Post by kirkquitar on 2007-10-26
> **mac-duff said:**
> Hi,
sorry for my late delay, but after I tried to uninstall my audio driver, how its written on the alsa homepage, I couldnt login anymore. but now i am back in my system, but still without sound ;)
I have the same hardware as u and I already tried all kinds of installation. I guess I ****** a bit my system.... because now I can install what I want, nothing change

edit:
does it help:
root@stephan-laptop:/home/stephan# sudo sh /etc/init.d/alsa reload
sh: Can't open /etc/init.d/alsa
??

I had the same problem, I just reinstalled Gutsy, since I didn't have anything important on the partition. You're getting the "Your session lasted less than 10 seconds" thing, right? When it gives you that notification, and asks if you want to see the log, post what's in the log and maybe someone can help you.

---

### Post by ctpaterson on 2007-10-26
> **mac-duff said:**
> Hi,
sorry for my late delay, but after I tried to uninstall my audio driver, how its written on the alsa homepage, I couldnt login anymore. but now i am back in my system, but still without sound ;)
I have the same hardware as u and I already tried all kinds of installation. I guess I ****** a bit my system.... because now I can install what I want, nothing change

edit:
does it help:
root@stephan-laptop:/home/stephan# sudo sh /etc/init.d/alsa reload
sh: Can't open /etc/init.d/alsa
??

Hey mac-duff.  Unfortunately, you're in territory I'm not familiar with.  I can't provide any advice other than to back up any data you care about, and re-install following the guide at the top of this thread.

When it comes to the audio fix, I'd suggest using alexander.forster's alternative as being the easiest and most straightfoward, and confirmed to work.  Remember, **choose only one** of the alternatives.

If you've removed the audio driver, than I'm not surprised that alsa's not there any more.

Sorry I couldn't be of more help.  Good luck.

---

### Post by mac-duff on 2007-10-26
mhhhhh,
ok, thanks four your help!

does ubuntu have a repair function as Windows XP? ;)

---

### Post by mac-duff on 2007-10-26
well, I did a fresh installation of ubuntu and still have the same problem with my sound. i followed 100% your instruduction, but nothing:

stephan@m-d-l:~$ amixer set InMux 4
amixer: Mixer attach default error: No such device
stephan@m-d-l:~$ su
Password: 
root@m-d-l:/home/stephan# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
root@m-d-l:/home/stephan# lspci -n | grep 00:1b.0
00:1b.0 0403: 8086:284b (rev 02)
root@m-d-l:/home/stephan#

edit:
finally it was this:
sudo module-assistant auto-install alsa :) (without the smilie)

---

### Post by mac-duff on 2007-10-27
well,
there I have no sound I have a problem with my mic :D
before (Ubuntu 7.04) I choosed analog and I could set the volume. Now I have to take digital and my phonepartner is complaining about the bad quality, to silent, cant hear very well.....

Can someone agree this?

---

### Post by mac-duff on 2007-10-29
Can please someone post his/her alsa-base file? by who the mic is working please. Also my line out doesnt check if I plug something, then I have sound on the normal speaker and my headset

---

### Post by chess360 on 2007-10-29
Mac-duff:

I got things right (sound and mic) after I installed irqbalance using Synaptic Package Manager. I'm new to Linux too so I don't know why. As we're using the same hardware you may give it a go.

The alsa-base should be removed to get sound.

I had the quality problem too. I tried different mixers at "System->Preferences->Sound->Default Mixer Tracks" and found "Intel" had better sound quality than "Sigmatel". You may try that too.

I showed the Compiz desktop to some of my friends. They're all impressed and a few of them were thinking on trying out Linux.

Good luck!

---

### Post by cellerit on 2007-10-29
hello i had installed gutsy 7.10 beta and all went fine. I eventually had to reinstall (windows install broke partitions :( ) and got everything to work again (first time all compiz effects were enabled by default, this time none ... weird since i used the same cd ). 

Well the point is the media buttons are recognised and an effect is shown but they dont actually affect the volume of alsamixer. I just get the animation. How could i fix this? thanks in advance.

---

### Post by mac-duff on 2007-10-30
ok, lets please give my soundcard a last try. Its really important for me that my mic is working fine there I am bit far away from home.

Current issues:
mic is very quite (have to choose digital input in the sound settings, with ubuntu 7.04 I choosed analog and the quality was perfect. So my phone partner cant hear me)

speaker cutoff when headphones plugged in doesnt work (when I plug a headset I have sound on both speaker. After a reboot just in the headset, but then I plug it off no sound)

I tried so many things....
I think the best think is we erase the hole alsa/sound settings but I need introductions ;)
Can please someone do it with me step by step, finally we all have the same NB.

Thx
root@m-d-l:/home/stephan# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
root@m-d-l:/home/stephan# lspci -n | grep 00:1b.0
00:1b.0 0403: 8086:284b (rev 02)

---

### Post by okilinux on 2007-10-31
I just put together a post for anyone using a Dell 1721.

[http://ubuntuforums.org/showthread.php?t=598314](http://ubuntuforums.org/showthread.php?t=598314)

---

### Post by mac-duff on 2007-10-31
Ok, I got it to work.
What I did, well I used the old files from 7.04:
alsa-firmware-loaders_1.0.13-1_i386
alsa-source_1.0.13-3ubuntu1_all

What I ask me is now, what will happen if I run the update wizard... and how can I deactivate these two updates?

---

### Post by kirkquitar on 2007-11-01
I found the following fix the only one that would work on a 1720:
```
sudo apt-get install linux-backports-modules-generic
```

It's probably better to try this first rather than the installing of various alsa libraries/modules.

If this has worked for others, maybe the OP should re-order the audio-fix steps to reflect this...

Note - if you have used Envy to update graphics drivers, you may have to run it again after the fix mentioned in this post.

---

### Post by ctpaterson on 2007-11-02
> **kirkquitar said:**
> I found the following fix the only one that would work on a 1720:
```
sudo apt-get install linux-backports-modules-generic
```

It's probably better to try this first rather than the installing of various alsa libraries/modules.

If this has worked for others, maybe the OP should re-order the audio-fix steps to reflect this...

Agreed and done.  I tried the backports fix, and it worked fine.

---

### Post by ctpaterson on 2007-11-02
I've added a note to the top post alerting people to this issue: [https://launchpad.net/bug59695.html](https://launchpad.net/bug59695.html) which seems alarming to me, and does affect my Dell Inspiron 1520.

I don't have a recommended solution, yet, but I'll post when I have one.  The bug thread has a few recommendations, including disabling the power saving feature, but I'm hoping for a solution that attempts to manage the power issue...just better.  My battery seems to have settled on 3 hours of life under regular use, so I'll measure any power savings change based on that.  I'm ignoring the issue of whose fault it is; I don't see anything I can change in the BIOS anyway.

In brief (for those who won't read the link), I ran the command "sudo smartctl -d ata -a /dev/sda", and in the Load_Cycle_Count record, found that my hard drive has cycled over 50,000 times (the last column).  My machine is about a month old.  Some monitoring scripts show that it's cycling the hard drive 4-8 times a minute while sitting idle, with the AC plugged in.

Comments, insight, and recommendations very welcome.

Cheers.

---

### Post by jebbiss on 2007-11-02
My Load Cycle Count was climbing at a very high rate on my Dell Vostro 1500, (same as Inspiron 1520)  I followed the instructions here:  [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26).  

Now it is climbing at a very low rate.  My battery is still lasting 3 hours or so.

---

### Post by Tensho on 2007-11-05
Hi. I'm a relative newcomer to Linux. I love the look of Gutsy and pretty much everything worked out of the box although I did need a proprietary driver for the wireless but it works just fine. Sound was an issue at first, but I was able to get it working with one of the fixes previously described. However, the modem... yikes. I'm one of those unfortunate individuals chugging away on dial-up, currently my modem is essential for me when I'm at home.

The laptop is the Inspiron 1520 of course.

Now I was aware that Dell released drivers for the modems shipped with the 1520's and other versions, however these seem restricted to 7.04, the old kernel - tried them and nothing works. I also had a look at linuxant's drivers they sell for a small fee of $20 (they really need to get with the FSF IMO) and they support 7.04, but not 7.10 as far as I know. Can anyone tell me where I can find drivers for the Conexant HDA D330 MDC V.92 modem... or at least if they even exist? Or will exist in the future? I hope Dell can churn out one pretty soon - I do understand Gutsy is still less than a month old, but c'mon! I need Internets! Also, why the heck is there no "connect/dial/whatever" option for network connections on the network manager? (particularly the modem) I want to at least know my lappie is making an attempt to connect!

Another little problem I have is getting Compiz to work. I'm not even able to run the graphical features on the 'normal' setting. I have the 965 chipset with the latest X3100 Intel gfx with around 350 mb or so allocated to it. It can run Vista Aero with no problems, so I would assume it's definitely able to handle Compiz! Are there any known issues with my current chipset and graphics?

I'm posting this from Vista right now, where my paging file is using up half of 2 GB. I'd rather not be on here longer than I have to. :P

Hoping someone can help!

---

### Post by Ali_ix on 2007-11-05
> **Tensho said:**
> Hi. I'm a relative newcomer to Linux. I love the look of Gutsy and pretty much everything worked out of the box although I did need a proprietary driver for the wireless but it works just fine. Sound was an issue at first, but I was able to get it working with one of the fixes previously described. However, the modem... yikes. I'm one of those unfortunate individuals chugging away on dial-up, currently my modem is essential for me when I'm at home.

The laptop is the Inspiron 1520 of course.

Now I was aware that Dell released drivers for the modems shipped with the 1520's and other versions, however these seem restricted to 7.04, the old kernel - tried them and nothing works. I also had a look at linuxant's drivers they sell for a small fee of $20 (they really need to get with the FSF IMO) and they support 7.04, but not 7.10 as far as I know. Can anyone tell me where I can find drivers for the Conexant HDA D330 MDC V.92 modem... or at least if they even exist? Or will exist in the future? I hope Dell can churn out one pretty soon - I do understand Gutsy is still less than a month old, but c'mon! I need Internets! Also, why the heck is there no "connect/dial/whatever" option for network connections on the network manager? (particularly the modem) I want to at least know my lappie is making an attempt to connect!

Another little problem I have is getting Compiz to work. I'm not even able to run the graphical features on the 'normal' setting. I have the 965 chipset with the latest X3100 Intel gfx with around 350 mb or so allocated to it. It can run Vista Aero with no problems, so I would assume it's definitely able to handle Compiz! Are there any known issues with my current chipset and graphics?

I'm posting this from Vista right now, where my paging file is using up half of 2 GB. I'd rather not be on here longer than I have to. :P

Hoping someone can help!
No idea about modem driver, i am waiting for it too!
I have used GPRS (with my motorola mobile hone) as an alternate to dialup connection.

For the second problem (compiz on intel965) check this: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)
But be aware that you have NO video playback while running compiz.

---

### Post by mac-duff on 2007-11-13
Does someone know how to get the webcam in skype2.0 to work?

---

### Post by ctpaterson on 2007-11-13
> **mac-duff said:**
> Does someone know how to get the webcam in skype2.0 to work?

Hey mac-duff,

I didn't even know Skype was testing a version with Linux video.  This is great news.

I don't have anything I can confirm yet, except that your post prompted me to finally test the video through the one means I did know (using Ekiga with V4L2).  The video did work without any extra steps required.

Also, I noticed a Skype web cam Ubuntu wiki page, that says the 1520 camera should work okay; [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

With this knowledge in hand, I'm hoping to try it out myself some time soon - so I'll let you know if I manage to obtain any success.  Good luck in the mean time, and let us know if you make any progress.

Cheers.

---

### Post by ctpaterson on 2007-11-13
> **mac-duff said:**
> Does someone know how to get the webcam in skype2.0 to work?

Just installed Skype 2.0 beta and tried it with my Inspiron 1520; worked like a charm.

In the Skype menu -> Options -> Video Devices...
- Check "Enable Skype Video"
- Click on "Test"

Video of me appears in the little box.  Check "Start my video automatically when I am in a call" if that's what you want.

Thanks very much for bringing this to my attention; I hope that's helpful in getting it to work for you.  Good luck.

---

### Post by mac-duff on 2007-11-14
ah ok, sorry.
restart fixed the problem

---

### Post by Surgeon General on 2007-11-14
previously, i18k was used to monitor the temperatures and control the fans for laptops. is there any change for gutsy or how are we supposed to monitor the temperature and control the fans?

---

### Post by Moonrider on 2007-11-15
I'm running ubuntu studio 64bit (Gutsy) on an Inspiron 1721

Alternative 2 is the only thing that got my sound up and running.

Now off to figure out why the boot takes so long

---

### Post by ctpaterson on 2007-11-15
I've just installed a modified fix for the hard drive cycling issue, modeled after the aforementioned fix at [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

I'll spell out what I did, but guys, no kidding, don't blindly copy and paste this to your machine unless you regularly allow complete strangers to sit down at your keyboard and change the way your hardware behaves.  Read the bug report, read the fix, get familiar with what's going on here, because (like I said), I've just installed it.  It may not even work.

I'll report more as I learn it...

$ vi /etc/hdparm.conf
```
/dev/sda {
	apm = 254
	spindown_time = 0
}
```
$ sudo update-rc.d hdparm defaults

$ sudo vi /etc/99-hdd-nospin-fix.sh
```
#!/bin/sh
hdparm -B 254 /dev/sda
hdparm -S 0 /dev/sda
```
$ sudo install /etc/99-hdd-nospin-fix.sh  /etc/acpi/suspend.d/
$ sudo install /etc/99-hdd-nospin-fix.sh  /etc/acpi/resume.d/
$ sudo install /etc/99-hdd-nospin-fix.sh  /etc/acpi/start.d/
$ sudo install /etc/99-hdd-nospin-fix.sh  /etc/acpi/ac.d/

$ sudo vi /etc/99-hdd-spin-fix.sh
```
#!/bin/sh
hdparm -B 128 /dev/sda
hdparm -S 0 /dev/sda
```
$ sudo install /etc/99-hdd-spin-fix.sh /etc/acpi/battery.d/

Good luck.

---

### Post by Surgeon General on 2007-11-18
so basically from what i understood, to test if you are affected your laptop's Load_Cycle_Count increments rapidly within 5 minutes or less.

i did "sudo smartctl -a /dev/sda | grep Load_Cycle_Count", checked every 2 minutes and my load count didn't increased even after more than 10 minutes. so i think my laptop is not affected.

dell 1520  with ubuntu 7.10

---

### Post by ctpaterson on 2007-11-18
> **Surgeon General said:**
> so basically from what i understood, to test if you are affected your laptop's Load_Cycle_Count increments rapidly within 5 minutes or less.

i did "sudo smartctl -a /dev/sda | grep Load_Cycle_Count", checked every 2 minutes and my load count didn't increased even after more than 10 minutes. so i think my laptop is not affected.

dell 1520  with ubuntu 7.10

I've found it increases more rapidly when the laptop is idle (that's when the aggressive power management will kick in).  So I recommend you check after a few minutes of inactivity.  If you find it increasing by a rate of...say...3 per minute or more, I'd be concerned.

Cheers.

---

### Post by ctpaterson on 2007-11-18
For whatever it's worth; the fix I cribbed and posted for the hard drive cycling issue seems to be coping okay on my machine.  I no longer see an alarming increase in the hard drive cycles, I've discharged/recharged the battery a few times with my normal usage pattern, and it still seems to be holding at three hours of run-time when fully charged.

(Especially irritating, since the thrashing of 10% of my hard drive's life didn't even seem to result in any realized power savings).)

So, a success on my end.  I'll update the top-level post with this fix, along with copious caveats and cautions.

Cheers.

---

### Post by Gunner_Sr on 2007-11-19
The alsa sound section works well for Dell Inspiron 1520 laptops/

:-)

---

### Post by alfredska on 2007-11-19
> **ctpaterson said:**
> I've just installed a modified fix for the hard drive cycling issue, modeled after the aforementioned fix at [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

[EDIT] :-: I removed my own post, as subsequent testing has shown that I need not apply this patch, my hard drive is not affected :-: [/EDIT]

Thanks for compiling a useful thread.

Matt
Inspiron 1520
Vista Home Premium + Ubuntu 7.10 x86-64

---

### Post by ubuntu_demon on 2007-11-21
The support thread for the Load_Cycle_Count issue is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

Please read the first post of this support thread :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

---

### Post by ctpaterson on 2007-11-27
Just a couple of updates:

I'll update the main post to refer to ubuntu_demon's thread on the hard drive load cycle; as there seems to be some discussion on the issue that people might find interesting.

Also, alexander.forster sent me a message with some advice that helped me get the internal mic working; I've tested with Audacity and a Skype call, and it sounds good - so I'll add that to the top post as well.

Cheers.

---

### Post by Lorac1949 on 2007-11-27
I have an Inspiron 1520 and went through the audio issue, too.  The next issue I solved was with OpenOffice.  It crashed every time I clicked on "Format."  It didn't matter if the document was imported or created within OO.  A reply at the OO forum solved the problem.  All I had to do was leave the Crux skin behind and don a Human skin.  Go figure.

Unfortunately, what now seems related to the skin change is the inability to read my external drive.  Before the skin change, I moved and added files to the external drive with no problem.  Now I get the message that I cannot view the contents.  Has anyone had this problem?  External drive is a 320GB Seagate FreeAgent.

---

### Post by alfredska on 2007-11-28
Note that this guide has been tested and is working for Ubuntu 7.10, 8.04, 8.10, 9.04.

I was having a difficult time finding a guide on dual booting Vista/Ubuntu while keeping MediaDirect functional (ie. no worries of a self-destruct button).  Thus, after I figured it out I thought I'd share a howto.

Guide 1: If you want to keep your current Vista installation as well as hold onto the recovery partition
Guide 2: If you want to delete the recovery partition (and reclaim ~5GB) and start from scratch with fresh OS installations

Note: I suggest using Vista's built-in partition editor since it is designed to work with the new NTFS file system that Vista uses.  Feel free to use another partition editor if you're sure it supports Vista's NTFS filesystem.

**Guide 1**
[LIST=1]
[*]In Vista, open Media Direct and use its built in update function to download the latest patch
[*]Shut down and hit the MediaDirect button, after it starts up, choose Update (it looks at the Vista partition and pulls the update from there)
[*]Use Vista's built in partition editor to resize the Vista partition
[*]Do a couple of shutdowns to make sure Vista and MediaDirect are working as expected.
[*]Boot from Ubuntu Disc
[*]Choose manual partitioning.  Create a set of partitions as you desire in the empty space freed up by Vista (I chose bulk of space to be "/" and the left-over 4GB to be SWAP). Select "Do not use" as the type for the Dell Recovery partition, the Dell Utility partition and the MediaDirect partition [Dell utility partition is usually at the start of the drive (~50MB), Dell recovery partition is usually 2nd to last on the drive (~5GB) and MediaDirect is at the end of the drive (~2GB)]
[*]When you arrive at the summary screen, take note of the partition number being formatted for "/". Choose advanced, and edit GRUB install location:
[LIST]
[*]If you're installing Ubuntu 7.10 or earlier: set GRUB installation location to (hd0,#) where # is one integer less than the partition number you read from the summary screen (grub counts the first partition as partition 0). This installs GRUB to the partition rather than MBR. Example: in my case, Ubuntu was being installed to partition #6, so I told GRUB to install to (hd0,5)
[*]If you're installing Ubuntu 8.04 or later: from the drop down list, select the partition being formatted as "/".
[/LIST] 
[*]Reboot computer, and let it start Vista
[*]Download and install [EasyBCD]("http://neosmart.net/dl.php?id=1")
[*]In EasyBCD, under "Add/Remove Entries", add a new Linux entry of type Grub, where the drive selection is obviously where Ubuntu resides.
[*]Restart and see Vista's boot screen. Select Ubuntu and see GRUB. You can delete the unneeded Vista/MediaDirect entries from GRUB's menu.lst
[/LIST]
**End of Guide 1**

**Guide 2**
**NOTE** This will remove your recovery partition!!! **NOTE**

CDs required before beginning:
Media Direct Restore Disc, Vista, Ubuntu (7.10 64bit requires use of "Alternative Install CD", versions 8.04 onwards can use the standard install disc)

I am assuming use of Media Direct 3.3

**NOTE** This will remove your recovery partition!!! **NOTE**

[LIST=2]
[*]Download all of the latest drivers and applications for your 1520.  (Note for Windows users: consider using [nVidia's own notebook driver]("http://www.nvidia.com/object/notebook_drivers.html") as the graphics driver provided by Dell is very out of date)
[*]Boot from MediaDirect CD, specify to create two partitions (leave ~15GB or more for Ubuntu)
[*]Boot from Vista Restore DVD, install to the first partition and LEAVE the other partition ALONE, do not delete, format, or otherwise alter it.
[*]In Vista, first install "Dell Notebook System Software" (this is actually a set of fixes for compatibility issues with the Inspiron 1520 and Vista), then any Vista service pack and updates, followed by all drivers.
[*]In Vista, reinsert MediaDirect CD and install
[*]While still in Vista, start MediaDirect and use its update function to download and install the latest patch
[*]Shut down and hit the MediaDirect button, after it starts up, choose Update (it looks at the Vista partition and pulls the update from there)
[*]Do a couple of shutdowns to make sure Vista and MediaDirect are working as expected.
[*]Boot from Ubuntu Disc
[*]Choose manual partitioning.  Create a set of partitions as you desire in the empty space freed up by Vista (I chose bulk of space to be "/" and the left-over 4GB to be SWAP). Select "Do not use" as the type for the Dell Utility partition and the MediaDirect partition [Dell utility partition is usually at the start of the drive (~50MB), MediaDirect is at the end of the drive (~2GB)]
[*]When you arrive at the summary screen, take note of the partition number being formatted for "/". Choose advanced, and edit GRUB install location:
[LIST]
[*]If you're installing Ubuntu 7.10 or earlier: set GRUB installation location to (hd0,#) where # is one integer less than the partition number you read from the summary screen (grub counts the first partition as partition 0). This installs GRUB to the partition rather than MBR. Example: in my case, Ubuntu was being installed to partition #6, so I told GRUB to install to (hd0,5)
[*]If you're installing Ubuntu 8.04 or later: from the drop down list, select the partition being formatted as "/".
[/LIST] 
[*]Reboot computer, and let it start Vista
[*]Download and install [EasyBCD]("http://neosmart.net/dl.php?id=1")
[*]In EasyBCD, under "Add/Remove Entries", add a new Linux entry of type Grub, where the drive selection is obviously where Ubuntu resides.
[*]Restart and see Vista's boot screen. Select Ubuntu and see GRUB. You can delete the unneeded Vista/MediaDirect entries from GRUB's menu.lst
[/LIST]
**End of Guide 2**

You now have the ability boot Vista and Ubuntu normally via boot screen or MediaDirect via its button.

On a completely separate issue, if you notice a considerable amount of hiss/pop/beep/etc coming from your headphone jack, there is a hardware fix that worked for me [here]("http://pctipguys.com/index.php?option=com_content&task=view&id=56&Itemid=36").

---

### Post by ctt1wbw on 2007-11-29
I installed Gutsy on my new Inspiron 1520 yesterday.  Vista didn't even get booted, I hit F12 to boot directly from cdrom.  I wiped out the whole Vista install and installed Gutsy.

Everything worked right off the bat except the new Intel High Def Audio.

I used the alternative #1 install method and got it working.

So far this thing kicks ****.

---

### Post by twbutler on 2007-12-15
> **alfredska said:**
> Perhaps this is repeated elsewhere, but I was having a hard time finding a definitive guide on dual booting Vista/Ubuntu while keeping MediaDirect intact and functional (aka no worries of a self-destruct button).

Here is my mini how-to:
**NOTE** This will remove your recovery partition!!! **NOTE**

CDs required before beginning:
Media Direct Restore Disc, Vista, Ubuntu (I used 64bit alternate install disc)

Download all of the drivers and applications from Dell's service/support webpage.  While I'm not usually a proponent of using drivers provided by computer manufacturer, these really have provided me with the most stable experience.

I am assuming use of Media Direct 3.3

**NOTE** This will remove your recovery partition!!! **NOTE**

1) Boot from media direct CD, specify to create two partitions (leave >10GB for Ubuntu)
2) Boot from Vista Restore disc, install to first partition and LEAVE the other partition ALONE, do not delete, format, or otherwise alter it.
3) Install Dell drivers, as well as Dell Utilities Application (this is actually a set of fixes for compatibility issues with the Inspiron 1520 and Vista)
4) Install MediaDirect from inside Vista
5) While in Vista, start MediaDirect and use its update function to download and install the latest patch
6) Shut down and hit MediaDirect button, after it starts up, choose Update (it looks at the Vista partition and pulls update from there)
7) Do a couple of shutdowns to make sure Vista and MediaDirect are working as expected.
8) Boot from Ubuntu Disc
9) Choose manual partitioning.  Delete the blank partition created by media direct and create a set of partitions as you desire (I chose bulk of space to be "/" and the left-over 2GB to be SWAP).  Select "Do not use" as the type for the Dell Utility partition at the start of the drive (~30MB) and MediaDirect partition at the end of the drive (~2GB).
10) When you arrive at the summary screen, take note of the partition number being formatted for "/".  Choose advanced, and edit GRUB install location to (hd0,#) where # is one integer less than the partition number you read from the summary screen (grub counts the first partition as partition 0).  This installs GRUB to the partition rather than MBR.  (Example: in my case, Ubuntu was being installed to partition #6, so I told GRUB to install to (hd0,5))
11) Reboot computer, and let it start Vista
12) Download and install EasyBSD
13) Add Ubuntu to the list of operating systems
14) Restart and see Vista's boot screen.  Select Ubuntu and see GRUB.  You can delete the unneeded Vista/MediaDirect entries from GRUB's menu.lst.

I am happy to have a working MediaDirect button.  Everything works as I would hope... now if I could just get rid of that hiss/pop/crack/whistle/beep/static that comes from the headphones port (in both Vista and Linux).

alfredska, thanks for posting this guide.  It looks very nice and seems to follow many points others have made elsewhere. I am looking to do the same thing, ie. install linux but keep Vista and MediaDirect.  Like you said, I have seen little mention of this kind of setup. 

I have a few questions.  
[LIST=1]
[*]What is the starting point for this guide?  You don't say it, but it seems implied that you have wiped the factory install clean and are starting from scratch with an empty hard drive. 
[*]I have read of others who have resized existing partitions and made room for Linux in this manner.  But others have warned that you cannot move (or resize) Vista OS partitions without screwing something up.  Is this why you are starting from scratch?  I'd like to avoid reinstalling Vista if I can help it.
[*]You do not mention creating the Dell Utility partition at the start of the drive, but then you say to mark it as "Do Not Use".  Does the VISTA install CD create this for you?  See, again, maybe you did not start with a clean HD - I am a little confused... :confused:
[/LIST]

Thanks - I look forward to your response. 
:)

---

### Post by alfredska on 2007-12-15
Hi twbutler,

> **twbutler said:**
> What is the starting point for this guide? You don't say it, but it seems implied that you have wiped the factory install clean and are starting from scratch with an empty hard drive.When you boot from the MediaDirect CD, it is going to delete the partition table on your laptop's hard drive.  Thus anything you may have on there, including Dell's recovery partition will be removed.  In this sense, we are starting from a "factory fresh install".
> **twbutler said:**
> I have read of others who have resized existing partitions and made room for Linux in this manner. But others have warned that you cannot move (or resize) Vista OS partitions without screwing something up. Is this why you are starting from scratch? I'd like to avoid reinstalling Vista if I can help it.In my case I was forced to use this method because MediaDirect became corrupted by the simple act of resizing the Vista partition using Vista's built-in disk management software.

NOTE: There is an option worth trying in which I was simply too late to try myself:

1) Install the update for MediaDirect through Vista.  Shut down and boot MediaDirect, then tell it to update (it'll reference the update you applied in Vista).

2) After you've verified that Vista and MediaDirect are behaving correctly, use Vista's built-in disk management to shrink vista.  Then reboot vista to make sure it went alright.  The try shutting down and booting MediaDirect.  If it worked, you're good to go on installing Ubuntu to the free space. (MAKING SURE TO INSTALL GRUB TO THE FIRST SECTOR OF THE UBUNTU PARTITION AND NOT THE MBR)  If it didn't work, you'll have to follow my guide from the beginning.
> **twbutler said:**
> You do not mention creating the Dell Utility partition at the start of the drive, but then you say to mark it as "Do Not Use". Does the VISTA install CD create this for you? See, again, maybe you did not start with a clean HD - I am a little confused...The MediaDirect boot CD creates the Dell Utility parition (without every asking your permission).  It is not a recovery partition, but rather a set of tools.

---

### Post by twbutler on 2007-12-15
Thanks, alfredska...

That clarifies things a bit.  I am going to attempt your "option worth trying", and will let you know how it goes.  Thanks...

---

### Post by starkawa on 2007-12-16
> **alfredska said:**
> 
In my case I was forced to use this method because MediaDirect became corrupted by the simple act of resizing the Vista partition using Vista's built-in disk management software.

NOTE: There is an option worth trying in which I was simply too late to try myself:

1) Install the update for MediaDirect through Vista.  Shut down and boot MediaDirect, then tell it to update (it'll reference the update you applied in Vista).

2) After you've verified that Vista and MediaDirect are behaving correctly, use Vista's built-in disk management to shrink vista.  Then reboot vista to make sure it went alright.  The try shutting down and booting MediaDirect.  If it worked, you're good to go on installing Ubuntu to the free space.


Hi I am trying to install ubuntu on my Insprion 1420. I used Vista shrink on C drive and freed up 40GB of free space. I have two questions:

1. My MediaDirect still works fine; I assume by shrinking or expanding back C drive along is not going to harm Media Direct?

2. I'm interested in understanding a bit more on your theory of the untried option; does it imply if it succeeds Ubuntu is going to be installed on the same extended partition as MediaDirect and I may create multiple logical partions to host other needs with use of Ubuntu?

Thank you~!!

---

### Post by alfredska on 2007-12-16
> 1. My MediaDirect still works fine; I assume by shrinking or expanding back C drive along is not going to harm Media Direct?If MediaDirect is still working for you after shrinking Vista, that's terrific.  Some users (including myself) experience a non-functional MediaDirect button by doing this, though I wonder if perhaps all of us had done a bit more... I wont go into detail.

> I'm interested in understanding a bit more on your theory of the untried option; does it imply if it succeeds Ubuntu is going to be installed on the same extended partition as MediaDirect and I may create multiple logical partions to host other needs with use of Ubuntu?Indeed, it is my theory that you need to install Ubuntu alongside MediaDirect in the extended partition where it resides.  I am only one user though, with minimal test scenarios and time.  I have been reporting what should work given my experiences.  Here is a screenshot of GParted, so that you can see my hard drive layout.  I obviously followed my own guide.

[IMG]http://bengal.missouri.edu/mdmnq5/comp/gparted.png[/IMG]

---

### Post by xshadow on 2007-12-18
Hi All!

I just want to announce that I was able to install 7.10 on my Dell Inspiron 1520 using this howto, Thank you very much. :cool:
For sound card: I used the **preferred way**.
To make internal mic work I used setting 8. (digital mic)
My Logitech Quickcam Pro5000 also works with luvc dirvers and latest skype beta. (2.0.0.27 or something)

Cheers,
[x]

---

### Post by twbutler on 2007-12-25
Hello again...  After getting delayed, I finally got back to trying the suggestions made here by alfredska. In short, his guide worked great for me too. His "option worth trying" allowed me to keep the factory Vista install, shrink the Vista OS partition to make room for Ubuntu, and then install Ubuntu while keeping Vista and MediaDirect working as before.
:)

Here are a few things I ran into that others might also:
[LIST]
[*]When shrinking the Vista partition to make room for Ubuntu, I found that the Vista Disk Manager would not allow me to shrink it more than 30 GB or so.  I think the paging files, hibernation data, system dumps, etc. are immovable, even if you use the disk defragment utility. Well, for now, 30 GB should be OK for Ubuntu... 
[*]The boot tool to use is **EasyBCD,** not EasyBSD - big difference there. 
[/LIST]

Thanks again, alfredska!  Now I am off to getting all the hardware working, etc.

---

### Post by juanpedrovale on 2007-12-25
Hi, i used the backports method in a 1521 and it worked perfectly.
The hardware is:

AMD Athlon 64 X2
1GB RAM
Sigmatel HD audio (Dell said it was an audigy but its just a software for windows, the ship isn`t Creative) 


Thanks a lot, i'm trying to leave definitevely windows but a had this problem with the sound, THANKS, THANKS, THANKS

---

### Post by alfredska on 2007-12-25
Thanks twbulter, I've updated my [post]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81").  I must have had the blue screen of death on my mind the first time I was typing things up.

---

### Post by twbutler on 2007-12-26
One final follow-up on this.  I found a comment on a blog post about using the Vista Disk Manager to shrink the OS partition, and it mentions ways to get around the page files, hibernate data, etc.  I followed these tips and was able to get about 6 GB more shrinkage from my Vista OS partition. Not a lot, but others seem to get better results than I did...  standard disclaimers apply.

NOTE: This tips are credited to Prashant Kalkar

> 11. RE: Repartition your hard disk on-the-fly with Windows Vista 

kalkar.prashant@... - 07/28/07

I was able to increase the size space to shrink. All we need to do is disable the pagefiles, hibernate option (clean the hibernate file with the disk cleanup before disabling the hibernate option), disable the core dump file creation containing debugging information, and remove the auto-restore points for the drive. 


The page file can be disabled from Computer > Properties > Advance Options > Advance > Performance Settings > Advance > Click change button > Set No page file and click set button. This will disable the pagefiles. 


To clean the hibernate file run the disk cleanup for that drive and select the hibernate file. Then disable the hibernate option by opening the command prompt in admin mode and running powercfg -h off command. 


To disable the core dump file creation, go to computer > properties > 
advance options > Advance tab > Setup and recovery section click settings, in Write debug information select none instead of Kernel dump file. 


To disable the auto-restore option go to the computer > properties > advanced > System protection tab > Deselect the drive in the automatic restore point section. 


Restart PC and now try to shrink the drive. I hope this information helps. 

Prashant 

One thing I'll add:  once you are finished shrinking the partition, you should consider going back to undo and restore the settings Prashant mentions.

---

### Post by apanda02 on 2007-12-27
Did anyone have problem with 64 bit live CD? Screen went blank for me when I used it. Seems to work fine with the 34 bit.

Also,does anyone no how to play AVI files in media direct? 

Panda

---

### Post by z_magyarics on 2007-12-28
Hi All,

   I've recently installed Kubuntu 7.10 i86 on my new Dell Inspiron 1520. The specs of this machine: Intel Core 2 Duo T7100 2000 MHz, 2x1 GB RAM, nVidia 8400 GS video, 120 GB hard drive, Dell Wireless card, 2Mp integrated webcam.

  Remaining main problem: after closing the lid, or executing "suspend" from KDE logout menu, the screen doesn't come back, and I have to reboot the system. 
  It seems to be related to X in other forum posts, but nobody gave a solution for this issue. Can anybody confirm this with nVidia driver (my version: 169.07), or having any solution? Just an idea, it may be related to the nVidia driver version - can anybody confirm this with other recent or older nVidia drivers?

  An installation remark: I can confirm that  the x64 version of Kubuntu and even Ubuntu did not boot.

   What's working, out of the box: clock speed management, webcam using uvcvideo module, built-in and plug-in microphone, wireless using bcm43xx module.
  Features working after some tricks: nVidia graphic card, using proprietary driver,  sound using the aforementioned simple "sudo apt-get install linux-backports-modules-generic" method. 
  
    Altogether, this laptop seems to be "Ubuntu-ready" in most aspects, and needs little and easy tweaking to get basic features working.

Zoltan

---

### Post by Denialdeath on 2007-12-28
I have the same setup and I have gotten everything to work so far, with exception of the mic (which I haven't tested) and the webcam. 
I tried the webcam in GYachE Improved v. 1.1.0
I get the following errors:

Error while querying mmap-buffers.

An error occurred at 'ioctl VIDIOCSPICT'. Could not set camera properties.

I checked the setup for GYachE and the webcam is enabled and the device is listed as "/dev/video0"

Is this a problem with GYachE or ist the device not setup correct?

---

### Post by adycopilu on 2007-12-29
I have a Dell Inspiron 1720. I managed to install the 64-bit version, but using the alternate install cd, as I had problems booting from the Live CD (only with this 64-bit version). My screen was turning black too during boot, but I read somewhere over the forum that there are some problems with the 64-bit Live CD on Intel processors and the suggestion was to install Ubuntu from the alternate install cd ;)

I solved the sound issue using the first option, the preferred one (thank you for the solution). And my mic is working fine (the one plugged-in on the right panel). Everything was working great, but I still got the boot problem: slow and blank screen during start-up. So I found this post from orange2k (thanks, btw):

> I found a solution that worked for me on kubuntuforums:

(before I did what follows, I used StartupManager to set the boot-splash resolution to 1024x768 16-bit)

edit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

blacklist vesafb
blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

No more blank screen dooring boot for me :D

---

### Post by apanda02 on 2007-12-31
Does anyone know how to get Ubuntu/XP AND media direct to work. Grub seems to be creating problems for Media Direct. 

Isn't there any ways to just edit the windows boot.ini file to add Ubuntu as a operating system??(Just like BCD does)

Panda

---

### Post by ctpaterson on 2008-01-01
> **z_magyarics said:**
> Remaining main problem: after closing the lid, or executing "suspend" from KDE logout menu, the screen doesn't come back, and I have to reboot the system. 
  It seems to be related to X in other forum posts, but nobody gave a solution for this issue. Can anybody confirm this with nVidia driver (my version: 169.07), or having any solution? Just an idea, it may be related to the nVidia driver version - can anybody confirm this with other recent or older nVidia drivers?

With an GeForce 8600M GT and the latest restricted nvidia drivers, I get unpredictable results from a suspend (sometimes it works, sometimes it doesn't).  Lid closing and reopening has never been a problem (though I have to unlock the screen).

Cheers.

---

### Post by alfredska on 2008-01-01
Post removed as it contained untrue information.

---

### Post by apanda02 on 2008-01-01
Yeah I guess I have...

I think I have found 2 sources that contain the solution. If only someone could help me understand them I would REALLY appreciate it...

[http://ubuntuforums.org/showpost.php?p=3113451&postcount=8](http://ubuntuforums.org/showpost.php?p=3113451&postcount=8)
[http://linux6400.wordpress.com/2007/04/06/installing-ubuntu-edgy-eft-610/](http://linux6400.wordpress.com/2007/04/06/installing-ubuntu-edgy-eft-610/)

Thanks,

Panda

---

### Post by apanda02 on 2008-01-01
I have Dell's Mini N Wireless card. How do I get that to work?

Thanks,

Panda

NEVERMIND: I found the solution!

---

### Post by b4d on 2008-01-01
Hi, is there any known reason, why the video from integrated webcam is lagging?

---

### Post by meateater on 2008-01-02
Be careful with media direct though. I read horror stories about it destroying the ubuntu partition.

---

### Post by apanda02 on 2008-01-02
Haha yeah well in the last 2 Days I reformatted my Laptop HDD 5 times in an effort to get Media Direct to work!

Still no sucess...

Panda

---

### Post by z_magyarics on 2008-01-02
> **ctpaterson said:**
> With an GeForce 8600M GT and the latest restricted nvidia drivers, I get unpredictable results from a suspend (sometimes it works, sometimes it doesn't).  Lid closing and reopening has never been a problem (though I have to unlock the screen).

That sounds promising, as my ultimate aim is to solve the lid closing and reopening issue at least.
My card is a 8400GS, but I guess it makes no major difference. Which driver are you using? I haven't found linux drivers on the Nvidia support page after selecting GeForce 8M series, just a driver for normal GeForce series (the latest version is 169.07, that's what I1m using now).
So the solution seems to be the driver that is suitable for this mobile GeForce card?

Thanks for your comment!

---

### Post by alfredska on 2008-01-02
> **apanda02 said:**
> Haha yeah well in the last 2 Days I reformatted my Laptop HDD 5 times in an effort to get Media Direct to work!

Still no sucess...

Panda

apanda02, it seems WinXP can boot Ubuntu.  One of the links you mentioned leads you to the answer.

Start by following my guide [here]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81").

If using Guide 1, replace steps 9 & 10 with the following steps.
If using Guide 2, replace steps 13 & 14 with the following steps.

[LIST=1]
[*]Reboot, and boot from the Ubuntu LiveCD (or any other LiveCD).
[*]From termial:  ```
sudo dd if=/dev/sdaX of=/media/thumb/ubuntu.bin bs=512 count=1
```where X is replaced by the partition where Ubuntu is installed, and thumb is any external storage device mounted there
[*]After you have ubuntu.bin on a storage device, reboot and let Windows XP start up.
[*]Copy ubuntu.bin to C:\
[*]Edit boot.ini and add line: ```
C:\ubuntu.bin="Ubuntu"
```
[*]Restart and you should see the WinXP boot screen
[/LIST]

---

### Post by apanda02 on 2008-01-03
hmm..I did that previously and I got that method to work...BUT the media direct error was still there....Maybe installtion of GRUB into the Linux partition is causing the problem. Should I like repair the MBR to XP default and then do this? Can I get rid of Grub altogether then?



PS: Does anyone no how I can make a image of my WHOLE harddrive. I am SICK of reformatting.

---

### Post by apanda02 on 2008-01-03
Just a quick question. 

Why is it that when I enable the restricted nVidia driver the screen starts acting up. And I mean no borders....flashes....all that good stuff..

---

### Post by ctpaterson on 2008-01-03
> **z_magyarics said:**
> That sounds promising, as my ultimate aim is to solve the lid closing and reopening issue at least.
My card is a 8400GS, but I guess it makes no major difference. Which driver are you using? I haven't found linux drivers on the Nvidia support page after selecting GeForce 8M series, just a driver for normal GeForce series (the latest version is 169.07, that's what I1m using now).
So the solution seems to be the driver that is suitable for this mobile GeForce card?

Thanks for your comment!

No problem.

I just followed the steps I detailed in the OP.  I installed Gutsy, upon logging in, I was given the pop-up restricted drivers message, and I enabled them.  I tried browsing around the menus to get the name and version, but can't seem to find anything beyond "NVIDIA accelerated graphics driver (latest cards)" from the Restricted Drivers Manager.

---

### Post by trmentry on 2008-01-03
I'm running into an issue.  When I boot the LiveCD, it comes up in Safe Graphics Mode.  It sees my nVidia card, but doesn't use the nv driver.  No biggie.. I just click continue and move on.  

However it then just locks up at the boot scripts and sits there doing nothing.

Any pointers?

I have the 1520 with same hardware listed on first post in thread.

---

### Post by trmentry on 2008-01-03
Just re-read the post and saw that it was done with the 32bit version.  I was trying with 64bit  I'll give this another go later when I get back home from work.

---

### Post by meateater on 2008-01-03
I was able to get bluetooth to work out of the box without any special config.
It was able to pair with my k800i mobile phone.

Also the front media buttons, volume controls work.
I have tested the media buttons and they work with banshee. (play / pause, stop, next, prev buttons).

So you can do media functionality while the lid is closed (assuming the lid closed does not suspend / hibernate ).

I tested headphones also, and I did not get the buzzing sound problem that the others have reported. Maybe they fixed it with the new laptops.

For those with the 3945 wireless and is having trouble reconnecting or is getting disconnected frequently from wireless, try to do the blacklist fix
in this link [http://ubuntuforums.org/showthread.php?t=551325&highlight=blacklist](http://ubuntuforums.org/showthread.php?t=551325&highlight=blacklist)
I tried this out and wifi has become more stable for me.

---

### Post by z_magyarics on 2008-01-04
> **ctpaterson said:**
>  I tried browsing around the menus to get the name and version, but can't seem to find anything beyond "NVIDIA accelerated graphics driver (latest cards)" from the Restricted Drivers Manager.

Now the lid closure issue seems to be solved. I've removed nvidia driver version 100.14.19 (installed by synaptic) and installed manually the 169.07 version driver (32-bit) downloaded from the Nvidia site. Of course, restricted drivers are enabled. Now it comes back from suspend and after lid closure. Thanks again for comments!

Cheers!

---

### Post by alfredska on 2008-01-04
> **apanda02 said:**
> hmm..I did that previously and I got that method to work...BUT the media direct error was still there....Maybe installtion of GRUB into the Linux partition is causing the problem. Should I like repair the MBR to XP default and then do this? Can I get rid of Grub altogether then?Installing WinXP should overwrite the MBR.  Also, you can boot from the WinXP CD and use the recovery console to overwrite the MBR: ```
fixboot
fixmbr
```This overwrites anything in the MBR with the WinXP boot loader.

> **apanda02 said:**
> PS: Does anyone no how I can make a image of my WHOLE harddrive. I am SICK of reformatting.

Look into Symantec Ghost, or if you must, Norton Ghost.  There are freeware alternatives as well, but I haven't tried them.

---

### Post by apanda02 on 2008-01-05
Alright well I tried what you had suggested by reformatting my whole Ubuntu partition, where GRUB was installed. Even then the media direct problem persists.

I have a feeling installing GRUB even to the Linux partition messed with the MBR too. 

Alright I am gonna try reformatting one LAST time.

PS: the fixboot/fixmbr thing gives error.

Panda

---

### Post by alfredska on 2008-01-05
> **apanda02 said:**
> Alright well I tried what you had suggested by reformatting my whole Ubuntu partition, where GRUB was installed. Even then the media direct problem persists.

I have a feeling installing GRUB even to the Linux partition messed with the MBR too. 

Alright I am gonna try reformatting one LAST time.

PS: the fixboot/fixmbr thing gives error.

Panda

I never suggested reformatting just the Ubuntu partition.  That wont affect MediaDirect in the slightest.  You need to have a working MediaDirect BEFORE installing Ubuntu.  Simply formating or deleting the Ubuntu partition isn't going to magically make MediaDirect work.

If you received and error when using fixboot or fixmbr from the recovery console of the WinXP boot disc, then something is wrong.  Did it give you the option to select which windows installation to work with?  Did you choose the correct one?  There are technically two windows partitions, one for WindowsXP and one for MediaDirect.  You would want to select the regular WindowsXP installation.

---

### Post by apanda02 on 2008-01-05
> **alfredska said:**
> If you received and error when using fixboot or fixmbr from the recovery console of the WinXP boot disc, then something is wrong.  Did it give you the option to select which windows installation to work with?  Did you choose the correct one?  There are technically two windows partitions, one for WindowsXP and one for MediaDirect.  You would want to select the regular WindowsXP installation.

Ok because of the error I just decided the reformat the whole thing and get a clean start. I followed your guide by first ensuring that I had working XP and Media Direct.

But then as soon as I install Ubuntu in the other partition-even though I choose NOT to install GRUB, Media Direct no longer loads. It gives me BSOD while loading....

So I guess no Media Direct for me. 

Panda

---

### Post by monkeyBox on 2008-01-05
I just got a 1520 with a GeForce 8600M GT. Suspend and Hibernate both do not work.  When initiate a suspend,  My screen goes black but the computer does not suspend.  I cannot regain control of the computer unless I manually power down and reboot.  The same happens with hibernate.

It's pretty important to me that I get at least suspend to work.  It gets annoying to have to shut down completely every time I'm done using my laptop.  Does anyone know what can be done about this?

---

### Post by alfredska on 2008-01-05
> **apanda02 said:**
> Ok because of the error I just decided the reformat the whole thing and get a clean start. I followed your guide by first ensuring that I had working XP and Media Direct.

But then as soon as I install Ubuntu in the other partition-even though I choose NOT to install GRUB, Media Direct no longer loads. It gives me BSOD while loading....

So I guess no Media Direct for me. 

Panda

Are you resizing the empty partition before installing Ubuntu?  If so, what tool are you using?

Are you installing the updates to MediaDirect before installing Ubuntu?  What version of MediaDirect are you using (2.x, 3.x, other)?

Install GParted (or boot from a GParted livecd) and take a screenshot of how your drive is partitioned.  Post it here.

---

### Post by apanda02 on 2008-01-05
> **alfredska said:**
> Are you resizing the empty partition before installing Ubuntu?  If so, what tool are you using?

Are you installing the updates to MediaDirect before installing Ubuntu?

Yeah the huge chunk of space I have left over after XP installtion...I resized using Ubuntu's Manual partitioner...using that I created ext3..for ubuntu...swap space and FAT32 for documents. 

No I did not bother with the Media Direct updates before installing ubuntu....y does it matter?

I read somewhere that this might have something to do with enabling AHCI in the bios....but whenever I do that my XP crashes. Does anyone know how to instal AHCI drivers in XP?

---

### Post by apanda02 on 2008-01-05
> **alfredska said:**
> Install GParted (or boot from a GParted livecd) and take a screenshot of how your drive is partitioned.  Post it here.

I will get it to you. Gimme 10 mins.

Panda

---

### Post by alfredska on 2008-01-05
> **apanda02 said:**
> Yeah the huge chunk of space I have left over after XP installtion...I resized using Ubuntu's Manual partitioner...using that I created ext3..for ubuntu...swap space and FAT32 for documents.

When you resize the extended partition where MediaDirect resides (it holds logical partitions MediaDirect and whatever you create for Linux), that messes MediaDirect up.

> **apanda02 said:**
> No I did not bother with the Media Direct updates before installing ubuntu....y does it matter?

The updates may help MediaDirect cope with parition changes.

> **apanda02 said:**
> I read somewhere that this might have something to do with enabling AHCI in the bios....but whenever I do that my XP crashes. Does anyone know how to instal AHCI drivers in XP?

Here is the guide for installing WinXP on Inspiron 1520, it talks about AHCI: [NotebookReview Forums]("http://forum.notebookreview.com/showthread.php?t=165176")
Notice the second post by user "DoubleBack"

---

### Post by apanda02 on 2008-01-05
> **alfredska said:**
> When you resize the extended partition where MediaDirect resides (it holds logical partitions MediaDirect and whatever you create for Linux), that messes MediaDirect up.

I did not touch the MediaDirect partition. I resized the left over space after XP, utilities and MediaDirect installtion....

---

### Post by alfredska on 2008-01-05
> **trmentry said:**
> I'm running into an issue.  When I boot the LiveCD, it comes up in Safe Graphics Mode.  It sees my nVidia card, but doesn't use the nv driver.  No biggie.. I just click continue and move on.  

However it then just locks up at the boot scripts and sits there doing nothing.

Any pointers?

I have the 1520 with same hardware listed on first post in thread.

I have successfully installed Ubuntu 64bit using the alternate install CD.  There is not boot logo when starting up, but it does work.

---

### Post by alfredska on 2008-01-05
> **apanda02 said:**
> I did not touch the MediaDirect partition. I resized the left over space after XP, utilities and MediaDirect installtion....

An extended partition holds the empty parition and MediaDirect.  They are logical paritions within the extended partition.  When you resize Windows XP (presumably making it smaller to give more room for Ubuntu?), and subsequently enlarge the space for Ubuntu, you're enlarging the extended partition.  Since MediaDirect lives here, it gets messed up.

---

### Post by apanda02 on 2008-01-05
Hey, do you know how to load drivers during installation? I guess he means at the VERY begining? like when its starting up XP from CD?

Also, the code
sudo dd if=/dev/sdaX of=/media/thumb/ubuntu.bin bs=512 count=1

should be 
sudo dd if=/dev/sda4 of=/media/thumb/ubuntu.bin bs=512 count=1

for me right, or is it supposed to use GRUB's special numbering?

---

### Post by apanda02 on 2008-01-05
> **alfredska said:**
> An extended partition holds the empty parition and MediaDirect.  They are logical paritions within the extended partition.  When you resize Windows XP (presumably making it smaller to give more room for Ubuntu?), and subsequently enlarge the space for Ubuntu, you're enlarging the extended partition.  Since MediaDirect lives here, it gets messed up.

I never resized XP though...I mean the media direct CD initially created XP partition for me...and even later I am only breaking a pre-created partition into smaller and smaller piece...to make room for swap,documents and linux...how else can I even go about this?!

---

### Post by alfredska on 2008-01-05
> **apanda02 said:**
> Hey, do you know how to load drivers during installation? I guess he means at the VERY begining? like when its starting up XP from CD?

Press F6 right when you're booting from the WinXP CD (it has a little message at the bottom of the screen).  Though without a floppy drive, I'm not sure where WinXP will let you look for the drivers.  ( I haven't tried this obviously )

> **apanda02 said:**
> Also, the code
sudo dd if=/dev/sdaX of=/media/thumb/ubuntu.bin bs=512 count=1

should be 
sudo dd if=/dev/sda4 of=/media/thumb/ubuntu.bin bs=512 count=1

for me right, or is it supposed to use GRUB's special numbering?

That would be true if you installed GRUB to (hd0,3)

---

### Post by apanda02 on 2008-01-05
[http://paparadit.blogspot.com/2007/06/installing-sata-hard-drive-with-windows.html](http://paparadit.blogspot.com/2007/06/installing-sata-hard-drive-with-windows.html)

Untested way to install AHCI drivers to get XP/Ubuntu/Media Direct up and running...which according to this link 

[http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html](http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html)

is essential for media direct 3.

---

### Post by meborc on 2008-01-06
just here to say thanks for the sound-tip :) works great

haven't read the whole thread... if someone is having troubles with bcm94311mcg wireless, then check this guide - [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

btw - loving my new insp 1520 / 2G c2d / 2G ram / geforce 8600m GT 256

---

### Post by monkeyBox on 2008-01-06
> **meborc said:**
> just here to say thanks for the sound-tip :) works great

haven't read the whole thread... if someone is having troubles with bcm94311mcg wireless, then check this guide - [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

btw - loving my new insp 1520 / 2G c2d / 2G ram / geforce 8600m GT 256

mebroc:  looks like you have similar specs as I do.  Does suspend (closing the lid) work for you very well?  Sometimes it works for me,  but sometimes I open the lid back up and my screen doesn't come on and I have to hold down the power button to force-shutdown.

---

### Post by ctpaterson on 2008-01-06
> **monkeyBox said:**
> I just got a 1520 with a GeForce 8600M GT. Suspend and Hibernate both do not work.  When initiate a suspend,  My screen goes black but the computer does not suspend.  I cannot regain control of the computer unless I manually power down and reboot.  The same happens with hibernate.

It's pretty important to me that I get at least suspend to work.  It gets annoying to have to shut down completely every time I'm done using my laptop.  Does anyone know what can be done about this?

When I suspend, I see the same behaviour if I leave the lid up.  What I have found work some of the time, is to suspend and immediately close the laptop lid.  The computer takes a few moments, but does suspend.

The laptop should wake back up when the lid is reopened.  This doesn't seem to work well if I try and wake it up fairly quickly after suspending it (ie. if I'm sitting there and testing it), and often works if I've left the computer alone for a while.

Really, though, I consider it unreliable.

Cheers.

---

### Post by monkeyBox on 2008-01-06
I may have found a fix for the suspend issue I was experiencing.  See here:

[http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/](http://boulderjams.wordpress.com/2007/02/20/ubuntu-dell-suspend-fix/)

This article says that the culprit was network-manager,  so he added network-manager to the STOP_SERVICES variable in /etc/defaults/acpi-support.  

I've tried suspending a few times without any problems,  but I'll give it a day or so of more  testing before I call it an official fix.

---

### Post by apanda02 on 2008-01-07
Just wanted to post some results of my testing with Media Direct. 

I tried to set SATA operation to AHCI from BIOS....loaded the right drivers during installtion...but then I never got Audio or Modem drivers to work. So that was no good. 


I also tried to shrink XP partition....instead of editing a "empty partition" through g-parted live CD. Funny how media direct crashed right after I finished the partitioning...and it was working before...even though Linux was not installed...I can only conclude partitioning creates a problem for Media Direct. 

And Yes, the update was installed.

---

### Post by trmentry on 2008-01-07
I followed the instructions to keep Vista and Media Direct intact.  Things are working great.  Media Direct is still working, as is Vista and Ubuntu is happily the first choice in the boot loader.

However I've run into a slight issue that I'm stuck on and not sure how to proceed.

eth1 which is my Intel Wireless 3945ABG card.  My wireless connection will just all of a sudden drop.  Network Manager in the Notification Area will show that its lost connection and looks like it attempts to reconnect.  But it never does.  Then it appears my CPU goes through the roof and I can't shutdown gracefully.  

This is while plugged into AC power and have power options set to keep things on when on AC power.  Just to blank the screen after 1 hour of idle.  

The logs show this:

```

Jan  6 23:03:38 kessel -- MARK --
Jan  6 23:23:38 kessel -- MARK --
Jan  6 23:27:59 kessel kernel: [128685.908000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan  6 23:28:34 kessel kernel: [128720.444000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

Then my reboot right after that.


Any ideas?  I'm not trying to suspend or resume or hibernate.  This happens when just browsing and not doing naything out of the ordinary.

Thanks


Edit:  Found this link from another post on these forums after some better search foo.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

Going to give it a try.

---

### Post by alfredska on 2008-01-07
> **apanda02 said:**
> Just wanted to post some results of my testing with Media Direct. 

I tried to set SATA operation to AHCI from BIOS....loaded the right drivers during installtion...but then I never got Audio or Modem drivers to work. So that was no good. 


I also tried to shrink XP partition....instead of editing a "empty partition" through g-parted live CD. Funny how media direct crashed right after I finished the partitioning...and it was working before...even though Linux was not installed...I can only conclude partitioning creates a problem for Media Direct. 

And Yes, the update was installed.

I'm sorry to hear that you weren't able to shrink the XP partition and keep MediaDirect intact.  It seems Vista's built in partition manager is able to help MediaDirect cope with this better than other partitioning utilities.

If you can afford to keep Ubuntu on a small partition, you should be able to install Ubuntu in the empty partition.

Strange how you weren't able to install Audio or Modem drivers just because you slipstreamed the AHCI storage drivers.  I don't have an answer for that one.

Good luck in your endless quest.

---

### Post by alfredska on 2008-01-07
> **trmentry said:**
> I followed the instructions to keep Vista and Media Direct intact.  Things are working great.  Media Direct is still working, as is Vista and Ubuntu is happily the first choice in the boot loader.

However I've run into a slight issue that I'm stuck on and not sure how to proceed.

eth1 which is my Intel Wireless 3945ABG card.  My wireless connection will just all of a sudden drop.  Network Manager in the Notification Area will show that its lost connection and looks like it attempts to reconnect.  But it never does.  Then it appears my CPU goes through the roof and I can't shutdown gracefully.  

This is while plugged into AC power and have power options set to keep things on when on AC power.  Just to blank the screen after 1 hour of idle.  

The logs show this:

```

Jan  6 23:03:38 kessel -- MARK --
Jan  6 23:23:38 kessel -- MARK --
Jan  6 23:27:59 kessel kernel: [128685.908000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan  6 23:28:34 kessel kernel: [128720.444000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

Then my reboot right after that.


Any ideas?  I'm not trying to suspend or resume or hibernate.  This happens when just browsing and not doing naything out of the ordinary.

Thanks


Edit:  Found this link from another post on these forums after some better search foo.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

Going to give it a try.

User meateater posted about a [similar issue]("http://ubuntuforums.org/showpost.php?p=4067462&postcount=112") and mentioned the fix that worked for him/her.

---

### Post by carminez on 2008-01-07
I have an issue where the title bar on a window is displaying large fonts and large icons when I first boot and login, but if I do a CNTRL-ALT-BACKSPACE and restart X, then I get smaller font and icons in the window title bar. Anyone have ideas? I'm logging in as the same user, so it should be using the same preferences. I'm attaching an example of each.

I have an Inspiron 1520 with Gutsy 32bit with nvidia 8600.

---

### Post by Metaleks on 2008-01-09
Installation went great on on my system.  However, there are only 2 problems that I would like to resolve now.

1. The wireless breaks after you don't use it for a while.  And then connecting back is really hard.  I remember reading about this somewhere else.  Has anyone found a fix?

2. This is probably the most annoying bug.  First of all, my cd/dvd drive works just fine.  But!  Every 3 seconds it checks if there is a disk inside!  You hear the two beeps, and then the drive spins and turns on it's LED.  Like I said, every 3 seconds.  It's really quite annoying and starting to drive me crazy, lol.  In fact, I have the drive open while I'm working on my laptop just so I don't have to hear the sounds.  Anyone know anything about this?

---

### Post by (pr) on 2008-01-10
Could someone please help: I've got some frustrated issues. I may just as well stop and try to use Ubuntu/Linux.

1) I must have done something wrong during the setup, because by default my keyboard is qwerty (while in real life it is azerty). I've been able to switch my 'user' to azerty by changing the settings in Gnome. However, while logging in or if I use another window manager (fluxbox, etc.) I'm stuck again to qwerty. (Yes I know it's not really an Inspiron issue, but frustrating nonetheless)

2) That damn display :mad: Everytime I log in to Ubuntu the display has a resolution of 1280x800. I can go to the display settings in Ubuntu and switch them to 1440x900, but still this doesn't seem work for more than a login period. I'm thinking I've must have chosen the wrong settings for the screen. I know the driver should be (in my case) the Nvidia, but what are the right settings for the screen? 

I'd love it if someone could help me. P.

---

### Post by alfredska on 2008-01-10
> **Metaleks said:**
> Installation went great on on my system.  However, there are only 2 problems that I would like to resolve now.

1. The wireless breaks after you don't use it for a while.  And then connecting back is really hard.  I remember reading about this somewhere else.  Has anyone found a fix?

Read two posts above your own.

---

### Post by Metaleks on 2008-01-10
> **(pr) said:**
> 2) That damn display :mad: Everytime I log in to Ubuntu the display has a resolution of 1280x800. I can go to the display settings in Ubuntu and switch them to 1440x900, but still this doesn't seem work for more than a login period. I'm thinking I've must have chosen the wrong settings for the screen. I know the driver should be (in my case) the Nvidia, but what are the right settings for the screen? 

I'd love it if someone could help me. P.
I don't know if this will solve it, but for me it did.  It also fixed the long login times i sometimes had.

Go to your
```
/etc/usplash.conf
```
and change the resolution there to your proper resolution, if it already isn't.

---

### Post by carminez on 2008-01-11
> **carminez said:**
> I have an issue where the title bar on a window is displaying large fonts and large icons when I first boot and login, but if I do a CNTRL-ALT-BACKSPACE and restart X, then I get smaller font and icons in the window title bar. Anyone have ideas? I'm logging in as the same user, so it should be using the same preferences. I'm attaching an example of each.

I have an Inspiron 1520 with Gutsy 32bit with nvidia 8600.

I found an answer for my problem. [http://ubuntuforums.org/showthread.php?t=583159&highlight=titlebar&page=3](http://ubuntuforums.org/showthread.php?t=583159&highlight=titlebar&page=3)

It involved adding the dpi to /etc/gdm/gdm.conf.

---

### Post by alfredska on 2008-01-11
ctpaterson,
   There are a number of issues with fixes posted throughout this thread which you might consider mentioning in the first post.  Here is a list of topics.  Some are not entirely 1520/Ubu7.10 specific, and they can be omitted if you believe them irrelevant.

Dell 1505N Wireless: [ctpaterson]("http://ubuntuforums.org/showpost.php?p=3595530&postcount=33")
Ubuntu 7.10 64bit Alternative Install works: [alfredska]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81")
Installing Ubuntu 7.10, keeping MediaDirect and Vista intact: [alfredska]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81")
Removing hiss/pop/crackle from headphone port: [alfredska]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81") (see very last sentence of post)
Using Vista's partition manager to make more room for Linux: [twbutler]("http://ubuntuforums.org/showpost.php?p=4019218&postcount=92")
Blank screen on bootup for Ubuntu 64bit: [adycopilu]("http://ubuntuforums.org/showpost.php?p=4033857&postcount=96")
Intel 3945 disconnects frequently, or has trouble reconnecting: [meateater]("http://ubuntuforums.org/showpost.php?p=4067462&postcount=112"), [trmentry]("http://ubuntuforums.org/showpost.php?p=4088830&postcount=135")
Broadcom BCM94311MCG Wireless issues: [meborc]("http://ubuntuforums.org/showpost.php?p=4084605&postcount=130")
Suspend issue: [monkeyBox]("http://ubuntuforums.org/showpost.php?p=4087984&postcount=133")
Titlebar displaying incorrectly sized fonts, unless GDM restarted: [carminez]("http://ubuntuforums.org/showpost.php?p=4113589&postcount=143")
Compiz doesn't work on Intel X3100: [Online]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility")
Winxp, Ubuntu, and functional Media Direct: [apanda02]("http://ubuntuforums.org/showpost.php?p=4141488&postcount=153")
Volume too low: [alfredska]("http://ubuntuforums.org/showpost.php?p=4187274&postcount=155")
REPORT: Bluetooth working out of box: [Horrendus]("http://ubuntuforums.org/showpost.php?p=3588614&postcount=27")

---

### Post by Metaleks on 2008-01-11
> **alfredska said:**
> Read two posts above your own.
I already have, the fixes don't work.

---

### Post by meateater on 2008-01-13
If wireless still keeps on breaking even with the iwl3945 module loaded.
You can check if its loaded when you do a 

> 
$ lsmod | grep iwl
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211


Try to check if you still have the ipw3945 module. If it is still there. You need to 
add that to /etc/modprobe.d/blacklist

> blacklist ipw3945

Can somebody who still has the wifi getting disconnected issue test this fix out.
I did not have to resort to this fix yet. As of now my wifi is fine. ( I haven't ran my box overnight yet. )
I hope this fixes it...

---

### Post by Metaleks on 2008-01-13
> **meateater said:**
> Can somebody who still has the wifi getting disconnected issue test this fix out.
I will test it right now.  I'll leave my laptop on overnight with some heavy network traffic.  I'll let you know tomorrow.

---

### Post by ctpaterson on 2008-01-14
> **alfredska said:**
> ctpaterson,
   There are a number of issues with fixes posted throughout this thread which you might consider mentioning in the first post.  Here is a list of topics.  Some are not entirely 1520/Ubu7.10 specific, and they can be omitted if you believe them irrelevant.

Hey Alfredska,

Thanks very much for compiling this list.  Looks like some useful stuff in there.  I'll look at it in a little more detail,and see what I can do to give them some prominence on the top post, while still keeping the top post relatively simple and non-threatening to a newb.

Please bear with me in terms of how long it takes.  I'll definitely aim to do it this week - but we've got a little newbie of our own at home who is...consuming a lot of resources.  :wink:

Cheers.

---

### Post by Styx on 2008-01-14
Hi 

Thanks for all the good information in this post.

And have a problem with my Inspiron 1520 with a 7.10 Ubuntu 64bit version on it.(using a 8600 nvidia) 
The problem is that i get a blank screen during boot. BUT not the normal i can´t see a boot splash thing. 
No the laptop just appears to be turned off. I do not even get the Dell start up screen. Now i do not now if it is a ubuntu problem but i gues so because i only get the error wenn i close the screen (lit:confused:) or wenn i log off out of gnome using the shutdown button. 

Well i know the system is running because it turns off wenn i use the tty1 and " init 0" or some like it. But i do not see anything. 

Dit anyone have a problem like this.
Wenn i get it back on i will post some logs maby there is something in there.

i hope this is the right place to post this. And sorry for my english i gues.

---

### Post by Metaleks on 2008-01-14
> **Metaleks said:**
> I will test it right now.  I'll leave my laptop on overnight with some heavy network traffic.  I'll let you know tomorrow.
Your fix, by using the other module, does not work.  In fact, it messes up the default keyring manager, and makes you input the password again.  It doesn't even remember.  That's not so bad, though.  But it really fixes nothing.  The connection still breaks.

---

### Post by apanda02 on 2008-01-15
SUCESS with the whole XP/Ubuntu/Media Direct setup!!!!!!!!

All thanks to alfredska's tips! 

I am gonna sulk in this glorious moment for a few more hours before typing up a little guide...

---

### Post by alfredska on 2008-01-15
apanda02, I'm thrilled to hear that you found a way to make it work.  Congratulations.  I look forward to reading your howto.

---

### Post by apanda02 on 2008-01-15
Well the whole idea was basically using the partitioning scheme you had&#8230;using a tool that doesn&#8217;t screw things up.
This is basically a combination of alfredska&#8217;s guide and this link:
[http://ubuntuforums.org/showpost.php?p=3855904&postcount=81](http://ubuntuforums.org/showpost.php?p=3855904&postcount=81)
[http://linux6400.wordpress.com/2007/04/06/installing-ubuntu-edgy-eft-610/](http://linux6400.wordpress.com/2007/04/06/installing-ubuntu-edgy-eft-610/)

The way to go about this is to **start clean.**
1. Put in the Media Direct CD and pick option 2...which allows you to pick a specific size. DO NOT PICK OPTION 1...it is impossible to resize XP and then partition the leftover space...you will wind up corrupting MD...

2. Next install XP in the designated partition. Get drivers.

3. Install Media Direct...DO THE UPDATE!~I was told it helps MD deal with partitioning~ 

4. Now boot up Ubuntu Live CD and in terminal type in "sudo gparted." Now delete the useless partition...and use the space to create proper Linux, Swap and Data partitions WITHIN the extended partition. DO NOT USE THE PARTITIONER IN THE CD. MAKE SURE ALL NEW PARTITIONS STAY WITHIN THE EXTENDED PARTITION AND NONE OF THEM BECOME PRIMARY PARTITIONS.

5. Apply changes, reboot, install linux, when it comes to time to install the bootloader MAKE sure its in the linux partition hd(0,#(MINUS 1!)).

6. Now when installation is done, choose to continue to work in the live environment, open up terminal and type in"

sudo dd if=/dev/sdaX of=/home/ubuntu.bin bs=512 count=1

Where X the linux partition number. Goto home directory and copy the ubuntu.bin file there into the external drive. Reboot into windows. 
Copy ubuntu.bin into the C drive
type in "c:\boot.ini" in run. Then add in the line at the very bottom. 
C:\ubuntu.bin="Ubuntu"
You can change the wait time here also. 

Restart to see XP boot loader with linux option.

---

### Post by apanda02 on 2008-01-15
DESCRIPTION OF THE CODE BY alfredska.

dd is a raw copy utility. since boot sectors are not written to a tidy little file that can simply be copied and moved around, you have to specify a way to pull the raw data from the first 512 bytes of partition. In this case, "if=/dev/sdaX" tells dd to read from that particular partition and read from 0 to 512 bytes into it (bs=512). "count=1" tells dd to read only 1 block of 512bytes, and not any further. "of=/home/ubuntu.bin" stores the data that was read in a file at /home/ubuntu.bin

---

### Post by alfredska on 2008-01-22
> **alfredska said:**
> 
STILL UNRESOLVED: Volume too low: [qbox]("http://ubuntuforums.org/showpost.php?p=3579318&postcount=24"), alfredska

Actually, it seems this problem is quite easily fixed.
[LIST=1]
[*]Right click on speaker icon in system tray, and select "Open Volume Control"
[*]Go to Edit: Preferences
[*]Put a check next to Front. Hit OK
[*]Turn Front volume all the way up.
[*]Now the master volume control raises and lowers the volume between much greater extremes.
[/LIST]

---

### Post by PiranhA2 on 2008-01-23
Hi.

Did anybody managed to get the Memory Sticks working (especially the Pro Duo ones)?
SD Cards work fine for me, but not Memory Sticks.

---

### Post by JudgeFudge on 2008-01-23
After trying a lot of other alternatives without success I followed this and the sound worked straight away after a reboot.

Thanks!

(Inspiron 1720 on gutsy)

> **kirkquitar said:**
> I found the following fix the only one that would work on a 1720:
```
sudo apt-get install linux-backports-modules-generic
```

It's probably better to try this first rather than the installing of various alsa libraries/modules.

If this has worked for others, maybe the OP should re-order the audio-fix steps to reflect this...

Note - if you have used Envy to update graphics drivers, you may have to run it again after the fix mentioned in this post.

---

### Post by trmentry on 2008-02-02
I got this How-To working on my 1520 and it worked fine.  I used the 'linux-backports-modules-generic' to get the sound working.

However it appears at least from what I can tell, my mic port on the side of the laptop doesn't work.  I plugged in my headset... the speakers on set work fine in the port.   

Is there something else I need to install or config to get this working?



(My test on this was while in Skype, I plugged in my headset with mic to the ports.   Then covered the 2 mic holes on laptop near the built in web cam, and my party couldn't hear me.  Yes the mic works, as I tested in windows and was fine.  


THanks

---

### Post by alfredska on 2008-02-02
> **trmentry said:**
> my mic port on the side of the laptop doesn't work.  I plugged in my headset... the speakers on set work fine in the port.   

Is there something else I need to install or config to get this working?

My mic port works fine, here are my settings:

Right click on speaker in system tray, and select "Open Volume Control"
Edit: Preferences
Check: Capture, Capture 1, Input Source (x2)
Select OK
Options Tab: Input Source: Mic
Recording Tab: Capture: Make sure nothing is muted and max volume (Skype will auto-adjust this)

Skype Options
Sound Devices: Sound In: HDA Intel (hw: Intel,0)

(if that device is mapped to your laptop built in mic, try Intel,1)

I hope this works for you.
~Matt

---

### Post by fejack on 2008-02-21
> When you boot from the MediaDirect CD, it is going to delete the partition table on your laptop's hard drive.

Goethedammit! That's the second time MediaDirect boots from the HDD and wipes my partition table. The first time I have a CD in the drive, so MD automatically booted. Hi had to reinstall everything. Fortunately I know better and perform backups regularly... on at least two other media.

This morning I accidentally pressed the Home button and the PC booted under MD again. I shut down the machine as soon as I noticed what was happening, but it seems MediaDirect wipes the partition right as it starts loading.

Unless I manage to restore my partition table as it was before, which seems unlikely, I'll try the following:
[LIST=1]
[*]install MediaDirect[*]boot MediaDirect[*]install Vista[*]boot MediaDirect[*]check if Vista still boots[*]then install Ubuntu[*]boot MediaDirect and see if it still messes things up even though it was given all the space it needed
[/LIST]

](*,)Schnitzel!

---

### Post by russasaurusRex on 2008-02-21
Fejack,

Have you tried pressing the MediaDirect button again?

I know this sounds crazy, but when I accidentally pressed that button I shut down the machine and pressed that button again and it booted properly.

I got the tip from another thread on here about MediaDirect, the URL of which I can't remember now.

Hope it works for you as it did for me.

Russ

---

### Post by alfredska on 2008-02-21
fejack,
  Have you followed the steps in [this post]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81")?

  Be aware that resizing partitions after using the MediaDirect disc to partition your hard drive is often the reason for a malfunctioning Home Button.

~Matt

---

### Post by Mamsaac on 2008-03-01
Anyone knows how to make the wireless work with monitor/promiscuous mode? I played a little bit with it, but I couldn't figure out how to make the drivers work.

Intel 3945 is the wireless adapter... but I can't make it work :S

Thanks in advance for future answers.

---

### Post by alfredska on 2008-03-01
You'll likely have to recompile the intel drivers yourself before issuing:
```
modprobe wlan0 mode=2
```

Uninstall ubuntu native 3945 drivers before installing your own.

[This thread]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/intel-3945-wireless-adaptor-setting-monitor-mode-450014/vv") is mildly relevant.

---

### Post by madgreek on 2008-03-09
I wrote an [article in my blog]("http://blogs.ittoolbox.com/eai/madgreek/archives/kubuntu-laptops-and-wireless-networks-22955") that summarizes fixing both my wireless and sound problem.  I made some minor modifications to the instructions from this site.  I hope this helps somebody.

[http://blogs.ittoolbox.com/eai/madgreek/archives/kubuntu-laptops-and-wireless-networks-22955](http://blogs.ittoolbox.com/eai/madgreek/archives/kubuntu-laptops-and-wireless-networks-22955)

---

### Post by scaryant on 2008-03-15
Thanks for your sound fix information, worked perfectly.

Also thought I would mention that the bluetooth on my install works perfectly, I tested connection and transfer with a Sony K810i. My Dell is a Inspiron 1520 same specs as the one in the original post.

Cheers

---

### Post by alfredska on 2008-03-15
> **scaryant said:**
> Thanks for your sound fix information, worked perfectly.

Also thought I would mention that the bluetooth on my install works perfectly, I tested connection and transfer with a Sony K810i. My Dell is a Inspiron 1520 same specs as the one in the original post.

Cheers

I can also attest to bluetooth working correctly with my Microsoft Presenter 8000 mouse.

---

### Post by CruxCalixtus on 2008-03-15
Hello everyone,

Before I start rambling, please note that I'm almost as newbie as you can get on Linux so please bear with me :P

I have an Inspiron 1520 with the following specs:

- Core 2 Duo T7500 2.2Ghz
- 4 GB RAM, 667 Mhz
- NVidia GeForce 8600GT video
- Creative Audigy audio (though on Windows Vista it showed something like 'SigmaTel 92XX High Definition Audio CODEC' ... was I conned somehow?)
- Bluetooth Adapter
- Intel Wireless LAN adapter

The laptop shipped with Windows Vista Home Premium; I downloaded the x386 build of Ubuntu 7.10, resized the Vista partition to make room for Ubuntu, and installed it. 

My issues:
- I can't get sound to work. (Big surprise, here.)
- The Dell Bluetooth TravelMouse that shipped with the laptop doesn't work. (Nay, Ubuntu does not even recognize it.) The adapter apparently works since I can configure some preferences and stuff, but no trick, procedure, spell or ritual has succeeded so far. (Don't you come suggesting a voodoo doll, please.)
- Wireless LAN doesn't seem to work either. 

I already removed the ALSA drivers, but to no effect. I'm out of ideas... anyone with a couple to spare?

****UPDATE****

I got sound working after following madgreek's advice. My most sincere and heartfelt thanks :)

---

### Post by LeoSolaris on 2008-03-17
Yay! Thank you, I had not realized that my mic was not working till recently, but because of your post, I was able to easily get it working again with just the switch of analog to digital 1 in alsamixer in the terminal.

Thank you very much! My system is so far 100% operational for all of the things I need it to do. I have not tested the firewire port (I do not have anything that uses it) or the audio in/out ports (I am thinking about buying a headset with a better mic than the intigrated one), or the modem (since I do hot have dialup, I doubt I ever will test that part.) Litterally everything else works, either out of the box, or with a little tweaking.

---

### Post by alfredska on 2008-03-17
> **CruxCalixtus said:**
> 
- The Dell Bluetooth TravelMouse that shipped with the laptop doesn't work. (Nay, Ubuntu does not even recognize it.) The adapter apparently works since I can configure some preferences and stuff, but no trick, procedure, spell or ritual has succeeded so far. (Don't you come suggesting a voodoo doll, please.)


For bluetooth I followed the section entitled "Using a Bluetooth Keyboard or Mouse" from the post [HERE]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu").

> **CruxCalixtus said:**
> 
- Wireless LAN doesn't seem to work either.


Can you provide some more details?  When you click on the NetworkManager icon in the system tray, do wireless networks appear?  If not, under a terminal, type iwconfig and see if any wireless devices are found (if none are found, all devices will say "xxxx    No wireless extensions").  Report back, and we'll go from there.

---

### Post by which_chick on 2008-03-17
I just finished installing Ubuntu (7.10, AMD64 alternate install) on my Inspiron 1520.  It all went smoothly and as described by previous posters.  The partitioning did just fine on the default choice.  XP complained (on first boot) exactly as described in this thread and then fixed itself and booted as normal.  The Grub worked as advertised and lets me pick what I want to boot into.  The fix for the "low graphics mode" message (NVIDIA) was in the forum and worked as advertised.  The fix for the sound (above, thanks to MadGreek) worked beautifully once I figured out how to get up a terminal window.  I even figured out how to get my bookmarks from Firefox on XP to Firefox on Ubuntu.  Yay!  This is so cool!

Thanks, everyone, for the helpful and informative thread.  I didn't have to ask any questions because they were all already answered for me.

---

### Post by CruxCalixtus on 2008-03-19
Your info about Bluetooth was immeasurably helpful, for which I thank you. ^^

Now, regarding wireless stuff, it reads something like this:

eth0    no wireless extensions

eth1      unassociated  ESSID: off/any  
          Mode: Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate: 0 kb/s   Tx-Power: 16 dBm   
          Retry limit: 15   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 3   Missed beacon: 0

I presume that eth0 is the standard wire-based LAN adapter and eth1 is the wireless adapter, but the wi-fi power light on the panel is still off.

---

### Post by alfredska on 2008-03-20
It looks like your wireless card is detected and modules loaded.  I'm curious about the "Invalid misc: 3", but I'll ignore it for the time being.

So when you left click on the NetworkManger icon in the sytem tray, do any networks appear?  If so, what problems are you encountering when you click on a network to connect?

---

### Post by CruxCalixtus on 2008-04-02
I'm logging on from a wireless network right now, so I guess I've figured this out. Thanks, Alfred!

I have another problem right now, but I guess I should go looking elsewhere for answers regarding how to configure Ubuntu and Samba to work with a Windows network.

---

### Post by jamsub on 2008-04-08
Has anyone tried to do the install with the packaged .iso Dell makes for the 1420?  On the Dell forums some people have tried it on a 1520 but didnt really report the results.  Its about 4 times as large as the LiveCD but it could eliminate the problems people are running into.  For me I will need to rebuild Media Direct when I get home since I installed Gutsy onto my 1520 and used the CD's partition sizer.  When I try to boot Media Direct it BSODs.  Also Vista has frozen on me unexpectedly since I added Ubuntu to my laptop.  I think because I also shrunk the Vista partition slightly as well.  I will likely just reinstall everything from scratch unless anyone has some suggestions.  BTW good job on the guide so far.  I used it to get my audio working and it got me started on the apt-get commands for other things.

James B.

---

### Post by alfredska on 2008-04-09
Hi jamsub,
  I haven't tried the Dell images yet, but I have considered them myself.

As far as the MediaDirect partition is concerned, there is a post in the middle of this thread which you might find useful:
[http://ubuntuforums.org/showpost.php?p=3855904&postcount=81](http://ubuntuforums.org/showpost.php?p=3855904&postcount=81)

---

### Post by jamsub on 2008-04-09
Thanks for that.  I copied that guide to my external drive and will use it when I get home.  The guide in this post [http://ubuntuforums.org/showthread.php?p=4030519#post4030519](http://ubuntuforums.org/showthread.php?p=4030519#post4030519) seems like it could painlessly fix it.  Not sure if that is a way to go or not.  

I took another look at those .iso files they supposedly will wipe everything out so they may not be very good for dual booting.  Here is the link for them [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

---

### Post by ctpaterson on 2008-04-17
Just wanted to drop in and note that I have updated the top post with some clearer instructions, and to give better prominence to some of the solutions that alfredska compiled together.  I'm long late on my promise to go through them and put them up there - but I've finally gotten to it.  Apologies and thanks in equal measure.

---

### Post by jamsub on 2008-04-17
ctpaterson....what is the advantage of using the 64 bit Gutsy?  You and I have the same 1520 specs are you also running the 64bit Vista?

---

### Post by ctpaterson on 2008-04-18
> **jamsub said:**
> ctpaterson....what is the advantage of using the 64 bit Gutsy?  You and I have the same 1520 specs are you also running the 64bit Vista?

I'd like to run the 64 bit version of Ubuntu, but I faced some challenges  getting the disc to boot, and I'm led to understand there are still a number of headaches getting everything to work.  I am running (and the instructions at the top of the thread are for) 32 bit Gutsy.

I'm planning to upgrade to Hardy (a little annoyed that the RC isn't out yet - but I'm busy this weekend anyway), but the 64bit beta disc wouldn't load - and a colleague tells me that he couldn't get the Lightening plugin for Thunderbird to install on his 64 bit installation of Gutsy, so I've more or less decided to stick with 32 bit for the next release.

The advantages mainly surround performance from what I understand - but there seems to be some debate as to how many gains will be realized.

Vista was gone within hours of my laptop's arrival.  The reinstall CD is in my basement in the bottom drawer of a locked filing cabinet, stuck upside-down in a disused toilet, with a sign on the door saying "Beware of the Leopard."

Cheers.

---

### Post by jamsub on 2008-04-18
> **ctpaterson said:**
> 

Vista was gone within hours of my laptop's arrival.  The reinstall CD is in my basement in the bottom drawer of a locked filing cabinet, stuck upside-down in a disused toilet, with a sign on the door saying "Beware of the Leopard."

Cheers.

Nice!  I am doing the dual-boot thing for awhile especially since I play alot of games.  I use Red Hat systems for my work so I wanted a Linux distro to learn in my off time.  I didnt realize that Red Hat and Ubuntu are opposites sides of the family tree until yesterday.  I will keep Ubuntu because you guys seem very helpful compared to the Fedora forums.

---

### Post by alfredska on 2008-04-19
Hey ctpaterson, thanks for updating the first post.  Looks great!
~Matt

---

### Post by ctpaterson on 2008-04-21
> **alfredska said:**
> Hey ctpaterson, thanks for updating the first post.  Looks great!
~Matt

No worries.  Just sorry I took so long.

Cheers.

---

### Post by trmentry on 2008-04-25
anyone done a dist-upgrade to 8.04 yet?    :)

---

### Post by which_chick on 2008-04-26
I upgraded to 8.04 last night, left it to run while I went to bed.  This morning, it was all ready to reboot, which I did.  On reboot, it didn't have wireless (again -- I had to twiddle that to get it to work in Gutsy, too) but I followed the instructions here: [http://ubuntuforums.org/showthread.php?p=4798063#post4798063]("http://ubuntuforums.org/showthread.php?p=4798063#post4798063") and that got the wireless up and running again.  

Other than that, so far, so good.  I haven't done much with it but yet but aside from the wireless, things seem to be pretty good.  Sound is OK.  Youtube is busted again (I had to fix this under Gutsy, too, so no biggie there).  DVDs play OK.  This is not a guarantee that nothing will go wrong, but you probably won't have a paperweight.

Good luck!

---

### Post by alfredska on 2008-04-26
> **trmentry said:**
> anyone done a dist-upgrade to 8.04 yet?    :)

I installed a fresh copy of 8.04 (did not choose the update route).
1) Audio now works out-of-box (to be expected since we were installing a backport previously)
2) Need to install nvidia-settings
3) Pink halos around windows (a bug in the nvidia-new driver: [link]("http://ubuntuforums.org/showthread.php?t=676358"))
4) Bluetooth worked (almost) out-of-box.  Only had to issue "sudo hidd --search" for my bluetooth mouse to work

Overall satisfied, though I had to disable Compiz effects because I couldn't stand the pink halo (will re-enable once the nvidia driver is updated).

---

### Post by trmentry on 2008-04-26
I have a couple questions for you guys. :)

First off, the linux-backports thing that mentioned in this guide worked for me at first but then stopped.  So I downloaded the linux-backports DEB from Dell and that seemed to work much better for audio.

I take it the backports aren't needed with the new Pulse Audio?  

I'm guessing that I will have to recompile VMWare Workstation that I have on my laptop for my work's VPN thing that only works in XP.  

On the wireless thing:  I'm running the ipw3945 driver for my Intel Wireless thing.  When you said you had to work on wireless again, what did you have to do?  Or was this b/c of the broadcom wireless  I take it you have.


And with YouTube being broke again, I take it you just had to install flash non-free again?

Also did you do this from cli or from Update Manager GUI?


Thanks and sorry for the questions.

---

### Post by which_chick on 2008-04-26
> **trmentry said:**
> 
On the wireless thing:  I'm running the ipw3945 driver for my Intel Wireless thing.  When you said you had to work on wireless again, what did you have to do?  Or was this b/c of the broadcom wireless  I take it you have.

I have a broadcom wireless that didn't work out of the box with the Gutsy install so I wasn't surprised when it barfed under Hardy.  (I can hook up to wire ethernet easily at home, so this didn't prevent me from searching for a fix.)  I used the instructions found in the second post here:
[http://ubuntuforums.org/showthread.php?p=4798063#post4798063]("http://ubuntuforums.org/showthread.php?p=4798063#post4798063") to fix the wireless thing again.  It's been trouble free since the fix.

> **trmentry said:**
> And with YouTube being broke again, I take it you just had to install flash non-free again?

I did that, but like an idiot, I somehow first picked a flash other than adobe's (not thinking clearly, apparently).  That gave me crappy video but no sound.  Argh.  I twinked around with it some more according to additional instructions on the fora and then it started working.  Not sure what actually made it work, but it was NOT working until the last thing I did, which was the suggestion (post #2 in thread, by Kilz) here:  [http://ubuntuforums.org/showthread.php?t=695674]("http://ubuntuforums.org/showthread.php?t=695674")

Sorry I can't give better explanations for how I fixed stuff -- usually I just search for people who have had the same problem as I am having and try what they are told to try until I find something that works.

---

### Post by ctpaterson on 2008-04-27
> **trmentry said:**
> anyone done a dist-upgrade to 8.04 yet?    :)

I did a fresh install - a little less trouble than Gutsy was (although I compensated for that simplicity by adding an encrypted partition).  I'll start a thread for that if people would like one (and if there isn't another one when I get to it).

Cheers.

---

### Post by alfredska on 2008-04-27
> **ctpaterson said:**
> I did a fresh install - a little less trouble than Gutsy was (although I compensated for that simplicity by adding an encrypted partition).  I'll start a thread for that if people would like one (and if there isn't another one when I get to it).

Cheers.

I'd like to see a thread, but I think it's important that a couple of issues are explained if the thread is to be useful:
[LIST=1]
[*]nVidia-new driver has visual bugs (I suffer from this problem) _[Forum Topic]("http://ubuntuforums.org/showthread.php?t=676358")_ _[Official Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382")_ _[Partial Fix]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37")_

[*]Intel 3945/4945 driver switch from ipw394 in Gutsy to iwl3945 in Hardy causes wireless issues for some users (I never suffered from this problem, though I've seen it on a friend's computer) _[Forum Topic]("http://ubuntuforums.org/showthread.php?t=765647")_[LIST]
[*]Some users are able to remedy this problem by installing a backport (linux-backports-modules-hardy-generic) and/or replacing NetworkManager with WiCD (see post _[here]("http://ubuntuforums.org/showpost.php?p=4799471&postcount=29")_ for explanation of both)
[/LIST]
[/LIST]

---

### Post by LeoSolaris on 2008-04-27
[FONT=Century Gothic][SIZE=3]I did a Distro upgrade to Hardy over the weekend, and so far the Intel Wireless N card works, after a little fiddling compiz is not really annoying me much anymore. (I had a copy of screenlets that was more advanced than Ubuntu's repo's version, and it caused a lot of crashes.)[/SIZE]

[SIZE=3]That was the good. Most everything I have tested so far has worked. The bad...  webcam is shot. It is detected. It even has a light, but the light is constently on. Makes me feel like my computer is watching me. I noticed when I logged off (because I do not have the splash screens up) that motion was constently saving jpg's to a file, so I removed motion. Still no dice. I checked with multimedia settings and the test would not show the feed, nor would the V4L2 test, which used to work in Gutsy. It does say something different though, "Video for Linux 2 (v4l2): Device '/dev/video0' cannot capture at 352x288" All of the rest say "Video for Linux (v4l): Could not get/set settings from/on resource."

I have a 64 bit disc comming in the mail from Ubuntu, and I will test it out when it gets here with a fresh install in a spare partition. That will be a couple of weeks though.

Leo

P.S. PulseAudio is nice for the HD sound card! Much better control and sound.[/SIZE][/FONT]

---

### Post by ctpaterson on 2008-04-28
New thread for Hardy here: [http://ubuntuforums.org/showthread.php?p=4822410](http://ubuntuforums.org/showthread.php?p=4822410).

Tried to capture what had already been mentioned, along with my own experiences - but as always; post early and post often.

---

### Post by noah3210 on 2009-04-24
uh hi i am wondering if this will work with Ubuntu 9.04 and with a dell xps m2010? thanks

---

### Post by Styx on 2009-05-16
On my Inspiron 1520 it works perfect. I use the 9.04 Kubuntu version with KDE 4. 
I even got the cairo-dock working like a charm.

---

