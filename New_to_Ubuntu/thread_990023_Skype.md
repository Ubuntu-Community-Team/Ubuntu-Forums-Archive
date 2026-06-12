---
title: "Skype"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by JimHebert on 2008-11-22
Hi:
I am brand new at using Linux. I decided to do a Wubi download since it  seemed the easiest. I like it. Just a bit difficult at first to get used to Ubuntu.  

I tried to download Skype from this site:

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

I clicked on    Ubuntu 7.04-8.04    and downloaded to desktop. 

I double clicked and a window opened with title Skype-2.0.0.72.tar.bz2

I clicked on open.  Another window opened with 5 folders in the right 
&#65279;panel. I  don't know what to do at this point. I don't see anything that looks like an application icon anywhere. I don't know how to put a shortcut quicklaunch tray on top of desk top.  Is there a path where I might find the Skype folder with the application and try to make a shortcut? I don't the words "create shortcut" anywhere. Thanks

---

### Post by zzHanks on 2008-11-22
I'm assuming that your computer is 64-bit, if the .deb file from the website does not work.

Try this: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by JimHebert on 2008-11-22
It's a brand new Acer Aspire 7720-6794 laptop. I think I saw 32 bit in "My computer" or someplace when I was using Vista. I don't know how to check it on Ubuntu. Sorry, it's all so new to me.










when I double click on the download on the desktop, I get an error "wrong architecture i386.

---

### Post by zzHanks on 2008-11-22
> **JimHebert said:**
> when I double click on the download on the desktop, I get an error "wrong architecture i386.
Then the link I posted will probably work. (You have 64-bit)

Good luck.

---

### Post by Kosimo on 2008-11-22
> **JimHebert said:**
> Hi:
I am brand new at using Linux. I decided to do a Wubi download since it  seemed the easiest. I like it. Just a bit difficult at first to get used to Ubuntu.  

I tried to download Skype from this site:

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

I clicked on    Ubuntu 7.04-8.04    and downloaded to desktop. 

I double clicked and a window opened with title Skype-2.0.0.72.tar.bz2

I clicked on open.  Another window opened with 5 folders in the right 
&#65279;panel. I  don't know what to do at this point. I don't see anything that looks like an application icon anywhere. I don't know how to put a shortcut quicklaunch tray on top of desk top.  Is there a path where I might find the Skype folder with the application and try to make a shortcut? I don't the words "create shortcut" anywhere. Thanks

But...
Why you didn't download the .deb version?

If you get the .deb version you will install skype by double click to that file easily and quickly.

---

### Post by buyyourall3 on 2008-11-22
[size=5]there are lots of [/size][**[size=5]chinese mobile phones[/size]**](http://www.buyyourall.com)[size=5] are very cool,such as [/size][**[size=5]spy watch mobile phone[/size]**](http://www.buyyourall.com)[size=5]  , it is a mobile phone and a watch . the picture is below .[/size][[img]http://www.buyyourall.com/syssite/home/shop/1/pictures/newsimg/1226099832.jpg[/img]](http://www.buyyourall.com/1180_007-spy-watch-mobile-phone.html)

---

### Post by grainbarcelona on 2008-11-22
When I dowloaded the file from the site you indicated, I got the following file on my desktop: skype-debian_2.0.0.72-1_i386.deb When I clicked on it, it started installing skype on my ubuntu.

Files with .deb extenstions should start installing when you double click on them. Perhaps you could check whether you have the 'gdebi package installer' installed in your ubuntu? (check under 'applications' --> add remove.)

---

### Post by JimHebert on 2008-11-22
Do you know what that error "wrong architecture i386" means. I don't see anything relating to that particular error on the link you sent that leads to this link

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by JimHebert on 2008-11-22
To Kosimo:

Whtheen I doubleclick on the download I get error "wrong architecture i386"

---

### Post by Kosimo on 2008-11-22
> **JimHebert said:**
> To Kosimo:

Whtheen I doubleclick on the download I get error "wrong architecture i386"

Ok then you probably have a 64Bit Ubuntu. Then you can do two things.
If you really don't need a 64bit architecture, you can download and install 32bit ubuntu witch will work fine for almost any single need you probably have and you can easily install many other apps
If you want to keep using 64bit for any reason, then there is a way to install skype:  Just follow this [link]("http://ubuntuforums.org/showthread.php?t=432295")

Hope it helps

---

### Post by lswest on 2008-11-22
you can install skype from the medibuntu repository.

follow the instructions on adding the repository here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) (not sure which Ubuntu version you have installed - probably 8.10 though), run the command at the end > sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update and install skype with ```
sudo apt-get install skype
``` it should be a lot easier for you.  It'll also update skype automatically then.

