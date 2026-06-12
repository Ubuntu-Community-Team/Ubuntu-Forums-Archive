---
title: "How to set up the server?!"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by sepids on 2012-11-10
Hi,
I'm very new to Linux and am going to do my first Ubuntu Server installation. I'm doing this for a work related project and is very important for me to get it right.

I'm currently running a Windows 7, 64 bit on my machine. I have 6 GB of RAM and Intel(R)Core(TM)i5-2300 CPU@ 2.80GHz 2.80GHz. 

What I have to do is:
1. Install a Linux Operating system without a GUI (no Xorg)
2. Install 9 programs in this environment. These programs are created by my company and while installing them a PostgreSQL database server will be installed and for the application server the default installation process will use the default Tomcat or Jetty server provided with each application
3. When the installation is done,  I have to put Apache in front of the tomcat containers such that:
localhost/ goes to first program
localhost/wiki goes to Second Program
localhost/source goes to Third Program
localhost/builds goes to Fourth Program
localhost/webdav goes to a webdav partition ( provided by apache module )

( any host name will do- localhost, something.localhost, somethingelse.com )

My questions are:
1. Based on what I explained above about my project, should I choose LAMP Server in the installation process or no?
2. I want to install Ubuntu alongside my Windows 7. I think a VM will make it a lot more complicated for me. So, which one of these should I choose when running the install:

1)Guided-Use entire disk
2)Guided-Use entire disk and set up LVM
3)Guided-Use entire disk and set up encrypted LVM
4)Manual

I appreciate your help in advance.

---

### Post by drdos2006 on 2012-11-10
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to your servers IP address to edit files, create shares, startup daemons etc..

regards

---

### Post by Gone fishing on 2012-11-10
+1 for Webmin 

However, to answer your other question you would need to manually partition and create at least 2 partions 1 for root and 1 for swap. I can't help thinking this is a mistake as you wont be able to use Windows and the server at the same time. I would suggest you need a dedicated box for the server and I'd go for a mirrored raid setup as it will be on all the time? Unless this is just an initial experiment.

I found this site [http://www.server-world.info/en/note?os=Ubuntu_12.04&p=install](http://www.server-world.info/en/note?os=Ubuntu_12.04&p=install) very useful when setting up a Centos server recently and I notice they also do Ubuntu.

---

### Post by Mopar1973Man on 2012-11-10
I also agree Webmin is the way to go with configuring your web server.

But I would download Webmin 1.600 which is out.
[http://www.webmin.com/](http://www.webmin.com/)

As for installing the LAMP server setup here is what I used.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Beyond that in tweaks and tuning I'm still green but maybe with the two links it might provide some help. I'm using mine as a standalone workbench for web site design.

---

### Post by sepids on 2012-11-11
Thank you all so much.

I think I made a successful installation.
I did one install to test how it looks like and the second install to keep working on!
Now, I want to install jdk-7u9 and when I type sudo apt-get install python-software-properties it can't find the repository!? How can I install it?
Also, how can I navigate to my external hard drive from the command line? I downloaded and copied the file to my drive on another computer but don't know how to access that file! ((
Thank you for your help!

---

### Post by sandyd on 2012-11-11
Run
```

sudo apt-get update
```
before a fist intall


To mount the disk, run
```

sudo fdisk -l
```
which will list all your partitions and disks.

The output will be something like
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa1441aae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   608380927   304087040    7  HPFS/NTFS/exFAT
/dev/sda3       608380928   610478079     1048576   83  Linux
/dev/sda4       610480126  1250262221   319891048    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       610480128   627257343     8388608   82  Linux swap / Solaris
/dev/sda6       627259392   934459391   153600000   83  Linux
/dev/sda7       934461440  1250262221   157900391   83  Linux

```
I don't have a USB drive or anything plugged in, but if there is, there should be another section, begining with
```

Disk /dev/sdx
```
where 'x' can be a letter.

The partitions are listed as ```

/dev/sdxy
``` and are under the line that starts with 'Device'
Where 'y' is the number of the partition.

Now, for example, if your external hard disk partition was /dev/sdb1, and you want it to be mounted to the /media/exthdd folder (has to exist), run
```

sudo mount /dev/sdb1 /media/exthdd

```

Note that sometimes, mount has a hard time determining the file system on the partition - you will have to specifiy it manually.

i.e.
```

sudo mount -t ntfs-3g /dev/sdb1 /media/exthdd
```

---

### Post by Mopar1973Man on 2012-11-11
> **sepids said:**
> Thank you all so much.

I think I made a successful installation.
I did one install to test how it looks like and the second install to keep working on!
**Now, I want to install jdk-7u9** and when I type sudo apt-get install python-software-properties it can't find the repository!? How can I install it?
Also, how can I navigate to my external hard drive from the command line? I downloaded and copied the file to my drive on another computer but don't know how to access that file! ((
Thank you for your help!

Here is the Java install method I used.
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

