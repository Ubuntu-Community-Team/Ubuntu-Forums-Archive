---
title: "&#65273;he Folders Disappeared ,What Happen Here"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by hemoali on 2011-09-09
Hey guys folders disappeared look my empty disktop 

[IMG]http://img13.imageshack.us/img13/8166/screenshot22kt.png

what is the solution

---

### Post by hemoali on 2011-09-09
Any help

---

### Post by grahammechanical on 2011-09-09
I see what happened!

The melt water from the spring thaw washed your icons into the waste basket.

The desktop icons are only symbolic links to the actual files/folders. The same is true for the icons in the Launcher.

1) You could try logging in with Ubuntu Classic and reversing the stuff you have been messing around with. Or, back up your files.

2) You could use a live CD to access the files on the hard disk and back them up. You might want to create a partition just for that.

3) You could boot into recovery and log-in as fail safe mode and do the back ups from there.

4) You could and should give more information. And do not expect instant answers.

Regards.

---

### Post by hakermania on 2011-09-09
Hello, please bumping after at least 24 hours :)

Ok, on the point now, my suggestion would simply to open a terminal and type in:
```

nautilus -q

```

---

### Post by hemoali on 2011-09-09
Hey hakermania 
The answer was

nautilus: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory

---

### Post by hemoali on 2011-09-09
Look My real problem is in any folder in the computer look to the iamge
[IMG]http://img23.imageshack.us/img23/3048/screenshot23r.png
no desktop icons And look to the launcher the files&folder icon not here

---

### Post by hakermania on 2011-09-09
Please, try to install the package
libgail18 either from synaptic if you have it installed or through a terminal:
```

sudo apt-get install libgail18

```

After this, re-try the nautilus -q trick!

---

### Post by hemoali on 2011-09-09
the output Is
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgail18 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-exe-thumbnailer : Depends: imagemagick
 shutter : Depends: imagemagick
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hakermania on 2011-09-09
Hm, it seems that something's broken here, you miss a library and the system thinks that it's still installed, as I see it...
Try these and post back the output please:
```

sudo apt-get -f install
sudo apt-get install libgail18
sudo updatedb
locate *libgail18*

```

---

### Post by hemoali on 2011-09-09
sudo apt-get -f install OUTPUT

[sudo] password for hemo: 
Sorry, try again.
[sudo] password for hemo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 libproc-simple-perl libsort-naturally-perl libfile-which-perl
  libenet0debian1 libfile-homedir-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
--------------------------------------------------------------------------
sudo apt-get install libgail18 OUTPUT
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgail18 is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 libproc-simple-perl libsort-naturally-perl libfile-which-perl
  libenet0debian1 libfile-homedir-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
--------------------------------------------------------------------------
sudo updatedb OUTPUT
--------------------------------------------------------------------------
locate *libgail18* OUTPUT
/usr/share/doc/libgail18
/usr/share/doc/libgail18/changelog.Debian.gz
/usr/share/doc/libgail18/copyright
/var/lib/dpkg/info/libgail18.list
/var/lib/dpkg/info/libgail18.md5sums
/var/lib/dpkg/info/libgail18.postinst
/var/lib/dpkg/info/libgail18.postrm
/var/lib/dpkg/info/libgail18.shlibs
/var/lib/dpkg/info/libgail18.symbols
Now?

---

### Post by hakermania on 2011-09-09
Hm, I have exactly the same files with you, you don't seem to miss anything...
A last try would be:
```

sudo apt-get purge libgail18
sudo apt-get install libgail18

```

---

### Post by hemoali on 2011-09-09
Ok And Now Should I restart the computer or what

---

### Post by hakermania on 2011-09-09
> **hemoali said:**
> Ok And Now Should I restart the computer or what

nautilus -q

Also, please remember **WHEN** this happened for first time?

---

### Post by hemoali on 2011-09-09
Today
output is
The program 'nautilus' is currently not installed.  You can install it by typing:
sudo apt-get install nautilus

---

### Post by hemoali on 2011-09-09
Now?

---

### Post by hemoali on 2011-09-09
I should install it Am I wrong?

---

### Post by hakermania on 2011-09-09
Yes, install nautilus and DO NOT restart your PC (omg :P)
EDIT: please stop posting a thousand times :) that's why 'Edit' is there :P

---

### Post by hemoali on 2011-09-09
but there are Alot of apps disappeared like ubuntu software center and gimp and other

---

### Post by hemoali on 2011-09-09
Output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkldap4 libstdc++5 kdepim-runtime libproc-simple-perl libgnome2-wnck-perl
  libsort-naturally-perl libbabl-0.0-0 libgegl-0.0-0 libmicroblog4
  libnet-ssleay-perl libxml-namespacesupport-perl python-dnspython
  libboost-program-options1.42.0 gnome-web-photo libproc-processtable-perl
  libextutils-pkgconfig-perl libxml-sax-expat-perl apturl-kde
  libgoo-canvas-perl kdesudo libwebkitgtk-3.0-0 libmailtransport4
  libakonadi-kde4 libkabc4 libgtkimageview0 libkresources4
  libwebkitgtk-3.0-common libkpimutils4 libgnome2-vfs-perl libfile-which-perl
  libxml-sax-perl libhttp-server-simple-perl libgail-3-0 libenet0debian1
  libkcal4 libknewstuff2-4 libkimap4 libwww-mechanize-perl libgnomevfs2-extra
  libxml-simple-perl software-properties-kde libkmime4 libakonadi-kabc4
  libx11-protocol-perl libextutils-depends-perl libgtk2-unique-perl
  akonadi-server libgnome2-gconf-perl libio-socket-ssl-perl
  libgtk2-imageview-perl perlmagick libakonadiprotocolinternals1
  libakonadi-kcal4 python-xmpp libfile-homedir-perl libakonadi-kmime4
  kdepimlibs-kio-plugins python-kde4 libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gnome-app-install
