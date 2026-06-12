---
title: "Universal-USB-Installer-1.8.7.4.exe Not Opening"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by BNZBKK on 2011-12-26
I'm trying to download the Universal USB Installer from PendriveLinux.com 

I get this on trying to open it....

[B]Archive:  /home/xx/Desktop/Universal-USB-Installer-1.8.7.4.exe
[/home/xx/Desktop/Universal-USB-Installer-1.8.7.4.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/xx/Desktop/Universal-USB-Installer-1.8.7.4.exe or
          /home/xx/Desktop/Universal-USB-Installer-1.8.7.4.exe.zip, and cannot find /home/xx/Desktop/Universal-USB-Installer-1.8.7.4.exe.ZIP, period.[/B]


How do I open it ? :confused:

---

### Post by holycow131415 on 2011-12-26
exe's arent executable by default in linux. right click on the exe file, go to permissions and check off executable.

---

### Post by coffeecat on 2011-12-26
PendriveLinux.com's Universal-USB-Installer-1.8.7.4.exe is a Windows application for creating Linux live USBs. That is, you can only run it in Windows. It has not been ported to Linux. It sounds as though you are trying to open it with Archive Manager. Are you trying to open it to examine it, or are you trying to run it? If you are trying to run it in Ubuntu, you can't. If you want to create a Linux live USB, you'd need to use something like unetbootin.

---

### Post by BNZBKK on 2011-12-26
> **coffeecat said:**
> PendriveLinux.com's Universal-USB-Installer-1.8.7.4.exe is a Windows application for creating Linux live USBs. That is, you can only run it in Windows. It has not been ported to Linux. It sounds as though you are trying to open it with Archive Manager. Are you trying to open it to examine it, or are you trying to run it? If you are trying to run it in Ubuntu, you can't. If you want to create a Linux live USB, you'd need to use something like unetbootin.

Yes I was trying to run it in Unbuntu, thanks for the explanation

---

