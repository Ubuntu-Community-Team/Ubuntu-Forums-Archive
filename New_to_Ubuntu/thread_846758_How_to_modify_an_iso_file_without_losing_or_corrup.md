---
title: "How to modify an iso file without losing or corrupting files."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-07-01
I made an iso copy of my windows xp disc.  Burn it and booted it so i know the original iso file is good.  Then i am extracting 5 files, modifiying them and putting them back.  
I copy the files i need modify them.  I am now trying to put the files back without corrupting the iso file.  
I have extracted the iso and made a new one a few different ways in windows and used archive manager in Hardy Heron to extract the iso, put the new files in and then use the terminal to create a new iso but everytime i burn the iso and load it it says files are missing.  
I am trying to make windows bootable from usb and the files i am modifying will do that.
Also the files i modify are never the ones that go wrong.  with windows it was cursors.inf is corrupt.  with ubuntu its always %%sumthing*_ is missing.

anyone have an idea.

also i have tried unionfs but there is an error. the build log says its a kernal version mismatch.

---

### Post by NT4usB on 2008-07-02
The new files going into folders in the iso?
I find my biggest trouble when working between Windows and Linux is file and folder permissions. Check these on the files you're adding and the folders you're adding them to.

---

### Post by cariboo on 2008-07-02
There is a program at [getdeb.net]("http://getdeb.net") called iso manager that might do what you need, unfortunately it is only available as 32 bit version.

Jim

---

