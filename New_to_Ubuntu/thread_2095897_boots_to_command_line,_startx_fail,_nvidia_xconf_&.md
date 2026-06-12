---
title: "boots to command line, startx fail, nvidia xconf &amp; recovery boot problems"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by dez93_2000 on 2012-12-18
[note: I've just noticed I mis-clicked and labelled this thread lubuntu when it should be ubuntu. Doh!] **fixed - Celene**

hi all. a rubik's cube of problems were waiting for me when i tried to boot up today.

First: it booted to grub screen, i chose ubuntu as normal (i dual boot XP) and it flashed one of the loading lights on the ubuntu splash screen graphic before dumping me into the command line. I've had this before since about 6 months ago and found the command 'reboot' by trial and error. This normally goes back through grub then ubuntu loads. Don't know the cause, but it's not enough of a problem for me to spend a day trying to work it out, i figure. This time: keeps going back to command line.

Second: i find out about the 'startx' command & try that, which results in the error from Xorg log:
> NVIDIA: API mismatch: the NVIDIA kernel module has version 310.14, but this NVIDIA driver component has version 304.43. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Fatal server error:
no screens foundSo I do some searching and people suggest booting into recovery mode then safe boot, aligning the drivers and rebooting. Sounds logical. I try that, but whatever option I choose in recovery mode other than 'root', this happens:
> /dev/sdb1: 1157132/30400512 files (0.2% non-contiguous), 37641347, ksthen... nothing. I'd expect it to check (or do whatever it's doing) the other drives (SATAs running ubuntu & winXP, sda1 & sda2 respectively) and... do whatever it's supposed to do. Safe boot, check the file systems, whatever. But it just stays there. I can type, but it doesn't achieve anything.

