---
title: "HOWTO: Install and Configure OpenVZ on Ubuntu 8.04"
date: 2008-09-24
forum: Outdated Tutorials &amp; Tips
---

### Post by dejitarob on 2008-09-24
There is a guide for OpenVZ [posted last year]("http://ubuntuforums.org/showthread.php?t=617225") for 7.10. While still useful, I found it does contain some outdated information. So I am sharing what I figured out to get OpenVZ working with Ubuntu 8.04.
[B]
Introduction[/B]

[OpenVZ]("http://wiki.openvz.org/Main_Page") allows multiple Linux distributions to run on a single computer or server, each with their own dedicated resources and configurations, also known as "Virtual Private Servers" (VPS). It is the free and open source alternative to [VMWare ]("http://www.vmware.com/")and [Virtuozzo]("http://www.parallels.com/en/products/virtuozzo") (actually based on OpenVZ and has many similarities). For more info see [http://wiki.openvz.org/Features](http://wiki.openvz.org/Features) and [http://wiki.openvz.org/FAQ](http://wiki.openvz.org/FAQ)

**Basic Terms**

I will give a step-by-step guide below, so don't worry if you don't get this all at first. The "host" computer or server is known as the *Hardware Node* (HN or HW). The HN hosts *Container Nodes* (CT) or *Virtual Environments* (VE) aka VPSs. Each VE is assigned a unique number or VEID. The VE runs off of a OS template. See [http://wiki.openvz.org/Category:Definitions](http://wiki.openvz.org/Category:Definitions) for more.

**Installing**

_Preparing and Installing OpenVZ_
1. It is recommended, but not necessary, to create a separate partition for the VE. Use [gparted]("http://gparted.sourceforge.net/livecd.php") if needed to resize partitions. After the partition is made, create the /vz directory (even if skipping the partition):
```

sudo mkdir /vz

```2. If making a separate partition, add the following to /etc/fstab:
```

/dev/sda1 /vz ext3 noatime,relatime,errors=remount-ro 0 1

```3. Create a symbolic link from /vz to a /var/lib/vz
```
sudo ln -s /vz /var/lib/vz
```4. Make sure backports is enabled. See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) for instructions and [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more info on repos. After backports is enabled, install the openvz packages:
```
apt-get install linux-openvz
``` and then reboot into the openvz kernel. 

5. After rebooting into the openvz kernel, install some tools:
```
apt-get install vzctl vzquota
```6. Add the following to /etc/sysctl.conf:
```

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.default.proxy_arp = 0
net.ipv4.ip_forward=1
kernel.sysrq = 1
net.ipv4.conf.default.send_redirects = 1
net.ipv4.conf.all.send_redirects = 0
```7. Restart the vz service:

```
/etc/init.d/vz restart
```_Creating the VE_
1. Get an OS template to create the VE. I am using the ubuntu 8.04 template, there are more available at [http://wiki.openvz.org/Download/template/precreated](http://wiki.openvz.org/Download/template/precreated)
```
wget download.openvz.org/template/precreated/ubuntu-8.04-i386-minimal.tar.gz
sudo mv ubuntu-8.04-i386-minimal.tar.gz /var/lib/vz/template/cache/
```2. Create the VE (don't use less than 101, since those are for internal use):
```
sudo vzctl create 101 --ostemplate ubuntu-8.04-i386-minimal
```_Configuring the VE_
1. Add the appropriate network settings to the VE. For a static IP:
```
sudo vzctl set 101 --ipadd 192.168.1.101 --hostname testvps --nameserver 192.168.1.100 --nameserver 10.0.0.1 --save 
```See [http://wiki.openvz.org/Common_Networking_HOWTOs](http://wiki.openvz.org/Common_Networking_HOWTOs) for DHCP or other network setups. 

2. Edit /etc/vz/conf/101.conf to give the VE some usable resources (for other templates or more info see [http://wiki.openvz.org/UBC_configuration_examples_table):]("http://wiki.openvz.org/UBC_configuration_examples_table%29:")
```
# UBC parameters (in form of barrier:limit)
KMEMSIZE="16384000:18022400"
LOCKEDPAGES="4096:4096"
PRIVVMPAGES="262144:292912"
SHMPAGES="131072:131072"
NUMPROC="400:400"
PHYSPAGES="0:2147483647"
VMGUARPAGES="102400:2147483647"
OOMGUARPAGES="102400:2147483647"
NUMTCPSOCK="500:500"
NUMFLOCK="200:220"
NUMPTY="64:64"
NUMSIGINFO="512:512"
TCPSNDBUF="5365760:10485760"
TCPRCVBUF="5365760:10485760"
OTHERSOCKBUF="1503232:4063232"
DGRAMRCVBUF="262144:262144"
NUMOTHERSOCK="500:500"
DCACHESIZE="4194304:4317184"
NUMFILE="9312:9312"
AVNUMPROC="200:200"
NUMIPTENT="128:128"

# Disk quota parameters (in form of softlimit:hardlimit)
DISKSPACE="5048576:5153024"
DISKINODES="1000000:1020000"
QUOTATIME="0"
```3. Start the VE:
```
sudo vzctl start 101
```4. Enter & test the VE's networking:
```
sudo vzctl enter 101
ping <HN ip>
ping google.com
```5. If it's working you can start using your VE just like another copy of Ubuntu or whatever distro you used for the OS template. Note: the Ubuntu template is a minimal install (only uses 46MB default). I updated the VE's /etc/sources.list to match my HN's repos, then installed whatever software I needed, using 'apt-cache search <package>' or [http://packages.ubuntu.com](http://packages.ubuntu.com) to find the package name.

**Useful Commands**

List all VEs and their state: vzlist -a
Delete VEs: vzctl destroy <veid> (no going back)
More commands: man vzctl
See VE stats: vzctl exec <veid> cat /proc/user_beancounters

I'll also soon be posting a guide for installing the free and open source control panel usermin + virtualmin.

**Troubleshooting**

Weird errors? Make sure you are booted into the openvz kernel:
```
uname -a
Linux vpsu4.4domains.com 2.6.24-19-**openvz** #1 SMP Thu Aug 21 04:18:17 UTC 2008 i686 GNU/Linux

```And all the openvz modules are loaded on the HN: 
```
sudo modprobe vzethdev vznetdev vzrst vzctp vzmon vzdquota vzdev
```Also, the [openvz wiki]("http://wiki.openvz.org/") is a good resource (watch out for outdated info) and there is a friendly community at [http://forum.openvz.org](http://forum.openvz.org) for configuring more complicated setups.

---

### Post by dejitarob on 2008-09-29
I posted [a howto]("http://ubuntuforums.org/showthread.php?t=930908") for setting webmin, a solid, feature-rich open source control panel that goes well with openvz VE's. It's like Plesk or cPanel but free!

---

### Post by fwre01 on 2008-09-29
Excelent! i am just about to rebuild my openvz server and wanted to use 8.04. Thanks

---

### Post by dejitarob on 2008-09-30
Great, let me know how it turns out. I am actually using OpenVZ and Webmin to launch a completely open source VPS product line for my work, 4domains.com.

---

### Post by dejitarob on 2009-03-11
Just found this really useful command:
```
vzsplit -n 10
```It will spit out the necessary configuration settings for 10 VPSs, equally dividing the resources it detects on the hardware node/server. I had a hardware node that kept getting "out of memory errors" and used this to tweak the configuration for all the VPSs hosted on there.

Edit: I've found vzsplit sets really low privvmpages. If you get failcnts with cat /proc/user_beancounters, see [http://wiki.openvz.org/Privvmpages#privvmpages](http://wiki.openvz.org/Privvmpages#privvmpages) for tweaking it.

---