However, I don't know if it offers the 64 bit package (seems like it does).

---

### Post by zzHanks on 2008-11-22
> **JimHebert said:**
> Do you know what that error "wrong architecture i386" means. I don't see anything relating to that particular error on the link you sent that leads to this link

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

Scroll down to the Ubuntu version you are using and paste the code in Terminal (Applications > Accessories > Terminal).

---

### Post by JimHebert on 2008-11-22
To Iswest:

Not sure what you mean "run the command at the end "? You mean copy and paste the command in Applications, Terminal?

---

### Post by lswest on 2008-11-22
> **JimHebert said:**
> To **l**swest:

Not sure what you mean "run the command at the end "? You mean copy and paste the command in Applications, Terminal?

first off, it's an L not an I :P but yeah, just copy and paste the commands listed for the version of ubuntu you have installed into the terminal, then run the command I quoted afterwards (it's not especially clear you have to do both).

---

### Post by JimHebert on 2008-11-22
I copy and pasted  "sudo apt-get install skype". It said this "E: Couldn't find package skype"

---

### Post by lswest on 2008-11-22
> **JimHebert said:**
> I copy and pasted  "sudo apt-get install skype". It said this "E: Couldn't find package skype"

did you do all the steps before-hand?

> Ubuntu 8.10 "Intrepid Ibex":

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

if you're not sure what release you have, run ```
lsb_release -a
``` in the terminal, and choose the right command from the list in the link I posted above.

> Then, add the GPG Key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

and then, only then, ```
sudo apt-get install skype
```

---

### Post by JimHebert on 2008-11-22
I completed all the steps including "sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update".

Now at the end of all that was downloaded, I read WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]?e way
 
Before going any farther, do I answer yse or no?

By the way, it is 8.1 version that I have.

---

### Post by lswest on 2008-11-22
type in "y" (without the quotes) and continue.  it's because it's not an "official" ubuntu repository, but I vouch for it :P

---

### Post by JimHebert on 2008-11-22
I've completed the last step "sudo apt-get install skype" of your post #15 and a whole slew of stuff downloaded. It looks good.  What should I do now?

---

### Post by lswest on 2008-11-22
once it's done, just hit alt + F2 and type "skype" it should start then.  It can also be found under Applications-->Internet-->Skype.

Glad I could help (and if you want, you can hit the red medal at the bottom of the post that helped you and "thank" me that way).

Lswest

Also, the reason it didn't work the way you were doing it was because you'd have to compile the program yourself, and re-compile with every update.  Linux offers repositories (servers with packages compiled for easy installation for certain distributions) that make installing programs easy.  If the program doesn't exist in the repository, checking [www.getdeb.net](www.getdeb.net) will probably help.  .Deb files are debian-specific (e.g. based off Debian, like Ubuntu is) packages that install a pre-compiled version of the program, saving you the hassle (also, download these if you need to download a program from a site, not tar.gz files, since those are the complicated ones).  You can also easily keep track of what's installed then.  Commands to know are:
```
sudo apt-cache search *searchterm*
sudo apt-get install *packagename*
sudo apt-get upgrade
``` where searchterm are your search terms, and packagename is the actual name of the package (usually found using the "apt-cache sarch" command if the program exists in the repositories).

Just thought I'd add to the stuff you learned so you can better understand why we did it this way.

---

### Post by JimHebert on 2008-11-22
One minor problem still exists.  I don't see the normal Test Call Center button in Skype. So I tried to place a call and it said " Problem with audio playback". I went to System, Preferences, Sound, clicked the sound tab, The first 3 sound tests buttons had a tone, but the 4th test for ALSA  Advanced Linux Sound Architecture did not produce any tone.

---

### Post by zzHanks on 2008-11-22
> **JimHebert said:**
> The first 3 sound tests buttons had a tone, but the 4th test for ALSA  Advanced Linux Sound Architecture did not produce any tone.
That's probably the sound capture selection. - There's no tone, you should hear yourself. (If you have a microphone of course)

Have you tried all options?

---

### Post by JimHebert on 2008-11-22
I need to know, for use on the getdeb site, if I definitely have a 64 bit machine. What is the path to determine that?

---

### Post by Kosimo on 2008-11-22
> **JimHebert said:**
> I need to know, for use on the getdeb site, if I definitely have a 64 bit machine. What is the path to determine that?

Go to terminal and type  ```
uname -a
```

---

### Post by lswest on 2008-11-22
check for 64 bit using ```
uname -a
``` it should say amd64 if it's 64 bit in that output.

About the sound, it has nothing to do whatsoever with Skype (in case you were thinking of re-installing), it's got to do with pulseaudio, I believe there are threads on how to fix it here.  Just search the forums for pulseaudio and skype as search terms.

Good luck.

See here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by JimHebert on 2008-11-22
Yes, it is a 64 bit. It said "Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux".

I've just added many settings under System,preferences,volume control. The path I followed was system,preferences, volume control window, I clicked preferences and ticked everything there. Went back to Vol control, playback tab, and maxed out all the levers and muted beep, clicked  recording tab and unmuted capture, clicked options and wrote Internal Mic. Now in the path: system, preferences, sound, click devices, click the 4th button next to sound capture ALSA and I hear a very short burst of static. I'm now going to try that Pulseaudio forum thread from post 24.

To do the pulseaudio routine, I'll need Adobe Flash. Do I download the .deb for ubuntu 8.04+, tar.gz, APT, rpm, or yum?

---

### Post by JimHebert on 2008-11-22
Skype says I need to download "install_flash_player_10_linux.tar-1" but I'm not given that option anywhere on the adobe site at [http://www.adobe.com/shockwave/download/static/Linux/ShockwaveFlash/English.html](http://www.adobe.com/shockwave/download/static/Linux/ShockwaveFlash/English.html)

---

### Post by lswest on 2008-11-22
```
sudo apt-get install ubuntu-restricted-extras
``` should install everything you need.

---

### Post by hankinator on 2008-11-22
```
http://www.skype.com/go/getskype-linux-ubuntu

