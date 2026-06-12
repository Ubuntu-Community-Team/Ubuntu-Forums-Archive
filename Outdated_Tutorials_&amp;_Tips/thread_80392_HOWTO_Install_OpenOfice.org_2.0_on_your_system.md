---
title: "HOWTO Install OpenOfice.org 2.0 on your system"
date: 2005-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by christooss on 2005-10-22
In repositories you can find only 1.9.129 - RC2 version so here is how you instal pure 2.0 on your system

**[COLOR="SeaGreen"]1.[/COLOR][COLOR="Red"] Installation from repositories[/COLOR]**

1. Open your sources.list and add this line in

```
deb http://people.ubuntu.com/~doko/OOo2 ./
```

AMD64 and ppc

You can help your self with these repositories

```
   deb http://people.ubuntu.com/~doko/OOo2-amd64 ./
   deb http://people.ubuntu.com/~doko/OOo2-powerpc ./
```
2.1 Do a update and upgrade

```
sudo apt-get update
sudo apt-get upgrade
```

This all will upgrade your previous version 1.9.129.

2.2 If you removed any OpenOffice.org installation from disk than simpli do a

```
sudo apt-get install openoffice.org2
```

BEWARE this are test packages :) But they simply work :)

**[COLOR="SeaGreen"]2.[/COLOR] [COLOR="Red"]2.0.0 version installed from DEB's[/COLOR]**
1. Download english version with wget

```
wget ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_LinuxIntel_install_en-US_deb.tar.gz
```

2. Extract file
```
tar -xzfv OOo_SRC680_m137_LinuxIntel_install_en-US_deb.tar.gz
```

4. Installation

Go to dir with debs and perform

```
sudo dpkg -i *.deb
```

5. Native language instalation

Download your language package from [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_native_LinuxIntel_langpacks_deb](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_native_LinuxIntel_langpacks_deb)
There are three packages. Donwload them all

Then install them with

```
sudo dpkg -i *.deb
```
**[COLOR="SeaGreen"]3. [/COLOR][COLOR="Red"]2.0.0 version installed from RPM's[/COLOR]**

1. Download
Download Linux file from OpenOffice.org just choose linux when it asks you for your platform. You can use bittorrent you can find when you choose server from which you download.

2. Extract tar.gz file

```
tar -xzfv OOo_2.0.0_LinuxIntel_install.tar.gz
```

3. Aliens in Ubuntu

With alien you transform all rpms to debs.

pit your self in RPMS subdir of directrory you just created and than execute

```
sudo alien *.rpm
```
or
```
fakeroot alien*.rpm
```
Wait till all the packages are transformed

4. Installation

Now performe this command
```
sudo dpkg -i *.deb
```
5. Put Openoffice in your gnome menu

Go in to desktop-integration dir and execute
```
sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb
```
and than
```
 killall gnome-panel
```

Now you should have new icons in you Programs/office menus


**[COLOR="SeaGreen"]4. [/COLOR][COLOR="Red"]RC3 version - easyer to insta[/COLOR]ll** :)
1. Download
Download Linux file

```
wget http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz
```

2. Extract tar.gz

Extract file with

```
tar xzfv OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz
```

4. When all packages are transformed execute. First o to DEBS derictory which has been created

```
cd DEBS/
```
```
sudo dpkg -i *.deb
```
and wait for all the packages to get install

5. Restart gnome-panel
```
killall gnome-panel
```

Now you will have menus shortcuts. But they will be dubled use OpenOffice 2.0 ... ones
[IMG]http://www.ahacic.5gigs.com/screenshots/menuji.jpg[/IMG]
pressing any of this options will show you splash screen
[IMG]http://www.ahacic.5gigs.com/screenshots/splash.jpg[/IMG]

Enjoy your OpenOffice.org 2.0

---

### Post by Juippisi on 2005-10-22
[QUOTE=christooss]```
killal gnome-panel
```[/QUOTE]

Shouldn't this be "killall" ;-).

But hey, thanks for this howto. I'll try it soon.

---

### Post by christooss on 2005-10-22
Fixed :)

Thanks

---

### Post by tseliot on 2005-10-22
Nice guide. Thanks!

---

### Post by Juippisi on 2005-10-22
OOo-2.0 works perfectly. Thanks!

(And for someone that doesn't use Gnome... the command to start OOo2 is *openoffice.org-2.0*)

---

### Post by abandoned_hussam on 2005-10-22
Is there a difference between 1.9.29 and 2.0? ( bugs, etc...)

---

### Post by Juippisi on 2005-10-22
At least bug and stability fixes. Find more about "What's new in 2.0" [here]("http://www.openoffice.org/press/2.0/index.html").

And wasn't 1.9.29 the "beta1"? After it has comed beta2, -rc1, -rc2 and is 2.0 "-rc3"? I think so. 

I recommend updating.

---

### Post by darehanl on 2005-10-22
I have a problem with the menus. At least for my system, the /usr/bin/openoffice.org-2.0 shell script points to the wrong file. The contents of the script is 
```

#!/bin/sh
exec /etc/openoffice.org-2.0/program/soffice "$@"
```

However, I need to change this to 
```

#!/bin/sh
exec /etc/openoffice.org-2.0/program/soffice[COLOR="Red"].bin[/COLOR] "$@"
```

Only after the modification do the menus work (it works just fine after adding the .bin part). My soffice file has permissions 000, while the soffice.bin file has execute bits on. The /usr/bin/openoffice.org-2.0-printeradmin script needs to be fixed also.

---

### Post by kashms on 2005-10-22
I don't want two versions of openoffice installed so i want to uninstall the version installed by default in Breezy, but in synaptics it wants to uninstall ubuntu-desktop as well! Is this safe? And what would it break if anything?

---

### Post by MakubeX on 2005-10-22
Sir, if it's okay, I would like to know the milestone/build or version name of the official OpenOffice 2.0. I am confused as to what I should place in the blank of "cvs co -r __________ OpenOffice" since the latest version of the source I had downloaded via CVS was the RC3 and the value of that blank was OOO680_m3 (or "cvs co -r OOO680_m3 OpenOffice"). Anyone who has an idea about this?

TIA.

---

### Post by Perfect Storm on 2005-10-22
You can savely remove ubuntu-desktop, just remember to add it again when making a distro upgrade.

---

### Post by sabitha on 2005-10-22
should i remove my old open office first
sorry im a newbie ;)

