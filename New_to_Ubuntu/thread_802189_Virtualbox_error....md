---
title: "Virtualbox error..."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-21
I recentley uninstalled the old virtualbox ose edition from my pc and installed the version from the innotek site but im having problems with using my usb pen drive. This is the error i get when i try to open up the settings window

```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x00004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {f95c0793-7737-49a1-85d9-6da81097173b}


```

thanks in advance

---

### Post by shifty_powers on 2008-05-21
[http://samiux.wordpress.com/2007/10/27/make-usb-works-on-virtualbox-152-ubuntu-710/](http://samiux.wordpress.com/2007/10/27/make-usb-works-on-virtualbox-152-ubuntu-710/)

might help...

---

### Post by farsight on 2008-05-21
I could be wrong in saying this but as far as I know the open source virtualbox does not yet support usb. However I believe I've read that people say the "closed source" does support usb. Correct me if I'm wrong because I too would enjoy using my printer inside the virtual machine :)

regards
Farsight

---

### Post by kamitsukai on 2008-05-21
> **farsight said:**
> I could be wrong in saying this but as far as I know the open source virtualbox does not yet support usb. However I believe I've read that people say the "closed source" does support usb. Correct me if I'm wrong because I too would enjoy using my printer inside the virtual machine :)

regards
Farsight

im not using the opensource one:mad: and the above did not work :(

---

### Post by bumanie on 2008-05-21
I believe farsight is correct. You need to use the binary (free for home use) version of virtualbox to get usb support. Follow [this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") to get usb function

---

### Post by kamitsukai on 2008-05-21
> **bumanie said:**
> I believe farsight is correct. You need to use the binary (free for home use) version of virtualbox to get usb support. Follow [this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") to get usb function

Refer to the above statement...and thanks i will try the bit about how to get usb support :)

---

### Post by shifty_powers on 2008-05-21
found it.

i had a bugger of a time getting usb to work with virtualbox until i followed this tutorial and it worked perfectly ;)

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

good luck ;)

---

### Post by kamitsukai on 2008-05-21
None of that is working...

---

### Post by bumanie on 2008-05-21
> None of that is working... It should work, I've installed vobx that way with usb support on many occassions. Are you sure you have the binary version and have uninstalled the ose version? The binary from innotek has .deb packages

---

### Post by kamitsukai on 2008-05-21
yes...

---

### Post by bumanie on 2008-05-21
If you have done all that, then I have no idea why it won't work. I use version 1.5.4, because the later versions won't allow me to grab the virtual mouse. Bit of a long shot, but you could try an earlier version and see if that works. I would also reset all the altered files (adduser, /etc/fstab etc.), back to how they were before you started. Sorry, I can't be of more help.

---

