---
title: "Boots in Command Screen"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Wolffee on 2012-10-12
Hey guys,
I have a dual partitioned hard drive with win 7 and ubuntu 12.04. I am using an AMD Radeon 7850 graphics card and did not have trouble booting unbuntu until after I installed the latest update on from ubuntu on my computer. Now ubuntu starts out booting just fine but then the screen goes back and it enters the command screen. There is no option that I can find for actually booting my computer the rest of the way up. I have tried looking for the answer to this problem on previous people's threads but nothing seems to be working. What should I do? 
Thank for reading! You guys are awesome
--Ty

---

### Post by NikTh on 2012-10-12
Hi , 

The problem can be related to graphics driver or/and to the kernel. 

What driver you use ? The pre-installed radeon or the fglrx from additional drivers ? 

Try during boot (if you haven't grub menu) hold down [Shift] key until the grub menu loaded. 
From there you can select an older kernel (Previous Linux versions) and try to boot from there.
Thanks

---

### Post by DuckHook on 2012-10-12
You mentioned that it was an update and not an upgrade. Please confirm. The difference is extremely important.

If just an update, then we have somewhere to start from because you at least have the command prompt.

Make sure you are logged in. Then type:

```
sudo service lightdm restart

```It is unlikely that your xsession will start, but what we are looking for is the error output. If it does start, then we will hunt for the reason in comfort. If not, and the error output goes by too fast, then type:

```
sudo service lightdm restart 2> ~/Desktop/errors.txt

```then:

```
nano ~/Desktop/errors.txt
```and let's see what we've got.

Note: I have a little more time this evening, but will probably be unavailable thereafter and throughout the weekend. If any one else can help, please feel free to jump in.

---

### Post by Wolffee on 2012-10-13
Hey guys, I tried both of those methods and they didn't work. Trying to boot from and older version resulted in the same problem and there was no way I could find around it. When I tried duckhook's method I got these responses in order:
Sudo: not found
Can't create -/desktop/errors.txt: nonexistent directory
Nano:not found
The screen my computer is booting into says "built in shell (ash)" at the top. And it gives me the option to type help for commands. Since it didn't recognize sudo I'm worried it might not be a command screen like it appeared to be. 
The commands it lists are: 
Alias break cd cdir command continue echo eval exec exit export false getopts hash help let local printf per read readonly return set shift test times trap true type unlimit unmask unalias upset wait [ [[ ash awl basename blockdev cat chmod chroot chvt clear cmp cp cut deallocvt df dnsdomainname du dumpkmap echo egrep env expr false fbset fdflush fgrep find grep gunzip gzip hostname iconfig ip kill ln loadfont loadkmap ls mkdir mkfifo mknod mkswap mktemp modinfo more mount mv openvt pidof printf ps pwd readlink reset rm rmdir sed seq setkeycodes sh sleep sort stat statistic-sh stty switch_root sync tail tee test touch tr true tty unmount uname uniq wc wget which yes zcat
I seriously don't understand this.

---

### Post by Wolffee on 2012-10-13
Yeah, realizing now that it's booting into buysbox which is I suppose a type of command screen but definitely not the same thing. This probably means I have a hard drive error. Any suggestions for what to do?

---

### Post by DuckHook on 2012-10-13
> **Wolffee said:**
> Yeah, realizing now that it's booting into buysbox which is I suppose a type of command screen but definitely not the same thing. This probably means I have a hard drive error. Any suggestions for what to do?

You are correct: you are in busybox. busybox is a dwarf-version of Unix that is part of your initramfs. ...nix that. All you need to know is that your system likely booted up to the point where it tried to mount your root file system and could not find it, so fell back to busybox.

This is probably reasonably easy to fix but also could mean a bad HD. No need to panic, but should proceed carefully.

1. What were you doing prior to this problem? You mentioned "updating" in initial post, but many new users say "updating" when they actually mean "upgrading". In short, were you already running 12.04 and just applying the usual patches, or were you upgrading from a prior version of Ubuntu to 12.04? (Sorry to sound too elementary, but don't know your Linux experience)

2. Does Windows boot up fine?

3. Is there critical data on your Linux partition and if so, do you have a recent backup?

4. Do you just get the busybox shell or are there error messages within? If so, please post here.

Fix could be as simple as boot repair (see here):

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not try this yet. First, answer four questions above.

---

### Post by Wolffee on 2012-10-13
1) My computer is fairly new so I was definitely updating not upgrading. I installed ubuntu on half of my hard drive a couple months ago and it was 12.04. I'm not even sure the updates had anything to do with this but ubuntu hasn't booted correctly since then so correlation might equal causation haha. And it's okay, elementary is just fine. I'm new to linux so I'm ignorant but I'm learning. 

2)Windows boots up just peachy. Absolutely no problems, I even ran a check on that half of my hard drive. 

3) There is no critical data on linux. 

4) Just the busy box shell, no error messages. 

Also, I feel this information might be pertinent, I had to run boot repair after I installed linux. grub wouldn't load at all so I went through the process of uninstalling then reinstalling it using the flash drive I booted ubuntu from and boot repair. I don't know if that's important but now you know. To be clear, linux ran just fine for weeks after having reinstalled grub. 

So what should I do, Duckhook? Or anyone else out there with my expertise than I?

---

### Post by NikTh on 2012-10-13
Boot with LiveCD/USb and run again the [boot-repair](https://help.ubuntu.com/community/Boot-Repair) program. 

Create a boot-info summary and attach the file here or give the link.

---

### Post by Wolffee on 2012-10-13
Done.

[http://paste.ubuntu.com/1278219/](http://paste.ubuntu.com/1278219/)

---

### Post by NikTh on 2012-10-14
[quote="Boot Info Script"]Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try[/quote] 

/dev/sda5 , I assume is Ubuntu partition , is corrupted. 

Follow [this](http://ubuntuforums.org/showpost.php?p=12286424&postcount=9) to correct the problem. 

Thanks

---

### Post by Wolffee on 2012-10-14
Thank you so much everyone! Linux is booting correctly again and running as good as ever. I really appreciate the help, I couldn't have figured that out on my own. I have another question though, Ubuntu has 34 updates it wants me to install. Updating is what seemed to cause this problem in the first place. What should I do? Some are "important security updates" and some are just "recommended" 
Thanks again

---

### Post by NikTh on 2012-10-14
> **Wolffee said:**
> Thank you so much everyone! Linux is booting correctly again and running as good as ever. I really appreciate the help, I couldn't have figured that out on my own. I have another question though, Ubuntu has 34 updates it wants me to install. Updating is what seemed to cause this problem in the first place. What should I do? Some are "important security updates" and some are just "recommended" 
Thanks again

You should definitely update the "important security updates". 

Personally I apply all of the updates (after review them, not in blind). 

If the problem occurs again , now you know how to correct it ;)

And mark the thread as solved , please . 

Thanks

---

### Post by Wolffee on 2012-10-14
EDIT; I responded to this twice because my internet was being stupid, thanks again. I will install the updates.

---

