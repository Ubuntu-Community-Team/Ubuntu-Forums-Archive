---
title: "wine not working 8.10"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by simbits on 2008-11-28
So I just installed Wine with sudo apt-get wine or w/e
and when i had ubuntu before, wine worked fine.

now when i try to install a .exe file, which i had on before, i get 

"an error occurred while trying to load the archive (null)


[HTML][/home/christine/Desktop/mtpaint-3.20-setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/christine/Desktop/mtpaint-3.20-setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/christine/Desktop/mtpaint-3.20-setup.exe or
          /home/christine/Desktop/mtpaint-3.20-setup.exe.zip, and cannot find /home/christine/Desktop/mtpaint-3.20-setup.exe.ZIP, period.
[/HTML]

---

### Post by wjaguar on 2008-12-02
> /home/christine/Desktop/mtpaint-3.20-setup.exe
  End-of-central-directory signature not found.

Your system attempted to open the file as a ZIP archive, instead of running it under Wine as a normal Windows executable. Running it as "wine mtpaint-3.20-setup.exe" from the console should work.

But anyway, "sudo apt-get install mtpaint" would work even better for this specific case. :-) mtPaint does not look good under Wine - better to install a native Linux version of mtPaint 3.21.

-= With best regards, Dmitry Groshev, maintainer of mtPaint =-

---

### Post by vahnx on 2009-01-05
I have the same issue. I was just running WinXP's MSPaint fine 20 minutes ago. I tried getting my sabma printer to print and that didn't work, then when I try to launch mspaint I get his error.

EDIT: It's because my print doesn't work. Very odd.

---

### Post by tarps87 on 2009-01-05
Right click and select open with wine, if it is in the repertoires I would suggest using that one.

---

### Post by atngplusultra on 2009-01-05
Speaking from experience,
I do not suggest using Wine for anything.
Perhaps it's the only route for some programs, but in this case, definitely go with 
```
sudo-apt get install mtpaint
```
as suggested already

---

### Post by Angry_Mushi on 2009-01-05
I have some problems with whine too, though I think it's from a different nature.
 I installed it the same way Christine Did (sudo apt-get install wine) but no matter what I do with it, all the buttons and text shows  up blank, I tried To install the driver for my Scanner like that anyways and it shows some errors on terminal: 

```

mauricio@mauricio-desktop:~$ wine lide90vst1300ea24.exe
fixme:setupapi:SetupDiGetINFClassA ".\\CNQ2412.INF" 0x33d254 0x33c664 32 (nil)
fixme:setupapi:SetupDiGetINFClassA ".\\CNQ2412.INF" 0x33cfbc 0x33c68c 32 (nil)

```

---

