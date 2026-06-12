---
title: "Moved over from Windows, been using Linux for a few months..."
date: 2016-09-02
forum: New to Ubuntu
---

### Post by bobdylan96 on 2016-09-02
I've been using Linux on my Raspberry PI 2/3 for the last 6 or so months. I've learned quit a lot. I decided to install Ubuntu 16.04.1 LTS on my main desktop which *was* running Windows 10. I hardly ever booted it until I started to use ubuntu. (10/10 for the great OS btw!)
Anyway, couple of questions, if you'd be so kind in assisting me! :-)

1: What is the best way to remove an app and clean it's files? I did ask on IRC and someone recommended: sudo apt-get purge *package* && sudo apt-get autoclean" - would this be OK to say I've installed an app and it'll remove it? or do I need to unhide the files in my home dir and manually delete?
2: Moving over from Windows, things were basically easy like installing apps etc. I have a Galaxy Core Prime LTE that is manufactured by Samsung, they offer something called "SmartSwitch" which will wipe your device and return it to stock. I know about Odin and stuff but they're windows apps. is there something like this for Linux? I know you can flash the Nexus line and other systems with fastboot and adb but I'm pretty stuck on *what* to do with Samsung devices. I already know how to use adb and fastboot on Linux but stuck with Samsung. Whilst on that subject, I don't have an iOS device atm but nearly everyone in my family use an iOS device and [i]sometimes[/] I have to use my Windows app (iTunes) to restore the OS on it. is there something like iTunes but for Linux? I know, I have seen a lot of people complain to Apple about their non existing support for Linux and thought here would be best to ask.
3: Is there a way to backup apps etc? like if I had to re-install ubuntu, could I somehow use a certain app, backup my files to USB or something and it's in a certain dir and install the backup app, copy over the backed up files to the special dir then restore the backup? So I wouldn't have to keep re-installing ubuntu's apps like i3-wm etc? I have an older system that I'll most likely will install ubuntu on but right now I have things and apps setup the way I want. apart from unhiding files located in my home dir, and backing up to a USB, and then copying over. is there another way?
I ask because I have certain things installed like uGet, Kodi, etc. they have there own data and settings and stuff. is it just easier to backup the hidden files from my home dir or some way else?
5: and last: with Windows, you'll have to pay yearly for a subscription to Microsoft office - I have looked and searched but couldn't really see anything. Is there something free and open source like Microsoft office? just so I can powerpoint, word documents etc. write up job CV's and stuff.

Sorry for the long post, I wanted to try and explain myself clearly.

Thank you and have a wonderful night.

PS: the best thing about Linux, it's free and open source and it gets your mind working. I love challenges!!!!!!

---

