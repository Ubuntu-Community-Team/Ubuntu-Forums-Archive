---
title: "HOWTO: Hoary After-Install Helper"
date: 2005-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Nis on 2005-03-30
In the tradition of the WAIH (Warty After-Install Helper) the HAIH (Hoary After-Install Helper) has arrived.  Or at least a rough version of it. ;)  The HAIH is very similar to ubuntu-geek's [automation script](http://www.ubuntuforums.org/showthread.php?t=22646&page=1&pp=10) but with a different philosophy: the HAIH is a simple GUI designed for new users to Ubuntu and Linux in general that will install certain applications and libraries.  It's main focus to enable support for things users are used to while using other operating systems, namely Java, Flash, MP3, DVD, and embedded video.  Here's what's done so far:
[list]
[*]Flash installation
[*]Java installation
[*]Embedded web media
[*]DVD support
[*]MP3 playing support
[*]MS core font install
[/list]
I'd like  to add MP3 encoding support eventually but that will have to be added to ubuntu-backports (which the HAIH uses extensively).  Hope some people find this useful. :)

Attached is the script.  Download it and run it with the following commands:
```

bunzip2 haih-0.8.bz2
./haih-0.8

```

Let me know of any bugs. :)

---

### Post by helmoltz on 2005-03-30
Script don't work 

rroot@Mitac-6120N:/home/gibbs/Stardict # bunzip2 haih-0.1.bz2
root@Mitac-6120N:/home/gibbs/Stardict # ./haih
-su: ./haih: No such file or directory
root@Mitac-6120N:/home/gibbs/Stardict # ls
haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # ./haih-0.1
-su: ./haih-0.1: Permission denied
root@Mitac-6120N:/home/gibbs/Stardict # ls -l total 4
-rw-r--r--  1 gibbs gibbs 3109 Mar 30 08:12 haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # chmod 774 haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # ls -l
total 4
-rwxrwxr--  1 gibbs gibbs 3109 Mar 30 08:12 haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # ./haih-0.1
Syntax error
oot@Mitac-6120N:/home/gibbs/Stardict # bunzip2 haih-0.1.bz2
root@Mitac-6120N:/home/gibbs/Stardict # ./haih
-su: ./haih: No such file or directory
root@Mitac-6120N:/home/gibbs/Stardict # ls
haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # ./haih-0.1
-su: ./haih-0.1: Permission denied
root@Mitac-6120N:/home/gibbs/Stardict # ls -l total 4
-rw-r--r--  1 gibbs gibbs 3109 Mar 30 08:12 haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # chmod 774 haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # ls -l
total 4
-rwxrwxr--  1 gibbs gibbs 3109 Mar 30 08:12 haih-0.1
root@Mitac-6120N:/home/gibbs/Stardict # ./haih-0.1
Syntax error
-----------------------------------------------------------------------------------------------------------------------

WHY?
Thanks.

---

### Post by b3nw on 2005-03-30
a) errors because you didn't run the proggy as root.

b) very cool proggy :)

---

### Post by ubuntu_demon on 2005-03-30
you made a little mistake :)

```

bunzip2 haih-0.1.bz
sudo chmod +x haih-0.1
sudo ./haih-0.1

```

It's nice. But it has to communicate to the user what is happening. Only when I clicked "web media" the word mozplugger was on the screen in a flash. Nothing got installed but it could be that I had everything already. Just helping improving/debugging :)

I'm more of a commandline user regarding installing packagages. But I know newbies aren't. So this is a very good development!

I have one question though :
Why are you talking about hoary backports (hoary-extras)?  nothing from hoary-extras gets installed for me.

Besides new users shouldn't be troubled by hoary-extras and hoary-backports at this point in time. Everything they need they can find in main universe multiverse marillat and maybe this one :

```

deb http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/ ./

```

or is hoary-extras going to make marillat unnecessary ?

---

### Post by Nis on 2005-03-30
If I understand jdong's intentions everything this script will try to get will be in hoary-extras.  Sun's JRE, w32codecs, and libdvdcss2 are already there.  Combine that with Flash, totem-xine, and mozplugger from universe and multiverse and a user has everything needed for most web browsing.  The WAIH used marillat for mplayer and mplayerplug-in, but since things change there it was really difficult to keep the script up to date and make sure everything was working.  That and mixing in marillat caused problems without proper pinning.

