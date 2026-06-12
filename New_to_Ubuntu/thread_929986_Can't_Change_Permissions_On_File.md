---
title: "Can't Change Permissions On File"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Spaceman Spiff on 2008-09-25
Hey guys,
  So I am messing around with wine and I decided I wanted to make my drive_c folder be on my fat32 drive that I use as a medium between my windows installation and linux installation.  I got the partition to automatically mount through my fstab file and it works great, I managed to convince wine that drive_c was located on the fat32 partition and now I am ready to install this file.  However, the file won't let me install, something about write permission, so I check the file and it doesn't have execute flags (but it's an exe so I guess it should.)  So I decided oh well I guess I need to make it executable.

```

  sudo chmod 777 *
  ls -la
             -rw-rw-rw- ....... file name
  sudo chmod 444 *
  ls -la
             -r--r--r-- ....... file name
  sudo chmod 777 *
  ls -la
             -rw-rw-rw- ....... file name

```

So my question is what the hell is going on?



Also on the side, I don't want to research this too much:
  - whats with the green background and blue font for 777 files sometimes, but not always?
  - how do I change my /media/disk partition to be owned by users group rather than root on start up?

---

### Post by Baelus on 2008-09-25
I'm guessing here, but in fstab does the line to mount the partition have the option 'noexec' listed? Maybe explicitly set to 'exec' if 'defaults' is used.

---

### Post by Spaceman Spiff on 2008-09-25
Hmm, it might but every single other file and folder has rwxrwxrwx capabilities.  Here are the options set in my fstab

```

     user,auto,fmask=0111,dmask=0000

```

---

### Post by Spaceman Spiff on 2008-09-25
Hey guys, any help on this would be appreciated, I don't think it's a difficult question.  I feel like I am missing something very very small.

---