---

### Post by christooss on 2005-10-22
Yes you can. THere is no need just when opening you have to oben Uper icons Fancy ones to open OOo 2.0

---

### Post by foxy123 on 2005-10-22
what's wrong with deb packages on [http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/?](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/?) You don't need to alienate them...

---

### Post by christooss on 2005-10-22
I couldn't find them. But there is nothing wrong with them

---

### Post by foxy123 on 2005-10-22
I've figured out what may be wrong with them: they are for Czech and Slovakian languages, though all labnguage packs are available. I wonder if I install Czech version and then GB language pack, will it be ok?

It's OK. Just have installed it. It fixes the most annoying bug for me with AutoFilter when you have to show all every time you want to use another criteria).

So the easier way is to go to 
[http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/)
and grab OOo_2.0_LinuxIntel_install_cs_deb.tar.gz or OOo_2.0_LinuxIntel_install_sk_deb.tar.gz
then go to
[http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/OOo_2.0_native_LinuxIntel_langpacks_deb/](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/OOo_2.0_native_LinuxIntel_langpacks_deb/)
and grab the language pack you need.

Untar OOo_2.0_LinuxIntel_install_cs_deb.tar.gz, it will create DEBS directory. Copy language pack debs (3 files) there.

```
cd DEBS
sudo dpkg -i *.deb
```

and you're done.

---

### Post by MichaëlVD on 2005-10-22
Everything works as described in your howto; thanks!

A couple of questions...

I know I can launch openoffice.org-2.0 with alt+f2. However that always opens Writer first. Is there a way to open Impress immediately?

Secondly, when I drag an icon from the applications menu to my desktop, there's something wrong with the permission and the icon is lost. I tried to look for the icon by changing the properties of the desktop shortcut, but I can't find it. How can I solve this?

Thanks

---

### Post by jeremie on 2005-10-22
After a successful install,
I get the following when trying to execute

```
jeremie@desktop:~$ openoffice.org-2.0
/usr/bin/openoffice.org-2.0: line 2: /etc/openoffice.org-2.0/program/soffice: Permission denied
/usr/bin/openoffice.org-2.0: line 2: exec: /etc/openoffice.org-2.0/program/soffice: cannot execute: Success

```

same thing when running it with sudo or as root

j

---

### Post by christooss on 2005-10-22
hm how about runing

openoffice.org-2.0 -writer

---

### Post by jeremie on 2005-10-22
same thing
i tried to run it in the terminal when i noticed there was no response from clicking the icons

```
jeremie@desktop:~$ openoffice.org-2.0 -calc %U
/usr/bin/openoffice.org-2.0: line 2: /etc/openoffice.org-2.0/program/soffice: Permission denied
/usr/bin/openoffice.org-2.0: line 2: exec: /etc/openoffice.org-2.0/program/soffice: cannot execute: Success

```

---

### Post by Jeldert on 2005-10-22
You need to give soffice execute and read permissions for all users. Give it a try and post the results please.

---

### Post by jeremie on 2005-10-22
Thanks for the hint.
Now it works.

Here's what i did:

```
jeremie@desktop:/opt/openoffice.org2.0/program$ ls -l soffice
----------  1 root root 6485 2005-10-15 10:02 soffice
jeremie@desktop:/opt/openoffice.org2.0/program$ sudo chmod o=rx soffice
jeremie@desktop:/opt/openoffice.org2.0/program$ ls -l soffice
-------r-x  1 root root 6485 2005-10-15 10:02 soffice

```

One question though,
Just curious... Why didn't dpkg set the permissions correctly?

---

### Post by darehanl on 2005-10-22
[QUOTE=jeremie]After a successful install,
I get the following when trying to execute

```
jeremie@desktop:~$ openoffice.org-2.0
/usr/bin/openoffice.org-2.0: line 2: /etc/openoffice.org-2.0/program/soffice: Permission denied
/usr/bin/openoffice.org-2.0: line 2: exec: /etc/openoffice.org-2.0/program/soffice: cannot execute: Success

```

same thing when running it with sudo or as root

j[/QUOTE]

That's the problem I reported earlier. The permissions are set incorrectly for soffiice. The correct executable file is [COLOR="Red"]soffice.bin[/COLOR] I believe. Changing the /usr/bin/openoffice.org-2.0 script as I noted on page 1 works for me.

---

### Post by jonrkc on 2005-10-22
[QUOTE=sabitha]should i remove my old open office first
sorry im a newbie ;)[/QUOTE]
You can install a new version such as 2.0 of OpenOffice.org along with an old version with no problem.  But it must be in a different directory or there WILL be problems, according to the OpenOffice.org website.

I installed version 2.0 alongside of version 1.1.3, and it ran OK except that it kept wanting Java, which I don't have.  Version 1.1.3 didn't care that much about Java, but version 2.0 seems to require it for some simple things!

So I went back to 1.1.3.

But the Java problem was unrelated to 1.1.3 being there.  They both ran fine, basically, coexisting together in separate directories.

---

### Post by zenwhen on 2005-10-23
This actually worked great. Anyone else notice that this version launches about 50% faster than the one that shipped with Breezy?

---

### Post by 43moon on 2005-10-23
Thank you christooss, I managed to install without a hitch.

christooss is just one more reason that ubuntu and the community are great.  :)

---

### Post by tseliot on 2005-10-23
[QUOTE=zenwhen]This actually worked great. Anyone else notice that this version launches about 50% faster than the one that shipped with Breezy?[/QUOTE]
Yep, same here.