As for user feedback, there is feedback if you do not have the programs already installed.  Synaptic is used to download and install the stuff much like the update-manager does.  The flash for mozplugger is a zenity progress bar (I couldn't avoid it completely) that downloads a mozpluggerrc that works for totem-xine.

As for the problems mentioned above, I'll fix them and post a new version.

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=Nis]If I understand jdong's intentions everything this script will try to get will be in hoary-extras.  Sun's JRE, w32codecs, and libdvdcss2 are already there.  Combine that with Flash, totem-xine, and mozplugger from universe and multiverse and a user has everything needed for most web browsing.  The WAIH used marillat for mplayer and mplayerplug-in, but since things change there it was really difficult to keep the script up to date and make sure everything was working.  That and mixing in marillat caused problems without proper pinning.

As for user feedback, there is feedback if you do not have the programs already installed.  Synaptic is used to download and install the stuff much like the update-manager does.  The flash for mozplugger is a zenity progress bar (I couldn't avoid it completely) that downloads a mozpluggerrc that works for totem-xine.

As for the problems mentioned above, I'll fix them and post a new version.[/QUOTE]
 I've never had problems with marillat. I don't use mplayer because I prefer totem-xine and xine.

---

### Post by Nis on 2005-04-04
The HAIH has come a long way since version 0.1.  The past releases have fixed some stupid bugs on my part (like misspelling the gstreamer0.8-mad package name) and added some notification area action to let the user know when something has finished.  The latest release has tightened this notification up some more and things appear to be working very smoothly.

I need to stress that this script is designed to work on fresh installs of Hoary, or at least machines that have only grabbed stuff from the main Ubuntu repos and Ubuntu backport repos.  If you've already mixed in marillat or some other repos then the HAIH might appear to not be working.  Fear not!  It just won't install some packages (like w32codecs) because you've already got it from somewhere else.

I hope to add MP3 encoding support (this depends on whether gstreamer0.8-lame makes it into hoary-extras on Ubuntu backports).  Anybody else got any suggestions for good candidates to a fresh (or almost fresh) Hoary install?  I'll consider any and all suggestions and those that fit the philosophy I'll add.  I'll point out that all candidates must come from official Ubuntu repos or Ubuntu backports and must have some immediate usefulness to a new install.  For example, DVD support is something often requested after first installing while games are not (not that there is anything wrong with games, particularly nethack :)).

Now on to the next phase: smart attempts at installation! :)

---

### Post by Nis on 2005-04-04
A couple quick tests and changes and now the HAIH (version 0.6) will pop up an info box informing you if you try to install something you've already got installed.  This way the user should only try to install things he or she have not installed previously and makes the script a little more informative.  This should cause less confusion over what the script is doing and will put less icons into the notification area.

---

### Post by Nis on 2005-04-04
Oops!  I've done something to make this stop working. :(   I'll try to get a fix up soon.

---

### Post by Nis on 2005-04-04
Now it works.  Just some wrong grepping but now everything is okay.

---

### Post by UbuWu on 2005-04-07
A little bug: I have the following line in my sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

And when I start the haih, it adds 2 more seperate lines for universe and multiverse... and the same for the security repo.

---

### Post by sb73542 on 2005-04-07
Very nice script, I've been hoping for something like this for months!  Thanks!

---

### Post by j_baer on 2005-04-07
Nis,

Good job on the script. I haven't tested it as of yet but I've been reviewing the code and it should work well. Here are my first thoughts.

- Should add ms core fonts.

- I'm sure the firefox enhancement script is something everyone will want.

For those who have nVidia/ATI cards they will want to add these drivers.

Thanks,

j baer

---

### Post by Nis on 2005-04-07
[QUOTE=j_baer]Nis,

Good job on the script. I haven't tested it as of yet but I've been reviewing the code and it should work well. Here are my first thoughts.

- Should add ms core fonts.

- I'm sure the firefox enhancement script is something everyone will want.

For those who have nVidia/ATI cards they will want to add these drivers.

Thanks,

j baer[/QUOTE]
 The corefonts and nvidia drivers are easy adds so those will go into the next version.  I don't have an ATI card so I'm not sure how easy/difficult that will be.  I had ATI instructions in the WAIH but I never knew if they worked correctly or not.  I'll see what I can do.

What is this Firefox enhancement script?  I'll do a search for it and if it is really cool and helpful then it can certainly go in.

