---
title: "New user.  Purple screen. No onboard graphics."
date: 2012-09-06
forum: New to Ubuntu
---

### Post by duskmask on 2012-09-06
Amd 4170
gtx 550 ti
windows 7
 
I have installed the latest ubuntu os. After rebooting I get asked what os to use. I select ubuntu. Very quickly goes to purple screen. Im guessing from what I have read that my video card and no onboard graphics is the problem. Can someone point me to some links or give me advice on how to get up and running? Thanks in advance.

---

### Post by Bashing-om on 2012-09-06
duskmask; Hi ! Welcome to the forum.

  here is the howto:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

  When booting the install cd, after the bios screen clears -hit any key to enable a boot options screen; choose "nomodeset" to boot up the ubuntu operating system.

I expect you will be able to. If you can, the howto has instructions to make the option permanent.

post back with an updated status and/or any further questions.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Bashing-om on 2012-09-06
duskmask;


  The gtx 550 ti is that an nvidia card ?(pops in my mind is). If the howto does not resolve your present problem, we may have to research into oldfred's threads for a solution; But, there are solutions!


[INDENT]BDQ
[/INDENT]

---

### Post by duskmask on 2012-09-06
I have installed Ubuntu using a USB.  At start up I get the Windows Boot Manager.  With Two options: Windows 7 or Ubuntu.  The only thing I can do at start up is press the DEL key and get into the Asus Bios.  Do I need to reinstall from usb and folow your post advice?

---

### Post by duskmask on 2012-09-06
Yes, it is a Nvidia Card

---

### Post by Bashing-om on 2012-09-06
I say again,,, as soon as the bios screen clears ...engage any key (shift key in past versions) ..hold it down... will bring you to a boot options screen. Follow the on-menu directions to boot with the parameter "nomodeset" ... I expect/hope you are able to boot up to ubuntu.
  If there is any problem at all I will try to clarify.
[INDENT][INDENT]BDQ
[/INDENT][/INDENT]

---

### Post by Epodx64 on 2012-09-07
I had a very similar problem with a integrated MCP61 Geforce 6150se Nforce 430 It appeared either Ubuntu installed the wrong driver or there where major regressions in the driver either way what I did was booted in to recovery mode into a console and did this

sudo add-apt-repository ppa: x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

It uses the 304 driver which worked well for me.

p.s. although the Nvidia problem became such a problem for me I sold my Jetway MCP 61 Athlon x2 6000+ and replaced it with a Gigabyte board w/ Intel Core 2 Duo and Integrated Intel Graphics haven't had a problem since.

---

### Post by Bashing-om on 2012-09-07
@duskmask;
as I am in the midst of a thunderstorm I am shutting my system down (preventive measures) and going to get some shuteye... will check on your status in my AM ..


[INDENT][INDENT]regards <==BDQ

[/INDENT][/INDENT]

---

### Post by duskmask on 2012-09-07
Got it to go to GNU GRUB version 1.99-21ubuntu3.1"  With two options: Ubuntu, with Linux 3.2.0-generic and Ubuntu, with Linux 3.2.0-generic (recovery mode)

---

### Post by duskmask on 2012-09-07
Thanks, got me headed in the right direction.  Made it in.  That problem solved, now on to the next one. ;>

---

### Post by Bashing-om on 2012-09-07
Outstanding!

 Please relate the steps you took to resolve.... so others will know.

and mark this thread as solved to aid others seeking solutions.

[INDENT]Tks, enjoy ubuntu <==BDQ
[/INDENT]

---

