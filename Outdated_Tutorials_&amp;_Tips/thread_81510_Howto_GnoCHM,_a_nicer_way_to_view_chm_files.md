---
title: "Howto: GnoCHM, a nicer way to view chm files"
date: 2005-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-10-24
Many of the computer books I read include a cd with a chm copy of the book. I like the ability to read these files under Ubuntu. Ubuntu does include xchm which does have a nice gtk2 interface now, but lack some of the searching feature that you get in Windows.

Gnochm ([http://gnochm.sourceforge.net/](http://gnochm.sourceforge.net/)) has some really nice features for viewing chm files. I have made the needed .deb files for Ubuntu Breezy.

1. Get Files
```

wget -c http://mikesplanet.net/deb/gnochm_0.9.6-1~breezy_all.deb
wget -c http://mikesplanet.net/deb/python-chm_0.8.2-3~breezy_i386.deb

```

2. Install chmlib
```
apt-get install chmlib
```

3. Install deb files
```
sudo dpkg -i python-chm_0.8.2-3~breezy_i386.deb gnochm_0.9.6-1~breezy_all.deb
```
*Please note: While compiling gnochm, Ubuntu told me that python-chm was superseded by another deb file in the Ubuntu repos, but I could not figure out which one.*

Let me know if you encounter any problems.
Mike

---

### Post by souled on 2005-10-24
Awesome thanks for this. No problems with this HOWTO, thanks.

---

### Post by Samuel on 2005-10-24
great stuff, been trying to get this working properly from an old howto and not getting anywhere, thanks for the .debs :)

---

### Post by mcrosmar on 2005-10-25
Thanks Mike for debs.... Very good HOWTO..... :)

---

### Post by flower on 2005-10-25
great ! thank you !

it's really nicer than xchm :)

---

### Post by waffen on 2005-10-25
Hello,

I found xchm in Breezy in this location:

Add programs>Graphics>More programs... :-)

---

### Post by Fester on 2005-10-26
Great FAQ, much appriecated.

As requested you said to post any problems, and I didn't have any.

Thanks again.

---

### Post by StormBlast on 2005-10-28
Cannot open chm with cyrillic content (cp1251), got this error:
```
Traceback (most recent call last):
  File "/usr/bin/gnochm", line 1861, in ?
    inst.open_file(args[i])
  File "/usr/bin/gnochm", line 1410, in open_file
    if self.request_file(self.chmfiles[-1].chmfile.home):
  File "/usr/bin/gnochm", line 1279, in request_file
    f, pathname, flink = self.internal_request_file(link)
  File "/usr/bin/gnochm", line 1273, in internal_request_file
    f, pathname = self.resolve_link(flink)
  File "/usr/bin/gnochm", line 1256, in resolve_link
    return func(link, internal)
  File "/usr/bin/gnochm", line 1174, in open_chm
    result, ui = self.chmfiles[-1].chmfile.ResolveObject(pathname)
  File "/usr/lib/python2.4/site-packages/chm/chm.py", line 390, in ResolveObject    return chmlib.chm_resolve_object(self.file, path)
TypeError: chm_resolve_object() argument 2 must be string without null bytes, not str
```
English chms opens with no errors.
Default locale is en_US.UTF-8.

---

### Post by Technoviking on 2005-10-28
[QUOTE=StormBlast]Cannot open chm with cyrillic content (cp1251),

English chms opens with no errors.
Default locale is en_US.UTF-8.[/QUOTE]
I will check into this.

Mike

---

### Post by ounas on 2005-10-30
Thanks, works a treat

-:D 

Ounas

---

### Post by bored2k on 2005-10-30
Hawt. Thanks.

---

### Post by SpEcIeS on 2005-11-04
Nice work. :D

---

