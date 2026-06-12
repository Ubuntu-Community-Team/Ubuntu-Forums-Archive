---
title: "Mozilla - migration from XP"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by dave_didlydodo on 2008-07-29
Hi,

I want to migrate my computer gradually from XP to Ubuntu. It's currently dual-boot but I'm only really experimenting with Ubuntu. I already use Thunderbird and Firefox in XP and when I make the switchover I'll want to retain my mailboxes and bookmarks. Does anyone know where I need to move those mailboxes and bookmarks to, within Ubuntu? Can I even do that? (ie are the file formats the same in XP and Ubuntu?) The XP locations are:

Thunderbird: 
C:\Documents and Settings\<profilename>\Application Data\Thunderbird\Profiles\<random string>.default\Mail\<popservername>

Firefox:
C:\Documents and Settings\<profilename>\Application Data\Mozilla\Firefox\Profiles\<random string>.default\bookmarks.htm

---

### Post by hyper_ch on 2008-07-29
you want to move the whole profile folders incl. the profile .ini

For TB from C:\Documents and Settings\<profilename>\Application Data\Thunderbird\Profiles to /home/USER/.thunderbird/

For FF from C:\Documents and Settings\<profilename>\Application Data\Mozilla\Firefox\Profiles\ to /home/USER/.mozilla/firefox/

or rather make a profile accordingly in TB and FF and verify the locations.

---

### Post by PA_Dummy on 2008-07-29
Bookmarks:

I use FoxMarks which is an add-on in Mozilla.   The bookmarks will "sync" however I log-on.

EMail:

I moved to GMail.  The in-box and previous messages are available on any machine-OS combo  ------  with an internet connection and a  browser.  You can setup GMail to receive and send mail accounts from you ISP.

There are other solutions but these worked for me.

_________

---

### Post by hyper_ch on 2008-07-29
you could even setup winxp and ubuntu using the same profile... so it won't even matter what OS you use...

---

### Post by SunnyRabbiera on 2008-07-29
You can pretty much copy stuff over, I found this out when I first stared to use linux.
Just copy files from C:\Documents and Settings\<profilename>\Application Data\Thunderbird\Profiles
or C:\Documents and Settings\<profilename>\Application Data\Mozilla\Firefox\Profiles\
to their linux counterparts /home/yournamehere/.thunderbird/ and /home/yournamehere/.mozilla/firefox/ as hyper_ch suggested, its how I transitioned.
The files should be readable in ubuntu as it comes with what is needed to read NTFS drives.
The opposite isnt as true XP doesnt see ubuntu's partitions right away unless you install a few things
like [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
or
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by knightcoder on 2008-07-29
Mere copying bookmarks and profiles didn't work for me in Firefox 3.
That's because FF3 doesn't use the html bookmarks anymore. It has a specialized SQL database to store bookmarks, history etc.

So, copy your bookmarks folder to Linux and then in FF3, you have to import the bookmarks.html file so that it gets parsed and read into the database.

---

### Post by hyper_ch on 2008-07-29
or rather first use FF3 on windows and then copy the profile folder.

---

