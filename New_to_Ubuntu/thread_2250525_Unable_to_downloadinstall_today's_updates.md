---
title: "Unable to download/install today's updates"
date: 2014-10-29
forum: New to Ubuntu
---

### Post by harfin on 2014-10-29
Four weeks ago I reported a problem regarding updates, [http://ubuntuforums.org/showthread.php?t=2245790](http://ubuntuforums.org/showthread.php?t=2245790)

It has now re-occurred!

The error is [I]"The upgrade needs a total of 93.3 M free space on disk '/boot'. Please free at least an additional 6,072 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."
[/I]
[LIST=1]
[*]I ran the suggested command and then tried to update and got same error message.
[*]Rebooted, and repeated the command and got same error message.
[*]I repeated the recommended steps from my earlier post (it cleared one update), rebooted and then re-ran and the then tried to run the upgrade. Same error and got same error message, *"The upgrade needs a total of 93.3 M free space on disk '/boot'. Please free at least an additional 6,072 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."*
[/LIST]
[I]&#8203;
[/I]Suggestions please

Ran [COLOR=#000000][FONT=Ubuntu Mono]ls -l /boot - output:[/FONT][/COLOR]total 134607
-rw-r--r-- 1 root root  1163858 Aug 15 03:56 abi-3.13.0-35-generic
-rw-r--r-- 1 root root  1164489 Sep 22 23:24 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  1164489 Oct  9 13:33 abi-3.13.0-38-generic
-rw-r--r-- 1 root root   165652 Aug 15 03:56 config-3.13.0-35-generic
-rw-r--r-- 1 root root   165712 Sep 22 23:24 config-3.13.0-37-generic
-rw-r--r-- 1 root root   165712 Oct  9 13:33 config-3.13.0-38-generic
drwxr-xr-x 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     1024 Oct 15 07:50 grub
-rw-r--r-- 1 root root 29224467 Sep 26 17:59 initrd.img-3.13.0-35-generic
-rw-r--r-- 1 root root 29242045 Sep 27 08:58 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 29243714 Oct 15 07:50 initrd.img-3.13.0-38-generic
drwx------ 2 root root    12288 Jul 28 12:48 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3386444 Aug 15 03:56 System.map-3.13.0-35-generic
-rw------- 1 root root  3386945 Sep 22 23:24 System.map-3.13.0-37-generic
-rw------- 1 root root  3386936 Oct  9 13:33 System.map-3.13.0-38-generic
-rw------- 1 root root  5806368 Aug 15 03:56 vmlinuz-3.13.0-35-generic
-rw------- 1 root root  5808280 Sep 26 17:58 vmlinuz-3.13.0-35-generic.efi.signed
-rw------- 1 root root  5808832 Sep 22 23:24 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  5810744 Sep 27 08:57 vmlinuz-3.13.0-37-generic.efi.signed
-rw------- 1 root root  5808736 Oct  9 13:33 vmlinuz-3.13.0-38-generic
-rw------- 1 root root  5810648 Oct 15 07:50 vmlinuz-3.13.0-38-generic.efi.signed

Then uname -a. 
Output
Linux harfin-HP-255-G1-Notebook-PC 3.13.0-38-generic #65-Ubuntu SMP Thu Oct 9 11:36:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Then [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get autoremove
[/FONT][/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 27 not to upgrade.

Then [COLOR=#000000][FONT=Ubuntu Mono]sudo du -h /boot
Output
[/FONT][/COLOR]3.4M	/boot/efi/EFI/ubuntu
3.4M	/boot/efi/EFI
3.4M	/boot/efi
12K	/boot/lost+found
2.4M	/boot/grub/fonts
2.9M	/boot/grub/x86_64-efi
9.0K	/boot/grub/locale
7.5M	/boot/grub
143M	/boot





[COLOR=#000000][FONT=Ubuntu Mono]Alan[/FONT][/COLOR]

---

### Post by coffeecat on 2014-10-29
It sounds as though /boot has filled up with kernels again, which is rather surprising in only 4 weeks. Before you run slickymaster's command again, post the output of this:

```
ls -l /boot
```

---

### Post by slickymaster on 2014-10-29
> **coffeecat said:**
> It sounds as though /boot has filled up with kernels again, which is rather surprising in only 4 weeks. Before you run slickymaster's command again, post the output of this:

```
ls -l /boot
```

Indeed coffeecat. It's odd to say the least.

---

### Post by coffeecat on 2014-10-29
Err - when someone asks you to post the output of a command, please post in a new post. If you simply edit your earlier post, the person asking for the information - and others - might  miss that you have added it.

But to your problem. You have three kernels only, so you need to remove the oldest. This should do the trick and is simpler than the command you used in the previous thread:

```
sudo apt-get autoremove
```

Please keep an eye on this thread. I'm going to ask you to add a me-too to a bug about this problem of an undersized /boot partition with encrypted installs. I need to find the link.

---

### Post by coffeecat on 2014-10-29
@slickymaster, any thoughts about 3 kernels taking up 143M?

---

### Post by Irihapeti on 2014-10-29
On my machine running 14.04, ONE kernel (linux-image plus linux-image-extra) takes up that much space.

Edit: just realised that it isn't only /boot.

One kernel amounts to approximately 25 MB in /boot

---

### Post by slickymaster on 2014-10-29
> **coffeecat said:**
> @slickymaster, any thoughts about 3 kernels taking up 143M?

```
-rw------- 1 root root 5806368 Aug 15 03:56 vmlinuz-3.13.0-35-generic
-rw------- 1 root root 5808280 Sep 26 17:58 vmlinuz-3.13.0-35-generic.efi.signed
-rw------- 1 root root 5808832 Sep 22 23:24 vmlinuz-3.13.0-37-generic
-rw------- 1 root root 5810744 Sep 27 08:57 vmlinuz-3.13.0-37-generic.efi.signed
-rw------- 1 root root 5808736 Oct 9 13:33 vmlinuz-3.13.0-38-generic
-rw------- 1 root root 5810648 Oct 15 07:50 vmlinuz-3.13.0-38-generic.efi.signed
```

I don't have anything to backup my reasoning since I never used them, but can it be due to the fact that the OP is booting a self-signed Linux kernel which include EFI stub loader a component of the kernel (as far as I remember)?

---

### Post by jhay2 on 2014-10-29
download ubuntu-tweak if you can access your desktop .. sudo apt-get install ubuntu-tweak , then go to janitor and clean all unwanted files and unused kernels .. :)    or you can use also synaptics

---

### Post by slickymaster on 2014-10-29
> **Irihapeti said:**
> On my machine running 14.04, ONE kernel (linux-image plus linux-image-extra) takes up that much space.

Edit: just realised that it isn't only /boot.

One kernel amounts to approximately 25 MB in /boot

I always keep two kernels in my boxes:```
~$ dpkg-query -l | awk '/linux-image-*/ {print $2}'
linux-image-3.16.0-22-generic
linux-image-3.16.0-23-generic
linux-image-extra-3.16.0-22-generic
linux-image-extra-3.16.0-23-generic
linux-image-generic

```Presently this is what it looks like```
~$ sudo du -h /boot
[sudo] password for slickymaster: 
2,3M	/boot/grub/fonts
20K	/boot/grub/locale
2,4M	/boot/grub/i386-pc
7,1M	/boot/grub
66M	/boot

```

---

### Post by coffeecat on 2014-10-29
> **slickymaster said:**
> I don't have anything to backup my reasoning since I never used them, but can it be due to the fact that the OP is booting a self-signed Linux kernel which include EFI stub loader a component of the kernel (as far as I remember)?

Yes, I was wondering that. [In their earlier thread]("http://ubuntuforums.org/showthread.php?t=2245790") they had five kernels - but only three with efi.signed - before they filled the /boot partition.

This is the bug we need to get more heat into by asking people to click on "affects me". I'll post it now and hopefully get the OP to do so when they come back.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

---

### Post by slickymaster on 2014-10-29
> **coffeecat said:**
> Yes, I was wondering that. [In their earlier thread]("http://ubuntuforums.org/showthread.php?t=2245790") they had five kernels - but only three with efi.signed - before they filled the /boot partition.

This is the bug we need to get more heat into by asking people to click on "affects me". I'll post it now and hopefully get the OP to do so when they come back.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

@harfin:
Please [create an account at Launchpad]("https://launchpad.net/"), if you don't already have one. Once that done, please follow the bug report link coffeecat provided, click the "_This bug affects 11 people. Does this bug affect you?_" link at the top left, and answer to 'Does this bug affect you' with '**This bug affects me**' adding any additional information as comments.

[ATTACH=CONFIG]257586[/ATTACH]

---

### Post by harfin on 2014-10-29
> **slickymaster said:**
> @harfin:
Please [create an account at Launchpad]("https://launchpad.net/"), if you don't already have one. Once that done, please follow the bug report link coffeecat provided, click the "_This bug affects 11 people. Does this bug affect you?_" link at the top left, and answer to 'Does this bug affect you' with '**This bug affects me**' adding any additional information as comments.

[ATTACH=CONFIG]257586[/ATTACH]
Hi slickymaster / coffeecat

Sorry for delay, but have been tied up for most of the day on other matters. 

I have done as requested and added a 'me-too' to the bug thread.

Not sure what else I need to / can do?

Harfin

---

### Post by slickymaster on 2014-10-29
> **harfin said:**
> Hi slickymaster / coffeecat

Sorry for delay, but have been tied up for most of the day on other matters. 

I have done as requested and added a 'me-too' to the bug thread.

Not sure what else I need to / can do?

Harfin

Until that bug gets fixed upstream what you can do is to follow coffeecat advise:> **coffeecat said:**
> <---snip--->
But to your problem. You have three kernels only, so you need to remove the oldest. This should do the trick and is simpler than the command you used in the previous thread:

```
sudo apt-get autoremove
```<---snip--->
After running that command, please post back again in this thread, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect, the output you get from```
ls -l /boot
```

---

### Post by harfin on 2014-10-29
> **slickymaster said:**
> Until that bug gets fixed upstream what you can do is to follow coffeecat advise:
After running that command, please post back again in this thread, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect, the output you get from```
ls -l /boot
```

Ran sudo apt-get autoremove:-
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ sudo apt-get autoremove
[sudo] password for harfin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 27 not to upgrade.

```[/QUOTE}

---

### Post by harfin on 2014-10-29
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -l /boot
total 134607
-rw-r--r-- 1 root root  1163858 Aug 15 03:56 abi-3.13.0-35-generic
-rw-r--r-- 1 root root  1164489 Sep 22 23:24 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  1164489 Oct  9 13:33 abi-3.13.0-38-generic
-rw-r--r-- 1 root root   165652 Aug 15 03:56 config-3.13.0-35-generic
-rw-r--r-- 1 root root   165712 Sep 22 23:24 config-3.13.0-37-generic
-rw-r--r-- 1 root root   165712 Oct  9 13:33 config-3.13.0-38-generic
drwxr-xr-x 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     1024 Oct 15 07:50 grub
-rw-r--r-- 1 root root 29224467 Sep 26 17:59 initrd.img-3.13.0-35-generic
-rw-r--r-- 1 root root 29242045 Sep 27 08:58 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 29243714 Oct 15 07:50 initrd.img-3.13.0-38-generic
drwx------ 2 root root    12288 Jul 28 12:48 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3386444 Aug 15 03:56 System.map-3.13.0-35-generic
-rw------- 1 root root  3386945 Sep 22 23:24 System.map-3.13.0-37-generic
-rw------- 1 root root  3386936 Oct  9 13:33 System.map-3.13.0-38-generic
-rw------- 1 root root  5806368 Aug 15 03:56 vmlinuz-3.13.0-35-generic
-rw------- 1 root root  5808280 Sep 26 17:58 vmlinuz-3.13.0-35-generic.efi.signed
-rw------- 1 root root  5808832 Sep 22 23:24 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  5810744 Sep 27 08:57 vmlinuz-3.13.0-37-generic.efi.signed
-rw------- 1 root root  5808736 Oct  9 13:33 vmlinuz-3.13.0-38-generic
-rw------- 1 root root  5810648 Oct 15 07:50 vmlinuz-3.13.0-38-generic.efi.signed 
```[/QUOTE]

---

### Post by coffeecat on 2014-10-29
Hmmm. apt-get autoremove is meant to uninstall surplus kernels in Trusty, but it didn't. It does in Utopic, which is odd.

Do you have the package manager synaptic installed? If you do, the simplest way to get rid of the 3.13.0-35 kernel is to search for "3.13.0-35" in synaptic and use it to uninstall the four packages it will show you that are installed for that version of the kernel. But that's not a long-term solution. It looks as though every time there is a kernel upgrade you are going to have to purge the third oldest kernel manually. We need to find a better way.

---

### Post by harfin on 2014-10-30
> **coffeecat said:**
> Hmmm. apt-get autoremove is meant to uninstall surplus kernels in Trusty, but it didn't. It does in Utopic, which is odd.

Do you have the package manager synaptic installed? If you do, the simplest way to get rid of the 3.13.0-35 kernel is to search for "3.13.0-35" in synaptic and use it to uninstall the four packages it will show you that are installed for that version of the kernel. But that's not a long-term solution. It looks as though every time there is a kernel upgrade you are going to have to purge the third oldest kernel manually. We need to find a better way.

Hi Coffeecat

I do not have Synaptic installed at the moment, but will do that later today. Wilad when I have done so and when I have done as you suggest as regards deleting the surplus files.

---

### Post by slickymaster on 2014-10-30
> **coffeecat said:**
> Hmmm. apt-get autoremove is meant to uninstall surplus kernels in Trusty, but it didn't. It does in Utopic, which is odd.
<---snip--->

Exactly. But let me also add something to the realm of oddity of this equation, coffeecat. After today's updates, which brought 3.16.0-24 kernel, I run **sudo apt-get autoremove** and to my surprise it didn't remove nothing. :confused:

This is what my box had, kernel wise, after installing 3.16.0-24
```
~$ dpkg-query -l | awk '/linux-image-*/ {print $2}'
linux-image-3.16.0-22-generic
linux-image-3.16.0-23-generic
linux-image-3.16.0-24-generic
linux-image-extra-3.16.0-22-generic
linux-image-extra-3.16.0-23-generic
linux-image-extra-3.16.0-24-generic
linux-image-generic
~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```I had to remove 3.16.0-22 manually. This is on a VV setup```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid
3.16.0-24-generic
```

---

### Post by harfin on 2014-10-30
> **coffeecat said:**
> Hmmm. apt-get autoremove is meant to uninstall surplus kernels in Trusty, but it didn't. It does in Utopic, which is odd.

Do you have the package manager synaptic installed? If you do, the simplest way to get rid of the 3.13.0-35 kernel is to search for "3.13.0-35" in synaptic and use it to uninstall the four packages it will show you that are installed for that version of the kernel. But that's not a long-term solution. It looks as though every time there is a kernel upgrade you are going to have to purge the third oldest kernel manually. We need to find a better way.

Just downloaded synaptic and searched for 3.13.0-35, 
It found five not four
linux-headers-3.13.0-35-62                          Vsn 3.13.0-35-62
linux-headers-3.13.0-35-generic                  Vsn-3.13.0-35-62
linux-image-3.13.0-35-generic                     Vsn-3.13.0-35-62
linux-image-extra-3.13.0-35-generic            Vsn-3.13.0-35-62
linux-signed-image-3.13.0-35-generic          Vsn-3.13.0-35-62

Never done this before, so are they the files I need to delete?
Harfin

---

### Post by Bashing-om on 2014-10-30
et al ; Just my bit to add:

autoremove does work in 'trusty':
```

sysop@1404mini:~$ sudo apt-get autoremove
[sudo] password for sysop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.13.0-36 linux-headers-3.13.0-36-generic
  linux-image-3.13.0-36-generic linux-image-extra-3.13.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 271 MB disk space will be freed.
Do you want to continue? [Y/n] y

```

Something peculiar to harfin's system ; linux-signed-image-, that kernel does not exist on my system:
```

sysop@1404mini:~$ dpkg -l | grep linux-signed-image
sysop@1404mini:~$ 

```

@ harfin; Yes those files are no longer needed and may be, and you do want to, remove them.

I also check the 'rc' flagged files in the system ( r = removed, c = config files remain ) and remove those files:
```

dpkg -l | grep linux-
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

[INDENT][INDENT]hope it is a bit of help
[/INDENT][/INDENT]

---

### Post by Irihapeti on 2014-10-30
I see to recall that sudo apt-get autoremove will remove old kernels on development releases. It does not remove old kernels on a released version. At that point, you have to remove them yourself.

---

### Post by mörgæs on 2014-10-31
No, for 14.04 and 14.10 ```
sudo apt-get autoremove
``` removes everything but the latest two kernels. It does not matter if the version is under development or released. 

After autoremove please run 
```
dpkg -l 'linux-*'
```

It gives a list of installed kernels (ii to the left) and removed kernels for which the config files have been kept (rc to the left).

---

### Post by harfin on 2014-11-01
> **mörgæs said:**
> No, for 14.04 and 14.10 ```
sudo apt-get autoremove
``` removes everything but the latest two kernels. It does not matter if the version is under development or released. 

After autoremove please run 
```
dpkg -l 'linux-*'
```

It gives a list of installed kernels (ii to the left) and removed kernels for which the config files have been kept (rc to the left).

Sorry to disagree mörgæs!
As was detailed and confirmed earlier in this post, the autoremove does **not **do as you suggest.
I did as you suggest several days ago, and after running autoremove the oldest of three kernels are **still **there; the outputs following the autoremove (as shown earlier) confirm this.

Harfin

---

### Post by mörgæs on 2014-11-01
The intended message was 'everything works as expected on my system'.

Could you post the output from the command I posted, please?

---

### Post by harfin on 2014-11-11
> **mörgæs said:**
> The intended message was 'everything works as expected on my system'.

Could you post the output from the command I posted, please?
I apologise for not responding sooner, but I had already followed earlier advice and downloaded Synaptic and deleted the earliest surplus kernel.
Yesterday  3.13.0-40.68 arrived, and again I have the same message as regards insufficient space as before.
As before before doing anything else:
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -l /boot
total 134631
-rw-r--r-- 1 root root  1164489 Sep 22 23:24 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  1164489 Oct  9 13:33 abi-3.13.0-38-generic
-rw-r--r-- 1 root root  1164547 Oct 28 14:25 abi-3.13.0-39-generic
-rw-r--r-- 1 root root   165712 Sep 22 23:24 config-3.13.0-37-generic
-rw-r--r-- 1 root root   165712 Oct  9 13:33 config-3.13.0-38-generic
-rw-r--r-- 1 root root   165712 Oct 28 14:25 config-3.13.0-39-generic
drwxr-xr-x 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     1024 Nov  1 08:22 grub
-rw-r--r-- 1 root root 29242045 Sep 27 08:58 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 29243714 Oct 15 07:50 initrd.img-3.13.0-38-generic
-rw-r--r-- 1 root root 29243454 Nov  1 08:23 initrd.img-3.13.0-39-generic
drwx------ 2 root root    12288 Jul 28 12:48 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3386945 Sep 22 23:24 System.map-3.13.0-37-generic
-rw------- 1 root root  3386936 Oct  9 13:33 System.map-3.13.0-38-generic
-rw------- 1 root root  3386936 Oct 28 14:25 System.map-3.13.0-39-generic
-rw------- 1 root root  5808832 Sep 22 23:24 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  5810744 Sep 27 08:57 vmlinuz-3.13.0-37-generic.efi.signed
-rw------- 1 root root  5808736 Oct  9 13:33 vmlinuz-3.13.0-38-generic
-rw------- 1 root root  5810648 Oct 15 07:50 vmlinuz-3.13.0-38-generic.efi.signed
-rw------- 1 root root  5808544 Oct 28 14:25 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  5810456 Nov  1 08:22 vmlinuz-3.13.0-39-generic.efi.signed


```

Ran the auto remove and then the ls -l /boot. 
Results of ls -l /boot :
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -l /boot
total 134631
-rw-r--r-- 1 root root  1164489 Sep 22 23:24 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  1164489 Oct  9 13:33 abi-3.13.0-38-generic
-rw-r--r-- 1 root root  1164547 Oct 28 14:25 abi-3.13.0-39-generic
-rw-r--r-- 1 root root   165712 Sep 22 23:24 config-3.13.0-37-generic
-rw-r--r-- 1 root root   165712 Oct  9 13:33 config-3.13.0-38-generic
-rw-r--r-- 1 root root   165712 Oct 28 14:25 config-3.13.0-39-generic
drwxr-xr-x 3 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     1024 Nov  1 08:22 grub
-rw-r--r-- 1 root root 29242045 Sep 27 08:58 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 29243714 Oct 15 07:50 initrd.img-3.13.0-38-generic
-rw-r--r-- 1 root root 29243454 Nov  1 08:23 initrd.img-3.13.0-39-generic
drwx------ 2 root root    12288 Jul 28 12:48 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3386945 Sep 22 23:24 System.map-3.13.0-37-generic
-rw------- 1 root root  3386936 Oct  9 13:33 System.map-3.13.0-38-generic
-rw------- 1 root root  3386936 Oct 28 14:25 System.map-3.13.0-39-generic
-rw------- 1 root root  5808832 Sep 22 23:24 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  5810744 Sep 27 08:57 vmlinuz-3.13.0-37-generic.efi.signed
-rw------- 1 root root  5808736 Oct  9 13:33 vmlinuz-3.13.0-38-generic
-rw------- 1 root root  5810648 Oct 15 07:50 vmlinuz-3.13.0-38-generic.efi.signed
-rw------- 1 root root  5808544 Oct 28 14:25 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  5810456 Nov  1 08:22 vmlinuz-3.13.0-39-generic.efi.signed

```



So nothing changed!


Then as requested I ran dpkg -l 'linux-*', and the output was:-

```
harfin@harfin-HP-255-G1-Notebook-PC:~$ dpkg -l 'linux-*'Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
un  linux-doc-3.13.0                <none>               <none>               (no description available)
ii  linux-firmware                  1.127.8              all                  Firmware for Linux kernel drivers
ii  linux-generic                   3.13.0.39.46         amd64                Complete Generic Linux kernel and headers
un  linux-headers                   <none>               <none>               (no description available)
un  linux-headers-3.0               <none>               <none>               (no description available)
un  linux-headers-3.13.0-35-generic <none>               <none>               (no description available)
ii  linux-headers-3.13.0-37         3.13.0-37.64         all                  Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic 3.13.0-37.64         amd64                Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-38         3.13.0-38.65         all                  Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-38-generic 3.13.0-38.65         amd64                Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39         3.13.0-39.66         all                  Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic 3.13.0-39.66         amd64                Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic           3.13.0.39.46         amd64                Generic Linux kernel headers
un  linux-image                     <none>               <none>               (no description available)
un  linux-image-3.0                 <none>               <none>               (no description available)
rc  linux-image-3.13.0-35-generic   3.13.0-35.62         amd64                Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic   3.13.0-37.64         amd64                Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-38-generic   3.13.0-38.65         amd64                Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic   3.13.0-39.66         amd64                Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-gen 3.13.0-35.62         amd64                Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-gen 3.13.0-37.64         amd64                Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-38-gen 3.13.0-38.65         amd64                Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-gen 3.13.0-39.66         amd64                Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic             3.13.0.39.46         amd64                Generic Linux kernel image
un  linux-initramfs-tool            <none>               <none>               (no description available)
un  linux-kernel-headers            <none>               <none>               (no description available)
un  linux-kernel-log-daemon         <none>               <none>               (no description available)
ii  linux-libc-dev:amd64            3.13.0-39.66         amd64                Linux Kernel Headers for development
un  linux-restricted-common         <none>               <none>               (no description available)
ii  linux-signed-generic            3.13.0.39.46         amd64                Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.13.0-35-ge 3.13.0-35.62         amd64                Signed kernel image generic
ii  linux-signed-image-3.13.0-37-ge 3.13.0-37.64         amd64                Signed kernel image generic
ii  linux-signed-image-3.13.0-38-ge 3.13.0-38.65         amd64                Signed kernel image generic
ii  linux-signed-image-3.13.0-39-ge 3.13.0-39.66         amd64                Signed kernel image generic
ii  linux-signed-image-generic      3.13.0.39.46         amd64                Signed Generic Linux kernel image
ii  linux-sound-base                1.0.25+dfsg-0ubuntu4 all                  base package for ALSA and OSS sound systems
un  linux-source-3.13.0             <none>               <none>               (no description available)
un  linux-tools                     <none>               <none>               (no description available)
harfin@harfin-HP-255-G1-Notebook-PC:~$ 

```
So I assume I need to do the manual delete of the ealiest package as before

Harfin

---

### Post by slickymaster on 2014-11-11
Thing is that kernel upgrades won't stop, since they're a needed process for several reasons like bug fixes, updates for potential security problems and hardware support improvements.

The best solution is to make the /boot partition large enough (2-3 GB) so that you don't have to worry for a couple of years or more!

---

### Post by mörgæs on 2014-11-11
If you run autoremove, do you see any changes to the last of the outputs?

---

### Post by harfin on 2014-11-11
> **slickymaster said:**
> Thing is that kernel upgrades won't stop, since they're a needed process for several reasons like bug fixes, updates for potential security problems and hardware support improvements.

The best solution is to make the /boot partition large enough (2-3 GB) so that you don't have to worry for a couple of years or more!

Is there simple guide as to how increase the size?  Not something I have ever had any input into up until now.

Harfin

---

### Post by harfin on 2014-11-11
> **mörgæs said:**
> If you run autoremove, do you see any changes to the last of the outputs?

Doesn't seem to be.  The suggestion from slickymaster seems to be a great idea to me.  I didn't set the current limit, I assumed that this was some setting that came from the Ubuntu 1st update after I bought this laptop (with pre-installed Ubuntu).

Harfin

---

### Post by oldfred on 2014-11-11
Unless you have to have a /boot which some server configurations or LVM installs require, but most desktops do not, is not to have a /boot partition at all and keep it inside / (root). Then you are sharing the unused space inside /, but still should houseclean old kernels and other old logs and cruft that grows over time.

If you comment out the /boot line in fstab and run updates to include a new kernel and reinstall of grub then you have eliminated the /boot. The /boot partition space will not be used and depending on where it is on drive may not be easy to reconfigure to use.

---

### Post by harfin on 2014-11-13
> **oldfred said:**
> Unless you have to have a /boot which some server configurations or LVM installs require, but most desktops do not, is not to have a /boot partition at all and keep it inside / (root). Then you are sharing the unused space inside /, but still should houseclean old kernels and other old logs and cruft that grows over time.

If you comment out the /boot line in fstab and run updates to include a new kernel and reinstall of grub then you have eliminated the /boot. The /boot partition space will not be used and depending on where it is on drive may not be easy to reconfigure to use.
ving 
Sorry Oldfred, your advice that means absolutely zero to me. I am a beginner at this, and I need a step by step direction to ensure I do exactly (no more / no less) than what is needed.

I am not sure if you are aware, but early on in this thread, there was a point raised about there was / could be an impact through my choice of having encrypted HD on this laptop. I have no idea why that should have anything to do with the set-up of the auto-removal of old kernels, but at earlier input from Moderators indicated that it did have something to do with the auto-remove not working.

Harfin

---

### Post by coffeecat on 2014-11-13
You opted for a full system encryption when you installed and this involved setting up LVM. With a LVM setup, the installer creates an inadequately-sized boot partition and I posted a link to the appropriate bug report about this. All we can really do is hope that the bug gets noticed, taken up and acted upon, but that won't help you now. I have no experience of LVM and I don't believe that it will be possible to resize the LVM volume to make room to enlarge the boot partition. If I am wrong, hopefully someone can correct this. 

The other issue is that it appears that the need to install a third kernel is the one that triggers the inadequate space problem, which is very odd. We have plenty of threads about this issue where people have set up LVM installations, but from memory this usually involves about 6 kernels. Not being able to install a third kernel makes it impossible to keep to a useful working rule, that of keeping the immediately previous kernel to the latest one, that is two kernels as a minimum. 

You have a most unsatisfactory situation. Assuming that is impossible to resize your boot partition, I can only offer one suggestion. That is to decide whether or not you really need whole volume encryption and whether home encryption only would be a better choice. If it is, then you could think about re-installing, this time opting for home encryption. This way, you can control your partition layout and, most importantly, not have a boot partition at all. With /boot in your root partition you simply won't run into this problem again and can collect kernels (almost) to your heart’s content!

---

### Post by harfin on 2014-11-14
> **coffeecat said:**
> You opted for a full system encryption when you installed and this involved setting up LVM. With a LVM setup, the installer creates an inadequately-sized boot partition and I posted a link to the appropriate bug report about this. All we can really do is hope that the bug gets noticed, taken up and acted upon, but that won't help you now. I have no experience of LVM and I don't believe that it will be possible to resize the LVM volume to make room to enlarge the boot partition. If I am wrong, hopefully someone can correct this. 

The other issue is that it appears that the need to install a third kernel is the one that triggers the inadequate space problem, which is very odd. We have plenty of threads about this issue where people have set up LVM installations, but from memory this usually involves about 6 kernels. Not being able to install a third kernel makes it impossible to keep to a useful working rule, that of keeping the immediately previous kernel to the latest one, that is two kernels as a minimum. 

You have a most unsatisfactory situation. Assuming that is impossible to resize your boot partition, I can only offer one suggestion. That is to decide whether or not you really need whole volume encryption and whether home encryption only would be a better choice. If it is, then you could think about re-installing, this time opting for home encryption. This way, you can control your partition layout and, most importantly, not have a boot partition at all. With /boot in your root partition you simply won't run into this problem again and can collect kernels (almost) to your heart’s content!



Thankyou Coffeecat (***again!***) for your advice.  I was totally unaware of the other encryption choice and I will (as soon as time permits) need to research the consequences of having the home encryption choice as opposed to the whole volume encryption before deciding which is the better option for me.

Harfin

---

### Post by coffeecat on 2014-11-14
Good luck with that. If you do decide to install afresh with home encryption, the choice comes later in the install process. At the partition stage, I would suggest avoiding all the first choices, which include LVM, and go with the something else option. You can then direct the installer to partitions you have already prepared using gparted (my preference) or set up your partitions there and then. After the installation commences, you are presented with the account username and password page with some other options, one of which is encrypt the home partition. The swap partition, if present, will also be encrypted.

---

