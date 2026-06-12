---
title: "How do I install Skype on the Dell Mini?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by dblxx on 2008-11-23
I did a search on Skype and it seems to be a difficult install?  If I am new to Ubuntu should I not mess around and try to install it?

Also...how do you get in and out of the command window?

Thanks

---

### Post by diablo75 on 2008-11-23
It's EASY to install.  See my signature for instructions.  (And you don't need to use the terminal either).

---

### Post by semitone36 on 2008-11-23
By command window do you mean the terminal? If so just go to Applications -> Accessories -> Terminal.

---

### Post by CatKiller on 2008-11-23
> **dblxx said:**
> Also...how do you get in and out of the command window?

Applications -> Accessories -> Terminal for just a terminal window.

Ctrl-Alt-F1 for a virtual console (Alt-F7 to get back).

---

### Post by dblxx on 2008-11-23
> **diablo75 said:**
> It's EASY to install.  See my signature for instructions.  (And you don't need to use the terminal either).

Says "wrong arcitecture i386" ????

---

### Post by earthpigg on 2008-11-23
> **dblxx said:**
> Says "wrong arcitecture i386" ????

searched google for:

> 64 bit ubuntu install skype

this was the first result:

[http://ubuntuforums.org/showthread.php?t=432295]("http://ubuntuforums.org/showthread.php?t=432295")

:)

---

### Post by diablo75 on 2008-11-23
Try pasting this into your terminal.  It will add the medibuntu repositories to your sources list and allow you to install skype at the command line with apt-get.  I've put this together just for you:

```
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p bluez-alsa && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install -y --force-yes medibuntu-keyring && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install skype
```

