---
title: "zoombinis, anyone?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-29
if anyone remembers the Zoombinis games, do you know if there is a port/installer/linux version of it? thanks!

---

### Post by Zopiac on 2008-04-29
bump

---

### Post by Ek0nomik on 2008-04-29
It doesn't look like it.  You can try to run it through Wine if you are feeling adventurous.  Otherwise there is a lot of free educational software for Linux.

---

### Post by Zopiac on 2008-04-29
> **Ek0nomik said:**
> It doesn't look like it.  You can try to run it through Wine if you are feeling adventurous.  Otherwise there is a lot of free educational software for Linux.

ok how do i do that, exactly; wine. i have it, i just need to know HOW to do it.

---

### Post by scragar on 2008-04-29
if you've installed wine you just double click the windows installer(if you have it), just like on windows.

---

### Post by bilal.17 on 2008-04-29
looks like it doesn't work in Wine [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7575&sAllBugs]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7575&sAllBugs")
but that was an old test so it might work now

---

### Post by Ek0nomik on 2008-04-29
> **Zopiac said:**
> ok how do i do that, exactly; wine. i have it, i just need to know HOW to do it.

I haven't used Wine in a bit, but assuming you have all the files somewhere, you just need to navigate to the installer.  Example:

```
cd /location/of/zoombinis/installer
wine installer.exe
```

Then it should walk you through the installation process.  I personally like to use Linux applications on Linux, so I'm not really a Wine fan myself.  But, if it works, more power to you.

---

### Post by Zopiac on 2008-04-29
> **Ek0nomik said:**
> I personally like to use Linux applications on Linux, so I'm not really a Wine fan myself.  But, if it works, more power to you.

me too...:)

plus, i cant access the files already on my computer: [http://ubuntuforums.org/showthread.php?t=774964]("http://ubuntuforums.org/showthread.php?t=774964")

---

### Post by Ek0nomik on 2008-04-29
> **Zopiac said:**
> me too...:)

plus, i cant access the files already on my computer: [http://ubuntuforums.org/showthread.php?t=774964]("http://ubuntuforums.org/showthread.php?t=774964")

Well, for the record, I don't think you can simply run the executable from Windows on Wine.  I think you may need to actually install it with Wine, and then Wine will make a fake path as if it were Windows.  Something like /home/user/.wine/c_drive/Program\ Files/Zoombinis.

I presume Wine needs the files within its install path to make use of it.  So, while it would be good to figure out your hard drive issue, I would suggest actually installing it through Wine and then trying to run it.

---

