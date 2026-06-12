---
title: "&lt;items cannot be installed or removed until the package catalog is repaired....help!"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by gs84 on 2012-09-07
<help, just received this brand new asus x54c pc today and have never used ubuntu before.....tried downloading skype in the software center and was unable to..can't recall the exact error message i received..something about repositories..???  <now, i thuink i've made a big mess, have no clue, <now i have the message 'items cannot be installed or removed until the package catalog is repaired, do you wantto repair it now...i hit repair...and an error message comes up saying 'package operation failed' withthe following details:

 installArchives() failed: Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16. 
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17. 
Preconfiguring packages ... 
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16. 
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17. 
Preconfiguring packages ... 
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16. 
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17. 
Preconfiguring packages ... 
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 



for goodness sake i jave only owned this computer for a few hours and i'm already making a mess....all i wanted to do was start downloading software...can anyone help this super ignorant ubuntu first timer?????  thanks so much

---

### Post by gs84 on 2012-09-07
Andddd...i restarted my asus and my internet key no longer works (it doesnt seem to be detected by the pc) so nowwww im writing from my smartphone.does the fact my key is no longer detectable have nething to do with the problems im having (above post) gosh i hope i dont regret buying this computer with ubuntu.can neone help?

---

### Post by Epodx64 on 2012-09-07
uhm... You could try opening a terminal and running 
sudo apt-get update
then
sudo apt-get upgrade
if sudo apt-get upgrade fails try
sudo apt-get upgrade -f

---

### Post by gs84 on 2012-09-08
Thanks i did what u said and at the end of avseries of operations the terminal says "unable to fetch some archives, maybe run apt-get or try with --fix-missing?
So i typed apt-get update....at the end it says: "unable to lock the administration directory (/var/lib/dpkg/) are you root?

By the way still writing from my phone.cant get internet running with my web key.....worked fine yesterday????  Thanks for ne help

---

### Post by newb85 on 2012-09-08
apt-get commands generally require administrator privileges.

```
$ sudo apt-get update
```

etc.

---

### Post by grahammechanical on 2012-09-08
Did Skype install? Or only partially install? That could be the reason for those error messages. something is looking for something else and not finding it.

You could try Using the Software Centre to remove Skype. That may remove the broken package list called 'available' in the var/lib/dpkg/ folder.

That is what this error message is saying:

> dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

I recently was unable to update because a package list had a missing header. Have you seen that message?

The solution is to run these two commands.

```
sudo rm /var/lib/apt/lists/* -rf
```

followed by

```
sudo apt-get update
```

The first command removes (deletes) all the file/scripts/lists in the /var/lib/apt/lists/ folder.

The second command downloads a new set of those files. This is how to rebuild the package catalogue.

You do the same thing when you run System Update and click on Check.

Regards.

---

