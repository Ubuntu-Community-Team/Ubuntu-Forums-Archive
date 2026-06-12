---
title: "'The following packages have unmet dependencies'"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by daneandrewlam on 2013-10-08
Hi all ...

I'm trying to install a new program on the computer but keep getting this error message.

Any help would be much appreciated.

With thanks in advance, 

Dane :)

Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 kdenlive : Depends: kdenlive-data (= 0.9.2-2ubuntu1) but it is not going to be installed
            Recommends: swh-plugins but it is not going to be installed
            Recommends: dvgrab but it is not going to be installed
            Recommends: recordmydesktop but it is not going to be installed
 linux-image-extra-3.5.0-28-generic : Depends: linux-image-3.5.0-28-generic but it is not going to be installed
 linux-image-extra-3.5.0-30-generic : Depends: linux-image-3.5.0-30-generic but it is not going to be installed
 linux-image-extra-3.5.0-36-generic : Depends: linux-image-3.5.0-36-generic but it is not going to be installed
 linux-image-extra-3.5.0-41-generic : Depends: linux-image-3.5.0-41-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.5.0-28-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by ibjsb4 on 2013-10-08
> You might want to run 'apt-get -f install' to correct these:

The command is:

```
sudo apt-get -f install
```

If your not familiar with terminal

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by daneandrewlam on 2013-10-08
Many thanks for this. It seemed to be working but returned this error message at end. 

" Errors were encountered while processing: /var/cache/apt/archives/linux-image-3.5.0-28-generic_3.5.0-28.48_amd64.deb
 /var/cache/apt/archives/linux-image-3.5.0-30-generic_3.5.0-30.51_amd64.deb
 /var/cache/apt/archives/linux-image-3.5.0-36-generic_3.5.0-36.57_amd64.deb
 /var/cache/apt/archives/linux-image-3.5.0-41-generic_3.5.0-41.64_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any advice would be greatly appreciated again!

---

