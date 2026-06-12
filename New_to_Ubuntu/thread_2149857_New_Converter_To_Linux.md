---
title: "New Converter To Linux"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by achilles316 on 2013-05-30
So i have just converted to Lubuntu Linux! As i am sure you know by now, i do have questions lol. Basically, what do i need to know? I have done some reading but i figured it best to ask you veterans out there. Any and all help would be greatly appreciated! Here is what i mostly use my computer for incase it helps to determine what advice to give.

I use it for every day things like checking my email on Yahoo, checking both my Instagram and Facebook and other regular sites like NFL.com and Youtube. I also watch movies either online or those that i have saved on my external hard drive. I also listen to music. 

Some questions i do have of the top of my head are:

1. How do i install things i will need? 
2. Do i need a Antivirus?
3. How do i enable firewall? Any other firewall rules i should know?
4. Truecrypt work with Lubuntu? Do i need to reformat my EHD with the linux version or will it work as it is?
5. Does yahoo messenger work with Lubuntu?
6. Any free screen recording software? I used hypercam 2 for windows, not sure if it works with Lubuntu.
7. I take it Utorrent works with Lubuntu?
8. Does Nero work with Lubuntu? I use it to burn videos so hopefully it does work.


Sorry for all the questions but just want to be prepared and get of to a good start. And again, any and all help will be greatly appreciated. Thanks!!

---

