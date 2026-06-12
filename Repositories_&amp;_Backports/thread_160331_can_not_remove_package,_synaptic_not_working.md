---
title: "can not remove package, synaptic not working"
date: 2006-04-14
forum: Repositories &amp; Backports
---

### Post by schweitzereffect on 2006-04-14
I installed this package
[http://packages.debian.org/unstable/web/torrentflux](http://packages.debian.org/unstable/web/torrentflux)
Which is torrentflux beta 2.0 but it did not work.  I installed the new 2.1 version manually and it works fine, but now because 2.0 is marked as broken, synaptic wont work, and no matter what i try (apt-get remove torrentflux, aptitude, dpkg, everything i know) it is unable to remove it!  dpkg says it should be reinstalled before trying to remove it because its in bad shape, but it will not install.  Does anyone have a solution?  Make it "forget" that it was ever installed?

---

### Post by aysiu on 2006-04-14
What happens when you try ```
sudo apt-get -f install
``` ?

---

### Post by schweitzereffect on 2006-04-15
root@router:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package torrentflux needs to be reinstalled, but I can't find an archive for it.

---

### Post by aysiu on 2006-04-15
[QUOTE=schweitzereffect]root@router:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package torrentflux needs to be reinstalled, but I can't find an archive for it.[/QUOTE] [I don't see *torrentflux* in any of the standard or extra Ubuntu repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flux&searchon=name&subword=1&version=all&release=all). What kind of sources.list do you have? Type ```
cat /etc/apt/sources.list
``` and post the output back here.

---

### Post by schweitzereffect on 2006-04-15
I didnt add anything to my sources.list, I downloaded torrentflux.deb and installed it, and now it wont go away.

---

### Post by aysiu on 2006-04-15
And ```
sudo apt-get remove torrentflux
``` is no good?

---

### Post by schweitzereffect on 2006-04-15
root@router:~# sudo apt-get remove torrentflux
Reading package lists... Done
Building dependency tree... Done
E: The package torrentflux needs to be reinstalled, but I can't find an archive for it.

Nope.  

dpkg gives
root@router:~# dpkg -r torrentflux
dpkg: error processing torrentflux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 torrentflux

---

### Post by az on 2006-04-15
You have to dpkg -i the 2.0 version first, then remove it and then reinstall the newer version.

That's shoddy packaging for you.  One version should not break the other.  Where did you get the newer version?

---

### Post by schweitzereffect on 2006-04-15
No, the new version was not a new package, it was just files you move into the www directory.  I have already tried to install it, and it will not work.

---

### Post by Linoman on 2006-04-16
Have you tried to remove version 2.1 and then 2.0? Then reinstall 2.1.

---

### Post by schweitzereffect on 2006-04-16
2.1 is not something you install, you just put the right files in you www directory and apache runs the torrent program and torrentflux is the interface.  I dont know why there even was a package, but I didnt use to know anything about it and thought it would be easier to just use the package then learn how to install it...

---

### Post by Linoman on 2006-04-16
I dunno what to say you have a very weird problem there on your machine. Have you tried clearing your sources list and then updating the system?

---

### Post by schweitzereffect on 2006-04-17
How do I do that?

---

### Post by fdoving on 2006-04-17
This is the manual dangerous, not recommended, hacker way:

Look for the torrentflux files in the dpkg system.
```

ls -l /var/lib/dpkg/info/torrentflux.*

```

is torrentflux.list present? 

if it is, it contains the list of files belonging to the torrentflux package.
Now that you know where they are, you can delete them manually.

When you're done deleting the files in the torrentflux.list file, you can delete /var/lib/dpkg/info/torrentflux.*


This is the dangerous part.
Now make a backup of /var/lib/dpkg/status
/var/lib/dpkg/status.bak is nice. 

Edit /var/lib/dpkg/status
search for 'torrentflux' delete the section with information on the torrentflux package. Make sure there is one blank line separating the sections for the remaining packages. Else things will break. 

Save and exit.

test with 
```

apt-get -f install

```

Hope it works.
(If not, replace the edited status file, with the backup status.bak.)


- Frode

---

### Post by schweitzereffect on 2006-04-18
IT WORKED (I think) OH GREAT ONE!
apt-get no longer gives errors, but I do not have the time to test synamptic.

I had to learn to edit text in the terminal because I do not currently have physical access to the pc so i can log into gnome and ftp corrupts the file.  But I needed to learn sometime or another.

Thanks many times for helping solve my problem!  

Now, since you all are so knowledgeable, can anyone tell me how to make the computer log into gnome by me typing some stuff into the terminal via ssh?

---

### Post by nchase on 2006-04-30
I had the same exact problem and fdoving's solution worked for me as well. Thanks very much.

---

### Post by ooops on 2007-04-28
I had the same problem and found this solution of removing broken package.
Thanks a lot!

---

### Post by StGermain on 2007-11-29
It worked for me when ndas-admin broke my synaptic, thanks! U Rock :guitar:

---

### Post by papafreebird on 2008-02-07
Sorry to bump such an old topic but I just wanted to say thank you to fdoving!  I had a broken package that had totally foobared my synaptic and my updates.  I've been looking for an answer to this for a week now.  I finally came across this thread and tried what was suggested in fdoving's post and it worked.  I can finally download my updates again.  Kudos fdoving!

---

### Post by kellemes on 2008-02-09
> **papafreebird said:**
> Sorry to bump such an old topic but I just wanted to say thank you to fdoving!  I had a broken package that had totally foobared my synaptic and my updates.  I've been looking for an answer to this for a week now.  I finally came across this thread and tried what was suggested in fdoving's post and it worked.  I can finally download my updates again.  Kudos fdoving!

Kudo's indeed.. I've also been using this post in the past, really saved my *** a couple of times.

---

### Post by GargoyleWB on 2008-04-30
Another thank you to fdoving!  I was troubleshooting my Dell laptop soundcard using a Dell-provided linux-backport-xxxxx package, that created the unremovable package problem.  No other forum fixes anywhere were working.

I was ready to wipe my drive in desparation and start over :( but gave this a try.  It worked (though I couldn't do it within Gnome, I had to use the recovery console)!

A million thank-you's!

Version 8.04
Dell Vostro 1500 (dual boot Win XP)

---