http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
```

Just Download the .Deb package, it practically auto installs for you, and it should install to the lib32, so it doesn't matter 64, or 32 bit. Also theres flashplayer in a DEB package. its much easier trust me :)

---

### Post by JimHebert on 2008-11-22
To lswest:

I did the code "sudo apt-get install ubuntu-restricted-extras" and at the end of the download a license agreement appears and, excuse my ignorance, but I don't know how to get out of the window. There is "<OK> at the end of the agreement. I pressed "enter" but nothing happened.



After an hour of searching, I found out about the tab button trick.

---

### Post by JimHebert on 2008-11-22
To hankinator: first

Will those 2 code entries you mention in post 28 eliminate the "problem with audio playback" when I try to make a call? I'm about to proceed with the Pulseaudio procedure in the URL mentioned in Post 24. Now I'm not sure which procedure to attempt first.

---

### Post by lswest on 2008-11-23
> **JimHebert said:**
> To lswest:

I did the code "sudo apt-get install ubuntu-restricted-extras" and at the end of the download a license agreement appears and, excuse my ignorance, but I don't know how to get out of the window. There is "<OK> at the end of the agreement. I pressed "enter" but nothing happened.

you would have to hit tab first to select the OK button, then hit enter.  Sorry for the slow response, I was sleeping :P

---

### Post by JimHebert on 2008-11-23
To lswest:

Reference to post 27. I no longer see "problem with audio playback". Now when I click the green phone to make a call, nothing happens.


To hankinator:
No such files exist.

---

### Post by lswest on 2008-11-23
> **JimHebert said:**
> To lswest:

Reference to post 27. I no longer see "problem with audio playback". Now when I click the green phone to make a call, nothing happens.

Have you looked through the thread I posted a link to in post 24?  If you did you'd have seen this: > **Skype:** Open Skype's Options, then go to Sound Devices. You need to set "Sound Out" and "Ringing" to the "pulse" device, and set "Sound In" to the hardware definition of your microphone. For example, my laptop's microphone is defined as "plughw:I82801DBICH4,0".
Try that and see if it works.

---

### Post by JimHebert on 2008-11-23
I went Applications, Internet, Skype. Skype 2.0 Welcome window opens. Entered password. Says "another Skype instance may exist". I clicked on small drop down arrow at lower left and a connection window opens up. Not good.

---

### Post by JimHebert on 2008-11-23
I just went to System, Preferences, sound. None of the test buttons have sound when I press them. Things are getting worse.

---

### Post by JimHebert on 2008-11-23
I need to do a system restore and forget about Skype Linux. Now, I can't listen to music or anything. Is there a way to restore everything to a previous date?
 


After clicking on the sound test buttons, it says failed to connect. Connection refused.

---

