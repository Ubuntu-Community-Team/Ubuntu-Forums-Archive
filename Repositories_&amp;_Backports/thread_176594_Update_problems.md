---
title: "Update problems"
date: 2006-05-15
forum: Repositories &amp; Backports
---

### Post by spahn on 2006-05-15
When i run **apt-get update**
i get this error message:
[COLOR="Lime"]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/COLOR]

And also, when i used the package manager it gave me a message pop up message about the CD. (i have not been able to get the message again, otherwise i would post it here).

Can anyone provide some insight as to what might be the problem?

---

### Post by bluevoodoo1 on 2006-05-15
This might help...

[http://ubuntuforums.org/showpost.php?p=1011398&postcount=2](http://ubuntuforums.org/showpost.php?p=1011398&postcount=2)

---

### Post by spahn on 2006-05-15
[QUOTE=bluevoodoo1]This might help...

[http://ubuntuforums.org/showpost.php?p=1011398&postcount=2](http://ubuntuforums.org/showpost.php?p=1011398&postcount=2)[/QUOTE]
Thank you, that was helpful (this is a laptop and it must have happened when the power went down).

However, now i get the same message (as i run **sudo apt-get update**) that i was getting before i got the message about not getting a lock:
[COLOR="Lime"]Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

Thank you in advance for any direction or assistance.

---

### Post by bluevoodoo1 on 2006-05-15
```
sudo gedit /etc/apt/sources.list
```

put a # mark in front of the line that refers to your CD rom... like this...

```
## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

save it. Then 'sudo apt-get update'

---

### Post by spahn on 2006-05-15
Sweet!
Thanks for the tip!

---

### Post by bluevoodoo1 on 2006-05-15
[QUOTE=spahn]Sweet!
Thanks for the tip![/QUOTE]

So you've got it working right??

---

### Post by meekrosoft on 2006-06-02
Hi,

I had the same problem.  Thanks for the help, indeed it does work!

meekrosoft

---

### Post by spahn on 2006-06-02
[QUOTE=bluevoodoo1]So you've got it working right??[/QUOTE]

Yes, it worked instantly!

Thank you!

---

