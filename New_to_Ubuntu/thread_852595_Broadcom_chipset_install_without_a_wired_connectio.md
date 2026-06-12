---
title: "Broadcom chipset install without a wired connection?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by xeriouxi on 2008-07-07
Hi!

I have a Belkin F5D7051uk Wireless Adapter install on my machine at the moment. I've read that you have to do something kinda complex to get them working in Ubuntu which involves wrappers and stuff, but I don't have access to a wired connection as the wireless box is too far away. Is there any instructions on how to set up the Broadcom-based adapter without a wired connection?

Thank you! =)

---

### Post by ZabiGG on 2008-07-08
Hi there ;)

There is a nice wireless setup guide [here]("http://ubuntuforums.org/showthread.php?t=571188").

I'd recommend you read it in its entirety as well as the posts by users who tried it before you start making any changes to your system, just to make sure you know what you're getting into and you are aware of the issues that may occur during the process.

I hope it helps,

Z.

---

### Post by xeriouxi on 2008-07-09
Thanks ZabiGG for the assistance link! It's much appreciated!

Unfortunately, unless I misread, I need to apt-get the wrapper... but as I have no wired connection to initiate this process I can't see how I'm to get this working. :(

---

### Post by ZabiGG on 2008-07-09
You are using the Internet to write these posts. Can you download the files you need from where you are and put them on a CD or a USB stick?

Then apt-get install from CD or USB.

You can download the deb packages that are in the repos from [here]("http://packages.ubuntu.com/")

---

### Post by framinglory on 2008-07-09
according to this ndiswrapper documentation
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
the ndiswrapper packages are available on the desktop install cd for ubuntu. so if you still have that, you can install ndiswrapper the way listed in the aforementioned documentation, using the cd.

---

### Post by RequinB4 on 2008-07-09
You can download any packages you need offline at packages.ubuntu.com

---

