---
title: "*noob*  need help removing extra Ubuntu boot option"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by hektikbx on 2008-11-24
I am a noob here, so I apologize if I have posted this in the wrong forum:

I have installed Ubuntu 8.10 on my sister's laptop (which is running Windows Vista) using the wubi installer, and it went smoothly. Unfortunately, the second time I installed Ubuntu 8.10 on my laptop (Vista), I accidentally installed it on an external drive I: instead of the C: drive. Unfortunately, I tried to run the uninstall .exe from the I: drive.  It would execute, and so now , after running the wubi again for the C: drive, I am stuck with two Ubuntu boot options.  SO my boot menu ask's me to boot Microsoft Windows Vista, Ubuntu (I: ), and Ubuntu(C: ), of course without the drives displayed.

My Question: 

How do I remove the boot the Ubuntu installed on the I: drive? All help is greatly appreciated. Thanks.

---

### Post by talsemgeest on 2008-11-24
Just open up the start menu, type in "msconfig.exe" and push enter. Go to the "boot" tab, select the entry that you want to delete and click "delete".

Hope this helps :)

---

### Post by hektikbx on 2008-11-24
When I do that, only Microsoft Windows Vista shows up. I will try again.  Thanks tho. :)

---

### Post by crazyness003 on 2008-11-24
**[COLOR=Red]THE FOLLOWING POST ONLY WORKS IN XP. SEE NEXT 2 POSTS FOR VISTA INSTRUCTIONS[/COLOR]**

you might need to edit the boot.ini file. There's a harder way to get to it, but i found this way to be easy.
Open notepad.exe
then go to 'Open file'
and type this into the input box
```
C:\boot.ini
```then, make sure you are [COLOR=Red]_***EXTREMELY CAREFUL NOT TO DAMAGE ANYTHING ELSE***_[/COLOR]
[COLOR=Black]remove the entry with the Ubuntu[/COLOR] install you dont want.

This is my boot.ini (i havent installe using WUBI
```
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /noexecute=optin /fastdetect 
```As long as you find the correct line, and not damage the windows one, you should be fine.

Have fun, and be careful.

**[COLOR=DarkGreen]IDEA:[/COLOR]** Make a backup of the boot.ini
Just save as.. and type something like boot.ini.backup

Then go back to the original boot.ini and do the modification.

**[COLOR=Red]THE NEXT 2 POSTS HAVE INSTRUCTIONS FOR VISTA USERS[/COLOR]**

---

### Post by logos34 on 2008-11-24
for vista you'll have to use [bcdedit.exe from the command line]("http://technet.microsoft.com/en-us/library/cc721886.aspx#BKMK_bcdedit") to change boot menu options.  Or use something like EasyBCD.

---

### Post by crazyness003 on 2008-11-24
oops! i forgot vista uses a copmpletely different way of doing this!
sorry. please disregard everything i posted if you use VISTA

yes bcdedit.exe is the way to go about doing this.
there's a GUI wrapper for the app called [BCD Editor]("http://www.zezula.net/en/fstools/bcdeditor.html"). You can download for free.

EDIT: Also as [logos34]("http://ubuntuforums.org/member.php?u=127804") stated, [EasyBCD]("http://neosmart.net/dl.php?id=1") can also be used as a GUI alternative.

---

### Post by talsemgeest on 2008-11-25
Although, one of the installations might have used the grub for the boot loader.

When you start up, is the menu different in style to when you just had vista and wubi? (Not just the extra menu item, a different kind of layout/position of the items)

---

