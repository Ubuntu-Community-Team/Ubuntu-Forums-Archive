---
title: "USB has no login screen on live persistence"
date: 2021-08-21
forum: New to Ubuntu
---

### Post by degarb on 2021-08-21
I am not ready to install on internal hd.  I am runing it off the external drive, using persistent storage, ventoy, with other os install isos.

I am too green to know how to secure the os with a log in.   I think I googled changing the blank default pw, but I want is to get a quick login screen with at least 1 or 2 keys for the password.  Other wise, I don't feel safe logging into the gmail.

---

### Post by ActionParsnip on 2021-08-21
Having a user password has absolutely zero bearing on anything to do with Gmail.
Are you using USB 3?if so, try USB 2. It may help

---

### Post by degarb on 2021-08-21
I never mentioned gmail. I did mention the danger of having browsers and other persistent information.

I just want a loginscreen for the usb 3 ubuntu.  I don't see any way to get it. I boot and bang, no security.

---

### Post by monkeybrain20122 on 2021-08-21
> **degarb said:**
> I never mentioned gmail. I did mention the danger of having browsers and other persistent information.

I just want a loginscreen for the usb 3 ubuntu.  I don't see any way to get it. I boot and bang, no security.

It would be secure without persistence. It stores nothing, so no sensitive info or malicious code either, you get a clean slate every time you reboot.

I am not being facetious, the USB + persistence setup is meant for testing and trouble shooting (say you need some tools to be installed in the rescue usb) It is not meant to be a substitute for a real installation. You can make a portable Ubuntu in a usb by installing in it, following all the steps like you install into the hard drive and have to format the USB in a Linux file system such as ex4. You will need two usbs, one is the live installer, the other the target to install. But I don't really recommend that since performance will be poor (maybe my usb drive was too small, others may have different experience)

---

### Post by C.S.Cameron on 2021-08-21
If running in persistent mode you can go to **Settings/Users** and create a new user with password.
You can set Ubuntu to ask for the password at boot.

---