### Post by ibjsb4 on 2013-10-08
Try a house cleaning.

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit
```

---

### Post by daneandrewlam on 2013-10-08
Thanks so much for your help. :DIt seemed to work and ended with this message:

[COLOR=#0000ff]W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-amd64_Packages)[/COLOR]
[COLOR=#0000ff]W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)[/COLOR]
[COLOR=#0000ff]W: You may want to run apt-get update to correct these problems[/COLOR]

I am still trying to install software and get the following messge now:

[COLOR=#0000ff]The package system is broken.

[/COLOR][COLOR=#0000ff]If you are using third party repositories then disable them, since they are a common source of problems.[/COLOR]
[COLOR=#0000ff]Now run the following command in a terminal: apt-get install -f

Details:

[/COLOR][COLOR=#0000ff]The following packages have unmet dependencies:[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]linux-image-extra-3.5.0-28-generic: Depends: linux-image-3.5.0-28-generic but it is not installed[/COLOR]
[COLOR=#0000ff]linux-image-extra-3.5.0-30-generic: Depends: linux-image-3.5.0-30-generic but it is not installed[/COLOR]
[COLOR=#0000ff]linux-image-extra-3.5.0-36-generic: Depends: linux-image-3.5.0-36-generic but it is not installed[/COLOR]
[COLOR=#0000ff]linux-image-extra-3.5.0-41-generic: Depends: linux-image-3.5.0-41-generic but it is not installed[/COLOR]
[COLOR=#0000ff]linux-image-generic: Depends: linux-image-3.5.0-28-generic but it is not installed[/COLOR]


I've tried to run the command but receive the message:

[COLOR=#0000ff]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)[/COLOR]
[COLOR=#0000ff]E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/COLOR]

---

### Post by mörgæs on 2013-10-08
> **daneandrewlam said:**
> [COLOR=#0000ff]are you root?[/COLOR]

It tries to tell you something...

---

### Post by daneandrewlam on 2013-10-08
> **mörgæs said:**
> It tries to tell you something...

What exactly it's trying to tell me is lost on me ...

---

### Post by mörgæs on 2013-10-08
You grant yourself temporary root privileges by adding **sudo** in front of the command.

---

### Post by daneandrewlam on 2013-10-09
Ahhh.... thanks!

> **mörgæs said:**
> You grant yourself temporary root privileges by adding **sudo** in front of the command.

---

### Post by mörgæs on 2013-10-09
You are welcome. 
If this solves your problem please mark the thread so.

---

### Post by daneandrewlam on 2013-10-09
Hi again...

I'm sorry and feel useless, but the same problem keeps occurring.

The reason for this thread in the first place (and I should have explained it properly) was because when I try and install something in Ubuntu Software Centre it won't happen and I get the following messages:

[COLOR=#0000cd]"Items cannot be installed or removed until the package catalogue is removed. Do you want to repair it now?"
[/COLOR]
To which I select 'Repair'

after which I get the same error message.

[COLOR=#0000cd]installArchives() failed: (Reading database ... [/COLOR]
[COLOR=#0000cd](Reading database ... 5%[/COLOR]
[COLOR=#0000cd](Reading database ... 10%[/COLOR]
[COLOR=#0000cd](Reading database ... 15%[/COLOR]
[COLOR=#0000cd](Reading database ... 20%[/COLOR]
[COLOR=#0000cd](Reading database ... 25%[/COLOR]
[COLOR=#0000cd](Reading database ... 30%[/COLOR]
[COLOR=#0000cd](Reading database ... 35%[/COLOR]
[COLOR=#0000cd](Reading database ... 40%[/COLOR]
[COLOR=#0000cd](Reading database ... 45%[/COLOR]
[COLOR=#0000cd](Reading database ... 50%[/COLOR]
[COLOR=#0000cd](Reading database ... 55%[/COLOR]
[COLOR=#0000cd](Reading database ... 60%[/COLOR]
[COLOR=#0000cd](Reading database ... 65%[/COLOR]
[COLOR=#0000cd](Reading database ... 70%[/COLOR]
[COLOR=#0000cd](Reading database ... 75%[/COLOR]
[COLOR=#0000cd](Reading database ... 80%[/COLOR]
[COLOR=#0000cd](Reading database ... 85%[/COLOR]
[COLOR=#0000cd](Reading database ... 90%[/COLOR]
[COLOR=#0000cd](Reading database ... 95%[/COLOR]
[COLOR=#0000cd](Reading database ... 100%[/COLOR]
[COLOR=#0000cd](Reading database ... 247401 files and directories currently installed.)[/COLOR]
[COLOR=#0000cd]Unpacking linux-image-3.5.0-28-generic (from .../linux-image-3.5.0-28-generic_3.5.0-28.48_amd64.deb) ...[/COLOR]
[COLOR=#0000cd]Done.[/COLOR]
[COLOR=#0000cd]dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-28-generic_3.5.0-28.48_amd64.deb (--unpack):[/COLOR]
[COLOR=#0000cd] cannot copy extracted data for './boot/System.map-3.5.0-28-generic' to '/boot/System.map-3.5.0-28-generic.dpkg-new': failed to write (No space left on device)[/COLOR]
[COLOR=#0000cd]No apport report written because MaxReports is reached already[/COLOR]
[COLOR=#0000cd]Examining /etc/kernel/postrm.d .[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic[/COLOR]
[COLOR=#0000cd]Unpacking linux-image-3.5.0-30-generic (from .../linux-image-3.5.0-30-generic_3.5.0-30.51_amd64.deb) ...[/COLOR]
[COLOR=#0000cd]Done.[/COLOR]
[COLOR=#0000cd]dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-30-generic_3.5.0-30.51_amd64.deb (--unpack):[/COLOR]
[COLOR=#0000cd] cannot copy extracted data for './boot/System.map-3.5.0-30-generic' to '/boot/System.map-3.5.0-30-generic.dpkg-new': failed to write (No space left on device)[/COLOR]
[COLOR=#0000cd]No apport report written because MaxReports is reached already[/COLOR]
[COLOR=#0000cd]Examining /etc/kernel/postrm.d .[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-30-generic /boot/vmlinuz-3.5.0-30-generic[/COLOR]
[COLOR=#0000cd]Unpacking linux-image-3.5.0-36-generic (from .../linux-image-3.5.0-36-generic_3.5.0-36.57_amd64.deb) ...[/COLOR]
[COLOR=#0000cd]Done.[/COLOR]
[COLOR=#0000cd]dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-36-generic_3.5.0-36.57_amd64.deb (--unpack):[/COLOR]
[COLOR=#0000cd] cannot copy extracted data for './boot/abi-3.5.0-36-generic' to '/boot/abi-3.5.0-36-generic.dpkg-new': failed to write (No space left on device)[/COLOR]
[COLOR=#0000cd]No apport report written because MaxReports is reached already[/COLOR]
[COLOR=#0000cd]Examining /etc/kernel/postrm.d .[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-36-generic /boot/vmlinuz-3.5.0-36-generic[/COLOR]
[COLOR=#0000cd]Unpacking linux-image-3.5.0-41-generic (from .../linux-image-3.5.0-41-generic_3.5.0-41.64_amd64.deb) ...[/COLOR]
[COLOR=#0000cd]Done.[/COLOR]
[COLOR=#0000cd]dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-41-generic_3.5.0-41.64_amd64.deb (--unpack):[/COLOR]
[COLOR=#0000cd] cannot copy extracted data for './boot/abi-3.5.0-41-generic' to '/boot/abi-3.5.0-41-generic.dpkg-new': failed to write (No space left on device)[/COLOR]
[COLOR=#0000cd]dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/COLOR]
[COLOR=#0000cd]No apport report written because MaxReports is reached already[/COLOR]
[COLOR=#0000cd]Examining /etc/kernel/postrm.d .[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-41-generic /boot/vmlinuz-3.5.0-41-generic[/COLOR]
[COLOR=#0000cd]Errors were encountered while processing:[/COLOR]
[COLOR=#0000cd] /var/cache/apt/archives/linux-image-3.5.0-28-generic_3.5.0-28.48_amd64.deb[/COLOR]
[COLOR=#0000cd] /var/cache/apt/archives/linux-image-3.5.0-30-generic_3.5.0-30.51_amd64.deb[/COLOR]
[COLOR=#0000cd] /var/cache/apt/archives/linux-image-3.5.0-36-generic_3.5.0-36.57_amd64.deb[/COLOR]
[COLOR=#0000cd] /var/cache/apt/archives/linux-image-3.5.0-41-generic_3.5.0-41.64_amd64.deb[/COLOR]
[COLOR=#0000cd]Error in function: [/COLOR]
[COLOR=#0000cd]Setting up initramfs-tools (0.103ubuntu0.2) ...[/COLOR]
[COLOR=#0000cd]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#0000cd]dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-30-generic:[/COLOR]
[COLOR=#0000cd] linux-image-extra-3.5.0-30-generic depends on linux-image-3.5.0-30-generic; however:[/COLOR]
[COLOR=#0000cd]  Package linux-image-3.5.0-30-generic is not installed.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]dpkg: error processing linux-image-extra-3.5.0-30-generic (--configure):[/COLOR]
[COLOR=#0000cd] dependency problems - leaving unconfigured[/COLOR]
[COLOR=#0000cd]Setting up linux-image-extra-3.5.0-26-generic (3.5.0-26.42) ...[/COLOR]
[COLOR=#0000cd]Running depmod.[/COLOR]
[COLOR=#0000cd]update-initramfs: deferring update (hook will be called later)[/COLOR]
[COLOR=#0000cd]Examining /etc/kernel/postinst.d.[/COLOR]
[COLOR=#0000cd]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic[/COLOR]
[COLOR=#0000cd]update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]gzip: stdout: No space left on device[/COLOR]
[COLOR=#0000cd]cpio: write error: Broken pipe[/COLOR]
[COLOR=#0000cd]E: mkinitramfs failure cpio 1 gzip 1[/COLOR]
[COLOR=#0000cd]update-initramfs: failed for /boot/initrd.img-3.5.0-26-generic with 1.[/COLOR]
[COLOR=#0000cd]run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1[/COLOR]
[COLOR=#0000cd]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.5.0-26-generic.postinst line 1010.[/COLOR]
[COLOR=#0000cd]dpkg: error processing linux-image-extra-3.5.0-26-generic (--configure):[/COLOR]
[COLOR=#0000cd] subprocess installed post-installation script returned error exit status 2[/COLOR]
[COLOR=#0000cd]dpkg: dependency problems prevent configuration of linux-image-generic:[/COLOR]
[COLOR=#0000cd] linux-image-generic depends on linux-image-3.5.0-28-generic; however:[/COLOR]
[COLOR=#0000cd]  Package linux-image-3.5.0-28-generic is not installed.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]dpkg: error processing linux-image-generic (--configure):[/COLOR]
[COLOR=#0000cd] dependency problems - leaving unconfigured[/COLOR]
[COLOR=#0000cd]dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-36-generic:[/COLOR]
[COLOR=#0000cd] linux-image-extra-3.5.0-36-generic depends on linux-image-3.5.0-36-generic; however:[/COLOR]
[COLOR=#0000cd]  Package linux-image-3.5.0-36-generic is not installed.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]dpkg: error processing linux-image-extra-3.5.0-36-generic (--configure):[/COLOR]
[COLOR=#0000cd] dependency problems - leaving unconfigured[/COLOR]
[COLOR=#0000cd]dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-41-generic:[/COLOR]
[COLOR=#0000cd] linux-image-extra-3.5.0-41-generic depends on linux-image-3.5.0-41-generic; however:[/COLOR]
[COLOR=#0000cd]  Package linux-image-3.5.0-41-generic is not installed.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]dpkg: error processing linux-image-extra-3.5.0-41-generic (--configure):[/COLOR]
[COLOR=#0000cd] dependency problems - leaving unconfigured[/COLOR]
[COLOR=#0000cd]dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-28-generic:[/COLOR]
[COLOR=#0000cd] linux-image-extra-3.5.0-28-generic depends on linux-image-3.5.0-28-generic; however:[/COLOR]
[COLOR=#0000cd]  Package linux-image-3.5.0-28-generic is not installed.[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]dpkg: error processing linux-image-extra-3.5.0-28-generic (--configure):[/COLOR]
[COLOR=#0000cd] dependency problems - leaving unconfigured[/COLOR]
[COLOR=#0000cd]Processing triggers for initramfs-tools ...[/COLOR]
[COLOR=#0000cd]update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic[/COLOR]
[COLOR=#0000cd]
[/COLOR]
[COLOR=#0000cd]gzip: stdout: No space left on device[/COLOR]
[COLOR=#0000cd]cpio: write error: Broken pipe[/COLOR]
[COLOR=#0000cd]E: mkinitramfs failure cpio 1 gzip 1[/COLOR]
[COLOR=#0000cd]update-initramfs: failed for /boot/initrd.img-3.5.0-26-generic with 1.[/COLOR]
[COLOR=#0000cd]dpkg: error processing initramfs-tools (--configure):[/COLOR]
[COLOR=#0000cd] subprocess installed post-installation script returned error exit status 1


[/COLOR]I realise my SSD is full, but cannot free space up if I can't delete programs.

I appreciate very much your advice and your patience!

Cheers,

Dane

---

### Post by mörgæs on 2013-10-09
Lots of things can go wrong when an operative system eats all hard drive space and is halted in the middle of whichever process it's doing. As you can see you have a long list of interesting error messages.

I wouldn't trust a system which has been through that, neither Buntu nor Windows, but erase and reinstall. That will also give you the opportunity to switch to the almost-released 13.10. You could however try booting the computer and running

```
sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove

```

---

### Post by daneandrewlam on 2013-10-10
I agree! Time to reinstall! I'm trying to reboot computer with USB Ubuntu ISO though it doesn't seem to be cooperating... any tips?

---

### Post by varunendra on 2013-10-10
> **daneandrewlam said:**
> I agree! Time to reinstall! I'm trying to reboot computer with USB Ubuntu ISO though it doesn't seem to be cooperating... any tips?

I would like to see the outputs of -
```
df -h
dpkg -l | grep linux-image
```

I expect to see almost zero remaining space and a lots of older kernels, removing some of which should give you plenty of space to successfully finish the current packages installation. That's the most common cause and most common fix for this kind of problems.

And the newer kernels do not necessarily perform better. In fact, you may find some new bugs that possibly don't exist in your current setup. So if your current installation is the LTS (12.04), you should try fixing it first. But of course you may try 13.10 in live mode and decide to install if you (and your system) like it. :)

---

