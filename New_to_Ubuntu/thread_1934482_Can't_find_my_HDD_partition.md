---
title: "Can't find my HDD partition"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Fantastic2m on 2012-03-02
Pardon me if this is a repetition.
I could not find any topic that matched correctly.


I recently installed ubuntu 11, I have 2 HDD partition, I used ex3 file journal file system and mounted on /.
I installed ubuntu to my second HDD as the C/: contained WIN7.
after installing it asked me to rest to use ubuntu but it finally loaded windows7 and I can't find my second HDD nor can I boot into ubuntu.
Can somebody help me with this pls?

---

### Post by oldfred on 2012-03-02
With two drives the grub boot loader may have installed to the other drive. Have you tried booting from it? Use one time boot key (f12 on my system, but it varys) or change BIOS boot order.

If you want to know all the details of what is installed where, boot_info  script gives us that.

The newer version still being updated have improvements.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

You can directly download it:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```This is the standard version, but has instructions if you need them:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by seawolf167 on 2012-03-02
Just to clarify - you have two hard drives, the primary hard drive contains Windows 7 and nothing else, and you just finished installing Ubuntu 11.xx to the second hard drive?

Which hard drive did you install Grub to? You'll need to install Grub to the primary drive (the one that BIOS first looks to for booting). This will overwrite the Windows MBR, at which point you'll be able to boot into Ubuntu and run

```
sudo update-grub
```

which will find your Windows partition loader.

Alternatively, you could change your boot order in BIOS to point to your secondary hard drive (the one with Ubuntu installed), and then have it chain from there to your primary for Windows.

---

