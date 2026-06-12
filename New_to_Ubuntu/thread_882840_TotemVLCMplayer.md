---
title: "Totem/VLC/Mplayer?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by anthonyglamis on 2008-08-07
Ok I have an issue with Totem as with a bunch of searching am understanding many people have issues as well.  I have read that it's a better option to install VLC or Mplayer.  Here is the deal.    I am in Iraq and am on my computer at work.  I want to be able to watch movies on my laptop but cannot.  I have Ubuntu loaded on it.  I do not have internet capabilities for my laptop.  How do I make this happen?
I am sorry as I am new to Linux and might need a write up.  I have read that I will need a .deb file?  Any info would be great.  Thanks in advance.

---

### Post by Bachstelze on 2008-08-07
For this purpose, .deb files can be thought of as equivalent to Windows' EXE files. In Windows, when you want to install a program, youdownload the installation EXE file, run it, and you're done. You can use a somewhat similar approach in Ubuntu, dy downloading and installing the DEB packages yourself, instead of letting the package manager do if for you.

The official Ubuntu packages can be downloaded from [http://packages.ubuntu.com/](http://packages.ubuntu.com/). Just search for the package you want, and download the DEB that matches your architecture.

However, you will have a problem when you'll need to install dependencies. To get rid of it, you can use a nice little CD made by a member of the French Ubuntu community, that contains everything you need to install vlc, mplayer and many more applications. There is a [tutorial](http://doc.ubuntu-fr.org/addon_cd), which is in French but the screenshots should make it easy to understand nevertheless.

---

### Post by anthonyglamis on 2008-08-07
Wow,
  Thanks for your help.  I have to be honest I am still quite confused.  There seem to be a million packages and I'm not sure I follow which particulars I might have to download and install.  Then I will also have to go about installing dependencies?  Interesting.  What would a dependency be?  Additional plug ins so to speak?  Would I be better off just trying to find a full disk with the deb files and dependencies all on the disk?  
  Who would have thought just installing a media type player would be so difficult without an internet connection....I'm really wishing I could just go through the terminal.  Ok I'll do some reading and see if any of this makes sense to me.  Thanks again for the help.

---

### Post by anotherdisciple on 2008-08-07
I prefer VLC... if you want to do things the easy way... just open your terminal (Applications > Accessories > Terminal) and type:

```
sudo aptitude install vlc
```

That will install VLC and handle all of the dependencies for you.

A .deb package contains information about all the dependencies... it should automatically retrieve them for you.

You may need to do a few things to do a few things to play all types of video files. I am not sure if VLC needs this or not, but it couldn't hurt to do this... let me list it off for you... Open the terminal and type:

```
sudo gedit /etc/apt/sources.list
```
It will ask you for your password (you can't see it being typed). That will open up a text editor (kind of like notepad in windows). It has all of your software sources. Now delete the "#" from the front of lines that start with "deb". That will allow you to download extra things from ubuntu's servers... like restricted codecs, etc. Close it and save. (Also, make sure not to delete the "#" signs in front of all the paragraphs about what each source is for.)

now if you need VLC and all the media codecs, type this in the terminal:
```
sudo aptitude install vlc ubuntu-restriced-extras
```

Also, firefox on ubuntu uses the totem plugins... so you may want to uninstall totem... the totem firefox plugins, and install the vlc firefox plugins. Let me know if you want to know how to do that.

---

### Post by gerben1 on 2008-08-07
Those commands will not work if you don't have an internet connection...

However, in case the program is on the Ubuntu cdrom you can make them work by adding the Ubuntu Cdrom to the list of repositories.
System->Administration->Software sources
then on the tab "Third-Party Software" check the box:
cdrom:[ubuntu etc.

insert the Ubuntu install disc and run your apt-get commands.

---

### Post by eluis.c on 2008-08-07
I would like to know how to uninstall the totem plugin and install the vlc plugin

---

### Post by zvacet on 2008-08-07
@ **anthonyglamis**

Best suggestion comes from **HymnToLife** an addon CD.

@ **eluis.c**

In synaptic find totem plugin and mark it for complete removal.Find vlc-plugin and mark it for install.

---

### Post by anthonyglamis on 2008-08-08
Actually I will not be able to download the cd addon to my computer at work as it is too big a file and I run the risk of getting into trouble.  
I think I might understand the install but am still unclear of the commands.  I did download the vlc package but have absolutely no idea how to install it once i have extracted it.  
1. get the vlc debian package.  How do I install this if I downloaded the package to my desktop and extracted it to /media/sda1 ?
2. install the package via a .deb file?  Once again I have searched through the whole extracted folder and cannot seem to find a .deb file or .tar file.  If I did see this file do I just double click it?
3. Download dependecies.  Will these be .deb files as well?  Same deal double click them?

---

### Post by anotherdisciple on 2008-08-08
oops... skipped over the no internet part!

---

### Post by gerben1 on 2008-08-08
> **anthonyglamis said:**
> Thank you for all the responses.  I am in the process of downloading the cd addon that was suggested.  I will repost with an update to see how this works. 
I might as well ask while I'm posting.  Once I have this cd, how do I install the programs I wish to install?  Is it as simple as double clicking the folder it comes in or do I have to look for a .deb file or a .tar file? Once I find that file is that all I will need to do?  I have to say that I really enjoy using ubuntu and am really trying to get my head around this operating system.  The help here is awesome to say the least.  Thanks again and have a good day.

You will need to add that add-on CD to the software repositories in which Ubuntu will search for available software. Then when you try to install a program, Ubuntu will also search the contents of that CD-ROM (if it is in the drive) for the installation packages.

So, two steps you need to know:
(1) How to add the CDRom to the list of repositories (also called "Software Sources")
(2) How to install something that is available in one of the repositories.

(1)
Goto: System->Administration->Software Sources, in the Tab "Third-party Software" click on the button "Add CD-Rom", then insert your add-on cdrom, and follow the rest of the procedure that it will take you trough.

(2)
There are a few different ways to work with the repositories, 
- you can use the command line command "apt-get"
- you can use the GUI program "System->Administration->Synaptic Package Manager"
- you can use the GUI program "Applications-> Add/Remove"
Via all three of these you can, install and uninstall packages, search whether a certain package is available, get some information on the files in the package etc.

---

### Post by gerben1 on 2008-08-08
> **anthonyglamis said:**
> Actually I will not be able to download the cd addon to my computer at work as it is too big a file and I run the risk of getting into trouble.  
I think I might understand the install but am still unclear of the commands.  I did download the vlc package but have absolutely no idea how to install it once i have extracted it.  
1. get the vlc debian package.  How do I install this if I downloaded the package to my desktop and extracted it to /media/sda1 ?
2. install the package via a .deb file?  Once again I have searched through the whole extracted folder and cannot seem to find a .deb file or .tar file.  If I did see this file do I just double click it?
3. Download dependecies.  Will these be .deb files as well?  Same deal double click them?

.deb files are simply Debian package files, Ubuntu also uses this type of packages. If you double click on a .deb file in Ubuntu a package installer will start and will install the package. 

So if you download a .deb file containing Vlc, you just need to copy that .deb file to you ubuntu computer and double click it. It is possible that Vlc will need programs or libraries that are in other .deb packages. These are called "dependencies for Vlc" as Vlc depends on them in order to work properly. So you will also need the .deb files that contain those dependencies.

---

### Post by AndyCooll on 2008-08-08
> **anthonyglamis said:**
> Actually I will not be able to download the cd addon to my computer at work as it is too big a file and I run the risk of getting into trouble.  
I think I might understand the install but am still unclear of the commands.  I did download the vlc package but have absolutely no idea how to install it once i have extracted it.  
1. get the vlc debian package.  How do I install this if I downloaded the package to my desktop and extracted it to /media/sda1 ?
2. install the package via a .deb file?  Once again I have searched through the whole extracted folder and cannot seem to find a .deb file or .tar file.  If I did see this file do I just double click it?
3. Download dependecies.  Will these be .deb files as well?  Same deal double click them?
It seems to me that what you have isn't a "Debian" file as talked about in previous replies. A Debian file is usually called something like vlc-0.8.6i.deb. It doesn't require extracting, you should just be able to double-click on it (as you used to do with an exe) and away you go.

However, I can understand your confusion because the vlc website doesn't only gives instructions for installation related to the official Ubuntu repos.

So ...what file have you downloaded? And where did you download it from?

:cool:

---

### Post by zipperback on 2008-08-08
Install VLC, it will handled just about every format you could possibly want.

- zipperback
:popcorn:

---

### Post by anthonyglamis on 2008-08-08
Ok maybe I did not download the correct file after all.  Good to know I'm not completely going insane.  I downloaded the file I have from vidoelan.org.  I am not at my pc right now but it was something along the lines of vlc-0.8.6.tar or something like that.  After extracted a folder was created named vlc-0.8.6h.  
I guess I need to search for a vlc.deb on google huh?  Any suggestions?

update it was vlc-0.8.6.tar.gz this was the file i downloaded.  I cannot seem to find a .deb anywhere in it however.

---

### Post by gerben1 on 2008-08-08
The tar.gz file contains the source code, you can extract it and than compile the program yourself.

---

### Post by gerben1 on 2008-08-08
You can dowload the debian package from here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

looks a bit intimidating perhaps, but isn't really, just search ("Search the contents of packages") for VLC  and you will get to this page:

[http://packages.ubuntu.com/search?searchon=contents&keywords=vlc&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=vlc&mode=exactfilename&suite=hardy&arch=any)

in that page click on "Vlc" in column "packages"

you'll go to this page:

[http://packages.ubuntu.com/hardy/vlc](http://packages.ubuntu.com/hardy/vlc)

on the very bottom of that page you can dowload a .deb packge of vlc, just choose the i386 link if you run normal Ubuntu or choose amd64 if you run the 64bit version.

---

### Post by Vorian Grey on 2008-08-08
> **zipperback said:**
> Install VLC, it will handled just about every format you could possibly want.

+1 It's all you need.

---