The following NEW packages will be installed:
  nautilus
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 1,163 kB of archives.
After this operation, 3,113 kB of additional disk space will be used.
Get:1 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) natty/main nautilus i386 1:2.32.2.1-0ubuntu13 [1,163 kB]
Fetched 1,163 kB in 4s (258 kB/s)     
Selecting previously deselected package nautilus.
(Reading database ... 205842 files and directories currently installed.)
Unpacking nautilus (from .../nautilus_1%3a2.32.2.1-0ubuntu13_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up nautilus (1:2.32.2.1-0ubuntu13) ...

---

### Post by hakermania on 2011-09-09
> **hemoali said:**
> but there are Alot of apps disappeared like ubuntu software center and gimp and other

Hmm, please tell me when was the last time you saw that nautilus was OK and what did you do that made it crash?

Let's try do the other way back.

EDIT: after reinstalling nautilus did this make a change?

---

### Post by hemoali on 2011-09-09
I tried to access the desktop cube only and then every that happend 11.04

---

### Post by hakermania on 2011-09-09
> **hemoali said:**
> I tried to access the desktop cube only and then every that happend 11.04

Oh, this is bad, if the nautilus re-installation didn't fix the problem, please do:
```

sudo apt-get install libgail-dev

```
and then again
nautilus -q

Post back for the results!

---

### Post by hemoali on 2011-09-09
As you see 

hemo@Ibrahim-PC:~$ nautilus -q
hemo@Ibrahim-PC:~$ 

no output

---

### Post by hakermania on 2011-09-09
> **hemoali said:**
> As you see 

hemo@Ibrahim-PC:~$ nautilus -q
hemo@Ibrahim-PC:~$ 

no output
that's good, did the icons came back?

---

### Post by hemoali on 2011-09-09
no no icons no mouse click on desktop

---

### Post by hakermania on 2011-09-09
> **hemoali said:**
> no no icons no mouse click on desktop

Can you open nautilus in any location?
For example, can you open nautilus in your Music folder or similar?

---

### Post by hemoali on 2011-09-09
only when I click super

---

### Post by DogMatix on 2011-09-09
Howabout,

Alt+F2

```
gksudo nautilus
```

Anything?

---

### Post by hakermania on 2011-09-09
> **hemoali said:**
> only when I click super
hemoali, please be more specific

---

### Post by hemoali on 2011-09-09
only with this code
gksudo nautilus
i can access nautilus

---

### Post by hemoali on 2011-09-09
hey firefox icon appeared on desktop

right click worked how can i appear the other icons

---

### Post by DogMatix on 2011-09-09
With gksudo you are running nautilus as root. So be a bit careful.

---

### Post by hemoali on 2011-09-09
I now but now ubuntu software center disappeared And other apps like gimp

---

### Post by DogMatix on 2011-09-09
What version of *buntu are you using?

---

### Post by hemoali on 2011-09-09
11.04

---

### Post by hakermania on 2011-09-09
Huh, this is somehow odd, how came that desktop shows 'some' icons?

---

### Post by DogMatix on 2011-09-09
As the problem occurred after fiddling with Compiz try resetting Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1
```
then

```
unity --reset
```

then reboot

---

### Post by hemoali on 2011-09-09
software center please what is the solution

---

### Post by hakermania on 2011-09-09
> **DogMatix said:**
> As the problem occurred after fiddling with Compiz try resetting Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1
```then

```
unity --reset
```then reboot
I am aware of this but also I am a bit afraid about rebooting now, thinking that nautilus draws the desktop, it's somehow risky, it would be a possibility not to let him log in...
Once I had messed up with nautilus and rebooted this is what actually happened! :(

---

### Post by hemoali on 2011-09-09
software center please what is the solution

---

### Post by DogMatix on 2011-09-09
> **hakermania said:**
> I am aware of this but also I am a bit afraid about rebooting now, thinking that nautilus draws the desktop, it's somehow risky, it would be a possibility not to let him log in...
Once I had messed up with nautilus and rebooted this is what actually happened! :(

Ahh! I see your point!

Although, could he not log-in in unity 2d?

---

### Post by hakermania on 2011-09-09
> **DogMatix said:**
> Ahh! I see your point!

Although, could he not log-in in unity 2d?

Nautilus draws both desktops so I think there will be a problem with this too (but if nautilus can draw the desktop but cannot display the icons I assume it won't be a problem, but it's a risk, and a newbie cannot be left in login screen unaware of Ctrl+Alt+F1-6).

OP: why are you posting about Ubuntu Software Center and 'solution'? We are trying to help but you don't post back if you've tried the solutions proposed!

---

### Post by hemoali on 2011-09-09
Ok tell me the solution and I will try It And write the output here

---

### Post by DogMatix on 2011-09-09
> **hakermania said:**
> Nautilus draws both desktops so I think there will be a problem with this too (but if nautilus can draw the desktop but cannot display the icons I assume it won't be a problem, but it's a risk, and a newbie cannot be left in login screen unaware of Ctrl+Alt+F1-6).

OP: why are you posting about Ubuntu Software Center and 'solution'? We are trying to help but you don't post back if you've tried the solutions proposed!

I'm not familiar with Unity 2d but I thought it used metacity?

**EDIT:** assuming the problem lay with compiz.

---

