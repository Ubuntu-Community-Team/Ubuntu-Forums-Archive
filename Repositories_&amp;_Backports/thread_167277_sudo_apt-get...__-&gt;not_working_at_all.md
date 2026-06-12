---
title: "sudo apt-get...  -&gt;not working at all"
date: 2006-04-28
forum: Repositories &amp; Backports
---

### Post by penywise on 2006-04-28
Hi all, I wrote in the newbies part of the forum so far...
I installed Ubuntu 5.04 several days ago. Last night I managed to reinstall the whole system...
As for the "update it to 5.10"... here in Bulgaria with the internet speed I have it would take me... few days non-stop downloadin (cool aye?)

So, last night I reinstalled. I follow the [www.ubuntuguide.org](www.ubuntuguide.org) carefully. Of course the first thing to do after the reinstall -> change the repositories, then run the "sudo apt-get update".
Of course I didn't do something all right! I kept on checking the sources.list file, looked it letter by letter, copied, pasted several times, trying everything... No matter - still the same result (I will provide the log file now).

Then I said - "Ah, f**k it, I will try to get some codecs for avi, mpeg, mp3..." and to get something like mplayer.
(the end of the log below is shown on EVERY command that starts with "sudo apt-get".
I can't download, can't update, can't upgrade, can't put new software... nothing

The log:

[HTML]penywise@penywise:~$ sudo gedit /etc/apt/sources.list
penywise@penywise:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary ReleaseIgn cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://security.ubuntu.com hoary-security Release
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://archive.ubuntu.com hoary/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
404 Not Found
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Get:3 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 4B in 16s (0B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ubuntu-backports.mirrormax.ne...86/Packages.gz 404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.ne...86/Packages.gz 404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.ne...86/Packages.gz 404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.ne...86/Packages.gz 404 Not Found
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restric ted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
penywise@penywise:~$[/HTML]

---

### Post by frodon on 2006-04-28
Open your source.list file and remove the line(s) about the CD, because here your source.list file expect you to have the install CD in the drive and it's why you get errors. Just remove this line and it should be good. If you don't know what you do just post here your source.list file.
Don't bother with backport errors these repositories aren't reachable sometimes.
About codecs you will find most of you need here : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by penywise on 2006-04-28
:shock: :idea: 

well... would you look at that ;)
I was always ready to reisntall again...

I will try that as soon as I get back home! Thank a lot!

As for the first reinstall...
I started upgrading to 5.10, but upon asking me I said "N" and closed the Terminal. Then in the "task-bar" right next to the "system clock" there was "process" running, saying that there were like 460 updates... so I started downloading them, but I saw that it would take days (my speed is too slow).

Then I created new user (sudo adduser...).

Then I downloaded some codecs *(sudo apt-get install gstreamer0.8-plugins)*
Then I started the installation...
At some point I got an error message pop-up saying "gnome-volume-manager stopped unexpectedly.." with 3 options available - "restart process, cancel, report to developers" (sth like that). So I canceled...

Rebooted the system after the codecs installation was done (damn Windows habits...)

Upon starting it showed me some error that "X graphical interface could not load"... it asked me if I want to see some information with "Yes", "No" choises... but the keywboard just not worked - no left, right, no up-down, no page-up, etc...

So I reinstalled... I have now idea how the installation of codecs messed up my GUI...

---

### Post by frodon on 2006-04-28
Yes really strange, the GUI shouldn't have something to do with codec installation.

Anyway good luck and feel free to ask as many things as you want.

---

### Post by penywise on 2006-04-28
Well... I changed what I thought I had to change...
No effect again, same "error" in the Terminal is shown...

[COLOR="Red"]##[/COLOR]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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



That's my file... I just put the "##" in the first line and tried to run the update again - no effect](*,)

---

### Post by penywise on 2006-04-28
Ok, I changed the repositories to some bg-mirrors (I am from Bulgaria)...

Still - I can't run ANY sudo apt-get...

[HTML]penywise@penywise:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: mozilla-firefox-locale-en-gb but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
penywise@penywise:~$[/HTML]

---

### Post by frodon on 2006-04-28
You have a missing repository but i don't think it is the problem here, modify these 2 lines : ```
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```by : ```
deb http://security.ubuntu.com/ubuntu hoary-security universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu hoary-security universe **multiverse**
```

---

### Post by penywise on 2006-04-28
No happy end again...

I tried all kinds and types of Repositories, changed them manually as you told me... no happy end...

I can't install anything... just by typing anything in the Terminal wiht "sudo apt-get..." and I see that lovely message I pasted above...

Damn...

Well, soon I will move on Debian, I have a guy to guide me through... besides that is what I will be needing at first place and in the future

But that freakin' message won't let me sleep!

---

### Post by frodon on 2006-04-28
no more luck if you use synaptic (GNOME) or adept (KDE) ?

It seems to be a really small details which generates this problem.

---

### Post by jobezone on 2006-04-28
ubuntuguide.org is no longer updated (or am I wrong?) as you can see it the page, it's for ubuntu Hoary. There is [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu) which is just like ubuntuguide, but for breezy.

---

### Post by Bloch on 2006-04-29
> penywise@penywise:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: mozilla-firefox-locale-en-gb but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
penywise@penywise:~$

Did you try entering
apt-get -f install

It is a big minus for ubuntu if with a clean reinstall and commenting-out of the cd, it doesn't work properly.  Give up on that Hoary installation cd. It WILL work eventually - after days and days But it's making things difficult for yourself. Get the latest cd and easyubuntu will work with it.

I'm just hoping you are not put off ubuntu with all these problems. Nobody will mind you moving to debian - it's still linux :-) but I think you will find Dapper Drake to be a lot easier to get up and running

---