Third: research [[COLOR=Blue]suggests[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=1081164")booting to recovery mode, root, and typing > nvidia-xconfigbut that results in:
> Using X configuration file: "/etc/X11/xorg.conf".
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.

ERROR: Unable to write to directory 'etc/X11'Sudo makes no difference, assumedly because i'm already root.


SO: i'm stumped. I can't get into the system via safe mode in order to align the drivers, update packages, etc etc, and fix the problem. The logical sounding method for fixing the drivers from outside the system fails. Someone's posted a lot of info _[COLOR=Blue][here]("http://ubuntuforums.org/showpost.php?p=11516779&postcount=6")[/COLOR]_ but it mostly looks like it relies on being in the system, and also looks like the kind of hardcore editing that I would really really like to avoid having to do if possible!

Other info: i already have "nomodeset" on my install, in order to allow multiple monitors, a previous problem.
Card is an nVidia 8800 GT (driver versions as posted above)

Can/should I manually fix/rebuild xorg.conf as suggested _[COLOR=Blue][here]("http://ubuntuforums.org/showpost.php?p=9827742&postcount=19")[/COLOR]_?
Is it likely that these problems (recovery modes hang, video drivers misaligned) are related?

Huge thanks in advance for any help. I assume the problem was created due to an update yesterday.

---

### Post by steeldriver on 2012-12-18
I don't have any insight on the underlying problem - however it sounds like your attempts to apply fixes in recovery mode are being blocked by the fact that the root filesystem is being mounted read-only (hence why it can't write to directory /etc/X11 and so on)

Try again but this time remount with read-write permissions as soon as you drop to the root shell

```
# mount -o remount,rw /
```

---

### Post by dez93_2000 on 2012-12-18
nice - thanks! changed from:
> Using X configuration file: "/etc/X11/xorg.conf".
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.

ERROR: Unable to write to directory 'etc/X11'                      to:
> Using X configuration file: "/etc/X11/xorg.conf".
 VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
 Device section "Default Device" must have a Driver line.
 
Backed up file 'etc/X11/xorg.conf' as
'etc/x11/xorg.conf.nvidia-xconfig-original'
Backed up file 'etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to 'etc/X11/xorg.conf'

But I still get the same fatal screens error when trying to boot into ubuntu using startx

---

### Post by SeijiSensei on 2012-12-18
You still need to fix the driver mismatch.  If you can boot into recovery mode and start the network, then try

```
# apt-get install nvidia-current
```

If you cannot get the network running, then try this.  First, connect the machine directly to your router with an Ethernet cable.  Then after selecting the root shell in recovery mode, use these commands:

```
/sbin/ifconfig eth0 192.168.1.200 netmask 255.255.255.0 broadcast 192.168.1.255
/sbin/ip route add default via 192.168.1.1

```

This assumes your router is handing out addresses in the range 192.168.1.2-254 with 192.168.1.1 assigned to itself.  The 192.168.1.200 address is arbitrary; just choose one not in use by any other machines on the network.  Massage as needed.  If you can now ping the router, you can update the driver using apt-get.

---

### Post by dez93_2000 on 2012-12-18
hmm...
trying network mode fails like the other recovery mode problems i.e. t just stops after 'sdb1'

simply trying sdo apt-get install nvidia current gives:

> W: Not using locking for read only lock file /var/liv/dpkg/locl
E: unable to write to /var/cache/apt
E: the package lists or status file could not be parsed or openedso i did the mount thing again and tried again, which gave:
> nvidia-current is already the newest version!!!

---

### Post by dez93_2000 on 2012-12-18
ugh. forgot to try sudo apt-get update first!
nvidia says my drivers are out of date ([http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)) so this might fix the problem. unfortunately I need to learn how to massage the networking thing: apt-get update gave:

> W: Failed to fetch [http://](http://)[various].gpg Could not resolve '[various]'
W: Some index files failed to download. They have been ignored, or old ones used instead.So... any massaging tips? ;)

thanks!

retrying the /sbin lines, the first gives no error or confirmation, the second results in:
> No such file or directory
when I try it with my router address (192.168.1.254) or 192.168.1.1
my usual IP address is 192.168.1.2

Any tweak suggestions?

Thanks again

---

### Post by dez93_2000 on 2012-12-18
pinged router with 75% success of 4 packets
retries apt-get update, get (for everything):

> W: Failed to fetch [http://](http://)[various] Something wicked happened resolving '[various]' (-5 - No address associated with hostname)Which feels like a nameserver problem?

route -n gives:
Destination ¦ Gateway ¦ Genmask ¦ Flags ¦ Metric ¦ Ref ¦ Use ¦ Iface
192.168.1.0 ¦ 0.0.0.0 ¦ 255.255.255.0 ¦ U ¦ 0 ¦ 0 ¦ eth0

could the command "ip route" be wrong?

/sbin/route gives:
Destination ¦ Gateway ¦ Genmask ¦ Flags ¦ Metric ¦ Ref ¦ Use ¦ Iface
192.168.1.0 ¦ * ¦ 255.255.255.0 ¦ U ¦ 0 ¦ 0 ¦ eth0

The star seems odd.... no?

[edit: the examples here give asterices as well [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/]](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/])

---

### Post by steeldriver on 2012-12-18
Hmm I wonder if that's because in the new resolvconf/dnsmasq scheme of doing things you don't have a 'static' DNS server? you could try starting the resolvconf service, or just temporarily brute force the file

# echo "nameserver 8.8.8.8" >> /etc/resolv.conf

(I don't think it will do any harm - resolvconf will just overwrite it when it starts)

---

### Post by dez93_2000 on 2012-12-18
@steeldriver: tried but no change. i put the whole thing in ver batim, i.e. included "nameserver 8.8.8.8" - i don't know the syntax of the command, so just in case: should i have replaced "nameserver 8.8.8.8" with something else?

edit: i was missing spaces around the >>, but having inserted them it's made no difference...

---

### Post by dez93_2000 on 2012-12-18
Some help from here re: ip route fixing, but i'm straining at the edge of my understanding here!
[http://serverfault.com/questions/252445/why-ip-route-add-doesnt-work-but-ip-route-add-with-less-details-and-then-chang](http://serverfault.com/questions/252445/why-ip-route-add-doesnt-work-but-ip-route-add-with-less-details-and-then-chang)

for ref: ifconfig output (abbreviated cos i gotta manually type it!)

eth0:
inet addr: 192.168.1.2
Bcast: 192.168.1.255
Mask: 255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

lo
inet addr 127.0.0.1
Mask 255.0.0.0

---

### Post by dez93_2000 on 2012-12-18
more deduction: if i ping the router, 3 out of 4 packets return. if i ping 8.8.8.8, i get "network is unreachable".
i'm still not getting SensiSenjei's tips to work, which i think have the potential to solve this...

---

### Post by steeldriver on 2012-12-18
OK let's see how your routing table looks - SeijiSensei's commands should have taken care of that but maybe something went astray

```
route -n
```

---

### Post by dez93_2000 on 2012-12-18
already done old chum - see earlier post :)

---

### Post by dez93_2000 on 2012-12-18
is it likely to be something to do with the default gateway and broadcast addresses, combined with my slightly-unusual router address of 192.168.1.254?

From the windows laptop on same network that i'm using to chat to you:
ipconfig /all = 

(for ethernet adapter. apologies in advance for mixing windows into linux help!)
DHCP Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IPv4 Address. . . . . . . . . . . : 192.168.1.4(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.254
DHCP Server . . . . . . . . . . . : 192.168.1.254
DNS Servers . . . . . . . . . . . : 192.168.1.254
NetBIOS over Tcpip. . . . . . . . : Enabled

---

### Post by steeldriver on 2012-12-18
oops ;)

So your router is 192.168.1.254, is that correct? if so, try

```

route del default
route add default gw 192.168.1.254 eth0
```

---

### Post by dez93_2000 on 2012-12-18
> route del default = no such process. looks like you don't need to delete it, the second command overwrites it. THANK YOU!
trying update now.... working! will post further progress in order ot make this a useful post for future unlucky chumps! :D


hm.... the something wicked problem happened with  dl.google.com ... but not at other times with the same URL.
ditto ppa.launchpad.net, one fail. two fails...
& it's going veeeeeeery slowly, which is odd. normally it flies through...

all security.ubuntu.com packages failing (something wicked...no address associated w/ hostname)
all launchpad, possibly all everything now failing...
why would it start fine and degrade?

---

### Post by dez93_2000 on 2012-12-18
any thoughts on this? stuck on one for about 10 minutes now, if not longer. normally this process goes "woooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooDONE"
i.e. a minute, tops. Now? 45 minutes and counting? All recently failed.... thinking there's a problem.

Can I update the nvidia drivers package separately?

---

### Post by dez93_2000 on 2012-12-18
i can: apt-get upgrade nvidia-xconfig
did it. re-ran nvidia-xconfig, it backed up xorg.conf, but startx gives the same problem: API mismatch, kernel module version different to driver component version.

===painful===

---

### Post by dez93_2000 on 2012-12-18
might anyone know why the system is stopping when trying to safe boot? feels like the GUI in safe mode would be a lifesaver...

---

### Post by steeldriver on 2012-12-18
what kernel are you running? do you have the option to boot to an earlier kernel? if it's not giving you the option to upgrade the driver, maybe the way to go?

FWIW I'm on a laptop here that is running 3.2.0-33-generic-pae with the 304.43 proprietary driver (which seems to be what you have)

---

### Post by MrSpike16 on 2012-12-18
If you now have a network connection then you can try:

```
rm /etc/X11/xorg.conf
apt-get install linux-headers-$(uname -r)
```

First command only needed if you created a xorg.conf file.

When there is a kernel or Nvidia driver update, a new NVIDIA kernel module must be 
built using the linux-headers  and this didn't happen.  Cause is usually the linux-headers
didn't get installed.   Once linux-headers is installed, it will build the module automatically.

When its completed reboot.  This should work but if it doesn't I will give you the commands to reinstall Nvidia driver.

P.S. "trying network mode fails like the other recovery mode problems i.e. t just stops after 'sdb1'"   This maybe caused by by a error in the fstab file.  In my case my swap had the wrong UUID and couldn't mount.

---

### Post by dez93_2000 on 2012-12-18
i got some good advice from someone here:
[https://devtalk.nvidia.com/default/topic/525877/linux/api-mismatch-means-ubuntu-can-t-boot-i-can-t-fix-i-please-help-/1](https://devtalk.nvidia.com/default/topic/525877/linux/api-mismatch-means-ubuntu-can-t-boot-i-can-t-fix-i-please-help-/1)

but by that point i'd already gotten it to boot - though i'm sure it's now more stable. my problem now is that the efforts to fix the problem resulted in the mouse and keyboard now not working. i researched and fixed the mouse by editing xorg.conf but the keyboard doesn't want to change - there are a lot of people out there who seem to have the same problem, and lots of them don't seem to have fixed it.
Some of them have said their solution was to upgrade to 12.10. i've been reluctant to do so as I use classic interface i.e. not unity, but i've been tempted to take the plunge. i can't though: i can't boot into ubuntu and type anything, and you can't upgrade from the root recovery command line.
BOOO.

i'll try those two suggestions now

---

### Post by MrSpike16 on 2012-12-18
With the Nvidia driver you don't need a xorg.conf, but if one is created it will be used which can lead to problems. 

Here is the instructions for re-installing Nvidia driver which might be a better solution here after re-reading the problem:

```
sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt-get install nvidia-current nvidia-settings
```

I added sudo because it sounds like you got back to the desktop.  This will install the default Nvidia driver version and not the latest.  One of my computers had a problem with this version though!!.

If all else fails reinstall Nouveau (the open source driver for Nvidia cards) for now till Nvidia mess is fixed:
```
sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt-get purge xserver-xorg-video-nouveau
sudo apt-get install xserver-xorg-video-nouveau

```

I have three computers that took the new kernel and Nvidia driver but the Nvidia Settings is broken on one and won't launch.

---

### Post by dez93_2000 on 2012-12-19
guys unfortunately i'm going to have to bank these answers as it's 5:05am and i've got an early flight tomorrow. A whole day wasted and complete problem not solved - thanks all for your help though. For ref: the nvidia forums guy was super helpful, defo worth asking there if you're in the same boat. The fixes I found had already sorted it, at the cost of screwing up my mouse (since fixed) and keyboard (not).

merry xmas problem solvers!

---

### Post by dez93_2000 on 2013-01-04
going to mark as solved, problem continuing at:
[http://ubuntuforums.org/showthread.php?p=12437797#post12437797](http://ubuntuforums.org/showthread.php?p=12437797#post12437797)

---

