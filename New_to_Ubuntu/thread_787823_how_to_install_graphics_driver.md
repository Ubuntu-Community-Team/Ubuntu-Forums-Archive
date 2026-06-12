---
title: "how to install graphics driver"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-05-09
I downloaded i915graphics.tar.gz driver for my graphics but have no idea how to install it..
keep going around in circles with the extract/ open in archive manager 
I have included a screenshot
thanks in advance for any assistance

---

### Post by sharks on 2008-05-09
GOto the folder via terminal. Then type > sh install.sh

---

### Post by kpkeerthi on 2008-05-09
Install the driver from ubuntu repository
[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

---

### Post by njparton on 2008-05-09
Read the readme file that's part of the tar file.
 
```
 
sudo gunzip i915graphics.tar.gz
sudo tar -xvf i915graphics.tar
cd i915graphics

```
 
look for a readme file in there.

---

### Post by scientist1971 on 2008-05-09
richard@richard-laptop:~$ sh install.sh
sh: Can't open install.sh
richard@richard-laptop:~$ sudo gunzip i915graphics.tar.gz
[sudo] password for richard:
gzip: i915graphics.tar.gz: No such file or directory
richard@richard-laptop:~$ 

will try the repository route...

---

### Post by scientist1971 on 2008-05-09
richard@richard-laptop:~$  sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
richard@richard-laptop:~$ sudo 915resolution 30 1280 800 32
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 30 to resolution 1280x800 complete
richard@richard-laptop:~$ sudo gedit /etc/default/915resolution
sudo: gedit: command not found
richard@richard-laptop:~$

---

### Post by njparton on 2008-05-09
You're not in the same directory as the gz file when you try to run the commands I suggested!

---

### Post by scientist1971 on 2008-05-09
njparton
sorry I am new to this
how do I find what the directory location is called?

---

### Post by njparton on 2008-05-09
Well, where did you save it to?

It's probably somewhere under /home/...

---

### Post by scientist1971 on 2008-05-09
ok thanks
btw liverpool will never win the league again....sorry

---

### Post by njparton on 2008-05-10
Gee thanks, I take it you're a Man U fan?

---

### Post by lazoneleo on 2008-05-10
> **scientist1971 said:**
> I downloaded i915graphics.tar.gz driver for my graphics but have no idea how to install it..
keep going around in circles with the extract/ open in archive manager 
I have included a screenshot
thanks in advance for any assistance

Hi all

I got some problems in my desktop, the display is blur when Ubuntu early starting in desktop mode (or like the TV lost tuning mode situation), only the mouse pointer are appear good condition. Plaese someone tell me how to solve it!

my computer spec:
[LIST=1]
[*]Intell P4 2.4 Ghz
[*]sata WD HHD 80 GB
[*]8X ATi 9200 SE graphic card
[*]MSI Neo V mother board
[*]512 DDR Ram(Memory).
[/LIST]

is that Ubuntu newly version doesn't support my graphic card

---

### Post by njparton on 2008-05-10
You'd be better off starting a new thread to be honest as this thread concerned onboard intel graphics.

---

