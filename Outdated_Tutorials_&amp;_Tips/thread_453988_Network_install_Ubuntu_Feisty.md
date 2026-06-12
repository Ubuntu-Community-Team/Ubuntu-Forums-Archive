---
title: "Network install Ubuntu Feisty"
date: 2007-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by andytof47 on 2007-05-25
Ok Hi, This is still fresh so here goes a little howto compiled from a few different Howto's found around town

Scenario is that you want to do 

 A) install a linux distro via the network because you can't do it any other way

B) install a linux distro via the network because you can  

or
C) you are stalking me and first want to get inside my head before waiting for three days outside of my house to abduct me, and you figure reading as much literature written by me will aid in bringing this diabolical plan to pass...:p

Whatever the Motivation here's how to install a couple of distro's over the wire

**This HOWTO IS AIMED AT NEWBIES**

A couple of things are needed first
1)[A PXE enabled system ]("http://en.wikipedia.org/wiki/Preboot_Execution_Environment")---- most systems nowadays! if you don't there are a couple of ways to acheive this but i'm not going into that here

2) A DHCP and a tftp server ------ PXE requires that the server dishes out an IP address so this is something you will need to setup

Install a tftp server so that you will be able to transfer to the PXE agent 
this is a good thing
```
apt get install tftpd-hpa
```

dhcp3 is what i've used so iwthout further rambling
```
apt-get install dhcp3
```
then
```
gedit /etc/dhcp3/dhcpd.conf
```

run ```
netstat -uap
```
and make sure you have a tftp server running
[I]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 *:tftp[/I]
make sure that you have the pxelinux.0 line in your dhcpd.conf file
```
subnet 192.168.2.0 netmask 255.255.255.0 {
        range 192.168.2.100 192.168.2.120;
       ** filename "pxelinux.0";**
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.2.255;
        option routers 192.168.2.1;

```

The file pxelinux is the file that the pxeboot agent is going to look for it rely's on a file that will be in a directory just below it called *pxelinux.cfg* this is the file to make changes to when we add a new distro.

The path that you include in the *pxelinux.cfg/default* file is relative to** /var/lib/tftpboot** keep that in mind when pointing the default file to a new linux image...

***************Important********************************
If you want to install Ubuntu from the server make sure the cd image  you use is ***[SIZE="5"]ALTERNATE[/SIZE]***
This is because it comes with it's own netboot directory and image!!!
You can download a netboot image from an online repository but it seems that this image want's to go online to look for the install files. It would be alot quicker for us to setup our files on the LAN and then install so make sure you use this image---you have been warned;)

3) make a directory in the /var/lib/tftboot/ directory called ubuntu/feisty


4) Copy the cd files into the directory
*/var/lib/tftpboot/ubuntu/feisty*

5) edit the default file so that it reads a little like this
```
DISPLAY boot.txt

DEFAULT edgy_i386_install

LABEL edgy_i386_install
kernel ubuntu/feisty/install/netboot/i386/linux
append vga=normal initrd=ubuntu/feisty/install/netboot/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw  --
```

make sure you have restarted you dhcp server
```
/etc/init.d/dhcpd stop
```
```
/etc/init.d/dhcpd start
```
I think you can just type restart there not sure i'm in Winblow$ at the moment

And make the files accessable via HTTP by setting up apache
```
apt-get install apache
```
fire up your browser and check that it's running you should see a web page telling you nothing has been added yet this is a good thing

next 
```
cd /var/www
```
```
ln -s /var/lib/tftpboot/ubuntu/feisty/ /var/www
```

Ok this works for alot of different distros 

just check out this page for another howto it's an awesome one that I learnt alot from

[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)

cheers all hope this helps

---

