---
title: "shared ntfs partition help"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-06-17
so i am dual booting ubuntu and windows 8 and have a shared ntfs partition. i have noticed that some files get deleted when i switch os's. i dont have hibernation nor do i have sleep enabled in my windows 8 so i dont think that is the problem.

what can i do to fix this? the files i have are pictures, music, etc. and are very important to me for them to just get deleted

---

### Post by zemega on 2013-06-17
Windows 8 default shutdown is in fact half-hibernation. You wil notice that interval between shutdown and booting of Windows 8 is fast. That is why when you shut down Windows 8 normally, it half hibernate. When you boot into Ubuntu, do some stuff, edit some documents, then boot again into Windows 8, Windows 8 will resume from its half-hibernation and restore the shared partition to its previous state. You can read this thread for more information.
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)

---

### Post by mreyna16 on 2013-06-17
ive actually read that whole thread, everything mentioned there is un checked in windows from my end, so why is it still deleting data? how do i get it to fully shut down rather than half hibernation?

---

### Post by coffeecat on 2013-06-17
There's a lot of off-topic background noise in that thread but the information you want is in the link in post #20. You need to disable fast startup.

---

### Post by MidnightGrey on 2013-06-17
Thats interesting about Windows 8 coffeecat i didnt know that.
Here's the direct link to Post #20
[http://ubuntuforums.org/showthread.php?t=1953674&page=2&p=12251891#post12251891](http://ubuntuforums.org/showthread.php?t=1953674&page=2&p=12251891#post12251891)

---

### Post by mreyna16 on 2013-06-17
yea thats unchecked, as i said before everything in that thread ive done and it still does that! any other ideas?

---

### Post by Morbius1 on 2013-06-18
> i have noticed that [COLOR=#0000cd]**some**[/COLOR] files get deleted when i switch os's. 
"some" may be the key here. How are you mounting the ntfs partition? Through nautilus?

Do the files that are saved in Linux have any of the following characters in in their name: [COLOR=#0000cd]**" * / : < > ? \ | **[/COLOR]

If they do then when you return to Windows they are ignored since Windows can't read them. If this is the case then there's a way to fix this by adding a correct line to fstab. We need some information though so please post the output of the following commands:
```
cat /etc/fstab
sudo blkid -c /dev/null
mount
```

---

### Post by mreyna16 on 2013-06-18
no, i rename my downloaded movies and stuff like that to have them all in order

---

### Post by HermanAB on 2013-06-18
Howdy,

Dual booting is rather last century.

The best solution is to not dual boot, but rather install Virtualbox on Linux and make a Windows VM.  That way, Windows can run in a window and you can use Windows and Linux applications concurrently.

---