### Post by shidai.liu on 2005-12-01
[QUOTE=StormBlast]Cannot open chm with cyrillic content (cp1251), got this error:
```
Traceback (most recent call last):
  File "/usr/bin/gnochm", line 1861, in ?
    inst.open_file(args[i])
  File "/usr/bin/gnochm", line 1410, in open_file
    if self.request_file(self.chmfiles[-1].chmfile.home):
  File "/usr/bin/gnochm", line 1279, in request_file
    f, pathname, flink = self.internal_request_file(link)
  File "/usr/bin/gnochm", line 1273, in internal_request_file
    f, pathname = self.resolve_link(flink)
  File "/usr/bin/gnochm", line 1256, in resolve_link
    return func(link, internal)
  File "/usr/bin/gnochm", line 1174, in open_chm
    result, ui = self.chmfiles[-1].chmfile.ResolveObject(pathname)
  File "/usr/lib/python2.4/site-packages/chm/chm.py", line 390, in ResolveObject    return chmlib.chm_resolve_object(self.file, path)
TypeError: chm_resolve_object() argument 2 must be string without null bytes, not str
```
English chms opens with no errors.
Default locale is en_US.UTF-8.[/QUOTE]


My locale is en_GB.UTF-8. I have the same problem and moreover, the navigator gif doesn't show up complaining about image missing while the same file opens fine in Windows.

---

### Post by ekravche on 2005-12-02
pretty cool software. Didn't know this existed

---

### Post by fhole on 2005-12-05
Much Thanks bro! 
Your a Star!

---

### Post by tylerjames on 2006-09-15
Does anyone know if this works in Dapper?

---

### Post by bodhi.zazen on 2006-09-16
> **waffen said:**
> Hello,

I found xchm in Breezy in this location:

Add programs>Graphics>More programs... :-)

I second that xchm is very nice as well.

---

### Post by felix_ahlner on 2006-09-26
> **tylerjames said:**
> Does anyone know if this works in Dapper?

Works fine for me. Seems GnoCHM has been added to the universe repositories.

Many thanks for this program!

---

### Post by rlozano on 2006-10-13
did it move? i got this error?

randall@randall-laptop:~$ wget -c [http://mikesplanet.net/deb/gnochm_0.9.6-1~breezy_all.deb](http://mikesplanet.net/deb/gnochm_0.9.6-1~breezy_all.deb)
--01:30:26--  [http://mikesplanet.net/deb/gnochm_0.9.6-1~breezy_all.deb](http://mikesplanet.net/deb/gnochm_0.9.6-1~breezy_all.deb)
           => `gnochm_0.9.6-1~breezy_all.deb'
Resolving mikesplanet.net... 62.214.98.58
Connecting to mikesplanet.net|62.214.98.58|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:30:34 ERROR 404: Not Found.

and how about this?

randall@randall-laptop:~$ sudo apt-get install chmlib
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

thanks in advance...

---

### Post by Lure_Angler on 2006-10-16
I could dld it but I got exaclty the same error msg as him, the second one...

---

### Post by Lure_Angler on 2006-10-16
I added sudo in front, and it WORKED...atta way!!...

---

### Post by foureight84 on 2006-10-17
i find that gnochm doesn't display the chm files correctly. my book has buttons to go to the next page and the previous. this doesn't get displayed correctly (not at all) in gnochm. i switched to xchm and i don't get the same error. 

anyways, i wanna customize the .chm icon instead of having the default unknown gnome file icon. how do i do this?

---

### Post by lukjad on 2007-08-20
Gnochm is now available in the Ubuntu repositories.  I did 
sudo apt-get install gnochm
It worked very well.

---

### Post by jason6g on 2007-09-17
installed from add/remove works like a charm =) and here i thought i was lost from all my chm files =)

---

### Post by monfreex on 2007-10-29
Thanks guys!

---

### Post by BobSongs on 2008-03-01
> **lukjad007 said:**
> Gnochm is now available in the Ubuntu repositories.  I did 
sudo apt-get install gnochm
It worked very well.[FONT=Verdana]True enough. I just installed a fresh copy of Ubuntu Linux, Gutsy Gibbon 7.10 and I tried that very line: it worked perfectly. None of my repositories have been tweaked yet. So this right from what's available to a new user.

Thanks.
[/FONT]

---

### Post by margazhang on 2009-12-09
A friend of mine sent me a few non-English (Chinese) chm files and I tried to read them with gnochm and xchm - both cannot display the non-English characters. Then I installed chmsee - nothing else - and you know what? I can now read all those chm files. So if you have trouble reading non-English chm files, try chmsee.

---

### Post by kennedyjch on 2010-07-30
I've just installed ChmSee from Software Center and it works like a charm,,,

---

