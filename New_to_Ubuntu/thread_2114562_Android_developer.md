---
title: "Android developer"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by BDogg718 on 2013-02-10
Hello boys and girls. Ive been following this thread [http://forum.xda-developers.com/showthread.php?t=2131391]("http://forum.xda-developers.com/showthread.php?t=2131391") so i finally got this all synced up. 

Now im starting to build...problem is: when i input this code:```
 mv platform_manifest/kernel_manifest.xml ../.repo/local_manifest.xml 
```It returns this error: 
```
mv: cannot stat `platform_manifest/kernel_manifest.xml': No such file or directory.
``` There is such a file, kernel_manifest.xml. PLEASE what am I doing wrong? I have successfully built before...mind u it was CM7 and it was about a year ago, and all I was doing was following steps like with this thread. SOmeone please help me out here. I promise to be a major contributor/maintainer if someone will have me...lol.. if I could just get it done once Ill be off and running. 
I know our devs are very busy guys and dont sometimes enjoy helping out kinda noobs like myself...but i assure whoever can help, that your time and help will not go unrewared. I just wanna finally be able to do this...been trying for weeks....was so happy when I saw this thread..just need a lil push in the right direction.
Im not sure if anyone here is an android developer or can help but i figured Id give it a shot.
Also, been noticing my wired internet dropping out quite frequently. Im on a clean install of ubuntu 12.04.
Any help at all would be greatly appreciated!!

---

### Post by linuxsyst on 2013-02-10
The link is broken and are you in the same directory where he file is?

---

### Post by schragge on 2013-02-10
> **BDogg718 said:**
> [http://forum.xda-developers.com/show....php?t=2131391](http://forum.xda-developers.com/show....php?t=2131391)
:?: Should it be [http://forum.xda-developers.com/showthread.php?t=2131391](http://forum.xda-developers.com/showthread.php?t=2131391)

---

### Post by BDogg718 on 2013-02-10
yes thank u. sry for broken link.

---

### Post by BDogg718 on 2013-02-10
> **linuxsyst said:**
> The link is broken and are you in the same directory where he file is?
Yes. Im in the aokp_jb directory I created and the file is present in the directory.

---

### Post by linuxsyst on 2013-02-10
As I understand platform_manifest is a directory so just cd in it, do this: ```
cd platform_manifest
```
```
mv kernel_manifest.xml ../../.repo/local_manifest.xml
```
when you CD write ls before moving and write ker and press tab so it automatically writes the whole filename

---

