---
title: "right click flash player that playing video and flash player crashed every time"
date: 2017-09-03
forum: New to Ubuntu
---

### Post by cuthead on 2017-09-03
here is what I installed flash and firefox version after I choose install third party property software when I install Ubuntu 17.04 AMD64
```
cuthead@cuthead-pc:~$ apt list --installed | grep flash

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

flashplugin-installer/zesty-updates,zesty-security,now 26.0.0.151ubuntu0.17.04.1 amd64 [installed,automatic]
cuthead@cuthead-pc:~$ apt list --installed | grep firefox

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

firefox/zesty-updates,zesty-security,now 55.0.2+build1-0ubuntu0.17.04.1 amd64 [installed,automatic]
firefox-locale-en/zesty-updates,zesty-security,now 55.0.2+build1-0ubuntu0.17.04.1 amd64 [installed]
firefox-locale-zh-hans/zesty-updates,zesty-security,now 55.0.2+build1-0ubuntu0.17.04.1 amd64 [installed]
unity-scope-firefoxbookmarks/zesty,zesty,now 0.1+13.10.20130809.1-0ubuntu1 all [installed,automatic]
cuthead@cuthead-pc:~$ 

```
When I play video or see ad in flash player in firefox,it crashed every time.when I upload picture by flash play uploader it also fail,I have to use basic uploaded instead of.please help me.

---

### Post by linuxissuperawesome on 2017-09-03
How Did You Install Flash?
Try Uninstalling The Flash Plug in And Try Or Switch To Chrome** (It Has Flash Built-In!)**
```
[B]sudo apt-get install flashplugin-installer
```

**And Anyway Why Are You Still Using Flash ([Adobe Cut Support For It!]("http://www.omgubuntu.co.uk/2017/07/adobe-flash-plugin-dead-2020"))**[/B]

---

### Post by cuthead on 2017-09-03
I installed flash player automatic by ubuntu usb flash installer.I reinstall 17.04 and use your manually install flash player it works.how to install chrome,I download chrome from google and after one click it does nothing.I have installed chromium but it does not have flash support.I try to stop using flash.

---

### Post by Dennis N on 2017-09-03
> I have installed chromium but it does not have flash support.

It does have flash player available, but it cannot use the same plugin as Firefox. You need to install the package 'adobe-flashplugin'. How: Enable the 'Canonical Parteners' repository in 'Software and Updates' utility, and then refresh your computer's software list to make it available for installation.

---

### Post by cuthead on 2017-09-03
```
sudo apt install chromium-browser pepperflashplugin-nonfree

```thank you,chromium flash works

---

