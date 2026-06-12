---
title: "HOWTO: Setup and Configure Vyatta OFR Router on Ubuntu Edgy with VMWare Server"
date: 2007-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dragonriot on 2007-03-19
[SIZE="5"]Vyatta OFR Router VC2 on Ubuntu Edgy with VMWare Server[/SIZE]

Credits go to larstr on the irc.freenode.net #vmware channel, the many Vyatta guides at [www.vyatta.com/documentation](www.vyatta.com/documentation), and my wife for supporting my not doing any work today to get this thing up and running.

The host machine is an AMD Athlon XP 2800+ with 512MB of RAM - soon to be 1.5GB - running Ubuntu Edgy i386 Desktop Edition.  The machine also has "Server" components installed, and will soon be hosting Windows 2003 Server as a Virtual Machine.  Kernel version is 2.6.17-11 for the host, and VMWare Server version 1.0.2.  This guide should work on any architecture that is capable of running VMWare, but this guide is specific to features of Ubuntu.

I thought it was pretty cool that Vyatta is based on Ubuntu Edgy, so it gave me even more reason to do a write-up on how I got it working at home.  This guide will take you step-by-step through the configuration and usage of the Vyatta Open Flexible Router.

You will need:
[LIST]
[*]a spare i386 or better computer - anything capable of running Ubuntu will work
[*]two Realtek 8139 NICs - or other compatible 100mbit network cards
[*]at least a 500MB hard disk
[*]at least 256MB of RAM
[*]a cd-rw drive
[/LIST]
-OR-
[LIST]
[*]a computer running a VMWare compatible OS - preferably Ubuntu Edgy
[*]no kernel version higher than 2.6.18 due to known VMWare issues with 2.6.19 and higher kernels - until such time as a patch is found for the problems.
[/LIST]

If you want to uninstall this software after you are done, by all means - delete the Virtual Machine from your VMWare Server or format the hard drive.  This is a standalone - albeit crippled - Ubuntu installation.

[SIZE="4"]Setting up your Host[/SIZE]

Assuming you are using Ubuntu Edgy as your host, the first thing you'll want to do is ensure you have all updates and two NICs installed.  Begin by editing your /etc/network/interfaces file to look like so....

```

auto lo
iface lo inet loopback

## //this will be your LAN interface IP address, so adjust accordingly
iface eth0 inet static  
address 10.0.0.2       
netmask 255.255.255.0
gateway 10.0.0.1

## //this interface will be used explicitly by the router - the host cannot have access to it
#iface eth1 inet dhcp   
#address                
#netmask 
#gateway 


```

Save the file, and check your network status with ifconfig:
```

~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 10:00:50:30:01:5A  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1200:50ff:fe30:15a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10561435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6565450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1087172393 (1.0 GiB)  TX bytes:2330407340 (2.1 GiB)
          Interrupt:201 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 10:00:50:30:01:57  
          inet6 addr: fe80::1200:50ff:fe30:157/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1353757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117717355 (112.2 MiB)  TX bytes:1534669 (1.4 MiB)
          Interrupt:209 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1520951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1520951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:288376600 (275.0 MiB)  TX bytes:288376600 (275.0 MiB)

```

If you don't see both eth0 and eth1, make sure you do:
```
sudo ifconfig ethx up
```
where 'x' is the interface number.

I'm making a huge assumption that you are already connected to the internet through a cheap-o Net-D-Link-Sys router and can log into it through http or telnet to steal it's running configuration.  If you are not, and you have a computer direct connected to your cable/dsl modem, may God have mercy on your soul.... Just kidding.  Either way, ensure that your eth0 interface is still connected to the network before going any further.  At this point, the Host machine is configured as much as it needs to be.

[SIZE="4"]Installing VMWare Server 1.0.2[/SIZE]

Before you actually install VMWare, it's a good idea to grab a few extra programs from apt-get or Synaptic, whichever you are more comfortable with.
```
sudo apt-get install xinetd
```
should do the trick, and you can now move on to installing VMWare Server.

Take a trip over to [VMWare.com]("http://www.vmware.com") to download the [Linux Server Package]("http://www.vmware.com/download/server/").  Click the "Register" button, enter in your real information, and receive your free VMWare Server Serial Number.  You should write that down or e-mail it to yourself for later.  Take the time to read the EULA if you wish, and then continue on to the download page.  Download the "VMWare Server for Linux" binary (tar.gz) package, and unpack it when it's done.