---

### Post by Juippisi on 2005-10-23
[QUOTE=zenwhen]This actually worked great. Anyone else notice that this version launches about 50% faster than the one that shipped with Breezy?[/QUOTE]

Hmm, here's a picture (attachment) that makes OOo's launching more faster, tip found on Ubuntuforums ;-).

I don't know if it works anymore because I imported my old settings to OOo-2 so  those settings were there from the beginning. But, it's worth of trying, mine OOo doesn't launch slowly ;-).

( Just in case that the attachment doesn't show to someone, [http://www.roskakori.org/files/pictures/screenshots/nopeuta_OOon_kaynnistymista.png](http://www.roskakori.org/files/pictures/screenshots/nopeuta_OOon_kaynnistymista.png) )

---

### Post by baRRacuda on 2005-10-23
Anyone tried this on Breezy-AMD64?

---

### Post by Y_Ernst on 2005-10-23
[QUOTE=baRRacuda]Anyone tried this on Breezy-AMD64?[/QUOTE]

it doesn't work!

Error Message: 
current build architecture amd64 does not appear in package's list (i386)

---

### Post by Sykil on 2005-10-23
Well, does anyone have an idea of how one could get this to work under AMD64? :x

---

### Post by Matchless on 2005-10-23
[QUOTE=Sykil]Well, does anyone have an idea of how one could get this to work under AMD64? :x[/QUOTE]

Try this and let us know :
[http://www.ubuntuforums.org/showthread.php?p=436622#post436622](http://www.ubuntuforums.org/showthread.php?p=436622#post436622)
;)

---

### Post by DGibFen on 2005-10-23
Worked like a charm! Thanks!

---

### Post by Y_Ernst on 2005-10-23
[QUOTE=DGibFen]Worked like a charm! Thanks![/QUOTE]

There is only a link for RC3! (or you have to download a cs or sk version)

Try this link: [http://openoffice.debian.net/](http://openoffice.debian.net/)

---

### Post by foxy123 on 2005-10-23
[QUOTE=Y_Ernst]There is only a link for RC3! (or you have to download a cs or sk version)

Try this link: [http://openoffice.debian.net/](http://openoffice.debian.net/)[/QUOTE]
sk and cz versions work fine together with language packs...

---

### Post by z!cHz@cH on 2005-10-23
Worked for me Thnx!

One question do, is there a mozilla plugin for 2.0 if yes how do i install it?

---

### Post by berserker on 2005-10-23
I had no problems with permissions.  Perhaps the HOWTO should be changed to

```
fakeroot alien *.rpm
```

---

### Post by rwabel on 2005-10-23
I'm just curious if it's worth to install the OO2 deb's from here: [http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/)

or wait until OO2 final comes somehow to breezy. Does anyone know if and when the final will be either backported or provided from the ubuntu breezy repositories?

---

### Post by jonrkc on 2005-10-23
If this might help anybody wanting to install OpenOffice.org 2.0...:

I merely went to the OpenOffice.org site, downloaded the Linux package they offer there, converted the rpms to deb files using alien, and then used dpkg -i to install all the resulting deb files, and it was done.  No further steps needed.

My only problem was that though the suite "worked," it required Java for customizing itself (which never used to be the case).  I don't have Java, so I was stopped at that point.  

If you have Java on your system already, what I did should give you OpenOffice.org 2.0 which works fine.  

It might be the simplest way to get it.

---

### Post by christooss on 2005-10-23
This howto has been changed.

No aliens anymore

---

### Post by christooss on 2005-10-23
Hm I will change back to alien version :)

I now found out that its RC3 version. And I am unable to find changelog for 2.0.0 openoffice.

Does anyone knows how much changed sfrom RC3 ---> 2.0.0?

---

### Post by strongmantim on 2005-10-23
[QUOTE=darehanl]I have a problem with the menus. At least for my system, the /usr/bin/openoffice.org-2.0 shell script points to the wrong file. ...I need to change this to 
```

#!/bin/sh
exec /etc/openoffice.org-2.0/program/soffice[COLOR="Red"].bin[/COLOR] "$@"
```
[/QUOTE]

I ran into the same issue. Once corrected, everything worked perfectly.

---

### Post by mustang on 2005-10-24
Very awesome christooss. Thank you very much. Everything worked perfectly.

Quick question---I'm using a low capacity hard drive and I would like to keep as much free space as possible. 

How can I safely remove the OpenOffice that came with breezy or should I not? 

And yep, OO does start up faster :)

EDIT:

Oh, and how do I go upon putting the OO writer icon on my desktop? When I drag it straight from the menu, it doesn't take the icon with it and I can't find where the icon from the menu is.

---

### Post by foxy123 on 2005-10-24
[QUOTE=christooss]Hm I will change back to alien version :)

I now found out that its RC3 version. And I am unable to find changelog for 2.0.0 openoffice.

Does anyone knows how much changed sfrom RC3 ---> 2.0.0?[/QUOTE]
it does not say anywhere that it is RC3, though the files are of Oct. 17-18. So it may be...

---

### Post by poofyhairguy on 2005-10-24
This thread just saved my grade in comm class. The OO that came with Breezy kept crashing on me just as I was getting done with they doc I was working on all night. The crash handler would not stop the crashing. But when I installed the new OOoffice it recovered and allowed me to save my work. Great how to!

---

### Post by Technoviking on 2005-10-24
I'm hoping for offical OO2 final debs from the Ubuntu Devs, but very nice HowTo.

Mike

---

### Post by rickmans on 2005-10-24
great howto works perfectly

---

### Post by floyd27 on 2005-10-24
Where is the "desktop-intergration" dir/?
Can you give me the path..
thanx

---

### Post by floyd27 on 2005-10-24
never mind  :)

---

