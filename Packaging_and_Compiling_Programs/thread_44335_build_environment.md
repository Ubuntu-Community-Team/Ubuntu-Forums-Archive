---
title: "build environment"
date: 2005-06-25
forum: Packaging and Compiling Programs
---

### Post by arkss on 2005-06-25
Hi,

Please, I need help with my card intallation.

Here is some info:
 
1. The distro I'm using:
SimplyMepis 3.3.1-1
 
2. What device 
PCI Planet WL-8305
 
3. The results of typing uname -r in my root-console:
2.6.10 (first attempt)
2.6.11.6 (second attempt, after 2.6.11.6 packages installation, correction in grub loader… add reboot of course &#61514;)
 
4. The results of typing: lspci -n in my root-console (with the card installed):
0000:00:00.0 0600: 1106:3099
0000:00:01.0 0604: 1106:b099
0000:00:09.0 0280: 104c:8400
0000:00:11.0 0601: 1106:3074
0000:00:11.1 0101: 1106:0571 (rev 06)
0000:00:11.2 0c03: 1106:3038 (rev 1b)
0000:00:11.3 0c03: 1106:3038 (rev 1b)
0000:00:11.4 0c03: 1106:3038 (rev 1b)
0000:00:11.5 0401: 1106:3059 (rev 10)
0000:01:00.0 0300: 10de:0110 (rev b2)

 
5. The results of typing: lsmod in my root-console:
Module                  Size  Used by
ipv6                  229536  13
parport_pc             31172  1
lp                      9480  0
parport                20544  2 parport_pc,lp
binfmt_misc             9224  1
ipt_limit               2560  2
ipt_state               2048  66
ipt_LOG                 7040  2
ipt_REJECT              5888  2
ip_conntrack_ftp       71952  0
ip_conntrack_irc       71184  0
ip_conntrack           37704  3 ipt_state,ip_conntrack_ftp,ip_conntrack_irc
iptable_filter          2816  1
ip_tables              21376  5 ipt_limit,ipt_state,ipt_LOG,ipt_REJECT,iptable_filter
pcmcia                 19088  0
yenta_socket           19080  0
rsrc_nonstatic          8960  1 yenta_socket
pcmcia_core            41120  3 pcmcia,yenta_socket,rsrc_nonstatic
8250                   21572  0
serial_core            18304  1 8250
ntfs                  167184  2
nls_iso8859_1           4352  3
nls_cp437               6016  1
snd_via82xx            22208  1
snd_ac97_codec         67448  1 snd_via82xx
snd_pcm_oss            46880  0
snd_mixer_oss          16512  1 snd_pcm_oss
snd_pcm                77956  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21124  1 snd_pcm
snd_page_alloc          7812  2 snd_via82xx,snd_pcm
gameport                4096  1 snd_via82xx
snd_mpu401_uart         6656  1 snd_via82xx
snd_rawmidi            20256  1 snd_mpu401_uart
snd_seq_device          7436  1 snd_rawmidi
snd                    46820  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               7776  1 snd
speedstep_lib           3844  0
freq_table              3984  0
thermal                11400  0
processor              20812  1 thermal
fan                     3716  0
button                  5520  0
battery                 8836  0
ac                      3972  0
floppy                 53264  1
evdev                   7552  0
uhci_hcd               28688  0
ohci_hcd               18952  0

A brief description of when/where things went wrong, or what exactly is not working:


I checked everything according to a guide ('Craig's ACX100/111 Guide for Linux') and got stuck in 'verifying the correct version of the kernel source' part.. I found out that I don't even have the directory /lib/modules/`uname -r`/build…

The stock kernel of Simply Mepis 3.3.1-1 is 2.6.10, but I couldn't find kernel-source-2.6.10, only 2.6.10 headers which I installed. I, however, decided that headers may not be enough to do the setup of the card in 2.6.10 (I read varied oppinions on this on the Net). I decided to do it in 2.6.11.6, because I was able to download all the packages that are needed (I think so…&#61514;).
I installed everything (including 2.6.11.6 kernel headers and kernel-source) according to another guide. The packages were deb files.
Next I checked again under 2.6.11.6 if the ls /lib/modules/`uname -r`/build/include/linux/version.h is present but was again unsuccesful... I don't even seem to have /lib/modules/2.6.11.6/build directory, only a link.
This is listing from 'ls -l' command done in /lib/modules/2.6.11.6 directory: 
lrwxrwxrwx  1 root root     23 2005-06-25 15:28 build -> /usr/src/linux-2.6.11.6
drwxr-xr-x  9 root root   4096 2005-06-25 15:28 kernel
drwxr-xr-x  2 root root   4096 2005-06-25 15:45 misc
drwxr-xr-x  2 root root   4096 2005-06-25 15:39 modem
-rw-r--r--  1 root root 170968 2005-06-25 15:42 modules.alias
-rw-r--r--  1 root root     69 2005-06-25 15:42 modules.ccwmap
-rw-r--r--  1 root root 200777 2005-06-25 15:42 modules.dep
-rw-r--r--  1 root root    295 2005-06-25 15:42 modules.ieee1394map
-rw-r--r--  1 root root    700 2005-06-25 15:42 modules.inputmap
-rw-r--r--  1 root root  26888 2005-06-25 15:42 modules.isapnpmap
-rw-r--r--  1 root root 136417 2005-06-25 15:42 modules.pcimap
-rw-r--r--  1 root root  87626 2005-06-25 15:42 modules.symbols
-rw-r--r--  1 root root 234765 2005-06-25 15:42 modules.usbmap
drwxr-xr-x  2 root root   4096 2005-06-25 15:39 net
drwxr-xr-x  2 root root   4096 2005-06-25 15:38 nvidia
drwxr-xr-x  2 root root   4096 2005-06-25 15:39 pcmcia
lrwxrwxrwx  1 root root     23 2005-06-25 15:28 source -> /usr/src/linux-2.6.11.6
drwxr-xr-x  3 root root   4096 2005-06-25 15:31 updates
drwxr-xr-x  2 root root   4096 2005-06-25 15:39 wireless

I spotted, of course, the arrows, and I read on the Net that they are links, so I thought that the source is in the /usr/src and tried to 'make' the driver as in the beginning of the 'Compiling the Driver' part of the guide but received errors. So I checked the /usr/src/ and the linux-2.6.11.6 directory isn't there either!:

arkss@1[src]$ ls -l
total 43216
-rw-r--r--  1 arkss users   122581 2005-03-22 14:49 bcm4400-3.0.8.tar.gz
-rwxr-xr-x  1 root  root    508039 2005-03-24 17:04 bcm5700-7.3.5.tar.gz
-rw-r--r--  1 arkss users   133396 2005-03-24 17:01 ipw2100-1.1.0.tgz
-rw-r--r--  1 arkss users   131876 2005-03-24 17:00 ipw2200-1.0.2.tgz
-rw-r--r--  1 arkss users   614212 2005-03-24 17:07 ivtv-0.3.2m.tgz
drwxr-xr-x  4 root  root      4096 2005-06-25 08:50 kernel-headers-2.6.10
drwxr-xr-x  4 root  root      4096 2005-06-25 15:43 kernel-headers-2.6.11.6
-rw-r--r--  1 root   1000     1107 2005-02-05 17:10 KERNEL-README
-rw-r--r--  1 root  root  37080187 2005-04-04 14:53 kernel-source-2.6.11.6.tar.bz2
drwxr-sr-x  2 root   1000     4096 2005-02-05 17:06 linux-2.4.29-patches
drwxr-sr-x  2 root   1000     4096 2005-02-23 16:40 linux-2.6.10-patches
-rw-r--r--  1 arkss users   456977 2005-02-19 14:03 linux-wlan-ng-0.2.1-pre26.tar.bz2
-rw-r--r--  1 arkss users   105472 2005-03-22 14:49 ltmodem-2.6-alk-6.tar.gz
-rw-r--r--  1 arkss users   580518 2005-03-24 17:09 ltmodem-8.31a10.tar.gz
-rw-r--r--  1 root  root   2573346 2005-03-30 09:10 madwifi_cvs_032405.tar.gz
drwxr-sr-x  2 root   1000     4096 2003-09-30 14:29 modules
-rw-r--r--  1 root  root     58373 2005-03-28 09:36 pwc-10.0.6a.tar.gz
drwxr-xr-x  7 root  root      4096 2005-02-19 20:31 rpm
-rw-r--r--  1 arkss users   841347 2005-03-22 14:54 rt2500-1.1.0.tar.gz
-rw-r--r--  1 root  root    710319 2005-03-28 09:24 slmodem-2.9.9b.tar.gz
-rw-r--r--  1 root  root    158660 2005-03-30 09:11 usbvision_cvs_032805.tar.gz
-rw-r--r--  1 root   1000    24757 2005-04-01 09:50 zr364xx-0.57.tar.gz

How to create a proper build environment? 

I am a newbe but I really would like to use linux. If you could enlighten my dumb ass I'd really appreciate this. Please, help...

---

### Post by nookadum on 2005-07-25
> **arkss]Hi,

Please, I need help with my card intallation.

Here is some info:
 
1. The distro I'm using:
SimplyMepis 3.3.1-1
 
2. What device 
PCI Planet WL-8305
 
3. The results of typing uname -r in my root-console:
2.6.10 (first attempt)
2.6.11.6 (second attempt, after 2.6.11.6 packages installation, correction in grub loader… add reboot of course &#61514 said:**
> $ ls -l
total 43216
-rw-r--r--  1 arkss users   122581 2005-03-22 14:49 bcm4400-3.0.8.tar.gz
-rwxr-xr-x  1 root  root    508039 2005-03-24 17:04 bcm5700-7.3.5.tar.gz
-rw-r--r--  1 arkss users   133396 2005-03-24 17:01 ipw2100-1.1.0.tgz
-rw-r--r--  1 arkss users   131876 2005-03-24 17:00 ipw2200-1.0.2.tgz
-rw-r--r--  1 arkss users   614212 2005-03-24 17:07 ivtv-0.3.2m.tgz
drwxr-xr-x  4 root  root      4096 2005-06-25 08:50 kernel-headers-2.6.10
drwxr-xr-x  4 root  root      4096 2005-06-25 15:43 kernel-headers-2.6.11.6
-rw-r--r--  1 root   1000     1107 2005-02-05 17:10 KERNEL-README
-rw-r--r--  1 root  root  37080187 2005-04-04 14:53 kernel-source-2.6.11.6.tar.bz2
drwxr-sr-x  2 root   1000     4096 2005-02-05 17:06 linux-2.4.29-patches
drwxr-sr-x  2 root   1000     4096 2005-02-23 16:40 linux-2.6.10-patches
-rw-r--r--  1 arkss users   456977 2005-02-19 14:03 linux-wlan-ng-0.2.1-pre26.tar.bz2
-rw-r--r--  1 arkss users   105472 2005-03-22 14:49 ltmodem-2.6-alk-6.tar.gz
-rw-r--r--  1 arkss users   580518 2005-03-24 17:09 ltmodem-8.31a10.tar.gz
-rw-r--r--  1 root  root   2573346 2005-03-30 09:10 madwifi_cvs_032405.tar.gz
drwxr-sr-x  2 root   1000     4096 2003-09-30 14:29 modules
-rw-r--r--  1 root  root     58373 2005-03-28 09:36 pwc-10.0.6a.tar.gz
drwxr-xr-x  7 root  root      4096 2005-02-19 20:31 rpm
-rw-r--r--  1 arkss users   841347 2005-03-22 14:54 rt2500-1.1.0.tar.gz
-rw-r--r--  1 root  root    710319 2005-03-28 09:24 slmodem-2.9.9b.tar.gz
-rw-r--r--  1 root  root    158660 2005-03-30 09:11 usbvision_cvs_032805.tar.gz
-rw-r--r--  1 root   1000    24757 2005-04-01 09:50 zr364xx-0.57.tar.gz

How to create a proper build environment? 

I am a newbe but I really would like to use linux. If you could enlighten my dumb ass I'd really appreciate this. Please, help...
 BUMP! I'm also wondering why I lack a "/lib/modules/`uname -r`/build".

---

### Post by black hole sun on 2005-07-25
Whoah. That's a lot of words. And you aren't using ubuntu? Why are you posting this here?

Regardless, I'll try to help, but I dont understand _what_ exactly it is you're trying to do! You say you're trying to "install a card." Fair enough; what card, exactly? What isn't working that you're going through all this?

A `proper build environment?` What makes you think you don't already have one?

---

### Post by black hole sun on 2005-07-25
[QUOTE=nookadum]BUMP! I'm also wondering why I lack a "/lib/modules/`uname -r`/build".[/QUOTE]
 I see you're following Craig's guide verbatim.

Well, for one thing you changed the kernel source without changing the kernel! The `kernel source` is the source code; the programming files written in C that you can look at and compile. The _binary_ part is the actual kernel (the engine you might say), which is located in /boot. Changing the kernel is a little complex for a newbie, do not bother with it. So now you understand why the command;

ls /lib/modules/`uname -r`/build/

failed, because `uname -r` prints the version number of the _running_ kernel, which has not changed, despite the fact that you installed the source code of a different kernel. Obviously, you don't have the kernel source for your current kernel installed.  You say you have 2.6.10? I dont know about that, few distros use unpatched kernels. Post the results of `uname -r` please.

---

