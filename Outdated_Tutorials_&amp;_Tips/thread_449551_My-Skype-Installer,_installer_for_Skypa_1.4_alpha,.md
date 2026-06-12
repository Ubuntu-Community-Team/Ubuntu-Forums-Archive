---
title: "My-Skype-Installer, installer for Skypa 1.4 alpha, works for 32 and 64 bit"
date: 2007-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by johnficca on 2007-05-20
Hi this is an installer I wrote for Ubuntu 7.04 32 or 64 bit, it will install Skype 1.4.0.64 alpha. I have changed it to use the new skype 1.4.0.64 alpha and I will be keeping it updated through the alpha phase and beyond. The Installer also now puts a nice launcher and icon under Internet. I hope you like it.  

Instructions 

1 download the script called My-Skype-Installer.sh, you'll see it at the bottom
2 save it to your Desktop 
3 open your gnome terminal 
4 copy and paste this or type this in the terminal : 
> cd Desktop
chmod a+x My-Skype-Installer.sh
./My-Skype-Installer.sh
5 then follow the instructions in the terminal 
6 have fun using Skype 1.4 alpha  

please let me know if you like it and it worked for you, if you have any ideas on how to make it better please post them here.

---

### Post by nike984 on 2007-05-20
> **johnficca said:**
> Hi this is an installer I wrote for Ubuntu 7.04 32 or 64 bit, it will install Skype 1.4 alpha. Its best if you already have the older Skype installed as this script does not make the menu luncher, if someone knows how to write that into the script please do or tell me and I will. 

Instructions 

1 download the script called My-Skype-Installer.sh, you'll see it at the bottom
2 save it to your Desktop 
3 open your gnome terminal 
4 copy and paste this or type this in the terminal : 

5 then follow the instructions in the terminal 
6 have fun using Skype 1.4 alpha  

please let me know if you like it and it worked for you, if you have any ideas on how to make it better please post them here.

Thanks for the script. :D
Its working fine. I've just installed 1.4 alpha using your script.

---

### Post by rsambuca on 2007-05-23
An [[COLOR="Red"]update to 1.4 alpha[/COLOR]]("http://share.skype.com/sites/garage/2007/05/skype_for_linux_14_alpha_updat.html") was just released to fix a number of bugs.  Will your script automatically use the new one?

---

### Post by Cappy on 2007-05-23
No, but he'll be updating it =p I just updated my guide:
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
It isn't as good as a script though because it can get "stuck" on a portion of the script and have to be partially recopied.

---

### Post by johnficca on 2007-05-24
I just updated it this morning so now it works for the new one and it puts a nice launcher in the gnome menu, hope you like it.

---

### Post by Cappy on 2007-05-24
You are missing a new library for the new skype alpha, see my guide. I like your script though ^^

Edit: Just to let you know, it's the libdbus + soft link

---

### Post by chrisLACHCIK5084 on 2007-05-24
even thou this may not be part of this subject, but how the heck do you uninstall that stupid Ekiga Softphone Skype crap in edgy?!?!?! i hate it and when i goto uninstall it it says "YOU ARE UNINSTALLING UBUNTU-DESKTOP"

---

### Post by johnficca on 2007-05-24
> **Cappy said:**
> You are missing a new library for the new skype alpha, see my guide. I like your script though ^^

Edit: Just to let you know, it's the libdbus + soft link

Thanks I Just updated it with some of your How To, it was dumb of me to assume that 64 bit didn't need any new libs. Thanks for the tip.

---

### Post by johnficca on 2007-05-24
> **chrisLACHCIK5084 said:**
> even thou this may not be part of this subject, but how the heck do you uninstall that stupid Ekiga Softphone Skype crap in edgy?!?!?! i hate it and when i goto uninstall it it says "YOU ARE UNINSTALLING UBUNTU-DESKTOP"

Ubuntu-desktop is just a meta package, so its ok to remove it, just install it again before you upgrade to the next release.

---

### Post by struess on 2007-05-28
I recently screwed a whole bunch of things up on my computer and might have accidentally deleted several libraries in the process, but when i ran your script i hit a snag:

```

skype: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtDBus.so.4)
skype: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtGui.so.4)
skype: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtNetwork.so.4)
skype: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtCore.so.4)
skype: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libdbus-1.so.3)
skype: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtXml.so.4)
./My-Skype-Installer.sh: line 59: skype-1.4.0.64/: No such file or directory

```