```

~$ tar xfz VMware-server-1.0.2-39867.tar.gz
~$ cd vmware-server-distrib
~$ sudo ./vmware-install.pl

```

You should accept most of the defaults for the setup, only possibly changing where you want your VMs to be installed.  Mine are located at /pub/misc because it's a 200GB empty drive, but the default /var/vmware is fine if you only plan to use Vyatta as a Virtual Machine.  As you have two NICs, when the networking setup dialogue starts, you'll want to answer 'Yes' to the question about "setting up another bridged network".  You'll also want NAT and Host-Only networking enabled, but you won't be using them for the router itself.  At the end of the install, it will ask you for the serial number you received earlier, so just copy and paste it into your console.

Head over to [Vyatta.com]("http://www.vyatta.com") and download the Community  Version of the Router software.  It comes as a LiveCD ISO and is about 100MB, so now is a good time to start the download.  You won't need to burn it at this point - unless you are using the spare computer we talked about earlier.

Close the console window when you are done - blasphemy, I know - and go to your Applications menu.  Go to System Tools, and select VMWare Server Console.  Chose "Local Host" for the machine to connect to, and hit ok.  As a side note, you should never run VMWare as root, you will break it and have to start from scratch.  Click on "Add a new virtual machine" in the new window, and go through the prompts to create a "Other Linux 2.6 kernel" machine.  You'll want to change the name of the machine from "Other...." to something like "Vyatta" or "VM-Router", and save the .vmdk file in the default directory.  You should make the hard disk size no larger than 1.0GB, and really 500MB is plenty.  You should also allocate no more than 256MB of RAM to the Virtual Machine, and after the .vmdk file has been written, you'll want to click the "Edit this Virtual Machine" button.

At this point, you can delete the floppy drive from the configuration, add a second Ethernet card, and manually assign eth0 and eth1 to /dev/vmnet0 and /dev/vmnet2 respectively.  vmnet0 corresponds to the physical eth0 on the host machine, and vmnet2 corresponds to the bridged connection on eth1 that you created with the VMWare setup.  When your download is finished, you should also edit the CD-Rom drive to "use an .iso image" from your local hard drive.  Navigate to your home folder - or wherever you downloaded the iso to - and double-click it.  Hit 'OK' and click "Start this Virtual Machine".

[SIZE="4"]Installing Vyatta[/SIZE]

As soon as you see the VMWare splash screen on bootup, click inside the VM, and press 'ESC' to get to the boot menu.  You'll want to pick CD-Rom from the menu, and now you should have a linux kernel boot prompt.  Type 'Vyatta', press enter, and wait a few minutes.  When you get to the login prompt, use 'root' for the login and 'vyatta' for the password.  Type "install-system" and accept the defaults again, especially the partitioning portion.

Once Vyatta is installed, you can reboot the machine, press any key to boot into grub, and let the kernel boot.  It is very likely you will never turn this machine off ever again.  Now you should be at the login prompt, type 'root' and 'vyatta' for the login/password again, and you'll find yourself at a bash shell.  Type 'xorpsh' and press enter.

[SIZE="4"]Configuring Vyatta[/SIZE]

From this point, most of the guide will be code... I've typed enough tonight, and it's getting late.  Giving credit where it is due, most of the code will be taken directly from the Vyatta Config Guide available on their website.  I'm changing certain things to make it work on a home network though.