### Post by jasongrieves on 2005-10-24
[QUOTE=floyd27]never mind  :)[/QUOTE]
Funny thing is I was about to post this :)

the folder is located in the RPMS directory where you converted everything to deb packages.

Great thanks for the guide.  Works like a charm here also

---

### Post by Technoviking on 2005-10-24
You may want to check this out:
[http://www.ubuntuforums.org/showpost.php?p=438068&postcount=10](http://www.ubuntuforums.org/showpost.php?p=438068&postcount=10)

---

### Post by christooss on 2005-10-25
Mike your repositories have been added. But I really hate this default Ubuntu OpenOffice look. How can I change this?

And why there is no Printer preferences installed. It comes with rpms?

---

### Post by christooss on 2005-10-25
And I cry that there are default ubuntu ugly OpenOffice icons in version installed from repositories. I would like to change this to. How can I do this?

---

### Post by Technoviking on 2005-10-25
[QUOTE=christooss]Mike your repositories have been added. But I really hate this default Ubuntu OpenOffice look. How can I change this?

And why there is no Printer preferences installed. It comes with rpms?[/QUOTE]
You can change the icons with smeg (menu editor) if you run it as root or sudo.

I don't kn ow about printer preferences. I think the Ubuntu OO2 packages get the printer setting from the Ubuntu Printing admin tool.

Mike

---

### Post by christooss on 2005-10-25
Thanks

What about a look of Openoffice?

---

### Post by waffen on 2005-10-25
[QUOTE=jeremie]After a successful install,
I get the following when trying to execute

```
jeremie@desktop:~$ openoffice.org-2.0
/usr/bin/openoffice.org-2.0: line 2: /etc/openoffice.org-2.0/program/soffice: Permission denied
/usr/bin/openoffice.org-2.0: line 2: exec: /etc/openoffice.org-2.0/program/soffice: cannot execute: Success

```

same thing when running it with sudo or as root

j[/QUOTE]
change the permisions for the instalation dir

---

### Post by bertilow on 2005-10-26
[QUOTE=christooss]
1. Open your sources.list and add this line in

```
deb http://people.ubuntu.com/~doko/OOo2 ./
```

2.1 Do a update and upgrade

```
sudo apt-get update
sudo apt-get upgrade
```

This all will upgrade your previous version 1.9.129.
[/QUOTE]

I successfully installed OpenOffice 2 using the above method (more or less - I used Synaptic).

Everything works as it should ... except for the Wizard "Install new dictionaries". When I click on that menu option absolutely nothing happens. Well, the hard disk makes a short noice, and then nothing, zip, nada.

Is this a general problem with OpenOffice 2 (on Linux), or is it a problem with the unofficial debs?

I tried starting the program with "sudo", but the Wizard was just as dead then.

---

### Post by foxy123 on 2005-10-26
[QUOTE=bertilow]I successfully installed OpenOffice 2 using the above method (more or less - I used Synaptic).

Everything works as it should ... except for the Wizard "Install new dictionaries". When I click on that menu option absolutely nothing happens. Well, the hard disk makes a short noice, and then nothing, zip, nada.

Is this a general problem with OpenOffice 2 (on Linux), or is it a problem with the unofficial debs?

I tried starting the program with "sudo", but the Wizard was just as dead then.[/QUOTE]
I use the version from linux.cz and it opens the wizard without any problem Actually the wizard itself a Ooo file with macros. You can d/l it from the web and open in OpenOffice and it will work. The file called I guess DicOOo.sxw you may try to find it on your PC first.

---

### Post by pjs_flyer on 2005-10-26
Not that I'm chicken, but any idea when the official deb is likely to appear in the repositories?

P.

---

### Post by christooss on 2005-10-26
You can install dictonaries through synaptic!!

---

### Post by rwabel on 2005-10-26
can you? I was looking in synaptic but couldn't find a thing for OO2

---

### Post by bertilow on 2005-10-26
[QUOTE=foxy123]I use the version from linux.cz and it opens the wizard without any problem Actually the wizard itself a Ooo file with macros. You can d/l it from the web and open in OpenOffice and it will work. The file called I guess DicOOo.sxw you may try to find it on your PC first.[/QUOTE]

There was no file named "DicOOo.sxw" in my computer. So there is obviously something wrong with the debs. But I found the file using Google, and it worked. Thanks for the help!

---

### Post by berserker on 2005-10-26
[QUOTE=bertilow]There was no file named "DicOOo.sxw" in my computer. So there is obviously something wrong with the debs. But I found the file using Google, and it worked. Thanks for the help![/QUOTE]

I installed the deb packages and found the file in /opt/openoffice.org2.0/share/dict/ooo/DicOOo.sxw

Interesting.

---

### Post by bertilow on 2005-10-26
[QUOTE=berserker]I installed the deb packages and found the file in /opt/openoffice.org2.0/share/dict/ooo/DicOOo.sxw

Interesting.[/QUOTE]

In my Kubuntu that is "/usr/lib/openoffice2/share/dict/ooo" - but there are no ".sxw" files in there.

---

### Post by IdoMcFly on 2005-10-28
I have this problem : 
[http://www.ubuntuforums.org/showthread.php?t=82221](http://www.ubuntuforums.org/showthread.php?t=82221)

---

### Post by soonindallas on 2005-10-28
anyone know when OOo 2.0 is likelt to show up in the repositories ?

---

### Post by christooss on 2005-10-28
When dapper will be in development stage. Zhen OOo2.o will be in backports

---

### Post by soonindallas on 2005-10-28
you're s****ing me.  you mean Breezy shipped with a beta and will not make the stable version of OOo available through Breezy repo's ?  2.0 of OOo came out 10 days after Breezy stable shipped.

---

### Post by christooss on 2005-10-28
True it really bad. But this is Ubuntu policy. And since backports are OFFICIAL its not such a problem

---

### Post by foxy123 on 2005-10-29
[QUOTE=soonindallas]you're s****ing me.  you mean Breezy shipped with a beta and will not make the stable version of OOo available through Breezy repo's ?  2.0 of OOo came out 10 days after Breezy stable shipped.[/QUOTE]
personally I am not looking forward to it. The Ubuntu Ooo look is horrible to my taste. An also I get used to some things which I different from official Ooo version (like delete contents with backspace and have a Delete options with Del, which is vice versa in Ubuntu version).

---

### Post by kevin_hill54 on 2005-10-30
Great info.

This was very simple to install.

I removed all of the original OO as it had a problem locating the files and would not run.

Following the install the program runs fine. Version 1.9.79.2 but the dictionary did not load. The spell check works but no dictionary.

I ran the file Dic00o.sxw and it downloaded the files.

On restart of OO there is still no dictionary?

Any ideas?

Thanks for your help

Kevin

---

### Post by christooss on 2005-10-30
You have to go to Tools > Options > Language  Settings ... and there choose your language

---

### Post by kevin_hill54 on 2005-10-31
Perfect.

Thanks for your help.

Kevin

---

### Post by Aeon17x on 2005-11-01
The icons in the OpenOffice.org Help apparently don't exist, so they don't show up other than a placeholder with the name of the icon... also the Media Player in  the Tools menu isn't there. I also didn't get the new shiny icons. =/ My method of installation was through Synaptic, you think I did something wrong there and should reinstall the whole thing?

---

### Post by christooss on 2005-11-01
yes Icons are from ubuntu. That sucks. And look is from ubuntu to. And it sucks. And  I stil&#269;&#269; don't know how to make OOo 2.0 from repositories look like one from original page.

---

### Post by Aeon17x on 2005-11-01
[QUOTE=christooss]yes Icons are from ubuntu. That sucks. And look is from ubuntu to. And it sucks. And  I stil&#269;&#269; don't know how to make OOo 2.0 from repositories look like one from original page.[/QUOTE]
Hey, I like the Ubuntu look, although I wish the buttons were a bit smaller. And I also want the rainbow OO.o icons. :(

---

### Post by manicka on 2005-11-03
This How-To is also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by aledie on 2005-11-03
[QUOTE=Aeon17x]Hey, I like the Ubuntu look, although I wish the buttons were a bit smaller. And I also want the rainbow OO.o icons. :([/QUOTE]

Guys, why not just go to Tools-->Options-->View, and change the icons to default or crystal and size to small.

---

### Post by christooss on 2005-11-03
First one is writer from RPMs and second one is from repositories.

I WANT first look

---

### Post by rwabel on 2005-11-03
[quote=aledie]Guys, why not just go to Tools-->Options-->View, and change the icons to default or crystal and size to small.[/quote]
great tip! thanks
are there other styles to install? I love the crystal version :-)

---

### Post by morvael on 2005-11-03
What can I do as I get the following error while trying to apt-get install openoffice2?

```

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
  openoffice.org2: Depends: openoffice.org2-core (> 2.0) but it is not going to be installed
                   Depends: openoffice.org2-writer but it is not going to be installed
                   Depends: openoffice.org2-calc but it is not going to be installed
                   Depends: openoffice.org2-impress but it is not going to be installed
                   Depends: openoffice.org2-draw but it is not going to be installed
                   Depends: openoffice.org2-math but it is not going to be installed
                   Depends: openoffice.org2-base but it is not going to be installed
E: Broken packages

```

I have completely removed openoffice2 packages before this as I got some other error.

---

### Post by manicka on 2005-11-03
[QUOTE=christooss]
I WANT first look[/QUOTE]

Setting the icons to default and small looks like that

---

### Post by christooss on 2005-11-03
Manicka thanks for the icons. Now how can I get rid of this grey color. I want brown. I LOVE brown

---

### Post by manicka on 2005-11-03
[QUOTE=christooss]Manicka thanks for the icons. Now how can I get rid of this grey color. I want brown. I LOVE brown[/QUOTE]

I use a variation of this

[http://gnome-look.org/content/show.php?content=29684](http://gnome-look.org/content/show.php?content=29684)

---

### Post by christooss on 2005-11-03
What does gnome theme got to do with OOo look?

---

### Post by aledie on 2005-11-04
[QUOTE=rwabel]great tip! thanks
are there other styles to install? I love the crystal version :-)[/QUOTE]
Couldn't find any, however the folder where the styles reside is:
/usr/lib/openoffice2/share/config

---

### Post by manicka on 2005-11-04
[QUOTE=christooss]What does gnome theme got to do with OOo look?[/QUOTE]

You said that you wanted it browner and less grey. This theme makes Ooo2 browner.

[IMG]http://img492.imageshack.us/img492/9449/screenshotuntitled1openofficeo.png[/IMG]

---

### Post by veloct on 2005-11-04
My icons stayed the same although it did upgrade to version 2.0.  Is there any way to change the icons to the cool colorful ones?

---

### Post by christooss on 2005-11-04
Yes through Smeg

---

### Post by veloct on 2005-11-05
Anybody know where the installation puts the pixmaps for OOo2?  I can't find them.

---

### Post by paolino73 on 2005-11-05
Where is the "desktop-intergration" dir/?
Can you give me the path..
thanx

---

### Post by christooss on 2005-11-05
It in tar ball which includes RPMs.

---

### Post by christooss on 2005-11-06
I addded installation from DEB's

---

### Post by guilag on 2005-11-06
Thanks a lot, I was impatient to upgrade to the final release of openoffice 2.0 and could only find the 1.9.129 beta 2 version in the ubuntu package list !

---

### Post by XDevHald on 2005-11-06
Just a quick heads up, this is not stable enough in Dapper Drake 6.04, so please note that before you upgrade to dapper.

**Note:** The icons and list for OO2 does not show up in the Office menu.

---

### Post by cowboycamilo on 2005-11-07
hey!!!! thanx, works great!!! but ther are  two things that is not working, one the GTK integration... i simply love GTK, is there anything that I can do to get the GTK working with oo2, i really mis the look...
the other thing is that now I have doble icons on mi panel, the oo2 and the oo1.9, the oo2 icon lounch the program ok, the others are obiusly not working... I looked in synaptic but only oo2 is intaled.... HELP..

but hey, thanX againg, oo2 working very good...

---

### Post by christooss on 2005-11-08
GO to synaptic and remove all open office packages . And than install open office through repositories.

or

```
sudo apt-get remove openoffice*
```

And than

**[COLOR="SeaGreen"]1.[/COLOR][COLOR="Red"] Installation from repositories[/COLOR]**

1. Open your sources.list and add this line in

```
deb http://people.ubuntu.com/~doko/OOo2 ./
```

AMD64 and ppc

You can help your self with these repositories

```
   deb http://people.ubuntu.com/~doko/OOo2-amd64 ./
   deb http://people.ubuntu.com/~doko/OOo2-powerpc ./
```
2.1 Do a update and upgrade

```
sudo apt-get update
sudo apt-get upgrade
```

This all will upgrade your previous version 1.9.129.

2.2 If you removed any OpenOffice.org installation from disk than simpli do a

```
sudo apt-get install openoffice.org2
```

:)

---

### Post by jamaas on 2005-11-08
I've installed 2.0 using synaptic and it all seems to work except I don't have a spell checker and I don't have any available language modules.  I've tried downloading and installing the 3 language modules using dpkg and they installed ok but still no luck.

Anyone tell me what I've done wrong?

Thanks and Regards

Jim

---

### Post by bertilow on 2005-11-08
[QUOTE=jamaas]I've installed 2.0 using synaptic and it all seems to work except I don't have a spell checker and I don't have any available language modules.  I've tried downloading and installing the 3 language modules using dpkg and they installed ok but still no luck.

Anyone tell me what I've done wrong?[/QUOTE]

First try the Wizard: File -> Wizards -> Install new dictionaries.

If the Wizard is dead (he was for me), then try this document:

[http://openoffice.mirrors.tds.net/pub/openoffice/contrib/dictionaries/dicooo/DicOOo.sxw](http://openoffice.mirrors.tds.net/pub/openoffice/contrib/dictionaries/dicooo/DicOOo.sxw) 

Download it, and then open it with Ooo. It should help you install dictionaries for spell checking. Afterwards you'll need to shut down Ooo, and restart it, and maybe activate the new dictionary in Options.

A lot of bother, but it's possible.

---

### Post by canadianwriterman on 2005-11-08
Excellent HOWTO, Christooss. I upgraded to 2,0 last night and it worked like a charm.

[QUOTE=christooss]In repositories you can find only 1.9.129 - RC2 version so here is how you instal pure 2.0 on your system

**[COLOR="SeaGreen"]1.[/COLOR][COLOR="Red"] Installation from repositories[/COLOR]**

1. Open your sources.list and add this line in

```
deb http://people.ubuntu.com/~doko/OOo2 ./
```

AMD64 and ppc

You can help your self with these repositories

```
   deb http://people.ubuntu.com/~doko/OOo2-amd64 ./
   deb http://people.ubuntu.com/~doko/OOo2-powerpc ./
```
2.1 Do a update and upgrade

```
sudo apt-get update
sudo apt-get upgrade
```

This all will upgrade your previous version 1.9.129.

2.2 If you removed any OpenOffice.org installation from disk than simpli do a

```
sudo apt-get install openoffice.org2
```

BEWARE this are test packages :) But they simply work :)

**[COLOR="SeaGreen"]2.[/COLOR] [COLOR="Red"]2.0.0 version installed from DEB's[/COLOR]**
1. Download english version with wget

```
wget ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_LinuxIntel_install_en-US_deb.tar.gz
```

2. Extract file
```
tar -xzfv OOo_SRC680_m137_LinuxIntel_install_en-US_deb.tar.gz
```

4. Installation

Go to dir with debs and perform

```
sudo dpkg -i *.deb
```

5. Native language instalation

Download your language package from [ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_native_LinuxIntel_langpacks_deb](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m137/Build-2/OOo_SRC680_m137_native_LinuxIntel_langpacks_deb)
There are three packages. Donwload them all

Then install them with

```
sudo dpkg -i *.deb
```
**[COLOR="SeaGreen"]3. [/COLOR][COLOR="Red"]2.0.0 version installed from RPM's[/COLOR]**

1. Download
Download Linux file from OpenOffice.org just choose linux when it asks you for your platform. You can use bittorrent you can find when you choose server from which you download.

2. Extract tar.gz file

```
tar -xzfv OOo_2.0.0_LinuxIntel_install.tar.gz
```

3. Aliens in Ubuntu

With alien you transform all rpms to debs.

pit your self in RPMS subdir of directrory you just created and than execute

```
sudo alien *.rpm
```
or
```
fakeroot alien*.rpm
```
Wait till all the packages are transformed

4. Installation

Now performe this command
```
sudo dpkg -i *.deb
```
5. Put Openoffice in your gnome menu

Go in to desktop-integration dir and execute
```
sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb
```
and than
```
 killall gnome-panel
```

Now you should have new icons in you Programs/office menus


**[COLOR="SeaGreen"]4. [/COLOR][COLOR="Red"]RC3 version - easyer to insta[/COLOR]ll** :)
1. Download
Download Linux file

