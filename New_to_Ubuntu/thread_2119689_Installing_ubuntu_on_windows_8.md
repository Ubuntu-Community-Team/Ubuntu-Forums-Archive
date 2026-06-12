---
title: "Installing ubuntu on windows 8"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by user_linux on 2013-02-24
Hi there,
I have a ubuntu 10.04 LTS CD and am trying to run a dual boot on my comp. I usually do wubi but heard wubi isn't compatible with Widnows 8. But even if I put the actual ubuntu CD, I just don't see installation screens. I tried to search online but nowhere does it answers my ques explicitly. Please help.
thx!

---

### Post by oldfred on 2013-02-24
Wubi does not work with gpt partitioning. And all new Windows 8 pre-installed systems are gpt partitioned as that is required for UEFI.

But if you installed Windows 8 yourself you may still have the old MBR partitioning? If so Wubi may work.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

    
But I would not attempt to install 10.04 now, go with 12.04LTS.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by user_linux on 2013-02-24
Exactly. I know that. That;s why I was trying to install using a CD, so that I can later upgrade from the old CD. But I just can't get the installation screens. I remember whenever I used to put the CD, on reboot it would automatically load up, but now now. How can I get the CD to work?
Thx!


> **oldfred said:**
> Wubi does not work with gpt partitioning. And all new Windows 8 pre-installed systems are gpt partitioned as that is required for UEFI.

But if you installed Windows 8 yourself you may still have the old MBR partitioning? If so Wubi may work.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

    
But I would not attempt to install 10.04 now, go with 12.04LTS.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