Thanks for your suggestions. :)

---

### Post by Nis on 2005-04-07
Version 0.8 now supports installing the MS core fonts and NVIDIA drivers.  I've got some instructions to install the ATI drivers but I am unable to test them.  If you can, please test and let me know of any problems.  Thanks. :)

---

### Post by Riggs on 2005-04-08
I'm sure it's just me, but here's what I'm getting now:

Package `flashplayer-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `flashplayer-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `sun-j2re1.5' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `sun-j2re1.5' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `msttcorefonts' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `msttcorefonts' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

That happens no matter what I select, and it tells me that the package is already installed.  What am I doing wrong?

---

### Post by Nis on 2005-04-08
[QUOTE=Riggs]I'm sure it's just me, but here's what I'm getting now:

Package `flashplayer-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `flashplayer-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `sun-j2re1.5' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `sun-j2re1.5' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `msttcorefonts' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Package `msttcorefonts' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

That happens no matter what I select, and it tells me that the package is already installed.  What am I doing wrong?[/QUOTE]
 I thought I had fixed that problem.  I'll look into it and try to make a release sometime soon.  Thanks for pointing this out.

---

### Post by la-karaviro on 2005-04-08
i used your 0.7 script, thank you very much,
where do you have 0.8, or isnt that nececair?

i just went away of gentoo, it was a great distri, but i have enough of working on the system wile other working WITH the system :)
so i got bloody user now, and thank you to let me be that, thank you for your help and work

---

### Post by sb73542 on 2005-04-08
Hello,

Thanks again for putting this thing together.  One (big) request: would it be possible to do a fresh Hoary install, run this script, and then burn the apt catch to an .iso for easy downloading?  We've been discussing that on this thread: [http://www.ubuntuforums.org/showthread.php?p=119307](http://www.ubuntuforums.org/showthread.php?p=119307) .  
In general, dialup users have to borrow a friend's computer or order a CD from a cheap online retailer, and it's just plain impossible to download all the packages and their dependancies by hand.  Thanks for the help!

---

### Post by angrykeyboarder on 2005-04-08
> **Nis]In the tradition of the WAIH (Warty After-Install Helper) the HAIH (Hoary After-Install Helper) has arrived. Or at least a rough version of it.  said:**
> automation script[/url] but with a different philosophy: the HAIH is a simple GUI designed for new users to Ubuntu and Linux in general that will install certain applications and libraries. It's main focus to enable support for things users are used to while using other operating systems, namely Java, Flash, MP3, DVD, and embedded video. Here's what's done so far:


[list]
[*]Flash installation
[*]Java installation
[*]Embedded web media
[*]DVD support
[*]MP3 playing support
[/list]I'd like to add MP3 encoding support eventually but that will have to be added to ubuntu-backports (which the HAIH uses extensively). Hope some people find this useful. :)

Attached is the script.  Download it and run it with the following commands:
```

bunzip2 haih-0.7.bz2
./haih-0.7

```

Let me know of any bugs. :)

 
I just attempted to use your latest (0.7) and got errors when it came to installing Java and Flash. Also it didn't recognize that I already had some of the entries it was trying to add to my apt sources.list (so now I have duplicates).

 
And lastly, I'd have sworn there was a Gstreamer plugin for DVD playback. If so that could have been used in place of totem-xine.

---

### Post by Tomcat_ on 2005-04-09
Great script! Really like it! :D

---

### Post by weichsel on 2005-04-10
Java and Flash fails. But the rest works great 
Hoary on AMD64

---

### Post by j_baer on 2005-04-10
Nis,

I ran the script of the release copy of Hoary. The only problem I had was the win32 codecs did not install. I was able to do that separately and everything worked great.

Thanks ...

---

### Post by j_baer on 2005-04-10
Nis,

The firefox enhancement was posted by Ubuntu-geek.

