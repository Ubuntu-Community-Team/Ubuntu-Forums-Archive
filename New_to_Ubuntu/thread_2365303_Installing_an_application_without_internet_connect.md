---
title: "Installing an application without internet connectivity"
date: 2017-07-05
forum: New to Ubuntu
---

### Post by petrusski on 2017-07-05
So I came on here earlier asking about installing Ubuntu on a separate partition on my laptop's SSD. Since it has built-in wireless connectivity it makes application installing really easy with just sudo apt-get install.
However, I have four other machines I've scavenged and plan on networking all together. These ones however I do not want to have wireless adapters, for security reasons. However, without wifi, I'm having a hard time getting my apps over.
Starting with Unity Tweak Tools, I downloaded the tar.gz file, extracted it, and transfered it over to my other machine's hard drive. I tried just sudo install as well as make and others, but I just keeping getting errors messages like "nothing to be done, stop".
Is there a terminal command to compile and install the application with all of the files I have?
I do see a file that simply says "unity-tweak-tool" with no extension, and I wonder if that's a binary file I can just move to a /bin or /sbin directory, but attempting that and then running the command in the terminal didn't even give me an error message, just nothing happened.
Thanks in advance.

---

### Post by gordintoronto on 2017-07-05
Install the programs on your internet-connected device. That will download some .deb files. You could copy them onto a USB stick, and move them to the disconnected devices.

If a .deb is available, it's a lot easier to use than a .tar.gz

I don't understand why you are blocking devices running Ubuntu from the Internet. If you are behind a router, the chance of a problem is minuscule.

---

### Post by lisati on 2017-07-05
If you're nervous about wireless, use the strongest security mode available on your WiFi setup, avoiding WEP like the plague where you can.

---

### Post by CatKiller on 2017-07-06
> **petrusski said:**
> These ones however I do not want to have wireless adapters, for security reasons. However, without wifi, I'm having a hard time getting my apps over.

Not having wireless adaptors is not the same as not having Internet access.

If you are determined that these computers should be networked together and should not have a route to the Internet, the appropriate tool for what you're trying to achieve is **apt-mirror**, or **apt-cacher** if you only want those applications that are installed on the Internet-enabled machine to be available to the others.

---

