---
title: "Grub problems"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by juliusroot on 2013-01-12
I just updated to 12.10 from 9.04 and have a long list that shows up in grub. I usually have Windows chosen as the default OS and I'd like for it to launch first. I've tried following all of the tutorials and installing the Grub Customizer but nothing shows up. It seems as if I've installed grub customizer but I can't find it anywhere to launch. If I try doing it by hand and editing the grub file nothing shows up when I try to fetch the file. Could someone help me figure out how to get Windows to boot first?

---

### Post by offgridguy on 2013-01-12
> **juliusroot said:**
> I just updated to 12.10 from 9.04 and have a long list that shows up in grub. I usually have Windows chosen as the default OS and I'd like for it to launch first. I've tried following all of the tutorials and installing the Grub Customizer but nothing shows up. It seems as if I've installed grub customizer but I can't find it anywhere to launch. If I try doing it by hand and editing the grub file nothing shows up when I try to fetch the file. Could someone help me figure out how to get Windows to boot first?
The info here might help.

[http://ubuntuforums.org/showthread.php?t=2088216](http://ubuntuforums.org/showthread.php?t=2088216)

And welcome to the forums.

---

### Post by Impavidus on 2013-01-13
If it's about the list being too long, you can uninstall some old kernels.

---

### Post by grahammechanical on 2013-01-13
Have you run the command?

```
sudo update-grub
```

We have to do that for our changes to be recognised. Sometimes we need to run

```
sudo grub-install /dev/sda
```

if sda is where Grub has been installed into.

Regards.

---

### Post by juliusroot on 2013-01-13
> **offgridguy said:**
> The info here might help.

[http://ubuntuforums.org/showthread.php?t=2088216](http://ubuntuforums.org/showthread.php?t=2088216)

And welcome to the forums.

Thanks but I've tried doing all those things and nothing works. I can't get Grub Customizer for some reason. I've tried to follow a guide that said how to download it and use it but.. well.. it didn't work.

> **Impavidus said:**
> If it's about the list being too long, you can uninstall some old kernels.

Thanks. I'll try doing this - it seems like it's the only thing I'll be able to do.

> **grahammechanical said:**
> Have you run the command?

```
sudo update-grub
```

We have to do that for our changes to be recognised. Sometimes we need to run

```
sudo grub-install /dev/sda
```

if sda is where Grub has been installed into.

Regards.

I haven't even been able to edit the grub file at all. It always opens up blank.

---

### Post by Impavidus on 2013-01-14
I don't know grub customizer, and although it may well work and has a pretty GUI, I generally try to stay away from that kind of tools. The problem is that most people don't have them installed and therefore can't help you with them. What we all have installed are the old-fashioned command line and the text files for configuration, which are the same for everybody, so we can help you that way.

You upgraded from 9.04, so you probably have grub legacy (as opposed to grub2).  Grub legacy was the default in 9.04 and if you used grub2 you wouldn't get a long list, as grub2 moves the old kernels in a separate menu. Actually, grub customizer is designed for grub2, so it's unlikely to work properly in your situation. It also explains why your /etc/default/grub is empty. It was introduced for grub2, so it isn't present on your system. You can check your grub version by looking at the menu when booting, it should be there at the top of the screen. The version number could be either  0.97 or 1.98 or higher.

I don't have grub legacy any more on any of my computers, but if I'm correct you can change its settings by editing the menu.lst file. First open a terminal (ctrl+alt+t). Then make a backup of your old menu.lst:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```(copy-paste this from this box to prevent typing errors)
Type your password (it won't show up, not even as asterisks). If you make an error your computer may become unbootable from the hard disk, but you can recover by booting from a live cd and restoring the backup.

Next open the file for editing:```
gksudo gedit /boot/grub/menu.lst
```Enter your password again.

When you scroll down you'll find some menu entries. The first entry has number 0, the second has number 1, etc. Find the number of the entry for windows. Then scroll up again. Somewhere (close to the top I think) must be a line saying something like```
DEFAULT=0
```Change that number to the number of the windows entry. Save the file and close gedit. This should be all you need to do.

If you need more help, please post the contents of your /boot/grub/menu.lst here.

Alternatively, you could move on and install grub2.

Considering the removal of old kernels: Type```
dpkg --get-selections linux-image*
``` in your terminal. It should give you a list of all installed kernels as "linux-image-some.version.number". Find the oldest ones and uninstall them using```
sudo apt-get purge linux-image-some.version.number
```It's best to keep the latest and one older one as a backup. It's easiest to remove the old kernels before you change menu.lst.

---

### Post by Cavsfan on 2013-01-14
> **juliusroot said:**
> I just updated to 12.10 from 9.04 and have a long list that shows up in grub. I usually have Windows chosen as the default OS and I'd like for it to launch first. I've tried following all of the tutorials and installing the Grub Customizer but nothing shows up. It seems as if I've installed grub customizer but I can't find it anywhere to launch. If I try doing it by hand and editing the grub file nothing shows up when I try to fetch the file. Could someone help me figure out how to get Windows to boot first?

You could use the link in my signature. It is similar to grub customizer. I too was tired of changing the default as I wanted my Windows 7 OS to be the default.
Once you make these changes, you will never have to mess with it again unless you delete a Ubuntu or something.

In a nutshell, you drop a picture in /boot/grub/ and make some changes to about 3 files.
Then once you are satisfied that everything is working well.
You make the other files unexecutable.

Here is what my grub screen looks like and I have 4 Ubuntus and Windows 7.

```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
```

```
     0	menuentry "Lucid Lynx 10.04" {
     1	menuentry "Lucid Lynx 10.04 (Recovery Mode)" {
     2	menuentry "Precise Pangolin 12.04" {
     3	menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     4	menuentry "Quantal Quetzel 12.10" {
     5	menuentry "Quantal Quetzel 12.10 Generic (Recovery Mode)" {
     6	menuentry "Raring Ringtail 13.04" {
     7	menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     8	menuentry "Windows 7" {
```

[[IMG]http://ompldr.org/taDI4aA[/IMG]]("http://ompldr.org/vaDI4aA")

Here is the link to post questions, problems, etc:

[[color=blue]_How to have a custom Grub2 menu that is maintenance free_[/COLOR]](http://ubuntuforums.org/showthread.php?t=2076205)

---