[http://www.ubuntuforums.org/showthread.php?t=22034&highlight=firefox+forms](http://www.ubuntuforums.org/showthread.php?t=22034&highlight=firefox+forms)

Thanks ...

---

### Post by Nis on 2005-04-10
Lots of things to respond to:

I'm not sure how well this script will work on AMD64.  I made this on a x86 and that's all I've ever had.  Flash is gotten from multiverse so there might be an AMD64 version but I'm not sure.  Java is from hoary-extras on Ubuntu backports so jdong will have to clue us in on whether there is an AMD64 deb for Java.

j_baer: How exactly did the w32codecs install fail?  Were there any messages outputted to the terminal?  I'll check the code for any stupid spelling mistakes that I often make. :)

version 0.8 apparently has some problems I thought I had fixed so I'll work on it and hopefully get it working.  I'll also see if I can prevent duplicate entries being put in /etc/apt/sources.list.  Right now the script assumes the user has not added any repositories to sources.list.

gstreamer DVD playback is not fully featured enough for most users while xine is.  Mostly, totem-gstreamer cannot handle DVD menus yet.  Also, totem-gstreamer will not play most formats that are streamed over the web, such as Quicktime at [www.apple.com/trailers/](www.apple.com/trailers/)  Until gstreamer-ffmpeg (which does most of the work for Quicktime, WMV, and such) becomes more realized, totem-xine will have to replace totem-gstreamer.

I think CD burning is out of the scope for the HAIH, but maybe another project could be made to burn the apt-cache.  If one has already started then maybe I'll look into doing some simple work for it.

---

### Post by sb73542 on 2005-04-11
Thanks, Nis, for your hard work and consideration!  

There is currently no official project to distribute a CD of all these necessary files.  Ubuntu will probably never officially initiate one either, as they do not encourage non-free software.  But they would probably help out someone who wanted to host it elsewhere.  Unfortuanately there is no other option for dialup users.  Maybe you could get with someone at:
[http://www.ubuntuforums.org/showthread.php?p=119307](http://www.ubuntuforums.org/showthread.php?p=119307)  or
[http://ubuntuforums.org/showthread.php?t=24402](http://ubuntuforums.org/showthread.php?t=24402)

By the way, did you know that there is now Adobe Reader 7 for Linux?  Not very publicized, but get it here: [ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/](ftp://ftp.adobe.com/pub/adobe/reader/unix/7x/7.0/enu/)

Thanks again!

---

### Post by Nis on 2005-04-11
I just uploaded version 0.8.  The changes I made were pretty small instead of being as huge as I thought.  MS core fonts install was added and some stupid spelling mistakes on my part were fixed.  Overall the script works pretty well. :)

If you've already got universe and/or multiverse enabled then the problem of duplicate entries in /etc/apt/sources.list still exists.  I'm working on fixing this but until then the workaround is manual removal of any duplicate repositories in /etc/apt/sources.list.  I must stress that this script is designed to be run before any repositories are added (as most brand new Ubuntu users will not add any repositories until told to do so).

---

### Post by xjimtx on 2005-04-12
I had most of the files already installed but used your script to fill in the blanks and get the plugins set up for firefox. unfortunitly neither totem or xine get any audio while playing dvds. Did a test ofthe plugins with quicktime movies over at apple.com, no audio from those either. No audio from mp3s in totem now also  

Jim

---

### Post by j_baer on 2005-04-12
xjimtx,

I am guessing your problem is the win32 codecs didn't install ...

j baer

---

### Post by kuleali on 2005-04-12
Nice, Pleas add some more programms in the future

---

### Post by Nis on 2005-04-12
[QUOTE=kuleali]Nice, Pleas add some more programms in the future[/QUOTE]
 Which ones would you like to see?  Remember, any applications that the HAIH installs should be 1) available in universe, multiverse, or Ubuntu backports; and 2) should be something that is commonly asked for by other users coming from a different OS background.

There's also another qualification I use to gauge whether to include something and that is the ratio of usefulness to complexity in practice.  This is very subjective on my part (and shouldn't really matter), but some things are just too difficult to implement cleanly.  The NVIDIA and ATI drivers, for example, while useful to most people, editing /etc/X11/xorg.conf in a safe way that doesn't mess anything up was too difficult to do.  In reality major configuration changes like the example above should really be done by the user since there is a possibility of doing things wrong in an automated script.

---

### Post by Nis on 2005-04-12
[QUOTE=xjimtx]I had most of the files already installed but used your script to fill in the blanks and get the plugins set up for firefox. unfortunitly neither totem or xine get any audio while playing dvds. Did a test ofthe plugins with quicktime movies over at apple.com, no audio from those either. No audio from mp3s in totem now also  