```
wget http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz
```

2. Extract tar.gz

Extract file with

```
tar xzfv OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz
```

4. When all packages are transformed execute. First o to DEBS derictory which has been created

```
cd DEBS/
```
```
sudo dpkg -i *.deb
```
and wait for all the packages to get install

5. Restart gnome-panel
```
killall gnome-panel
```

Now you will have menus shortcuts. But they will be dubled use OpenOffice 2.0 ... ones
[IMG]http://www.ahacic.5gigs.com/screenshots/menuji.jpg[/IMG]
pressing any of this options will show you splash screen
[IMG]http://www.ahacic.5gigs.com/screenshots/splash.jpg[/IMG]

Enjoy your OpenOffice.org 2.0[/QUOTE]

---

### Post by j_baer on 2005-11-08
Here is an alternate method which installed everything including the Thesaurus.

The link is ...

[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)

I first uninstall the current OOo and then downloaded the "OOo_SRC680_m138_LinuxIntel_install_en-US_deb.tar.gz" file, extracted to a temporary folder, and ran "*sudo dpkg -i **"

Cheers  :)

---

### Post by christooss on 2005-11-08
j_baer I already added this in howto :P

Everybody who installed OOo from repositories!!!!
Langage packs are in repositroies. I think :)

---

### Post by christooss on 2005-11-08
Yes it is :)

