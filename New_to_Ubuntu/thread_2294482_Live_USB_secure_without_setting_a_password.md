---
title: "Live USB secure without setting a password?"
date: 2015-09-11
forum: New to Ubuntu
---

### Post by dave194 on 2015-09-11
Running Ubuntu 14.04 from a live USB with persistence, I'm not prompted to set a password.  Should I set up a user and password anyway?  If so, can I get it to default to that user when booting up?

Articles say Ubuntu is secure because root is locked and a hacker can't guess your userID and password, so I'm wondering if I lose that benefit by continuing to run with the default.

Thanks,
Dave

---

### Post by sudodus on 2015-09-11
If you want the security of a password also against an intruder that has physical access to the drive, you should have an installed system with encrypted disk (or encrypted home). It is difficult to create your own secure system.

But then you need a good backup routine, because there is no way to recover the data if you forget the password/passphrase or if the drive is corrupted somehow.

---

### Post by dave194 on 2015-09-11
> **sudodus said:**
> If you want the security of a password also against an intruder that has physical access to the drive, you should have an installed system with encrypted disk (or encrypted home). It is difficult to create your own secure system.

But then you need a good backup routine, because there is no way to recover the data if you forget the password/passphrase or if the drive is corrupted somehow.
I don't need to protect against anyone with physical access to the drive.  My question relates, rather, to accessing the web via browser, Filezilla, etc., using the default "ubuntu" user which has no password.

Thanks,
Dave

---

### Post by yancek on 2015-09-11
I don't have a persistent usb to test on but you could open System Settings, go to User Accounts and see if you could add a password for the default ubuntu user.  If that fails, create another user with administrative privileges and create a password for that user.

---

### Post by dave194 on 2015-09-11
Thank you sudodus and yancek.  My concern about using the live USB is confirmed in this article [https://www.maketecheasier.com/persistent-live-usb-vs-full-install-usb/](https://www.maketecheasier.com/persistent-live-usb-vs-full-install-usb/) which says:
> The main disadvantage of a Persistent Live USB is the security issue.  When you boot up a live USB, it boots directly to the desktop. There is  no login or any security mechanism to protect anyone from accessing your  data. The live USB is meant for you to test the distro and install it  to the hard drive if you like it. It is not meant to be used as a  production OS.
But the article was written in July 2013, a little over 2 years ago.

Is this lack of security still valid?  Or have things changed since then?

---

### Post by sudodus on 2015-09-11
It is still valid. So if you need high security, I suggest that you install a system with encrypted disk with LVM.

One good point is that a 'live only' system does not save anything, which means that malware does not survive poweroff and reboot. But a 'persistent live' system does not have this simple way to clean itself.

So for personal use, a live only system can be quite good, if you reboot after each risky internet adventure ;-) 

You can also combine it with separately encrypted files or folders 'somewhere else', not in the live system, but for example in another pendrive or in a 'data' partition in the same pendrive.

---

### Post by dave194 on 2015-09-13
> **sudodus said:**
> It is still valid. So if you need high security, I suggest that you install a system with encrypted disk with LVM.

One good point is that a 'live only' system does not save anything, which means that malware does not survive poweroff and reboot. But a 'persistent live' system does not have this simple way to clean itself.

So for personal use, a live only system can be quite good, if you reboot after each risky internet adventure ;-) 

You can also combine it with separately encrypted files or folders 'somewhere else', not in the live system, but for example in another pendrive or in a 'data' partition in the same pendrive.
Thank you, again, sudodus.  I'm in the process of purchasing a small external SSD drive for under $50, and will do a full install on that drive, so that a password will be required.  Thanks.

---

### Post by sudodus on 2015-09-13
You are welcome :-)

When you have a working system in that SSD, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by mastablasta on 2015-09-15
for that kind of money you get a small 500 GB external drive. what would be the benefit of using external SSD besides paying a lot more for it? 

also the password identifies that it is the user accessing the PC not some program. it doesn't protect the data. to really protect the data you need encryption. and if you want something really strong read articles about Ubuntu hardening. Firewall will be your biggest protection. the less services people can access to from internet the better.

---