Jim[/QUOTE]
 For a little while I was worried something had gone wrong.  But the latest version has installed totem-xine, mozplugger, and w32codecs with no problem.  I was getting what you were describing though: no sound on apple.com trailers.  I then ran totem from the command line and sent a URL with the Fantastic Four trailer and I got sound no problem.  I then watched that trailer embedded in Mozilla and got sound this time.  I'm not sure why I needed to run totem once externally to get sound for Quicktime but I guess it's a workaround.  My only guess is that something in totem-xine or libxine is not picking up changes unless totem is called independently of mozplugger.

---

### Post by xjimtx on 2005-04-12
J Baer
I might try a new install and run this script from the start, before i ran this script everything was working but plugins for firefox. Since this is my first try with Ubuntu I was using the info from [http://ubuntuguide.org/](http://ubuntuguide.org/) 

Jim

---

### Post by coughcool on 2005-04-12
> **Nis]In the tradition of the WAIH (Warty After-Install Helper) the HAIH (Hoary After-Install Helper) has arrived.  Or at least a rough version of it.  said:**
> automation script[/url] but with a different philosophy: the HAIH is a simple GUI designed for new users to Ubuntu and Linux in general that will install certain applications and libraries.  It's main focus to enable support for things users are used to while using other operating systems, namely Java, Flash, MP3, DVD, and embedded video.  Here's what's done so far:
[list]
[*]Flash installation
[*]Java installation
[*]Embedded web media
[*]DVD support
[*]MP3 playing support
[*]MS core font install
[/list]
I'd like  to add MP3 encoding support eventually but that will have to be added to ubuntu-backports (which the HAIH uses extensively).  Hope some people find this useful. :)

Attached is the script.  Download it and run it with the following commands:
```

bunzip2 haih-0.8.bz2
./haih-0.8

```

Let me know of any bugs. :)


Thanks this worked great! now I just need to get .ogm video working.

---

### Post by Toastermax on 2005-04-12
i cant get it to work. i guess i have to figure it out. its not exactly newbie proof.

---

### Post by Nis on 2005-04-12
[QUOTE=Toastermax]i cant get it to work. i guess i have to figure it out. its not exactly newbie proof.[/QUOTE]
 Are you getting any errors?  What is the exact sequence you're using?  I've tried to make it as newbie-proof as possible.

---

### Post by Toastermax on 2005-04-12
i download the fonts to my home/username folder and then i open a root terminal and run bunzip2 haih-0.8.bz2
./haih-0.8

and it cant find file.the actual error " bunzip2: Can't open input file haih-0.8.bz2: No such file or directory.
"

---

### Post by Nis on 2005-04-12
[QUOTE=Toastermax]i download the fonts to my home/username folder and then i open a root terminal and run bunzip2 haih-0.8.bz2
./haih-0.8

and it cant find file.the actual error " bunzip2: Can't open input file haih-0.8.bz2: No such file or directory.
"[/QUOTE]
 Try running it as a normal user.  Most new users don't know about running things as root so the script should prompt you for your password (using gksudo).

---

### Post by Toastermax on 2005-04-12
[QUOTE=Nis]Try running it as a normal user.  Most new users don't know about running things as root so the script should prompt you for your password (using gksudo).[/QUOTE]

same thing again  " bunzip2: Can't open input file haih-0.8.bz2: No such file or directory."

please be specific, i should go to applications-->system tools--> terminal 

and then i can paste this line "bunzip2 haih-0.8.bz2"

is this correct so far?

---