### Post by lethall1 on 2013-05-30
> S[COLOR=#000000]orry for all the questions but just want to be prepared and get of to a good start. And again, any and all help will be greatly appreciated. Thanks!![/COLOR]
Why don't you use google? Internet is very big library, and there are a lot of interesting things, for the begginers too.
[http://www.linux.org/tutorial/view/beginners-level-course](http://www.linux.org/tutorial/view/beginners-level-course)
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)
[http://www.makeuseof.com/pages/ubuntu-an-absolute-beginners-guide](http://www.makeuseof.com/pages/ubuntu-an-absolute-beginners-guide)
[http://www.techradar.com/news/software/operating-systems/25-ubuntu-tips-for-beginners-906002](http://www.techradar.com/news/software/operating-systems/25-ubuntu-tips-for-beginners-906002)

If you have some problems write here but you must search first

---

### Post by Impavidus on 2013-05-30
1 (install software): Use the software centre, synaptic package manager (you may have to install it first) or, if you like terminals, apt-get.
2 (anti-virus): Not really, unless you're setting up a mail server or want to protect windows machines on a local network. Just be careful.
3 (firewall): Chances are you already have a firewall in your router. Also, by default (L)Ubuntu has no listening ports open.
4-6: Not my specialty.
7 (torrent): I think Transmission is the default torrent application in Lubuntu.
8 (burn): I usually burn with Xfburn. I think it's included in Lubuntu by default. There used to be a Linux version of Nero, but it's no longer supported.

Make sure you install flash player and some codecs for youtube and your local media collection. The easy way is going to the software centre and installing lubuntu-restricted-extras.

---

### Post by howefield on 2013-05-30
> **achilles316 said:**
> 1. How do i install things i will need? 
2. Do i need a Antivirus?
3. How do i enable firewall? Any other firewall rules i should know?
4. Truecrypt work with Lubuntu? Do i need to reformat my EHD with the linux version or will it work as it is?
5. Does yahoo messenger work with Lubuntu?
6. Any free screen recording software? I used hypercam 2 for windows, not sure if it works with Lubuntu.
7. I take it Utorrent works with Lubuntu?
8. Does Nero work with Lubuntu? I use it to burn videos so hopefully it does work.

1. Through the Lubuntu Software Centre or Synaptic Package manager.
2. Generally no, but there are reasons why you might consider it, have a read here.. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
3. [https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)
4. Haven't a clue about Truecrypt.
5. Don't believe so, but you can use a number of chat clients which will connect to your yahoo account, eg Pidgin which is included in Lubuntu. 
6. gtk-recordmydesktop
7. Lubuntu has an included torrent client in a default installation called Transmission.
8. There is Nero for Linux, alternatively you *may* get the windows version working via Wine, but the best bet would be to use a native application, like the included Xfburn.

A lot of your questions can be answered here.. [https://help.ubuntu.com/community/Lubuntu/Setup](https://help.ubuntu.com/community/Lubuntu/Setup)

---

### Post by 3rdalbum on 2013-05-30
You have been given two good replies. I will just add that you should look for a recent guide about installing codecs and DVD playback on Lubuntu so you can watch all movie formats.

Also, Windows programs don't run on Linux. They are far, far too different. For video DVD burning I use Devede, but Brasero works too. (Brasero is preinstalled).

---

### Post by Mark Phelps on 2013-05-30
Don't know if Nero for Linux is still available.  I used it for a while -- but it was not free.

---

### Post by mastablasta on 2013-05-30
4. truecrypt works in linux. als during install you had an option to encrpy your home (which is where data is store). it's not with truecrypt but the encryption is just as strong.
5. yahoo messanger does not work in linux. gyache improved is attempt to build one and is most compatible with it: [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)
[http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html)

Although you will be able to send IM's just fine with pidgin. however sharing files over pidgin might not work for example.
8. if you don't like other burner's interface then k3b is quite close to Nero.

you use computer to surf the web, watch videos and such. make sure you have restricted extrass installed as well as libdvdcss. more here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by MirrorUniverse on 2013-05-30
> 
2. Do i need a Antivirus?
3. How do i enable firewall? Any other firewall rules i should know?
4. Do i need to reformat my EHD with the linux version or will it work as it is?
6. Any free screen recording software? I used hypercam 2 for windows, not sure if it works with Lubuntu.

I'm no expert, in fact I am as new to this as you are lol.   But I have done some poking around and have some answers to the  questions above.

on antivirus/security - Looking around on the forums here, found some resources you may be interested in.
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)  [http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)  [http://www.insanitybit.com/2012/12/17/hardening-ubuntu-linux/](http://www.insanitybit.com/2012/12/17/hardening-ubuntu-linux/)   I skimmed over the insanitybit.com post and it talks about a  preinstalled firewall for Ubuntu called UFW.  I'll be reading these  three and the links howefield provided hopefully next week.

EHD  - Should work, no matter if it is FAT32 or NTFS.  If it is NTFS and  cannot be read, use Synaptic Package Manager, search for ntfs-3g and install it.

hypercam2  - howefield mentioned recordmydesktop, which you can get in the ubuntu  software center.  Hypercam2 seems to work in Wine with some limitations.  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5266](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5266)  That test was done in Wine version 1.1, so kinda old as the current version is 1.4.

---

### Post by Rob Sayer on 2013-05-30
While you can run a number of windows problems under wine, it's very buggy and problematic with many programs.  Judging by the nature of your original questions I'd just look for linux equivalents if I were you.  The only windows program I haven't been able to find one for is dvdfab hd decrypter ... there doesn't seem to be a linux one that's updated nearly as often ... but I've ripped pretty much all my dvd's anyway.

Actually before I switched to linux (I still have one windows 7 partition but it's feeling neglected) I mostly had switched to programs that were linux ports anyway.  I had gotten very sick of windows program installers putting in 3rd party codecs that aren't really compatible without informing me first, or messing with the registry in other ways.  Linux programs that are also available in linux are almost always much better behaved in that respect.  You *can't* mess with the registry in linux like you can win windows.

I do have a linux antivirus program installed (clamav) but that's only because I still have a windows partition and a dl'ed file may end up there or I may share it with a win user.  And I only use it in on demand scan mode.  But one running full time as you'd do in windows?  I don't know a single linux user who does that.

A firewall isn't a bad idea at all, though since linux (unlike windows) doesn't keep any ports open when online you don't need one nearly as much.  In windows you'd be crazy not to use one.

I don't burn a lot of discs anymore but from what I've been able to find out K3b is the one to go for, the only one as good as imgburn in windows (which is infinitely better than nero BTW).

---

### Post by ShadowVegan on 2013-05-30
> **achilles316 said:**
> 1. How do i install things i will need? 
2. Do i need a Antivirus?
3. How do i enable firewall? Any other firewall rules i should know?
4. Truecrypt work with Lubuntu? Do i need to reformat my EHD with the linux version or will it work as it is?
5. Does yahoo messenger work with Lubuntu?
6. Any free screen recording software? I used hypercam 2 for windows, not sure if it works with Lubuntu.
7. I take it Utorrent works with Lubuntu?
8. Does Nero work with Lubuntu? I use it to burn videos so hopefully it does work.


I'll post my answers too just because you have a lot of questions.

1) You can either use the synaptic package manager, or use the terminal. To open a terminal type 'ctrl+alt+T'. To search for software, type 'apt-cache search <keyword or software name>'. To install, type 'sudo apt-get install <software name>'.
2) Not really, but if you want it, to install it open a terminal and type 'sudo apt-get install clamav'. To run a scan, in a terminal type 'sudo clamscan -r --bell -i /'
3) Not my area
4) Yes, to install it go to the downloads page at [TrueCrypt.org]("https://www.truecrypt.org/"). If you need help knowing which package to download, or how to verify the signature, send me a PM and I can give you a walkthrough. However, note that you CANNOT encrypt your entire hard drive with TrueCrypt--if you want to do that, use the built-in encryption when installing Lubuntu/Ubuntu. In Linux TrueCrypt can only be used to encrypt files, not the entire drive. You can create an encrypted volume (max size 4GB) and put whatever files you want in it.
5) You can sign into your Yahoo account with Pidgin. To install pidgin type 'sudo apt-get install pidgin'
6) gtk-recordmydesktop
7) I assume so, I know that Vuze and Miro do.
8) Not familiar with Nero, but if you want to burn CDs I suggest brasero.

