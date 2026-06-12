---
title: "my files are suddenly marked read only, how can I access them?"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by NedraE on 2014-05-13
I've been cropping screen shots and moving them off to a wireless backup drive on my network all day.  Suddenly, for some unknown reason the file I cropped refused to save and I was told it was marked as read only.  I pulled out the files list, and the desktop and all folders under my name have a lock icon on them, and all files are marked as read only.  

I have no idea what triggered this.  I'm not sure how to unlock it all.  Can I simply reboot and login to have all unlocked?

When I click on the circle at the top, and type ga... it doesn't call up my games... if I type in terminal, it does not call up the link for the terminal.

Nedra

---

### Post by HiImTye on 2014-05-13
where are they stored, using what filesystem, and how is it mounted?

---

### Post by NedraE on 2014-05-13
This is Ubuntu, and I don't know what the file system is that Ubuntu uses.  I can get to the files, but they are LOCKED as read only. I pull out  the bar from the left side and click on the icon for Files - as I always have.  I don't know how it's mounted.  It's mounted the same as it was when the files were NOT locked.  

When I click on Files, it selects Home.  It shows the desktop, and multiple file folders.... downloads... documents... pictures... ubuntu One... Videos... Xsane Scanss... all the files are where they always are... but now there's a lock icon overlayed over every one.

---

### Post by HiImTye on 2014-05-14
ok, I wanted to be sure it wasn't an external storage drive, network drive, etc

it sounds like you were doing something as root and your folder permissions got messed up. use this command, but ensure that it is typed exactly (copy and middle click paste into the terminal):```
sudo chown "$USER":"$USER" "$HOME"
```

---

### Post by Impavidus on 2014-05-14
That, or the file system has been remounted read-only. That is standard behaviour when there is an error accessing the drive. After rebooting, the file system should be read-write again, but this could indicate a failing hard drive.

---

### Post by SeijiSensei on 2014-05-14
Before you go mucking about, I'd try a reboot.  Watch and see if the OS checks the drive for errors.

If a filesystem develops errors, Linux will mark it read-only to protect you from making the problem worse.  If you reboot and let the OS check the filesystem, it will be marked writable when mounted.

If this happens once, I'd call it a fluke.  But if it happens again, chances are good that the hard drive itself may be developing problems.  You can install **smartmontools** from the repositories and use them to check the status of the drive.

---

### Post by olliemonster on 2014-05-14
Also if unity isn't starting terminal the standard shortcut (in case you didn't know) is ctrl alt and t.

---

