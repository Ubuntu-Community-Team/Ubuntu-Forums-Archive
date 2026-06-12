---
title: "cant sudo on 12.04 lts"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by donwolfani on 2013-03-04
I already tried the recovery mode fix and it did not do anything to fix this!!!!!!!

[IMG]http://i1205.photobucket.com/albums/bb425/donwolfani/Screenshotfrom2013-03-04133740.png[/IMG]

ok so um i get this error. as i said recovery mode does not work and even logging in as admin does not give me the permissions needed to do this.  how do i fix and why didn't recovery mode work????

also luna is best pony

---

### Post by arpanaut on 2013-03-04
Is the account you are trying to use the first user account created at installation?
If not any subsequint user needs to be added to the sudo group to have privledges.

A link about how things work with root and sudo in Ubuntu, it is not recomended to use "su" to access a root command line.
better to use "sudo -i"  See Link:
[URL="https://help.ubuntu.com/community/RootSudo"]https://help.ubuntu.com/community/RootSudo

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
[/URL]

---

### Post by donwolfani on 2013-03-05
i have tried with both of my accounts. both the one i created and the admin one. both created at install.

i have also tried the recovery mode trick to fix this but still nothing

---

### Post by steeldriver on 2013-03-05
> **donwolfani said:**
> i have also tried the recovery mode trick to fix this but still nothing

It's hard to help unless you post exactly what you tried and any error messages that resulted

---

### Post by mamamia88 on 2013-03-05
Is this account the first account created after install?  If it's a secondary account you need to add your account to /etc/sudoers

---

### Post by El Tito on 2013-03-05
@steeldriver is right. With the current data about your problem ... reinstall. If you don't have superuser privileges, you cannot edit the sudoers file.

---

### Post by schragge on 2013-03-05
Check your group membership:
```
groups
```
If *sudo* is not in the list, try
```
pkexec adduser donwolfani sudo
```

---

### Post by donwolfani on 2013-03-05
just tried pkexec adduser donwolfani sudo   and it still wont allow sudo.

im a out to try reinstall bit firsy i need to ask about something. if i restore a backup of my entire home folder will this cause this problem again after the reinstall? and if so what file is causing it so i know what not to allow in the backup.

i have to use my home folder as it.is to lengthy a process moving every individual config file for.the.stuff i use to be able do it without messing up one program or another.

---

### Post by schragge on 2013-03-06
> **donwolfani said:**
> just tried pkexec adduser donwolfani sudo   and it still wont allow sudo.But [pkexec](http://manpages.ubuntu.com/manpages/precise/en/man1/pkexec.1.html) itself worked? I mean, is *donwolfani* now member of the *sudo* group? What does the *groups* command show? If pkexec didn't work, what was the error message? I guess it was clear, but just to remove any misunderstandings: *pkexec* works as a poor man's replacement for *sudo*, you must enter it as is, without *sudo*.

---

### Post by donwolfani on 2013-03-06
yes pkexec worked im part of the group but it still will not let me sudo after.  pkexec worked fine but.then when i tried to sudo anything it gave me the original error all over again.

---

### Post by schragge on 2013-03-06
Then please post the output of
```

pkexec cat /etc/sudoers

```

---

### Post by donwolfani on 2013-03-06
corrrection it did work when i added myself to the sudoers file using pkexec but i hadnt rebooted and so linux being linux hadnt applied the changes to any and all system files as per usual linux safety standards simply because those files were still used by the system untill i rebooted.   i only tried a reboot on a wild guess while preparing to try the next command you guys asked me to try and so far it seems to wotk now. sorry for adding to all the confusion but i hope this thread helps another beginner understand something as well.  ugh i hate having to post this thru my phone

---

### Post by donwolfani on 2013-03-06
second correction it has now removed me from sudo again... wtf is going on?

---