Just install openoffice2-l10n-XX (XX is your language code)

---

### Post by christooss on 2005-11-08
And you still have to change language from English.

Go to Tools > Options > Language settings

---

### Post by j_baer on 2005-11-08
christooss,

Sorry for the reduntant post. What is the situation with the Thesaurus?

j_baer

---

### Post by Beire on 2005-11-09
i'm still having this problem 
```
/etc/openoffice.org-2.0/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/etc/openoffice.org-2.0/program/soffice.bin: error while loading shared libraries: libcomphelp4gcc3.so: cannot open shared object file: No such file or directory

```

i read some somelutions here but they are very vage to my liking.

---

### Post by yesplease on 2005-11-10
With Synaptic one can choose that only open-office packages will be upgraded, while sudo apt-get upgrade will upgrade everything (depending on which repositories are open). Please, correct me if I am wrong.

Anyway, method 1 seems very easy, why would anyone choose one of the other methods?

---

### Post by christooss on 2005-11-10
I choose deb over repositories beacause of the look and default menu icons :)

Other paths to install OOo are still there so you can choose :) And that you can upload OOo from backports which are offical ubuntu :) I makeing this up so.... :)

---

### Post by sherwindennis on 2005-11-10
help pls!

i installed the openoffice, i have the shortcuts but it won't launch. 

