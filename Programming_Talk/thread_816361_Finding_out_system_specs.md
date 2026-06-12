---
title: "Finding out system specs"
date: 2008-06-02
forum: Programming Talk
---

### Post by yaazz on 2008-06-02
Hello, I am trying to write a script or program  to find out the hardware specs on a computer. 
How does ubuntu go about finding this information?

---

### Post by LaRoza on 2008-06-02
> **yaazz said:**
> Hello, I am trying to write a script or program  to find out the hardware specs on a computer. 
How does ubuntu go about finding this information?

What specs interest you. They are not all in one place.

---

### Post by yaazz on 2008-06-02
CPU type/speed
Ram Size
Video card type
Hard drive size 

and anything else possible

---

### Post by LaRoza on 2008-06-02
> **yaazz said:**
> CPU type/speed
Ram Size
Video card type
Hard drive size 

and anything else possible
[list]
[*] CPU type: **grep "model name" /proc/cpuinfo**
[*] CPU speed: **grep "cpu MHz" /proc/cpuinfo**
[*] RAM: **grep "MemTotal" /proc/meminfo**
[*] Video: **lspci | grep "VGA"**
[*] Hard disks: **sudo fdisk -l | grep "Disk"**
[/list]

---

### Post by LaRoza on 2008-06-02
I found this script online, it is pretty good. It takes a screenshot also, but you may want to get rid of that (scrot is the program for that)

```

#!/bin/bash
#####
##### iphitus' screenshot script :D
#####
#####RENAME THIS FILE EXTENSION FROM .txt to .sh
#####-edit as needed
#####-execute from a terminal or run dialog with
#####sh info.sh

# screenshot dir
ssdir="$HOME/screenie/"
# screenshot description
ssdesc="$HOME/screenie"
# screenshot format
ss=`date +%d%m%Y`.png

# Extra hdd details?
hdddetails=0
# Use comments file?
comments=0
# Automatically grab gnome theme info
autognome=1

#echo
#date
echo
echo "Kernel:         `uname -r`"
#echo "Distro:         `cat /etc/*release`"
. /etc/lsb-release
echo "Distro:         $DISTRIB_ID $DISTRIB_RELEASE $DISTRIB_CODENAME"
echo "Uptime:         `uptime |cut --delimiter=" " -f 2`"
echo ___________________________________________________________________
echo "CPU:           `grep "model name" /proc/cpuinfo|cut --delimiter=":" -f 2`" 
echo "Speed:         `grep "cpu MHz" /proc/cpuinfo|cut --delimiter=":" -f 2` mhz"
echo "Bogomips:      `grep "bogomips" /proc/cpuinfo|cut --delimiter=":" -f 2` bogomips"
echo ___________________________________________________________________
let memtotal=`grep "MemTotal" /proc/meminfo|cut -c 12-22|indent -i0`/1024
echo "Memory Total:   $memtotal mb"
let memfree=`grep "MemFree" /proc/meminfo|cut -c 12-22|indent -i0`/1024
let memcache=`grep "Cached" /proc/meminfo|cut -c 12-22|indent -i0`
let memcache=$memcache/1024
let memfreetotal=$memfree+$memcache
echo "Memory Free:    $memfreetotal mb"
echo ___________________________________________________________________
#echo "Graphics:       `grep "Product" /proc/fb0/vbe_info|cut --delimiter=" " -f 5`" 
cat /proc/driver/nvidia/version
echo ___________________________________________________________________
if [ $autognome == 1 ]; then
  echo "GTK2:           		`gconftool-2 --get /desktop/gnome/interface/gtk_theme`"
  echo "Metacity:                       `gconftool-2 --get /apps/metacity/general/theme`"
  echo "Icons:          		`gconftool-2 --get /desktop/gnome/interface/icon_theme`"
#  echo "Titlebar Font:      		`gconftool-2 --get /apps/metacity/general/titlebar_font`"
  echo "Application Font:  		`gconftool-2 --get /desktop/gnome/interface/font_name`"
  echo "Terminal Font:  		`gconftool-2 --get /apps/gnome-terminal/profiles/Default/font`"
fi
sleep 4
scrot $ss
echo
exit 0
```

---

### Post by geirha on 2008-06-02
> **yaazz said:**
> CPU type/speed
Ram Size
Video card type
Hard drive size 

and anything else possible

```
sudo lshw
``` will list all that. There's a graphical version of lshw available too, which you will get by installing [lshw-gtk](apt://lshw-gtk).

---

### Post by Skip Da Shu on 2008-06-02
Why does lshw (and lshw-gtk) give DIMM frequency as if the CPU/MOBO/FSB where running at default?  

For example I have a Q6600 that's running the clock at 346 (vs stock of 266).  These utils report my memory is running 667MHz.  I can divide 667 by the stock FSB of 266 and come up with the 2.5 ratio (matches BIOS setting of memory ratio).  So I believe my memory is running 865MHz (346 * 2.5).  

Other then mucking about with wine and CPU-Z (last attempt didn't work) is there any way to confirm actual DIMM frequency and latency timings?

Thanx, Skip

---

