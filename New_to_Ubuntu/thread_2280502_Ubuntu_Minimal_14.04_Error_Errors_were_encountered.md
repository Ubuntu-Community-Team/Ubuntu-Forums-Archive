---
title: "Ubuntu Minimal 14.04 Error: Errors were encountered while processing."
date: 2015-05-31
forum: New to Ubuntu
---

### Post by dillon4 on 2015-05-31
[IMG]http://i.imgur.com/Na1lwFt.png[/IMG]

Hello I'm very new to Ubuntu I just bought a VPS and wanting to Install a virtual box on it, Anytime I do

apt-get update
apt-get upgrade

I get that weird error. Anytime I get any program in apt it throws that error at me? Any ideas? 

Thank you ~ Dillon

---

### Post by dino99 on 2015-05-31
in case you need an install howto  [https://www.bitronictech.net/knowledgebase/10117/Getting-Started-with-an-Ubuntu-VPS-Running-1404-Server.html](https://www.bitronictech.net/knowledgebase/10117/Getting-Started-with-an-Ubuntu-VPS-Running-1404-Server.html)

---

### Post by dillon4 on 2015-05-31
I did everything till it told me to use this command

Visudo

Got a message that said -su: visudo: Command not found.

Any ideas ?

---

### Post by sandyd on 2015-05-31
> **dillon4 said:**
> [IMG]http://i.imgur.com/Na1lwFt.png[/IMG]

Hello I'm very new to Ubuntu I just bought a VPS and wanting to Install a virtual box on it, Anytime I do

apt-get update
apt-get upgrade

I get that weird error. Anytime I get any program in apt it throws that error at me? Any ideas? 

Thank you ~ Dillon

Hi, can you post the entire output, starting from when you run apt-get.

You can do this by running
```

sudo apt-get -y upgrade &>test
```

A file called *test* will be created in your current directory and you can SCP it to your computer to read the output.

Thanks.

---

### Post by dillon4 on 2015-05-31
> **sandyd said:**
> Hi, can you post the entire output, starting from when you run apt-get.

You can do this by running
```

sudo apt-get -y upgrade &>test
```

A file called *test* will be created in your current directory and you can SCP it to your computer to read the output.

Thanks.


[IMG]http://i.imgur.com/jvHbY2R.png[/IMG]


I have no idea how to post it like a code so I did a photo hope that helps.

---

### Post by Bashing-om on 2015-05-31
dillon4; Hello;

Allow me to jump in here .

Nope that photo does not help much. We do need to see the entire contents of the command's results.
Please consult:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And if you have continued problems posting between the [code] tags, we will provide additional guidance.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by dillon4 on 2015-05-31
```
 Reading package lists...Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.13.0-53-generic (3.13.0-53.89) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-53-generic
vmlinuz(/boot/vmlinuz-3.13.0-53-generic
) points to /boot/vmlinuz-3.13.0-53-generic
 (/boot/vmlinuz-3.13.0-53-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-53-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-53-generic
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.13.0-53-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-53-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-53-generic:
 linux-image-extra-3.13.0-53-generic depends on linux-image-3.13.0-53-generic; however:
  Package linux-image-3.13.0-53-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-53-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-53-generic; however:
  Package linux-image-3.13.0-53-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-53-generic; however:
  Package linux-image-extra-3.13.0-53-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.53.60); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.13.0-53-generic
 linux-image-extra-3.13.0-53-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dillon4 on 2015-05-31
Anyone have any ideas? could this be a broken OS ?

---

### Post by Bashing-om on 2015-05-31
dillon4; Hey;

It is frowned upon to respond to a thread with out a positive input.
But no, it is not broken, I just have not decided on how to address:
> 
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-53-generic.postinst line 1025.


Might be interesting to see why the package manager is unhappy.

Is my stanza the same as yours ?
```

## Run user hook script here, if any
if ($postinst_hook) {
  &run_hook("postinst", $postinst_hook);
}

if (-d "/etc/kernel/postinst.d") {
  print STDERR "Examining /etc/kernel/postinst.d.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " . ##my line 1025 <----------------------
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d") &&
            die "Failed to process /etc/kernel/postinst.d";
}

if (-d "/etc/kernel/postinst.d/$version") {
  print STDERR "Examining /etc/kernel/postinst.d/$version.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " .
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d/$version") &&
            die "Failed to process /etc/kernel/postinst.d/$version";
}


```

And yes, Here I too am wearing my learning cap.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by dillon4 on 2015-05-31
> **Bashing-om said:**
> dillon4; Hey;

It is frowned upon to respond to a thread with out a positive input.
But no, it is not broken, I just have not decided on how to address:


Might be interesting to see why the package manager is unhappy.

Is my stanza the same as yours ?
```

## Run user hook script here, if any
if ($postinst_hook) {
  &run_hook("postinst", $postinst_hook);
}

if (-d "/etc/kernel/postinst.d") {
  print STDERR "Examining /etc/kernel/postinst.d.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " . ##my line 1025 <----------------------
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d") &&
            die "Failed to process /etc/kernel/postinst.d";
}

if (-d "/etc/kernel/postinst.d/$version") {
  print STDERR "Examining /etc/kernel/postinst.d/$version.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " .
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d/$version") &&
            die "Failed to process /etc/kernel/postinst.d/$version";
}


```

And yes, Here I too am wearing my learning cap.
[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]



Sorry but whats stanza  ?

---

### Post by Bashing-om on 2015-05-31
dillon4; Hey ;

> 
Sorry but whats stanza ?


That 'paragraph' within the file that contains line number 1025 .

open the file in a text editor, here gedit:
```

gksudo gedit /var/lib/dpkg/info/linux-image-3.13.0-53-generic.postinst

```
copy and paste the 'paragraph' (stanza) back to the thread.

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by dillon4 on 2015-05-31
> **Bashing-om said:**
> dillon4; Hey ;



That 'paragraph' within the file that contains line number 1025 .

open the file in a text editor, here gedit:
```

gksudo gedit /var/lib/dpkg/info/linux-image-3.13.0-53-generic.postinst

```
copy and paste the 'paragraph' (stanza) back to the thread.[INDENT][INDENT]all a process of learning
[/INDENT]
[/INDENT]




Weird error.

```
 -bash: gksudo: command not found 
```

---

### Post by sandyd on 2015-05-31
Is this openvz, KVM or XEN virtualization.

Can you post the output of
```

uname -a
ls -l /proc/vz

```

OpenVZ uses a shared kernel, and as a result RTC does not work.

```

chmod -x /usr/share/initramfs-tools/hooks/fixrtc
```
is a temp fix, but you shouldn't have the kernels installed in the first place.

---

### Post by dillon4 on 2015-05-31
> **sandyd said:**
> Is this openvz, KVM or XEN virtualization.

Can you post the output of
```

uname -a
ls -l /proc/vz

```

OpenVZ uses a shared kernel, and as a result RTC does not work.

```

chmod -x /usr/share/initramfs-tools/hooks/fixrtc
```
is a temp fix, but you shouldn't have the kernels installed in the first place.

Its OpenVZ
And the code I get is.

```
 
Linux server1 2.6.32-042stab104.1 #1 SMP Thu Jan 29 12:58:41 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```

total 0
-r--------  1 root root 0 May 31 23:45 veinfo
-r--------  1 root root 0 May 31 23:45 vestat
dr-x------ 13 root root 0 May 31 23:45 vzaquota

```

---

### Post by sandyd on 2015-06-01
Can you post the output of
```

dpkg -l | grep -i "linux-generic\|linux-image\|linux-tools\|linux-headers"
```

---

### Post by dillon4 on 2015-06-01
> **sandyd said:**
> Can you post the output of
```

dpkg -l | grep -i "linux-generic\|linux-image\|linux-tools\|linux-headers"
```


Here ya go.

```

iU  linux-generic                         3.13.0.53.60                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-53               3.13.0-53.89                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic       3.13.0-53.89                          amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                 3.13.0.53.60                          amd64        Generic Linux kernel headers
iF  linux-image-3.13.0-53-generic         3.13.0-53.89                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-53-generic   3.13.0-53.89                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                   3.13.0.53.60                          amd64        Generic Linux kernel image

```

---

### Post by sandyd on 2015-06-01
Post output of
```

apt-get -s remove linux-image-generic linux-image-extra-3.13.0-53-generic linux-image-3.13.0-53-generic linux-headers-generic linux-headers-3.13.0-53-generic linux-headers-3.13.0-53 linux-generic
```

Just need to make sure nothing else important gets caught in the crossfire

---

### Post by dillon4 on 2015-06-01
> **sandyd said:**
> Post output of
```

apt-get -s remove linux-image-generic linux-image-extra-3.13.0-53-generic linux-image-3.13.0-53-generic linux-headers-generic linux-headers-3.13.0-53-generic linux-headers-3.13.0-53 linux-generic
```

Just need to make sure nothing else important gets caught in the crossfire


Here you go. Thank you for being very helpful so far. :D

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  crda grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common iw
  os-prober wireless-regdb
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic linux-headers-3.13.0-53 linux-headers-3.13.0-53-generic
  linux-headers-generic linux-image-3.13.0-53-generic
  linux-image-extra-3.13.0-53-generic linux-image-generic
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
4 not fully installed or removed.
Remv linux-generic [3.13.0.53.60]
Remv linux-image-generic [3.13.0.53.60]
Remv linux-image-extra-3.13.0-53-generic [3.13.0-53.89]
Remv linux-image-3.13.0-53-generic [3.13.0-53.89]
Remv linux-headers-generic [3.13.0.53.60]
Remv linux-headers-3.13.0-53-generic [3.13.0-53.89]
Remv linux-headers-3.13.0-53 [3.13.0-53.89]

```

---

### Post by sandyd on 2015-06-01
Lets give this a go
```

chmod -x /usr/share/initramfs-tools/hooks/fixrtc
apt-get remove linux-image-generic linux-image-extra-3.13.0-53-generic linux-image-3.13.0-53-generic linux-headers-generic linux-headers-3.13.0-53-generic linux-headers-3.13.0-53 linux-generic
apt-get update && apt-get upgrade

```

It shouldn't attempt to install or upgrade any more kernel stuff after that.

Side note: Unless its a different calendar format, your date is wrong, its definitely not "Thu Jan 29". Time is controlled by openvz host node, so you will have to ask the host to fix it.

I'm going to sleep, but will check on this in the morning.

---

### Post by dillon4 on 2015-06-01
Yay Thank you. fixed that issue. I have one last one if thats okay to ask here if not ill make another thread talk to you soon.

---

### Post by sandyd on 2015-06-01
New thread :)

---

### Post by dillon4 on 2015-06-01
[IMG]http://i.imgur.com/JyRNseu.png[/IMG]


Hello again! To my second post! Thank you all for your great support here. I have another question. Any ideas why I get this error code? 

Thank you ~Dillon

---

### Post by TheFu on 2015-06-01
"Kernel driver not installed " - seems to say it all. Minimal probably doesn't have all the dependencies that virtualbox is expecting.  But I don't know. Sorry, can't help more.  

Look to the log files for more specific data.
Also - a web search for the specific error found lots of people with the same issue and a likely solution: 
[https://forums.virtualbox.org/viewtopic.php?f=7&t=61267](https://forums.virtualbox.org/viewtopic.php?f=7&t=61267) - DKMS

Update - after seeing the merged threads ... I haven't a clue. Can you run a full hypervisor under an already openVZ environment? I didn't think that was possible.  Perhaps lxc is a better answer?

---

### Post by cariboo on 2015-06-01
Instead of creating multiple threads I would like to see the responses in one place, so as to not break continuity.

---