please help me, ubuntu experts!

---

### Post by christooss on 2005-11-11
try running openoffice2 -writer in terminal and give us an error

---

### Post by foxy123 on 2005-11-11
[QUOTE=sherwindennis]help pls!

i installed the openoffice, i have the shortcuts but it won't launch. 

please help me, ubuntu experts![/QUOTE]
you may also take a look at ~/.gnome/apps. If you've got ooo menu files there, delete them.

---

### Post by sherwindennis on 2005-11-12
Thanks for replying  but i got the answer from jeremie's post....
______________________________________________________________
[email]jeremie@desktop:/opt/openoffice.org[/email]2.0/program$ ls -l soffice
----------  1 root root 6485 2005-10-15 10:02 soffice
[email]jeremie@desktop:/opt/openoffice.org[/email]2.0/program$ sudo chmod o=rx soffice
[email]jeremie@desktop:/opt/openoffice.org[/email]2.0/program$ ls -l soffice
-------r-x  1 root root 6485 2005-10-15 10:02 soffice
_________________________________________________________________

I only need to change oo2 permission. :)

---

### Post by nomeat on 2005-11-12
I have been frustrating around with this for more than half a day.
First I tried with synaptic but it can not find a few files even after apt-get update and manually editing my repository list.

Then I tried version one and after over an hour and downloading over 200MB I get 
broken files.
There are about 100MB more in my hard drive.
Why do I get broken files and how do I get rid of them again?

---

### Post by nomeat on 2005-11-12
Here are some of my errors:

Fetched 206MB in 1h9m36s (49.2kB/s)
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main) /binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb  404 Not Found

...and many more like that

further down:

The following packages have unmet dependencies:
  openoffice.org2: Depends: openoffice.org2-core (> 2.0) but it is not going to be installed
                   Depends: openoffice.org2-writer but it is not going to be ins talled
                   Depends: openoffice.org2-calc but it is not going to be insta lled
                   Depends: openoffice.org2-impress but it is not going to be in stalled
                   Depends: openoffice.org2-draw but it is not going to be insta lled
                   Depends: openoffice.org2-math but it is not going to be insta lled
                   Depends: openoffice.org2-base but it is not going to be insta lled
E: Broken packages


Then I try as a test:
root@computer:/home/computer # sudo apt-get install openoffice.org2-core
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
  openoffice.org2-core: Depends: openoffice.org-debian-files (>= 1.1.4-3+2ubuntu4) but 1.1.3-3+1ubuntu1 is to be installed
                        Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu13 is to be installed
                        Depends: libcurl3 (>= 7.13.1-1) but 7.12.3-2ubuntu3 is to be installed
                        Depends: libgcc1 (>= 1:4.0.1) but 1:4.0-0pre6ubuntu7 is to be installed
                        Depends: libmyspell3c2 but it is not installable
                        Depends: libportaudio0 but it is not installable
                        Depends: libstartup-notification0 (>= 0.8-1) but 0.8-0ubuntu1 is to be installed
                        Depends: libstdc++6 (>= 4.0.1) but it is not going to be installed
                        Depends: libstlport4.6c2 but it is not installable
                        Depends: libxml2 (>= 2.6.20) but 2.6.17-0ubuntu1 is to be installed
                        Depends: openoffice.org2-java-common but it is not going to be installed
E: Broken packages


Any help would be much appreciated
Thanks.

---

### Post by nomeat on 2005-11-12
and here are some entries in my repositores list that should point to that missing  files above:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


...but whatever I do I can't seem to download them.

---

### Post by christooss on 2005-11-12
Why hoary repositories?

---

### Post by nomeat on 2005-11-12
So where do I get the missing files?

like libgcc1-4 and libstdc++6 and gcc-4.0

Synaptic reports that they can't be found
and apt-get update doesn't help either.

---

### Post by christooss on 2005-11-12
breezy repositories?