### Post by Nis on 2005-04-12
Here's some more involved instructions:
Download [this file](http://www.ubuntuforums.org/attachment.php?attachmentid=743) to your home directory (~).
Do the following and report back if it worked:
```

bunzip2 ~/haih-0.8.bz2 && sh ~/haih-0.8

```

---

### Post by fire59 on 2005-04-12
This doesn't work for kubuntu.  Can someone list all the packages name so I can manually install them through apt?

---

### Post by Toastermax on 2005-04-12
[QUOTE=Nis]Here's some more involved instructions:
Download [this file](http://www.ubuntuforums.org/attachment.php?attachmentid=743) to your home directory (~).
Do the following and report back if it worked:
```

bunzip2 ~/haih-0.8.bz2 && sh ~/haih-0.8

```[/QUOTE]
i think it worked. it asked for a password and then it seems to have worked. what should i look for to confirm?

---

### Post by Nis on 2005-04-12
[QUOTE=Toastermax]i think it worked. it asked for a password and then it seems to have worked. what should i look for to confirm?[/QUOTE]
 If you get a dialog box with mutliple options then it has worked.  Now you can choose what you'd like to install.

---

### Post by mohaham on 2005-04-12
great job...
keep up the good work..
thanks

---

### Post by Toastermax on 2005-04-13
[QUOTE=Nis]If you get a dialog box with mutliple options then it has worked.  Now you can choose what you'd like to install.[/QUOTE]
i did not get that. it just sort of stopped.

---

### Post by michealm on 2005-04-13
im getting the following error:
Failed to run ./haih-0.8:
Child terminated with 1 status

---

### Post by Nis on 2005-04-13
[QUOTE=michealm]im getting the following error:
Failed to run ./haih-0.8:
Child terminated with 1 status[/QUOTE]
 Alright.  Try this:
```

sudo ~/haih-0.8

```

---

### Post by michealm on 2005-04-13
[QUOTE=Nis]Alright.  Try this:
```

sudo ~/haih-0.8

```[/QUOTE]
 still nothing i get the following:
sudo: ./haih-0.8sudo: micheal@1x-xxx-xxx-xxx:~$ ./haih-0.8
bash: ./haih-0.8: Permission denied

---

### Post by Nis on 2005-04-13
[QUOTE=michealm]still nothing i get the following:
sudo: ./haih-0.8sudo: micheal@1x-xxx-xxx-xxx:~$ ./haih-0.8
bash: ./haih-0.8: Permission denied[/QUOTE]
 How about this?
```

chmod +x ~/haih-0.8
sudo ~/haih-0.8

```

---

### Post by devil28 on 2005-04-13
just tried your script under kubuntu 5.05 amd64 and it messed up my whole sources.lst. maybe this is no good for amd64. if kubuntu, you will have to install synaptic first

---

### Post by simianMiscreant on 2005-04-13
very nice work man, thanks a lot

---

### Post by davegod75 on 2005-04-13
[QUOTE=simianMiscreant]very nice work man, thanks a lot[/QUOTE]
 i'm getting radio buttons for selecting the things i want to install...shouldn't they be check boxes?

also, after unzipping the program is not executable by default..It probably should be given your instructions

---

### Post by Nis on 2005-04-13
[QUOTE=davegod75]i'm getting radio buttons for selecting the things i want to install...shouldn't they be check boxes?

also, after unzipping the program is executable by default..I probably should be given your instructions[/QUOTE]
 I'm thinking about doing checkboxes for the next version.  Right now it was easier to just do radio buttons.

I'm not sure what your second phrase means.  Is the file not executable after 'bunzip2 haih-0.8.bz2'?

---

### Post by davegod75 on 2005-04-13
[QUOTE=Nis]I'm thinking about doing checkboxes for the next version.  Right now it was easier to just do radio buttons.

I'm not sure what your second phrase means.  Is the file not executable after 'bunzip2 haih-0.8.bz2'?[/QUOTE]
 correct....i had to do a chmod +x on it

---

### Post by Random Destruction on 2005-04-13
I had to chmod +x it as well, plus once i did:


```
random@moshi:~$ ./haih-0.8 
./haih-0.8: line 199: gksudo: command not found
```

```
random@moshi:~$ sudo ./haih-0.8 
./haih-0.8: line 132: zenity: command not found
```

Though I'm sure its grand ;)

---

### Post by Wardhog on 2005-04-13
Brilliant work.  Thanks heaps.

You've let me relegate Windows into the 'sometimes booted' OS on my system, and leave Ubuntu as the default OS in grub.

---

### Post by Nis on 2005-04-13
[QUOTE=Random Destruction]I had to chmod +x it as well, plus once i did:


```
random@moshi:~$ ./haih-0.8 
./haih-0.8: line 199: gksudo: command not found
```

```
random@moshi:~$ sudo ./haih-0.8 
./haih-0.8: line 132: zenity: command not found
```

Though I'm sure its grand ;)[/QUOTE]
 Are you using Kubuntu?  gksudo and zenity are things that come in GNOME Ubuntu.

---

### Post by lykoszine on 2005-04-14
Nis,

Great script, cheers for that. I read that it includes NVIDIA drivers, but they don't seem to be there?

I also can't seem to select multiple options, and have had to install the things 1 at a time, any chance of an 'install all the above' check box?

Lastly, could you include unrar for .rar archive support?

Thanks loads!

---

### Post by loom001 on 2005-04-17
This is a great script thanks so much!  It has saved me a ton of time.


Thanks again!

---

### Post by Bug on 2005-04-18
[QUOTE=loom001]This is a great script thanks so much!  It has saved me a ton of time.


Thanks again![/QUOTE]
 Thanks, this is great, wish I found it when I first started messing around with ubuntu.

Adam

---

### Post by lionel47 on 2005-04-23
I get the following errors when I run that script:

"W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)"

Can anyone help?

---

### Post by XplOzIOn on 2005-04-23
well backports server seems down or something. Im getting same error. and some of the apps seems to come from there.. So i dunno

---

### Post by KroniX on 2005-04-23
doesnt do anything when sh'd.

---

### Post by piggyaugu on 2005-05-05
works great \\:D/ thx

well, that will be better if the list can be a check-list, i mean cheking several item at one time. that will be perfect. go on!!

---

### Post by evermind on 2005-05-30
here my own script which I run on an newly installed system


[http://ubuntuforums.org/showthread.php?p=187304](http://ubuntuforums.org/showthread.php?p=187304)

---

### Post by cjavier on 2005-07-05
The repository at [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) is not avaible for every body, so I think haih should point to one of the mirrors.

Great thing this script

Thank you

---

### Post by Julian David Pitt on 2005-08-03
[QUOTE=Nis]

Attached is the script.  Download it and run it with the following commands:
```

bunzip2 haih-0.8.bz2
./haih-0.8

```

Let me know of any bugs. :)[/QUOTE]
[COLOR=Blue]**Please tell me where I am going wrong here**[/COLOR]

root@ubuntu:/home/julian # bunzip2 haih-0.8.bz2
bunzip2: Output file haih-0.8 already exists.
root@ubuntu:/home/julian # chmod +x haih-0.8.bz2
root@ubuntu:/home/julian # ./haih-0.8
bash: ./haih-0.8: Permission denied
root@ubuntu:/home/julian #

Many thanks people

---

### Post by evermind on 2005-08-08
[QUOTE=Julian David Pitt][COLOR=Blue]**Please tell me where I am going wrong here**[/COLOR]

root@ubuntu:/home/julian # bunzip2 haih-0.8.bz2
bunzip2: Output file haih-0.8 already exists.
root@ubuntu:/home/julian # chmod +x haih-0.8.bz2
root@ubuntu:/home/julian # ./haih-0.8
bash: ./haih-0.8: Permission denied
root@ubuntu:/home/julian #

Many thanks people[/QUOTE]


you have to chmod the unpacked script not the packed archive
chmod +x haih-0.8
and then execute it
./haih-0.8

---

### Post by munchkina on 2005-08-15
**am newbie.**
this is probably a _**small thing**_, but I don't know what to do   ](*,)   and need somebody to tell me where to fix this, please.
When I run ./haih-0.8 I get the following:

[http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 401 Authorization Required

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Downloading and running HAIH-0.8 is the first thing I did after reinstalling UBUNTU (had same trouble before). So what do I do now?   :-s

---

### Post by munchkina on 2005-08-18
Problem was solved in another thread by heimo sharing his knowledge   :-) 


Read this:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

You need to change your sources.list to use mirrors.

---

### Post by angrykeyboarder on 2005-08-18
[QUOTE=Nis]I'd like to add MP3 encoding support eventually but that will have to be added to ubuntu-backports (which the HAIH uses extensively). Hope some people find this useful. :)
 
Let me know of any bugs. :)[/QUOTE]

 
My first exposure to Ubuntu was with Hoary so I have no Warty experience. Are you saying that warty backports includes support for MP3 encoding but Hoary doesn't?

 
Actually mp3 support in Hoary exists, but indirectly. It's it's via the hoary-extras archive (maintained by the same folks to maintain hoary-backports).

 
e.g.:


 [http://ubuntu-backports.mirrormax.net]("http://ubuntu-backports.mirrormax.net/") hoary-extras main restricted universe

 
or


 [http://public.planetmirror.com/pub/ubuntu-backports]("http://public.planetmirror.com/pub/ubuntu-backports/") hoary-extras main restricted universe
 
or

 
[http://acm.cs.umn.edu/ubp]("http://acm.cs.umn.edu/ubp/") hoary-extras main restricted universe

---

