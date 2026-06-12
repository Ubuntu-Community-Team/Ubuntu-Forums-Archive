---
title: "Inxi : Easy Information Retrieval Script"
date: 2009-12-12
forum: Outdated Tutorials &amp; Tips
---

### Post by airtonix on 2009-12-12
Inxi is a bash script that collects, formats and provides multiple ways to output data about your system configuration.

If it were to become a default part of ubuntu installations, it would make it easier for new users to provide information about their system.


[SIZE=4][COLOR=RoyalBlue]**Step One : Get Dependencies**[/COLOR][/SIZE]
 Inxi needs gawk, which isn't installed by default on ubuntu : 
```
sudo apt-get install gawk pastebinit
```[SIZE=4][COLOR=RoyalBlue]**Step Two : Make it easy to access**[/COLOR][/SIZE]

[LIST=1]
[*]Best place to put inxi for now is in your ~/bin folder :
```
mkdir ~/bin
```
[*]Make the ~/bin folder a part of your $PATH so yo ucan run executables in this folder from anywhere without prefixing them with ~/bin
```
source ~/.profile && gedit ~/.profile
```
[*]At the end append this text (if it's not already there): 
```
#
# set PATH so it includes user's private bin if it exists
#
if [ -d "$HOME/bin" ] ; then
        PATH="$HOME/bin:$PATH"
        if [ -d "$HOME/bin/depot_tools" ] ; then
                PATH="$HOME/bin/depot_tools":"$PATH"
        fi
fi
```
[/LIST]
[SIZE=4][COLOR=RoyalBlue]**Step Three : Get the Script**[/COLOR][/SIZE]
Get the inxi script and put it in the ~/bin folder, then make it an executable : 

```
wget smxi.org/inxi && chmod +x ./inxi
```[COLOR=RoyalBlue]**[SIZE=4]Step Four : Confirm that all this worked[/SIZE]**[/COLOR]

Test that you can use it outside the ~/bin folder :
```
cd ~/ && inxi
```Should provide you with the output : 

```
~$ inxi 
CPU[-Dual core Intel Core2 Duo E6550 (SMP) clocked at 1998.000 Mhz-] Kernel[-2.6.31-16-generic-pae i686-] Up[-1 day-] Mem[-1274.2/4025.0MB-] HDD[-670.1GB(32.8% used)-] Procs[-188-] Client[-Shell-] inxi[-1.2.7-]

```
[COLOR=RoyalBlue]**[SIZE=4]Using it in xChat [/SIZE]**[/COLOR]

```
/exec -o ~/bin/inxi | pastebinit
```Because the output of inxi can be quite large(spanning several lines) this will pipe the output through pastebinit and the url will appear in the chat channel.

---

### Post by h2-1 on 2010-01-13
Please note that Cathbard has packaged inxi and also that Mint uses that package in its default installs.

You can add the cathbard repo following these directions: [http://cathbard.com/cathbard-repo-howto.html](http://cathbard.com/cathbard-repo-howto.html)
Then simply do: apt-get install inxi
and it will handle all the dependencies. mesa-utils is also required, not sure if Ubuntu uses that same package name. And there are several recommends to get full support for all features, like inet-utils, hddtemp, lm-sensors, etc. Some of these require additional setup.

Current options can show output like this (or less, or more, or single line output): 
```
$inxi -o
Unmounted: ID: /dev/sda7 size: 15.73G label: sys-dd-root-1 uuid: 527dd5c2-0375-454f-88f1-1edd6922f80d fs: ext3
           ID: /dev/sda9 size: 8.10G label: N/A uuid: 32dd515d-8137-4be0-9a73-902994cb9c78 fs: ext4
           ID: /dev/sdb1 size: 10.49G label: N/A uuid: 56593cab-0eb4-440f-9f0c-c1c216d7ea84
...
$ inxi -F
System:    Host trial Kernel 2.6.30-7.dmz.1-liquorix-686 i686 (32 bit) Distro sidux-20070102-d:1
CPU:       Dual core AMD Athlon 64 X2 3800+ (SMP) cache 1024 KB flags (sse3 nx lm) bmips 8051.06
           Clock Speeds: (1) 2000.00 MHz (2) 2000.00 MHz
Graphics:  Card nVidia G86 [GeForce 8400 GS] X.Org 1.6.3 Res: 2560x1024@50.0hz
           GLX Renderer GeForce 8400 GS/PCI/SSE2/3DNOW! GLX Version 3.2.0 NVIDIA 190.42 Direct Rendering Yes
Audio:     Card nVidia CK804 AC'97 Audio Controller driver Intel ICH at ports f000 ec00
           Sound: Advanced Linux Sound Architecture Version 1.0.20
Network:   Card-1 nVidia CK804 Ethernet Controller driver forcedeth at port b400
           Card-2 Marvell 88E8053 PCI-E Gigabit Ethernet Controller driver sky2 at port 8c00
Disks:     HDD Total Size: 490.1GB (50.5% used) 1: /dev/sda ST380817AS 80.0GB 29C
           2: /dev/sdb ST3160827AS 160.0GB 29C 3: /dev/sdc ST3250824AS 250.1GB 33C
Partition: ID:/ size: 13G used: 8.3G (70%) fs: ext3 ID:/home size: 15G used: 7.8G (56%) fs: ext3
           ID:swap-1 size: 2.10GB used: 0.00GB (0%) fs: swap
Sensors:   System Temperatures: cpu: 47.5C mobo: 39.0C gpu: 0.0:58C
           Fan Speeds (in rpm): cpu: 2136 mobo: 6367 fan-1: 0
Info:      Processes 210 Uptime 53 min Memory 1350.9/2026.6MB Client Shell inxi 1.3.1

```I would also like to see inxi adopted and packaged in either Ubuntu or Debian, ideally both, anyone interested in doing that can talk to cathbard, who already provides the Mint inxi package, he knows what is required, or you can simply use his, he tends to update it fairly soon after inxi updates happen, and is on the inxi svn email update list.

---

