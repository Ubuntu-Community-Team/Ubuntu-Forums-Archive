---
title: "HowTo: &quot;sharing&quot; firefox profile between Ubuntu and Windows"
date: 2006-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by eilu on 2006-10-21
This has probably been done, how-to'd and faq'd to death, but I took a different approach, which other people might find useful. My system is dual-booting Win98 and Ubuntu Dapper, but this should work in any system with an internet connection.

1. **Copy **your original FF profile (from Windows). It's in C:\WINDOWS\Profiles\<profile name>\Application Data\Mozilla\Firefox\Profiles In newer systems (2000, XP) you can access the Application Data folder by running %appdata%

2. **Paste **the profile in /home

3. In **terminal**, run Firefox with the profile manager:
```
$ firefox -p
```

4. Choose to create a **new profile** in Profile Manager. It'll ask you for the installation folder, and you select the profile you copied. Profile Manager will recognize it as an existing profile and allow you to use it. You now have all your bookmarks, extensions, cookies, saved forms, etc. in Ubuntu.

5. Install **[Google Browser Sync]("http://www.google.com/tools/firefox/browsersync/")** on both Ubuntu FF and Windows FF. In my case I set it up so I just sync bookmarks between the two, but this will also let you sync cookies, passwords, etc. This is so that any new bookmarks I add in one system will be available in the other.

And that's how I got Ubuntu and Windows to "share" my FF profile. Hope someone found it useful. :)  

I know you could always just point profile manager to your existing Windows profile, but this way you can unmount Windows and still keep the profile. Also, since you're not sharing extensions, Linux-only extensions (like Fireget) won't clutter up the Windows installation.

---

### Post by aknapp on 2006-10-21
Nice HowTo, thanks. :)

---

### Post by eilu on 2006-10-28
you're welcome. I'm glad someone found it useful.

---

### Post by chaumurky on 2006-11-13
Will this address the issue I'm having with firefox not using the correct media player in Ubuntu? I'm currently just pointing to my windows profile (stored in a third partition (FAT32) that is accessed by both OS's). For windows it uses WMP9 or whatever but Ubuntu just gives me a white space where the player should be (I do have the correct mplayer/mozilla plugin installed). Will your method allow me to have a seperate player config? Perhaps a third way is to have seperate profiles but create some softlinks to the windows items that can be shared...

---

### Post by CyBuzz on 2007-03-14
I use browsersync across my work and portable editions (all windows XP) of Firefox, but on my Edgy install, it wont sync my password.  does the bookmarks fine, just not passwords.

---

### Post by lcohen999 on 2007-03-15
There is a much easier way.

use google browser sync on both machines.

You get everything copied over all the time, it is seemless and you don't have to worry about NTFS writes, or otherwise

---

