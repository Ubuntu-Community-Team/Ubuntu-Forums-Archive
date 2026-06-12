---
title: "[SOLVED] How to fix broken packages?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by CJ Master on 2008-10-14
Hello, thank you very much for looking at my topic!

whenever I try to add new programs I get this error:

"Could not apply changes! Fix broken packages first."

So I went to Package Manager>Edit>Fix broken packages but it seems to think none of em are broke. I also tried:

```
sudo apt-get -f install
```

And that didn't work either.

;_;

---

### Post by oedha on 2008-10-14
sudo apt-get install -f

---

### Post by eternalnewbee on 2008-10-14
Which packages need to be fixed?

---

### Post by rybaxs on 2008-10-14
try to download again the package.. uninstall and install again..

---

### Post by CJ Master on 2008-10-14
Oedha, didn't work, same result as the other way around.

Eternal, no idea whatsoever.

Rybax, I can't install any packages...


Thanks for replying!

---

### Post by oedha on 2008-10-14
what about sudo apt-get update
have you activated your repository ?

---

### Post by rybaxs on 2008-10-14
havn't u try Synaptic?

---

### Post by Liviu-Theodor on 2008-10-14
Is your internet connection working? And if so, please list your [FONT="Courier New"]/etc/apt/sources.list[/FONT] file.

---

### Post by Gazneth on 2008-10-14
Try ```
sudo apt-get update 
``` to update your package list.
Then ```
sudo apt-get autoclean
``` to clean up any partial packages.
Then ```
sudo apt-get clean
``` to clean up the apt cache.
```
sudo apt-get autoremove
``` will clean up any unneeded dependencies.
If while doing this you can identify the broken package this code will very forcefully remove it.
```
sudo dpkg --remove -force --force-remove-reinstreq package name
```
Change package name to the real name of course.

---

### Post by CJ Master on 2008-10-14
To everybody that helped:

Thanks so much! I finally got it working. Couldn't do it without ya'll. =]

---

### Post by sub.mesa on 2009-11-16
Had the same problem, appears synaptic was still running even though being invisible.

Fixed it with:

sudo killall synaptic

(repeat this until you get a "no processes found" message)

---

### Post by amarendra on 2010-01-16
To use Thunderbird's latest version I installed Ubuntuzilla. But later I decided to with Ubuntu releases of Firefox and Thunderbird as the name, icons were changed to something I didn't like. I removed Thunderbird. But in case of Firefox, it was in /opt after Ubuntuzilla install with disabled "check updates". It was showing 3.5.6 where 3.5.7 is released. So removed Ubuntuzilla but update still didn't work. I checked source list and removed repos for Ubuntuzilla and Mozilla-Daily ppa (repo) so that only Ubuntu updates will show in Synaptic. Which is mentioned as: (I think this is 3.5.7):

"firefox-3.5 3.5.7+nobinonly-0ubuntu0.9.10.1 safe and easy bro.."

Update still didn't work (not even with system update).
Then tried a fresh Firefox install from repo and so removed /opt/firefox and also in other places. Even, "firefox" and "firefox-3.5" executables from /usr/bin/ and some files from other places. Cleaned my Firefox profile in ~/.mozilla, I have backed up my profile and settings. Installed firefox from the repo and it's not working. May be because links were symlinked to the one in /opt/firefox/ and moreover I have removed "executables", I am not sure.

How can I go back to original Firefox that came with my Ubuntu Live-CD? Cleaning the mess my stupid attempt might have created. Of course with the latest version available and also the updates should work with Ubuntu updates.

---

### Post by amarendra on 2010-01-16
Well, I think I solved it. Went to "Synaptic>World Wide Web" and installed latest Firefox available and created the required executables. Then went to "System>Preference>Main Menu> Internet>Firefox" and clicked on "Property" and browsed to "/usr/bin/firefox-3.5" command. And then it's working.
Added Panel shortcut after it.

---

### Post by arjun2504 on 2010-04-04
[I]I was too sufferring frm same problem .. now fixed!

Thanks a lot.[/I]
:p):P

---

### Post by wizard_karan on 2010-06-27
Hey many thanks gazneth!:p

I tried the commands given by you and they fixed my broken package problem.
This broken package problem happened with me when i un-installed Avant Window Manager(AWN) dock.:confused:

Thanks to all you and all the guys on this thread for the help!

from
name == Karan Pratap Singh
location == India

P.S. i am moving to Cairo-Dock now!Cheers!
):P

---

### Post by piyushchandrakar on 2010-07-22
: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_dockbar-main_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_gnomenu-team_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


my terminal shows that pls help me out

---

### Post by robins80 on 2010-09-16
I've tried all the suggestions here and I still get the broken packages error.  I'm almost to the point of reinstalling to see if that helps me out any.  Are there any other suggestions out there?

Thanks!

---

### Post by florinpnicola on 2011-02-16
I'm no expert but I saw this on another forum, run this in terminal

sudo apt-get dist-upgrade

and reboot

some software may not be compatible with the new kernel after that but it' s up to you.
Good luck.;)

---

### Post by gypsumwolf on 2011-06-02
I tried:

```
sudo dpkg --remove -force --force-remove-reinstreq xplico
```

It didnt work.

```
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by smuthavarapu on 2011-09-14
+1

---

### Post by jakelong00 on 2011-10-23
i found that  --libreoffice-core-- is broken.
how to fix this??

---

### Post by nothingspecial on 2011-10-23
Create your own thread.

This one is old.

Closed.

---

