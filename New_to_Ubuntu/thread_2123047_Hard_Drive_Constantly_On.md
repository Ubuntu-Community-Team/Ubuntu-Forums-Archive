---
title: "Hard Drive Constantly On"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by doctorj on 2013-03-06
Hi,

I am running Ubuntu 12.10 and have noticed that my hard drive is constantly flicking on without stopping. This seems rather unusual and want to know if there is anything that can be done to make it stop. I have a browser open with several tabs. I have gmail in one tab, St George Bank in another tab, Facebook, Google+ and Telstra in another tab. Does anyone have a similar experience and what can be done about the hard drive constantly flickering.

Doctor J
A novice
++

---

### Post by DuckHook on 2013-03-07
Without more info, it is impossible to tell. There are many possibilities, but the likeliest explanation is that you are constantly swapping. Please provide the following:
```
free -m
``````
sudo lshw -C memory
```It is also useful to run iotop to see what process is actually creating the disk I/O, but you would have to install it first:```
sudo apt-get install iotop
``````
sudo iotop -o
```You will have to run iotop with sudo. The -o switch instructs iotop to show only currently I/O-active processes. You will need to run this in a terminal while running all of the apps that you normally do to create the disk activity.

---

### Post by r-senior on 2013-03-07
Is the light off more than it is on?

What would you estimate is the ratio of time off to time on?

---

### Post by doctorj on 2013-03-07
> **DuckHook said:**
> Without more info, it is impossible to tell. There are many possibilities, but the likeliest explanation is that you are constantly swapping. Please provide the following:
```
free -m
``````
sudo lshw -C memory
```It is also useful to run iotop to see what process is actually creating the disk I/O, but you would have to install it first:```
sudo apt-get install iotop
``````
sudo iotop -o
```You will have to run iotop with sudo. The -o switch instructs iotop to show only currently I/O-active processes. You will need to run this in a terminal while running all of the apps that you normally do to create the disk activity.

free -m
-----------------------------------------
             total       used       free     shared    buffers     cached
Mem:          4023       3695        327          0        112        208
-/+ buffers/cache:       3374        648
Swap:         4077       2208       1869

sudo lshw -C memory
----------------------------------------
*-firmware              
       description: BIOS
       vendor: Award Software International, Inc.
       physical id: 0
       version: F1
       date: 02/11/2011
       size: 128KiB
       capacity: 4032KiB
       capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: a
       slot: Internal Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: b
       slot: External Cache
       size: 6MiB
       capabilities: synchronous internal write-back
  *-memory
       description: System Memory
       physical id: 17
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) 1333 MHz (0.8 ns)
          physical id: 0
          slot: A0
          size: 4GiB
          width: 2244 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
          physical id: 1
          slot: A1
     *-bank:2
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
          physical id: 2
          slot: A2
     *-bank:3
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
          physical id: 3
          slot: A3

sudo iotop -o
-----------------------------------
It is impossible to copy the readout as it is changing all the time. What I can tell you is that "chrome" "Firefox" and "Unity-web" feature every few seconds. Readout is constant every second or so a new set of readings is created. How can I freeze readout to copy and report here?

DoctorJ
++

---

### Post by DuckHook on 2013-03-07
> **doctorj said:**
> free -m
-----------------------------------------
             ```
total       used       free     shared    buffers     cached
Mem:          4023       3695        327          0        112        208
-/+ buffers/cache:       3374        648
Swap:         4077       2208       1869

```
sudo lshw -C memory
----------------------------------------
```
*-firmware              
       description: BIOS
       vendor: Award Software International, Inc.
       physical id: 0
       version: F1
       date: 02/11/2011
       size: 128KiB
       capacity: 4032KiB
       capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: a
       slot: Internal Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: synchronous internal write-back
  *-cache:1
       description: L2 cache
       physical id: b
       slot: External Cache
       size: 6MiB
       capabilities: synchronous internal write-back
  *-memory
       description: System Memory
       physical id: 17
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) 1333 MHz (0.8 ns)
          physical id: 0
          slot: A0
          size: 4GiB
          width: 2244 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
          physical id: 1
          slot: A1
     *-bank:2
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
          physical id: 2
          slot: A2
     *-bank:3
          description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-10-09 11:44+0000X-Generator: Launchpad (build 16112) [empty]
          physical id: 3
          slot: A3

```
sudo iotop -o
-----------------------------------
It is impossible to copy the readout as it is changing all the time. What I can tell you is that "chrome" "Firefox" and "Unity-web" feature every few seconds. Readout is constant every second or so a new set of readings is created. How can I freeze readout to copy and report here?

DoctorJ
++

Tip: Output posted back is much easier to read if you enclose it in *CODE* marks. As an example, I have taken the liberty of doing so in quoting your reply. Just highlight the text and use the hash (#) button at the top of the reply box.

You do not need to attach output from the *iotop* command. You have described it well and it was primarily for your own info.

You have plenty of system RAM, but are still swapping significantly and this is what is likely causing your disk activity. There are a number of fixes:

1. Do not have as many sites open at the same time. Especially if you have both Chrome and FF open concurrently, they will eat up your available memory, as both are memory hogs. Also, the fewer tabs open, the lower your memory use. Each tab counts as a current site, so ten tabs equals ten times the memory of one site. You can also try reducing cache size for FF. Don't know if possible in Chrome.

2. You can add more system RAM.

3. You can reduce swappiness to a low number. In your case, start out with 10 and reduce even further if system is still swapping like mad. Instructions are [here]("https://help.ubuntu.com/community/SwapFaq").

4. If your system is running quite well and not slowing you down, you may wish to simply leave well enough alone. This is usually my philosophy.

---

