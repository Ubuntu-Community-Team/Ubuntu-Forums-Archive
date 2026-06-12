---
title: "Rhythmbox sees MacBook music files, but says they don't exist"
date: 2017-02-20
forum: New to Ubuntu
---

### Post by ankvigil on 2017-02-20
Trying to share music files from my MacBook (with Sierra).   Rhythm box able to see my folders, but when I click on any folder it says the files don't exist.

---

### Post by HermanAB on 2017-02-21
That sounds like a SMB permissions problem with your Mac - assuming that you are running a SMB server on your Mac.  You will only be able to figure it out by using the command line utility smbclient from your Linux workstation, since you need to see the error messages.

---

### Post by ankvigil on 2017-02-23
Ok.  Got smbclient and 12 lines.  Now need to figure out how to select and copy with hp pavilion dv6 laptop.... To show what it has

---

### Post by guinea2 on 2017-02-25
I have the same problem, when I try to click on my Macs hard drive from ubuntu it just says it can't access it. It must be some kind of security thing that MacOS has.

---