```

## //set your router's host-name
root@vyatta# set system host-name $YOURCHOICE
OK
[edit]
root@vyatta# commit
OK
[edit]
## //note the hostname has changed
root@$YOURCHOICE# set system domain-name mydomain.com
OK
[edit]
root@R1# commit
OK
[edit]
## //set the default gateway for the LAN to the router
root@R1# set system static-host-mapping host-name YOURCHOICE
inet 127.0.0.1
OK
[edit]
root@R1# commit
OK
[edit]
## //set your default gateway from your live router to Vyatta
root@R1# set protocols static route 0.0.0.0/0 next-hop 99.99.99.1 
OK
[edit]
root@R1# commit
OK
[edit]

```
The previous sequence set up our router's host-name, domain-name - if you have one - set the router as the default gateway for the internal network, and set the current default gateway to the internet on the router.  Next you'll be setting up your DNS servers, IP addresses, DHCP Server, SSH and HTTP access.
```

## //set dns servers
root@R1# set system name-server 24.196.64.53
[edit]
root@R1# set system name-server 24.196.64.39
[edit]
root@R1# commit
OK
[edit]
## //set interface ip addresses
root@R2# set interfaces ethernet eth0 address
10.0.0.1 prefix-length 24
[edit]
## //your current public dhcp-isp ip address
root@R1# set interfaces ethernet eth1 address
99.99.99.43 prefix-length 23  
[edit]
## //your current router's mac address
root@R1# set interfaces ethernet eth1 mac 00:00:00:00:00 
[edit]
root@R1# commit
OK
[edit]
## //set loopback interface to anything other than 127.0.0.1 - it is reserved
## //you'll still be able to ping 127.0.0.1, but it automagically routes to
## //whatever IP you set below.
root@R1# set interfaces loopback lo address 10.0.0.65
prefix-length 32
[edit]
root@R1# commit
OK
[edit]
root@R1# show interfaces

```
Here's the DHCP sequence...
```

## //define your dhcp ip pool
root@R1# set service dhcp-server name ETH0_POOL start
10.0.0.2 stop 10.0.0.50
[edit]
## //define the network mask - 24 means 255.255.255.0
root@R1# set service dhcp-server name ETH0_POOL
network-mask 24
[edit]
## //bind dhcp to your LAN interface - eth0
root@R1# set service dhcp-server name ETH0_POOL
interface eth0
[edit]
## //define a public dns or internal dns server
root@R1# set service dhcp-server name ETH0_POOL
dns-server 24.196.64.53  
[edit]
root@R1# commit
OK
[edit]
## //allow http access to the router on port 8080
root@R1# set service http port 8080
[edit]
root@R1# commit
OK
[edit]
## //allow ssh access to the router with all ssh versions
root@R1# set service ssh protocol-version all
[edit]
root@R1# commit
OK
[edit]

```
If you want access to the internet when you plug this baby in, you'll need to add a couple of NAT rules to the system.  Here they are:
```

## //set up IP_Masquerade so your network machines can get out to the internet
root@R1# create service nat rule 1
[edit]
root@R1# edit service nat rule 1
[edit service nat rule 1]
root@R1# set type source
[edit service nat rule 1]
root@R1# set translation-type masquerade
[edit service nat rule 1]
root@R1# set outbound-interface eth1
[edit service nat rule 1]
root@R1# set protocols all
[edit service nat rule 1]
root@R1# set source network 10.0.0.0/24
[edit service nat rule 1]
root@R1# set destination network 0.0.0.0/0
[edit service nat rule 1]
root@R1# top
[edit]

```
```

## //routes ssh traffic away from the router to a machine on your internal network
root@R1# create service nat rule 2
[edit]
root@R1# edit service nat rule 2
[edit service nat rule 2]
root@R1# set type destination
[edit service nat rule 2]
root@R1# set translation-type static
[edit service nat rule 2]
root@R1# set inbound-interface eth1
[edit service nat rule 2]
root@R1# set protocols tcp
[edit service nat rule 2]
root@R1# set source network 0.0.0.0/0
[edit service nat rule 2]
## //your public IP address
root@R1# set destination address 99.99.99.43  
[edit service nat rule 2]
root@R1# set destination port-name ssh
[edit service nat rule 2]
## //Internal machine with sshd installed and running
root@R1# set inside-address address 10.0.0.2   
[edit service nat rule 2]
root@R1# top
[edit service nat rule 2]
root@R1# commit
OK
[edit]

```
That's it really... you should now be able to pull the plug from your current router, plug it into the open eth1 interface on your server, and you'll have internet shortly after a power cycle of your cable/dsl modem.

This is REALLY just a very basic walkthrough to get you on the internet with this outstanding OSS Router.  There are MANY more features available for use in larger networks, and even for home networks where security is paramount.  Everything is available in this router package.  You can find all of the configuration guides at [www.vyatta.com]("http://www.vyatta.com/documentation") and do so much more than I have outlined here.  My next step is installing dhcp3-client in Vyatta so you don't have to spoof your MAC Address and set a static IP on the WAN side.

***Do use this guide at your own risk.  I am by all accounts, a n00b, and should not be trusted to give you good, or even acceptible data in any of my posts.  Support is available through the Vyatta website, #vmware freenode channel, and hopefully myself.***

---