---

### Post by nomeat on 2005-11-14
So then it is not possible to install open office 2 on a 5.04 system with KDE 3.4?

I tried changing to breezy repo's and updating and ugrading but it just crashed.
Luckily my system didn't take any damage.

---

### Post by foxy123 on 2005-11-14
[QUOTE=nomeat]So then it is not possible to install open office 2 on a 5.04 system with KDE 3.4?

I tried changing to breezy repo's and updating and ugrading but it just crashed.
Luckily my system didn't take any damage.[/QUOTE]
if you are on Hoary, try to use deb method described in the first post. It should work (at least it always worked for me when I was on Hoary).

---

### Post by donpaolo on 2005-11-14
There is a little dependency bug in ooo2 package.

I actually have es localization installed, I don't need the en one.

But when I intall ooo2 it install mandatoryly the en loc.

---

### Post by donpaolo on 2005-11-14
Please correct Openofice to Openoffice (2 f) in the thread title

---

### Post by christooss on 2005-11-14
Deb method works with breezy flawlessly

---

### Post by nomeat on 2005-11-14
[QUOTE=sherwindennis]help pls!

i installed the openoffice, i have the shortcuts but it won't launch. 

please help me, ubuntu experts![/QUOTE]


I managed to get something installed with the deb files and have shortcuts too
but nothing executes. The symbol just bounces for half a minute and dissapears again.

How do I start it in terminal?
I can't see anything that looks executable in the openoffice dir.
What should I look for?

I don't think I have a permission issue and that gnome dir has no OO related files in it.

---

### Post by N8K99 on 2005-11-15
fantastic job on the HOWTO. I was able to use apt-get to upgrade just fine. Since I have already yanked Gnome off and use Enlightenment the menus update was a cinch too. I only wish teh Firefox 1.5rc were this easy!! :p

---

### Post by christooss on 2005-11-15
nomeat:  openoffice-2.0 -writer
openoffice-2.0 -calc etc

---

### Post by nomeat on 2005-11-15
File not found

Tried reinstalling the debs again and saw a lot of errors in the log like:


Unpacking replacement openoffice.org-core04 ...
dpkg-deb: unexpected end of file in version number in openoffice.org-core04u_2.0.0-137_i386.deb
dpkg: error processing openoffice.org-core04u_2.0.0-137_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2

and

dpkg: error processing openoffice.org-writer (--install):
 dependency problems - leaving unconfigured

I am really out of luck with this one.


Looks like it is back to micro$ but I would hate that.
Trying another distro and starting all over again, no thanks.

---

### Post by christooss on 2005-11-15
sudo apt-get remove openoffice*

And than install debs again or try installing it through repositories

---

### Post by nomeat on 2005-11-15
Christoss, I am really stuck here.
It won't remove.
I think that is because apt-get is asking for horary again.
My system wouldn't upgrade to breezy.
Is there another way to remove or uninstall the deb installation without using the repositories?

---

### Post by confused on 2005-12-22
check this website. it may have some answers. I am also in the same problem.
[http://documentation.openoffice.org/setup_guide2/2.x/en/SETUP_GUIDE.pdf](http://documentation.openoffice.org/setup_guide2/2.x/en/SETUP_GUIDE.pdf)

---

### Post by everbot on 2005-12-27
Hi everyone !!

Answering to Nomeat problem (hope he doesn't lost his hopes on Ubuntu)

* to uninstall the openoffice .deb files, just do this: 

sudo dpkg -P openoffice.org-base openoffice.org-calc openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org-draw openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-impress openoffice.org-javafilter openoffice.org-math openoffice.org-pyuno openoffice.org-spellcheck openoffice.org-testtool openoffice.org-writer openoffice.org-xsltfilter

* and then:

sudo dpkg -P openoffice.org-debian-menus

* If you install language packages:

sudo dpkg -P openoffice.org-es openoffice.org-es-help openoffice.org-es-res

* (Or the language you install instead "es")

Then uninstall everthing of openoffice from Synaptic

Download the .tar.gz file again from [www.openoffice.org](www.openoffice.org) and install it again !! 

:rolleyes: and thats that !! Openoffice is out of your system !!

By the way, i have a question too, i want the openoffice nice look instead the ugly one, i enter to Tools >> Options >> View , But find anything about the icons, just about the size of the icons, nothing else :( .

So then, how do i change the looks ? I install openoffice from .rpm files, but the look still the same !! why could that be ? 
Someone halp me please

Greetings from Mexico !! Bye !!

---

### Post by manicka on 2005-12-29
[QUOTE=nomeat]Christoss, I am really stuck here.
It won't remove.
I think that is because apt-get is asking for horary again.
My system wouldn't upgrade to breezy.
Is there another way to remove or uninstall the deb installation without using the repositories?[/QUOTE]

You should be able to remove it effectively with Synaptic

---

### Post by 4ebees on 2006-05-12
Christooss,

Thanks for that. Your first suggestion worked for me.

Much appreciated.

---

### Post by Pjotor on 2006-05-13
Well,

if you use Automatix you can get OOo 2.0.1 and the msttcorefonts...

[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix]("http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix")

---

### Post by MikeMLP on 2006-07-22
First off, sorry to bump up an old thread, however...

I used this guide to try and install openoffice.org 2.03 along side openoffice.org 2.02, and the method described here worked fine until the point where I install the menus.  

```
mike@Ubuntu:~/Desktop/OOC680_m7_native_packed-1_en-US.9044/RPMS/desktop-integration$ sudo dpkg -i openoffice.org-debian-menus_2.0.3-2_all.deb 
dpkg: regarding openoffice.org-debian-menus_2.0.3-2_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.0.3-2_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.0.3-2_all.deb

```

Anybody know what this is all about, and how to resolve?

thanks!

---

### Post by whitegorilla on 2006-07-25
Thought I'd bump this as I want to upgrade to 2.0.3

---