This is based upon this guide:  [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

Simply copy and paste all that code into a terminal window (be sure you select all of it before copying) and then paste it using either CTRL-Shift-V or Edit>Paste.

Let us know if it works.

---

### Post by dblxx on 2008-11-23
Went to the terminal and put in that link (the whole thing) and it ran a series of things and after 45 seconds it was done.  I went back to your link and ran the deb.  Still got the same error code.

---

### Post by phantomgunex on 2008-11-23
Its quite easy just download the deb. package and double click it once it is downloaded to install. SimpLE

---

### Post by diablo75 on 2008-11-23
You didn't need to do anything after pasting that code.  Skype should now be installed.  Look for it in Applications>Internet>Skype.

---

### Post by diablo75 on 2008-11-23
> **phantomgunex said:**
> Its quite easy just download the deb. package and double click it once it is downloaded to install. SimpLE

We're dealing with 64-bit ubuntu so it's not so cut and dry...

---

### Post by dblxx on 2008-11-23
Crud....not there.

I ran that command again....still nothing.

---

### Post by dblxx on 2008-11-23
Not sure if it matters I am on a Dell Mini-9 with 8.04.

---

### Post by diablo75 on 2008-11-23
Try typing

```
sudo apt-get install skype
```

And then copy and paste the text starting with the text that you paste in from the terminal into a reply back here so we can see what happens when you paste it in.

---

### Post by dblxx on 2008-11-23
> **diablo75 said:**
> Try typing

```
sudo apt-get install skype
```

And then copy and paste the text starting with the text that you paste in from the terminal into a reply back here so we can see what happens when you paste it in.

david@david:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
         Depends: libgcc1 (>= 1:4.3) but 1:4.2.3-2ubuntu7 is to be installed
         Depends: libqt4-dbus (>= 4.4.3) but it is not installable
         Depends: libqt4-network (>= 4.4.3) but it is not installable
         Depends: libqtcore4 (>= 4.4.3) but it is not installable
         Depends: libqtgui4 (>= 4.4.3) but it is not installable
         Depends: libstdc++6 (>= 4.3) but 4.2.3-2ubuntu7 is to be installed
         Depends: libv4l-0 but it is not installable

---

### Post by diablo75 on 2008-11-23
Lets try:

```
sudo apt-get install libqt4-core libqt4-gui && sudo apt-get install skype
```

---

### Post by dblxx on 2008-11-23
> **diablo75 said:**
> Try pasting this into your terminal.  It will add the medibuntu repositories to your sources list and allow you to install skype at the command line with apt-get.  I've put this together just for you:

```
wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p bluez-alsa && sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install -y --force-yes medibuntu-keyring && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install skype
```

This is based upon this guide:  [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

Simply copy and paste all that code into a terminal window (be sure you select all of it before copying) and then paste it using either CTRL-Shift-V or Edit>Paste.

Let us know if it works.

THEN FROM THE OTHER LINK.

david@david:~$ wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; sudo dpkg -i getlibs-all.deb; sudo getlibs -p bluez-alsa && sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install -y --force-yes medibuntu-keyring && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install skype
--21:05:16--  [http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
           => `getlibs-all.deb'
Resolving boundlesssupremacy.com... 209.123.149.151
Connecting to boundlesssupremacy.com|209.123.149.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,498 (6.3K) [text/plain]
Server file no newer than local file `getlibs-all.deb' -- not retrieving.

(Reading database ... 95353 files and directories currently installed.)
Preparing to replace getlibs 2.06 (using getlibs-all.deb) ...
Unpacking replacement getlibs ...
Setting up getlibs (2.06) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bluez-alsa
--21:05:24--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]

100%[=================================================================================>] 230           --.--K/s             

21:05:25 (6.54 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release                                    
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release              
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release                               
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release             
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages                                     
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages                                 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages                               
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages   
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages   
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources          
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources      
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources    
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources    
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources     
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources   
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources   
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages    
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources     
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources 
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg      
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release                               
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release             
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages                                     
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages             
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages  
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources         
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources     
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages       
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
         Depends: libgcc1 (>= 1:4.3) but 1:4.2.3-2ubuntu7 is to be installed
         Depends: libqt4-dbus (>= 4.4.3) but it is not installable
         Depends: libqt4-network (>= 4.4.3) but it is not installable
         Depends: libqtcore4 (>= 4.4.3) but it is not installable
         Depends: libqtgui4 (>= 4.4.3) but it is not installable
         Depends: libstdc++6 (>= 4.3) but 4.2.3-2ubuntu7 is to be installed
         Depends: libv4l-0 but it is not installable
E: Broken packages
david@david:~$

---

### Post by dblxx on 2008-11-23
Still not there.

david@david:~$ sudo apt-get install libqt4-core libqt4-gui && sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-core is already the newest version.
libqt4-core set to manually installed.
libqt4-gui is already the newest version.
libqt4-gui set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
         Depends: libgcc1 (>= 1:4.3) but 1:4.2.3-2ubuntu7 is to be installed
         Depends: libqt4-dbus (>= 4.4.3) but it is not installable
         Depends: libqt4-network (>= 4.4.3) but it is not installable
         Depends: libqtcore4 (>= 4.4.3) but it is not installable
         Depends: libqtgui4 (>= 4.4.3) but it is not installable
         Depends: libstdc++6 (>= 4.3) but 4.2.3-2ubuntu7 is to be installed
         Depends: libv4l-0 but it is not installable
E: Broken packages
david@david:~$

---

### Post by GuitarRocker2562 on 2008-11-23
you aren't running 64 bit ubuntu if your on a mini 9, by the way, how is the keyboard?

---

### Post by diablo75 on 2008-11-23
Well I'm stumped (and tired).  Anyone else have ideas?

---

### Post by dblxx on 2008-11-23
> **GuitarRocker2562 said:**
> you aren't running 64 bit ubuntu if your on a mini 9, by the way, how is the keyboard?

The keyboard is SMALL...and takes a bit of getting used to....but this little baby rocks.

---

### Post by GuitarRocker2562 on 2008-11-23
[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
did you try just downloading that and running it?

---

### Post by dblxx on 2008-11-23
> **diablo75 said:**
> Well I'm stumped (and tired).  Anyone else have ideas?

Not running 64 according to someone else...I have no idea what that means by the way.

---

### Post by dblxx on 2008-11-23
> **GuitarRocker2562 said:**
> [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
did you try just downloading that and running it?

Yeah...I get an error i386.

---

### Post by earthpigg on 2008-11-23
netbooks use an architecture different from both i386 and i386-64... i can't remember what it is called. that is what he meant when he told you that you weren't running 64 bit :)

don't mini 9's come preinstalled with skype?

---

### Post by GuitarRocker2562 on 2008-11-23
Okay, download from the link I gave you, then di the following (I got it from the skype forums.)

After initial excitement, I had resolution problems with the static build. So I used the actual official Ubuntu packages from Skype and forced the installation regardless of the architecture error. To do it:

1. Download the Ubuntu package1. Download the Ubuntu package
2. open terminal (menu Accessories)
3. move into the folder you downloaded the package
4. Type:

sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb

It should work.

My microphone, bundled with the 1.3MP webcam, worked out of the box.

---

### Post by GuitarRocker2562 on 2008-11-23
Still alive?

---

### Post by LouisZepher on 2008-11-23
As for "going in and out of" a terminal, I use a terminal program called 'Tilda' (open 'Add/Remove', and simply search for it using the search-box, or type "sudo apt-get install tilda" in a terminal).  This acts much like the chat sub-window you might've seen in online games (assuming you've played any).  By setting this to start on boot, and assigning a convenient otkey, you can, as I used to say in my early days of 'Nixperimentation', "drop to command" at the simple press of a single key.  [Screenshot.]("http://revmagus.deviantart.com/art/Tilda-screenshot-104447720")

---

### Post by dblxx on 2008-11-23
> **GuitarRocker2562 said:**
> Still alive?

Giving it a try now....hold the phone.:)

---

### Post by dblxx on 2008-11-23
What does this mean?

3. move into the folder you downloaded the package

---

### Post by GuitarRocker2562 on 2008-11-23
usind the cd command, move into the folder you downloaded the deb, assuming it was downloaded to your home folder, run, cd . in terminal

---

### Post by dblxx on 2008-11-23
> **GuitarRocker2562 said:**
> usind the cd command, move into the folder you downloaded the deb, assuming it was downloaded to your home folder, run, cd . in terminal

I hate to say this to you...I have no idea what any of that means.  Sorry.

Now it is saying I have broken packages.

---

### Post by GuitarRocker2562 on 2008-11-23
Open terminal. Then, assuming that you downloaded the file to your home folder, type into the terminal box "cd ."

---