---

### Post by achilles316 on 2013-05-30
[COLOR=#DD4814][COLOR=#000000]@[lethall1]("http://ubuntuforums.org/member.php?u=1700819"),  The reason i asked for help is cause their are things i wanted some conformation about or was hoping to get more updated information. I did my own research as stated in my post.

The firewall i had already activated it and had found other rules to apply. The thing is that the rules guide was made in 2011 and i was hoping for more updated ones so that is why i asked.


[/COLOR][/COLOR][COLOR=#000000]Yahoo Messenger i need so i can see webcam so that i do still need to find a program that will allow me to do that if Yahoo Messenger don't work for Lubuntu. Does that pidgin messenger allow you to see webcam? 
[/COLOR][COLOR=#DD4814][COLOR=#000000]
[/COLOR][/COLOR][COLOR=#000000]Also, i get a KVM disabled on bios when i first start my pc. I get it after the Dell screen and right before the Lubuntu screen. Again, researched it but again, not sure what to do. Any help will be appreciated. Thanks! Okay i found what this is and i found how to fix it. It says to enable it in bios which i found. The question is, should i enable it or not? Does it  matter?
[/COLOR][COLOR=#DD4814][COLOR=#000000]
Is their a way to delete history, cookies, cache and other things in linux? For windows i used to use ccleaner, any similar program for Lubuntu. I think i saw a link about it last night but i been going over so much trying to learn Lubuntu and now i can't find it.

Do i need to defrag my disks? 

[/COLOR][/COLOR][COLOR=#DD4814][COLOR=#000000]Last but not least. How do i know if i have to install software for my audio and video drivers?

[/COLOR][/COLOR]

---

### Post by achilles316 on 2013-05-30
[COLOR=#000000]UPDATE: I have yet to find newer rules for firewall. I wonder if the ones i have found are still valid.

[/COLOR][COLOR=#000000]UPDATE: Seems Gyache Improved allows you to see webcams but will it work if the other person has yahoo messenger in windows?

[/COLOR][COLOR=#000000]UPDATE: I enabled KVM  and message went away. Hopefully it don't mess up something else.

[/COLOR][COLOR=#000000]UPDATE: Still can't find anything on a software for deleting browser history among other things.

[/COLOR][COLOR=#000000]UPDATE: Answer seems to be no on having to defrag the drive. Thoughts?

[/COLOR][COLOR=#000000]UPDATE: Found where additional drivers are installed but it don't show anything. What does that mean?[/COLOR]

---

### Post by 3mutts on 2013-05-31
> **achilles316 said:**
> [COLOR=#000000]
[/COLOR][COLOR=#000000]UPDATE: I enabled KVM  and message went away. Hopefully it don't mess up something else.

[/COLOR][COLOR=#000000]UPDATE: Still can't find anything on a software for deleting browser history among other things.

[/COLOR][COLOR=#000000]UPDATE: Answer seems to be no on having to defrag the drive. Thoughts?[/COLOR]

1. Unless you are doing anything with virtual machines, it doesn't matter if KVM is enabled or not (correct me if I'm wrong, I'm just going off Wikipedia)

2. You don't need one, there should be a option in your browser to do it.

3. Unless you are using the NTFS file system (what Windows uses) you don't really need to defrag.

---

### Post by mastablasta on 2013-05-31
> **achilles316 said:**
> [COLOR=#000000]UPDATE: I have yet to find newer rules for firewall. I wonder if the ones i have found are still valid.

use GUFW to configure firewall with GUI.

> 
[/COLOR][COLOR=#000000]UPDATE: Seems Gyache Improved allows you to see webcams but will it work if the other person has yahoo messenger in windows?
[COLOR=#000000]
it should but to be honest i never tried it. note that pidgin has plenty of plugins. it might be there is a plugin to integrate it better with yahoo. though the problem is yahoo protocol (like skype) is closed source.[/COLOR]

[/COLOR][COLOR=#000000][COLOR=#000000]> [/COLOR]
[/COLOR][COLOR=#000000]UPDATE: Still can't find anything on a software for deleting browser history among other things.
[COLOR=#000000][/COLOR]
does computer janitor do it? : [http://manpages.ubuntu.com/manpages/lucid/man8/computer-janitor.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/computer-janitor.8.html)
there is a nice gui for it.
> 
[/COLOR][COLOR=#000000]UPDATE: Answer seems to be no on having to defrag the drive. Thoughts?

That is correct. ext4 and a few other linux files sytems dont' really need to defrag their drives. imagine google defraging their servers :-D
> 
[/COLOR][COLOR=#000000]UPDATE: Found where additional drivers are installed but it don't show anything. What does that mean?[/COLOR]
wha do you mean? if nothing is showing under additional drivers it means there are none available for your hardware in repositories. if everythign works then it mmeans it works using the opensource drivers provided in the Linux kernel (core).

---

### Post by achilles316 on 2013-05-31
Thanks for the replies!

Configured firewall using the GUFW. So turning it on and setting incoming to deny and outgoing to allow enough? 

Computer janitor didn't work. Says package is missing, obsolete or only supported by another source.


Do have one last question. I hope!!

What is best codec to compress videos and audio (or combo of both) in openshot video editor. I can do everything else with it but i can't find a codec to make files smaller. I used to use xvid mpeg 4 in windows but i can't seem to find it in openshot and to download it. I think it said it was already installed but i can't find it when i look for the codec in openshot unless it has some other name. Lots of codecs there seem like they do.


I didn't think switching to Linux was gonna be so complex. Maybe it is just me lol. Well i am not gonna give up. And this is reason i'd rather ask questions than read out dated articles. I installed some codecs as it said in the article and now every other time i try to open openshot video editor everything crashes. At least i think that is what has made it crash since that is all i installed. I think i will need to do fresh install of Lubuntu.

---

### Post by mastablasta on 2013-05-31
> **achilles316 said:**
> Thanks for the replies!

Configured firewall using the GUFW. So turning it on and setting incoming to deny and outgoing to allow enough? 


seems more or less the default setting even if you didn't install GUFW... maybe outgoing to allow only for programmes you want to allow internet access?
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[http://www.howtogeek.com/115116/how-to-configure-ubuntus-built-in-firewall/](http://www.howtogeek.com/115116/how-to-configure-ubuntus-built-in-firewall/)

i am not sure what you plan to do. settings depend on that, obviously.
> 
Computer janitor didn't work. Says package is missing, obsolete or only supported by another source.

Even if you install it from software center?

you can also try Bleachbit: [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)
you can use deb file to install if software center install fails.

[/QUOTE]
What is best codec to compress videos and audio (or combo of both) in openshot video editor. I can do everything else with it but i can't find a codec to make files smaller. I used to use xvid mpeg 4 in windows but i can't seem to find it in openshot and to download it. I think it said it was already installed but i can't find it when i look for the codec in openshot unless it has some other name. Lots of codecs there seem like they do.[/QUOTE]

did you install restricted extras package from software center? it has all codecs you want/need. ;-)

> 
I didn't think switching to Linux was gonna be so complex. Maybe it is just me lol. Well i am not gonna give up. And this is reason i'd rather ask questions than read out dated articles. I installed some codecs as it said in the article and now every other time i try to open openshot video editor everything crashes. At least i think that is what has made it crash since that is all i installed. I think i will need to do fresh install of Lubuntu.

it's not. it helps if you install all things you might need after system install. and if you already used open source software in previous OS.

not sure why openshot crashes or how you installed the codecs. but if you run openshot from terminal you should get any error outputs you can then use (copy it) to trouble shoot the crash or to ask for help on their (Openshot) forums (or their other support channels).

---

### Post by achilles316 on 2013-05-31
> **mastablasta said:**
> seems more or less the default setting even if you didn't install GUFW... maybe outgoing to allow only for programmes you want to allow internet access?
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[http://www.howtogeek.com/115116/how-to-configure-ubuntus-built-in-firewall/](http://www.howtogeek.com/115116/how-to-configure-ubuntus-built-in-firewall/)

i am not sure what you plan to do. settings depend on that, obviously.  Pretty much only basic stuff. I will mostly be using my browser, and which ever software that i can use to view yahoo messenger cam. As well as software i have already mentioned here, like Transmission, openshot, recordmydesktop.

> Even if you install it from software center?

you can also try Bleachbit: [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)
you can use deb file to install if software center install fails.
 It don't come up when i try to install it from Lubuntu software center. Bleachbit did though.

> did you install restricted extras package from software center? it has all codecs you want/need. ;-) I found it. Is their a way to choose what to install. Chrome already comes with flash so no need to install it again. I don't use Java either so why install it.



> it's not. it helps if you install all things you might need after system install. and if you already used open source software in previous OS.

not sure why openshot crashes or how you installed the codecs. but if you run openshot from terminal you should get any error outputs you can then use (copy it) to trouble shoot the crash or to ask for help on their (Openshot) forums (or their other support channels).I am a former Windows user that have just started (been 1 day barely lol) using Lubuntu Linux. It is why i am asking alot of questions.

How do i safely remove a usb or external drive that i connect to my computer? In windows you used to have to safely remove the drive (or whatever it was) before you unplugged it. I can't find anything like that in Linux.

Will need to do fresh install of Lubuntu. I couldn't open openshot so i rebooted and when i got back on it was gone. I tried to install again and nothing. I think the article that i read and followed how to install the codecs messed me up. 

Live and learn right.

---

### Post by MirrorUniverse on 2013-05-31
> How do i safely remove a usb or external drive that i connect to my  computer? In windows you used to have to safely remove the drive (or  whatever it was) before you unplugged it. I can't find anything like  that in Linux.

When I plug in a usb flash drive, it comes up as an icon on my desktop.  You can right click that and select Eject Volume to unmount it.  I assume external hard drives would work the same way.

---

### Post by mastablasta on 2013-05-31
> **achilles316 said:**
> Pretty much only basic stuff. I will mostly be using my browser, and which ever software that i can use to view yahoo messenger cam. As well as software i have already mentioned here, like Transmission, openshot, recordmydesktop.
well in that case you could have just left it as it is on install. you would need to  open ports in case you want some server (LAMP) or something.

> 
 I found it. Is their a way to choose what to install. Chrome already comes with flash so no need to install it again. I don't use Java either so why install it.

yes, to hunt individual packages for codecs in synaptic. but it might be easier to install it and then remove what you do not need.all in all it doesn't take up that much space.

> 
I am a former Windows user that have just started (been 1 day barely lol) using Lubuntu Linux. It is why i am asking alot of questions.
don't worry. i am still a windows user. ;-)
> 
How do i safely remove a usb or external drive that i connect to my computer? In windows you used to have to safely remove the drive (or whatever it was) before you unplugged it. I can't find anything like that in Linux.

you should be able to right click on USB drive icon and then select eject (if icon is not on desktop then it's surely in file manager PCManFM). not sure how Lubuntu has it done as i use Kubuntu (which does it the same way as windows - > select icon in taskbar and then eject). so eject = safely remove

in general Kubuntu feels a lot more like windows. but it does need at least 1 GB ram to run it.

---

### Post by Rob Sayer on 2013-05-31
> **achilles316 said:**
> ... What is best codec to compress videos and audio (or combo of both) in openshot video editor. I can do everything else with it but i can't find a codec to make files smaller. I used to use xvid mpeg 4 in windows but i can't seem to find it in openshot and to download it. I think it said it was already installed but i can't find it when i look for the codec in openshot unless it has some other name. Lots of codecs there seem like they do.

mpeg4 & xvid are there in openshot, under file -> export.

Openshot isn't my first choice for encoding to xvid.  I prefer avidemux.  I only use openshot to convert files others choke on.  It doesn't have the range of options I want.

> I didn't think switching to Linux was gonna be so complex. Maybe it is just me lol. Well i am not gonna give up. And this is reason i'd rather ask questions than read out dated articles. I installed some codecs as it said in the article and now every other time i try to open openshot video editor everything crashes. At least i think that is what has made it crash since that is all i installed. I think i will need to do fresh install of Lubuntu.

You're still thinking in terms of windows ... and windows <= XP at that.  You shouldn't install 3rd party codecs in windows vista or later, and the same logic doesn't 100% apply in linux.

I don't know what "articles" you mentioned or what software sources you used to install those codecs, but you should stick to standard repositories and avoid other ppa's until you seriously know what you're doing.  Yank whatever codecs you installed that made openshot crash.  Install ubuntu-restricted-extras, as mentioned.  You don't need anything else.

You should not need a separate program to delete browser history.  I realize chrome/chromium is *severely* lacking in this ... one reason I have chromium installed but rarely use it ... but you can force it to start in incognito mode.

---

### Post by achilles316 on 2013-05-31
Again thank you for all the help everyone!!

Is the gufw grayed out and in need of the password so that no one can change my settings?

Also, i have gotten an error message 2 times within the last hour even though it is a fresh new install. Error message reads: Sorry, Ubuntu 13.04 has experienced an internal error. 

Executable Path: /usr/lib/i386-linux-gnu/libmenu-cache/libexec/menu-cached
Package: libmenu-cache2 0.4.1-0ubuntu1
Problem Type: Crash

It has alot of other stuff, not sure how much u need. I hope not all of it cause i would hate to have to type it all out lol.

---

### Post by achilles316 on 2013-05-31
Also, i don't get any icon on the desktop or anything on the bottom right taskbar that shows that i have an external hard drive mounted. I do see it when i go to disk but it does not give me the option to eject it. Anything i can use to safely remove my EHD cause i don't want to have to keep just unplugging it and therefore end up damaging it.

Again, thanks for any and all help as i really do appreciate it.

---

### Post by AgentZ86 on 2013-05-31
> **achilles316 said:**
> So i have just converted to Lubuntu Linux! As i am sure you know by now, i do have questions lol. Basically, what do i need to know? I have done some reading but i figured it best to ask you veterans out there. Any and all help would be greatly appreciated! Here is what i mostly use my computer for incase it helps to determine what advice to give.

I use it for every day things like checking my email on Yahoo, checking both my Instagram and Facebook and other regular sites like NFL.com and Youtube. I also watch movies either online or those that i have saved on my external hard drive. I also listen to music. 

Some questions i do have of the top of my head are:

1. How do i install things i will need?   
Many ways most use Software Center build into ubuntu but you can also install synaptic or command line with apt-get etc.

2. Do i need a Antivirus? 
Not really but some install it to protect the spread of viruses to Windows computers mostly IMO but I've never used in for 7 years on linux

3. How do i enable firewall? Any other firewall rules i should know? 
Software Center too many options to choose from

4. Truecrypt work with Lubuntu? Do i need to reformat my EHD with the linux version or will it work as it is?
Software Center but there are more options then only whats in the software center just fyi

5. Does yahoo messenger work with Lubuntu?
Yes Typically Linux messengers have can use multiple protocols on one messenger interface so you could for example: chat on one interface with all your aim,yahoo,msn,jabber,irc,icq contacts all in one messenger program

6. Any free screen recording software? I used hypercam 2 for windows, not sure if it works with Lubuntu.
Yes Software Center a bunch I've used RecordMyDesktop that works well but there are several others in there too

7. I take it Utorrent works with Lubuntu?
I don't think so but Utorrent is a Bittorrent client for mac/windows so we have Bittorrent and torrent clients galore too many to list but Ubuntu has it by default and no pesky malware installs

8. Does Nero work with Lubuntu? I use it to burn videos so hopefully it does work.
No but there are zillions of really nice DVD designers and burner apps everyeone including the Software Center

Sorry for all the questions but just want to be prepared and get of to a good start. And again, any and all help will be greatly appreciated. Thanks!!


If thats all you need to do you should be more then happy with all the options available for Linux

Happy hacking

---

### Post by achilles316 on 2013-05-31
> **AgentZ86 said:**
> If thats all you need to do you should be more then happy with all the options available for Linux

Happy hacking

Actually i did ask alot more questions that were generously answered. Only one i could use some help on is on how to safely remove my external hard drive. I go to disks and it shows it but i get no option to eject. I wonder if that has to do with the fact that the entire drive is encrypted with truecrypt.

Any ideas?

---

### Post by achilles316 on 2013-05-31
Thanks for the help everyone!

---

### Post by Javelin Dan on 2013-05-31
achilles316 -

It seem as though you're on the right track with the generous help of many good people here. If you don't mind, I'm going to offer my two cents. I do aplogize if I'm wrong, but it sounds as though you might be trying to apply too many "Windows" programs, concepts, or whatever to Linux. It's a real easy mistake to make for a Windows refuge and/or newbie, and I speak from experience. You will be advised here and other places many times that Linux is not Windows and for good reason. Too many differences to point out here, but suffice it to say that*_ almost_* anything you can do in Windows, you can do in Linux - sometimes even easier or better. But there are still differences you'll never resolve. Still, very much worth the effort in my opinion.

One thing that seems a little awkward at first is the software selection issue. With Windows, you might if you're lucky, have a choice of a 2 or 3 software programs to accomplish a task. With Linux, it could very easily be dozens, and they're all free! You just have to get past the odd names at first. Many of those weird names are actually acronyms for an accurrate description of the program. Others may have a seemingly odd name because they were designed in a different country with a different language as Linux is truly an international effort. But for just about anything you want do do, there's a Linux program to do it. While certainly not a complete list by any means, please log onto[SIZE=2][SIZE=2] "[/SIZE]The table of equivalents / replacements / analogs of Windows software in Linux[/SIZE]" at:[FONT=&amp][ http://www.linuxrsp.ru/win-lin-soft/table-eng.html]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html"). [/FONT]I hope this will help you with some of the tasks you are looking to perform. Regards and good luck.

P.S. - I forgot to mention to download "Ubuntu Tweak" using the following commands:

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak 

Computor Janitor works very well from there and has a very nice graphical interface to boot!

---

### Post by 3rdalbum on 2013-05-31
If you have no option to eject, then it is not mounted and you can simply unplug it.

You said you had no idea switching to Lubuntu would be so complex... well, it is a different operating system entirely, so it was never going to be instantly familiar to you. You didn't need antivirus, a firewall, a browser history cleaner, a defragmenter, or even any additional drivers. I don't see how this is complex, it is just different!

---

### Post by craig10x on 2013-05-31
Pidgin: an excellent multi messenger (yahoo, msn, aol, etc)
K3b: An EXCELLENT linux dvd burner
Simple program to turn on Firewall:  GUFW
Excellent media Player: Rhythmbox
Video Player:  VLC Media Player

Those are some examples of excellent linux alternatives to programs you used in windows...all available in ubuntu software center...

---

### Post by achilles316 on 2013-05-31
Thanks for the replies guys. Yes i have noticed it is easier [ 						 					]("http://ubuntuforums.org/member.php?u=61044") 				 				 					 						 	[**[COLOR=#000000]3rdalbum[/COLOR]**]("http://ubuntuforums.org/member.php?u=61044"). The thing is that for someone that has only used windows since the start, it seems some what complex till you get the hang of it. And yes i getting the hang of it now. 
				 				 					 						 	
Thanks  				 				 					 						 	[**[COLOR=#000000]craig10x[/COLOR]**]("http://ubuntuforums.org/member.php?u=869825"), i have already found alternatives to programs that i used to use in windows. If for some reason they don't work i will give the ones you mentioned a try.

Only problem i need help with is safely remove hard drive as i can't find a single answer on the web. But i have created a new thread for that so will mark this one solved. 

Again thank you everyone for all the help.

---