### Post by poorguy on 2016-09-02
This is probably the best way.
[https://help.ubuntu.com/stable/ubuntu-help/addremove.html](https://help.ubuntu.com/stable/ubuntu-help/addremove.html)

I use it and it works good for me it removes the app and any dependencies that were installed with the app.
From here you could open the terminal and enter *sudo apt autoremove* for any left overs.

---

### Post by poorguy on 2016-09-02
Have you looked at LibreOffice suite that comes installed with Ubuntu 16.04 it works for my office needs.

Here is some user documentation about it you can download.
[https://wiki.documentfoundation.org/Documentation/Publications](https://wiki.documentfoundation.org/Documentation/Publications)

---

### Post by TheFu on 2016-09-02
Welcome to the forums!

Lots of opinions follow. Nobody has to agree with these.


Answer 1:
Remove package-installed files:
  sudo apt purge {package-name}

This removes settings and the program in /etc/ and /usr/.  It doesn't
remove anything placed into your HOME, like config files or data files.

If the pkg was something like apache or nginx or a DBMS, then those
files in /var/.... aren't removed either.

If you use:
  sudo apt remove {package-name}
then the settings in /etc/ aren't touched. This is handy if you want to
install a different version or install from a non-package method.


Answer 2: Don't know anything about iOS.

Answer 3:
You can backup stuff however it works for you. YOU are responsible for
determining what should be backed up, how it should be backed up and
where it should be backed up.

Just know that both the files AND the permissions (perm-bits, owner,
group) are necessary at restore time. Any method that doesn't capture
that data will lead to issues later.

Unix and Linux systems have 50+ different backup answers. The best
answer for you probably isn't the best answer for me. We each need to
discover the best backup tool for our needs.  This is a system-level
thing, not 1 app at a time, if you stay within the package management
system.
Hidden files aren't really hidden.  They just aren't displayed by
convention because they begin with a '.' (period). There isn't any file
permission called "hidden" in Unix. Forget the idea of "hidden files."

There are 50 threads in these forums where people ask about backing up.
I suggest you review those and ask specific questions. There are also
many, many, many blog articles about backing up systems - I've written
about 10 myself as I worked through all the options for the 5 that I've
tried.

BTW, backups are 10% of the job. 90% is actually using those backups to
restore. THAT is the real reason to make backups - for the restore. If
you don't actually test the restore, then you don't really have a
backup, you just have hope.  And as they say - "hope is not a plan."

Answer 4:
TL;DR - use google.

There are many programs available to run all sorts of different things
on Linux.  There are websites with hints for which programs are
available for any specific task.  Most people would look inside their
package maanger first. If you need a word processor ... I'd search for
"word processor" or something like that.
There is also a website - alternativeTo.net ... plus there are thousands
of blogs, magazines, groups, lists, where Linux users post their reviews
and favorite tools for any specific task.

BTW, Unix was doing "word processing" for decades before Windows thought
about it, so there are some methods that are different than you'd
expect, but still used by professionals around the world.
[http://www.wikihow.com/Write-a-Resume-in-LaTeX](http://www.wikihow.com/Write-a-Resume-in-LaTeX)

There's a whole world of programs written in "the Unix way" that you can
uncover and try on Linux, if you like.  Some of these programs might
seem difficult or odd or strange, but they are also extremely efficient
for certain uses and usually provide some features that typical
Windows-desktop programs do not.

Anyway - hope this helps in some small way.

---

### Post by The Cog on 2016-09-02
Welcome to the forums, bobdydlan96.

When apps are installed, the application files get put in several different directories. apt-get puts them where they need to be, and "apt-get purge packagename" removes them all again.

However, when a user runs the application, their data and settings get saved somewhere in their home directory. This would have been in a hidden file or folder called /home/username/.appname, but it is becoming the norm to put them in /home/username/.config/appname. These user files do not get removed when you remove the application. If you want to remove those, you must do so yourself. However, it does mean that if you back up your home folder, you are backing up these settings along with the rest.

So, 1: Yes, use apt-get to install and remove applications.

2: I don't back up the OS. Just my user data, which includes all the app settings. If I need to reinstall then I will just install from the installer. That's how I upgrade.

3: I don't back up my apps. But I install so many that I keep a small script that installs them. I use if after I install an upgrade e.g. 15.10 to 16.04. It starts like this although I will probably change it to use "apt instal..." rather than "aptitude install..." now that apt can do installs itself:
```
set -v
nice apt-get update
nice apt-get upgrade
nice apt-get install aptitude
nice aptitude install -y -r htop
nice aptitude install -y -r sysstat
nice aptitude install -y -r jfsutils
nice aptitude install -y -r btrfs-tools
nice aptitude install -y -r gparted
nice aptitude install -y -r vim
nice aptitude install -y -r synaptic
nice aptitude install -y -r gnome-disk-utility
```

---

### Post by zephar123 on 2016-09-02
3: Is there a way to backup apps etc? like if I had to re-install ubuntu, could I somehow use a certain app, backup my files to USB or something and it's in a certain dir and install the backup app, copy over the backed up files to the special dir then restore the backup? So I wouldn't have to keep re-installing ubuntu's apps like i3-wm etc? I have an older system that I'll most likely will install ubuntu on but right now I have things and apps setup the way I want. apart from unhiding files located in my home dir, and backing up to a USB, and then copying over. is there another way?
I ask because I have certain things installed like uGet, Kodi, etc. they have there own data and settings and stuff. is it just easier to backup the hidden files from my home dir or some way else?
I reccomend backing up your home directory it should hold all your data files. (unless the program is really wierd.) Even for an example works with your thunderbird mail.

5: and last: with Windows, you'll have to pay yearly for a subscription to Microsoft office - I have looked and searched but couldn't really see anything. Is there something free and open source like Microsoft office? just so I can powerpoint, word documents etc. write up job CV's and stuff.

Libre Office should do everything you want =). Other then if you need MS publisher =(. Their are many other alternatives on this. 


Sorry for the long post, I wanted to try and explain myself clearly.

Thanks for posting and always love to help out =)

Paul

---

### Post by Bucky Ball on 2016-09-02
Welcome. A tip for future reference. Asking more than one question, let alone five, in one thread can only get convoluted and confusing.

You are much better off, and it is advised and preferred, if you stick to one question per thread. Easier that way and you will get better support for each. Also, a search engine is your friend. See second link in my signature. 

Good luck. :)

Incidentally.

1/ Yes. That is correct commands.
5/ Yes. You already have it installed in a standard Ubuntu install: Libreoffice.

---

### Post by bobdylan96 on 2016-09-03
Thank you for all your replies. I look forward to learning more!

---

### Post by Mark Phelps on 2016-09-03
As to #5, there really is no drop-in full replacement for MS Office, primarily because they keep adding functionality with every new release.  And yeah, there are open-source apps that can write documents, create spreadsheets, and create presentations -- but that's not the same as successfully opening and modifying an MS Office file in XML format that uses OLE to embed other stuff.

For a long time, Open Office, and then LibreOffice offered a suite that was CLOSE to MS Office, but it had problems with the XML format files.  Folks would open .docx files they received from others that use MS Office and either, the files wouldn't render properly, or when they saved them and sent them back to the MS Office folks, those folks complained that the files would no longer render properly.

Then, the MOST compatible office suite became Kengsington Office, later renamed WPS.  But, it went commercial and lots of folks stopped using it.  But I've heard, that it's either free again, or they have a version that is free.  For an MS Office replacement for the more common components, check out WPS Office.

---

### Post by Bucky Ball on 2016-09-03
Yep, looks like WPS is free again. Love to try it but I'm a heavy Zotero user, specifically the Zotero Libreoffice plugin and don't think that would work in WPS. :|

---

### Post by howefield on 2016-09-03
Not easy to tell from the website, it appears WPS Office 2016 is free of cost (advert sponsored) for the Windows platform. No "free" equivalent edition for Linux.

---

### Post by Bucky Ball on 2016-09-03
Try [this]("http://wps-community.org/downloads"). :)

Looks free to me. At least when I clicked a .deb file it offered a download. Maybe when you download it is a trial. Didn't go that far.

[From here ]("http://wps.com/")which is linked from the main WPS page when you click 'WPS for Linux'.

---

### Post by howefield on 2016-09-03
> **Bucky Ball said:**
> Try [this]("http://wps-community.org/downloads"). :)

Looks free to me. Maybe when you download it is a trial. Didn't go that far.

Thanks, I already did download that file and installed, there is no mention of price or trial on the download site or the installation process, I'd love to be corrected but I believe it is time limited. I do like the look of it.

---

### Post by Bucky Ball on 2016-09-03
> **howefield said:**
> I'd love to be corrected but I believe it is time limited.

:| Thanks for the unfortunate info. Nonetheless, I'll check it out on a VM.

---

### Post by sotiris2 on 2016-09-04
As for your phone my **old **&#8203;Samsung worked with adb just as my Nexus does now. Make sure you enable USB debugging.

---