is libc.so.6 a library in the repos?  any idea how i get around this?

---

### Post by Cappy on 2007-05-28
```

sudo apt-get --reinstall install libc6-i386 ia32-libs ia32-libs-sdl ia32-libs-gtk lib32asound2

```

Hopefully that will repair any problems.

---

### Post by struess on 2007-05-29
no luck there.. i got the same message after reinstalling the libraries.  heh, i didn't realize this script was for fiesty, though -- i'm still using dapper.  might that be the problem?

---

### Post by Cappy on 2007-05-29
Actually it is because you are running dapper because you have libc 2.3 and not 2.4. There were posts about this on the skype forums. If you tried manually upgrading your i386 glibc to a newer version it would probably hose your system. I don't think there is anything you can do.

---

### Post by struess on 2007-05-29
that makes me a saaaaaad panda :( 

thanks for your help.  i suppose it's time i broke down and upgraded.

---

### Post by Cappy on 2007-05-29
Skype 1.3 works on dapper I think? You might as well just use that.

```

wget http://skype.com/go/getskype-linux-deb
sudo dpkg -i --force-architecture skype_debian-1.3.0.53-1_i386.deb

```

The dpkg line may be incorrect; you may need to change it for a newer version.

---

### Post by struess on 2007-06-03
a quick follow-up on the library problems:  they no longer exist.  i upgraded to feisty.  thanks for all your help!

---

### Post by aboutblank on 2007-06-04
Thanks a bunch!! My audio capture didn't work with 1.3, but it does in the beta!

---

### Post by macubo on 2007-06-07
Thank you for the script. Skype is now working but there were some minor issues buring installation.

I don't know.. maybe it just showed up too quickly for me to see the output in the terminal, but that's what I grabbed:
```
16:46:21 (12.62 MB/s) - "Skype-1.4.0.desktop" salvato [172/172]

ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.ATIIXP.pcm.modem.0:CARD=0'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3968:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM phoneline

```

And every time I start up Skype (by the Apps's menu) the gnome-power-manager hangs up (no more indication on the tray of the battery-status of the laptop). Just obtain a non closeble blank window of the gnome-power-manager itself.

Is there something I missed?
Thanks

---

### Post by jdmcg on 2007-06-10
I tried installing 1.4 in Feisty, but all it does is just start and a second or two later blank the Skype window so I have to force quit it. Any ideas why this would happen, and I know it is alpha.

---

### Post by Cappy on 2007-06-10
Were there any errors during installation?
Run "skype" on the terminal and see if it gives any errors when you run it.

---

### Post by jdmcg on 2007-06-10
Were no errors in it when I ran it. It gives me the login screen just for a second, then poof, nothing but a bare Skype window. It tries to sign in without anything in the password window.

Edit:
Nevermind got the problem solved, just needed a little reboot. :D

---

### Post by leonox on 2007-06-21
Hi, I ran the script and it seems like it worked, but when I run it, I always get the end user license agreement.  and when I try to sign in, it says "sign in failed", then I try to sign in again it says "database failure"... any idea of this problem?

---

### Post by nickdjones on 2007-08-04
Great news, I ran this script and it worked for me - nice one! 

Note: big thanks to Cappy to for his approach [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790), which got pretty close to working for me. Seems it might have worked had a waited a few minutes for Cappy's reply - thanks Cappy, never expected it to come so quick!

The feedback during the installation was pretty confusing tho, so thought I'd copy it here in case it's helpful in improving the useability of this script:

```
./My-Skype-Installer.sh
Welcome to My-Skype-Installer, this will install skype 1.4 alpha on 64 or 32 bit ubuntu 7.04


*****Welcome to My-Skype-Installer*****
====--- You will be asked for your root password during installation. ---===
====--- Installation can take some time depending on you internet speed. ---===
[1] continue and install for 64 bit Ubuntu 7.04
[2] Continue and install for 32 bit Ubuntu 7.04
[3] Stop/Exit
Enter your menu choice [1-3]: 1
Please enter your password and wait as My-Skype-Installer downloads some needed files
--14:28:56--  http://www.skype.com/go/getskype-linux-alpha-generic
           => `getskype-linux-alpha-generic'
Resolving www.skype.com... 198.173.5.35
Connecting to www.skype.com|198.173.5.35|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://download.skype.com/linux/skype-alpha-1.4.0.94-generic.tar.bz2 [following]
--14:28:57--  http://download.skype.com/linux/skype-alpha-1.4.0.94-generic.tar.bz2
           => `skype-alpha-1.4.0.94-generic.tar.bz2'
Resolving download.skype.com... 198.63.211.251, 209.0.200.2, 209.0.200.3, ...
Connecting to download.skype.com|198.63.211.251|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:28:58 ERROR 404: Not Found.

mv: cannot stat `skype-alpha-1.4.0.64-generic.tar.bz2': No such file or directory
tar: skype-alpha-1.4.0.64-generic.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./My-Skype-Installer.sh: line 64: cd: skype-1.4.0.64/: No such file or directory
Password:
mv: cannot stat `skype': No such file or directory
mkdir: cannot create directory `/usr/share/skype/': File exists
mkdir: cannot create directory `/usr/share/skype/sounds/': File exists
mv: cannot stat `sounds/*': No such file or directory
--14:29:34--  http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.2.3-0ubuntu3_i386.deb
           => `libqt4-gui_4.2.3-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,962,990 (4.7M) [text/plain]

100%[====================================================================================================>] 4,962,990    161.10K/s    ETA 00:00

14:30:02 (182.24 KB/s) - `libqt4-gui_4.2.3-0ubuntu3_i386.deb' saved [4962990/4962990]

--14:30:02--  http://mirrors.kernel.org/ubuntu/pool/main/q/qt4-x11/libqt4-core_4.2.3-0ubuntu3_i386.deb
           => `libqt4-core_4.2.3-0ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,205,696 (1.1M) [text/plain]

100%[====================================================================================================>] 1,205,696    318.11K/s    ETA 00:00

14:30:06 (293.59 KB/s) - `libqt4-core_4.2.3-0ubuntu3_i386.deb' saved [1205696/1205696]

--14:30:06--  http://mirrors.kernel.org/ubuntu/pool/main/libs/libsigc++-2.0/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb
           => `libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34,224 (33K) [text/plain]

100%[====================================================================================================>] 34,224        65.39K/s             

14:30:07 (65.20 KB/s) - `libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb' saved [34224/34224]

--14:30:07--  http://mirrors.kernel.org/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu3_i386.deb
           => `libdbus-1-3_1.0.2-1ubuntu3_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 204.152.191.7
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 269,248 (263K) [text/plain]

100%[====================================================================================================>] 269,248      228.63K/s             

14:30:09 (228.06 KB/s) - `libdbus-1-3_1.0.2-1ubuntu3_i386.deb' saved [269248/269248]

mv: cannot move `/home/nickdjones/Desktop/skype-1.4.0.64/usr/lib/qt4' to a subdirectory of itself, `/usr/lib32/qt4'
ln: creating symbolic link `/usr/lib32/libdbus-1.so.2' to `/usr/lib32/libdbus-1.so.3': File exists
rm: cannot remove `/home/nickdjones/Desktop/skype-alpha-1.4.0.64-generic.tar.bz2': No such file or directory
--14:30:09--  http://allyouneedisblog.freehostia.com/skype_icon.png
           => `skype_icon.png'
Resolving allyouneedisblog.freehostia.com... 64.72.119.253
Connecting to allyouneedisblog.freehostia.com|64.72.119.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64,782 (63K) [image/png]

100%[====================================================================================================>] 64,782        70.57K/s             

14:30:11 (70.45 KB/s) - `skype_icon.png' saved [64782/64782]

--14:30:11--  http://allyouneedisblog.freehostia.com/Skype-1.4.0.desktop
           => `Skype-1.4.0.desktop'
Resolving allyouneedisblog.freehostia.com... 64.72.119.253
Connecting to allyouneedisblog.freehostia.com|64.72.119.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 172 [text/plain]

100%[====================================================================================================>] 172           --.--K/s             

14:30:11 (20.50 MB/s) - `Skype-1.4.0.desktop' saved [172/172]




```

---

### Post by Cappy on 2007-08-04
This script is out of date, it installs the proper libraries but does not install skype (which is the reason for all those errors).
See: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by nickdjones on 2007-08-04
hm, it's definitely worked, as Skype is running, 1.4.0.94, but there's a high probability that the only reason why is the setup was done by your script, and this one just installed QT4 libs in the right place... would love to have the knowledge to clean out both installs and start again, to know for sure.. thanks!

---

