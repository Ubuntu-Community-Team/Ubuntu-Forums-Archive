---
title: "How-to install HP Data Protector on Ubuntu 6.06 and 7.04"
date: 2007-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by imbo on 2007-10-09
At work, we have a storagetek tape backup library and the software we use is HP Data Protector 6.0.

The Data Protector server console is call the cell manager.
To backup a server with the library, I need to install the Disk Agent client on it.

Pre-requisite:
[LIST=1]
[*]The Cell Manager need to be already installed and running
[*]You should be able to resolv the name of the Cell Manager from the Disk Agent client
[*]If you have a firewall, the port 5555 should be open
[/LIST]

For clarity and ease of understanding, I will call **ClientServer** the server were I want to install the Data Protector Disk Agent client (this is the one that will be backup by the library).
The Data Protector server console server will be call **CellManagerSrv**.

I succeeded in installing the HP Data Protector Disk Agent client onto my 32 bits Ubuntu 6.06 server, with the following steps.

First things first, open up a console on the ClientServer and let's get into "root" mode:
```
$ sudo -s
```

Type in your password.

The installation programs that come on the installation DVD are in rpm format. 
So we need to install the rpm manager with:
```
# aptitude install rpm
```

We then need to create a directory for rpm :
```
# mkdir -p /var/lib/rpm
```
then initialize a database for it:
```
# rpm --initdb
```

Great !  Next, the Disk Agent client will use inetd to listen on port 5555 and start is client.
We have to install inetd with:
```
# aptitude install netkit-inetd
```

Done !

Insert the DVD named: "*HP Data Protector Starter Pack for HP-UX, Solaris and Linux Version 6.0*" and mount it:
```
# mount /dev/cdrom /media/cdrom
```

Let's start that install, shall we ?
```
# cd /media/cdrom/LOCAL_INSTALL
# ./omnisetup.sh -server CellManagerSrv -install da

```

Here are some check points to validate your installation:

```
# tail /etc/services
```

the last two lines should read:
```
[I]
# Local services
omni  5555/tcp     # DATA-PROTECTOR[/I]

```

```
# grep omni /etc/inetd.conf

```

You should have:
```
[I]omni stream tcp nowait root /opt/omni/lbin/inet inet -log /var/opt/omni//log/inet.log
[/I]

```

You'll need to test if the new program will respond on the 5555 port.

Let's try that from the CellManagerSrv with telnet:
```
telnet ClientServer 5555
```

If you have a responce, you now may import that new server into your cell manager from the Data Protector console and you're done !

Best regards,

Imbo

---

### Post by oddworker on 2007-10-12
So far everything you described worked here. The installation of the client went smooth. But how do you perform a backup in DataProtector GUI on the cell manager?

I see the linux client, but if I create a new job for this client and run it, I get the message:

All mountpoints on host "linux" are excluded.

Nothing will be backed up.


Then the backup session fails. I tried to configure some file trees in the backup object summary, but this did not work.

Any hint?

---

### Post by imbo on 2007-10-12
In your cell manager, in the client drop down list, you want to import your Ubuntu server that as the Disk Agent installed.
I have specified the ip address of my Ubuntu server instead of the name, because my Ubuntu server was not yet included in the windows DNS.

After this, your Ubuntu server will be listed in the client list.
Now you'll be able to back it up as a client.

Your error message looks like you tried to back it up in the "share" mode (a sort of nfs or samba type) , instead of backing it up as a client.

Try that and keep me posted !

Imbo :KS

---

### Post by oddworker on 2007-10-17
The problem was that the Linux system was running inside a VServer virtualization environment. It seems that this does not work with the DataProtector Disk Agent, perhaps due to the network virtualization.

I tested the DP Disk Agent on a Debian Etch system which is running directly on hardware - and it works!

Should work on Ubuntu too because your tutorial worked also on Debian Etch ;-)

Thanks for your how-to and your answer!

---

### Post by TWGTech on 2007-11-07
This is a great how-to. Very simple to follow.

I only had one problem...I couldn't get the Starter Pack (we already have our licenses), so i downloaded all of the UX and Linux software I could find and started to run the install command against each version.

The one I found to function is - B6960-10020 - HP Data Protector for HP-UX IA-64 - Installation Server 1 of 2 (CD ISO image) from [https://h20392.www2.hp.com/portal/swdepot/try.do?productNumber=DP60SWD1](https://h20392.www2.hp.com/portal/swdepot/try.do?productNumber=DP60SWD1)

Copying it to the server and executing the install in the LOCAL_INSTALL dir had me backing up my server in 10 minutes. It even imported the server into the cell for me.

The full command I ran was - 
# sudo ./omnisetup.sh -server FQDN.of.Cell.Manager -install da

I think I am going to go one step further and will install the Installation Server so I can push from the Cell Manager.

Again, thanks for the how-to. Much appreciated.

---

### Post by jeremybrummett on 2008-03-11
Thank you for the simple instructions.  I tried these instructions on Gentoo 2007.0 and they worked great (there were some gentoo specific differences.  I had to use emerge to get the rpm utilities instead of aptitude).

The download links for the CDs in the previous post worked great for me.  I used the HPUX-IA64 CD 1 of 2.  My same exact physical CD would not work.  Both discs are apparently the same (version 6.0).

I modified my install script command to: ./omnisetup.sh

This allowed me to walk through prompts and install the disk agent and the media agent.  I then went into my cell manager and imported my gentoo system.  DataProtector has the following info for the Platform of my newly imported system:  gpl i686 linux-2.6.23-gentoo-r8 with the disk and media agents at version A 06.00.

One more thing.  This instance of Gentoo is running inside a VMWare ESX 3.0.1 server virtual machine.

---

### Post by bernieke on 2009-03-17
I also had to "apt-get install xinetd"

Otherwise it worked like a charm, many thanks!

---

### Post by nyali on 2009-04-10
Guys i want to install HP DP on ubuntu as client but my ubuntu box is kerberos authenticated how my client get kerberos tickets.

---

### Post by Cloud79 on 2009-11-20
> **oddworker said:**
> So far everything you described worked here. The installation of the client went smooth. But how do you perform a backup in DataProtector GUI on the cell manager?

I see the linux client, but if I create a new job for this client and run it, I get the message:

All mountpoints on host "linux" are excluded.

Nothing will be backed up.


Then the backup session fails. I tried to configure some file trees in the backup object summary, but this did not work.

Any hint?

I have the same problem with ubuntuserver 9.10 and dp 6.11 client. Epic fail. I haven't found a solution for this yet

---

### Post by rarendes on 2010-02-16
I've the same problem with Ubuntu 9.10 and DP 6.0

I managed to install the CORE and DA via remote-push from a Unix Installation Host through the GUI, but somehow the DA fails to work.

The CORE itself is fine, the client installs successfully and gets imported into the cell. However, I'm not able to browse the filesystems and if I start a backup, I get the well-known error 
```
"All mountpoints on host "x.y.z" are excluded."
```

The culprit seems to be either the DA, or the connection between Agents and the inet in general. Any ideas where to check...?

HP forum support is a big fail.

---

### Post by Cloud79 on 2010-02-18
> **rarendes said:**
> I've the same problem with Ubuntu 9.10 and DP 6.0

I managed to install the CORE and DA via remote-push from a Unix Installation Host through the GUI, but somehow the DA fails to work.

The CORE itself is fine, the client installs successfully and gets imported into the cell. However, I'm not able to browse the filesystems and if I start a backup, I get the well-known error 
```
"All mountpoints on host "x.y.z" are excluded."
```

The culprit seems to be either the DA, or the connection between Agents and the inet in general. Any ideas where to check...?

HP forum support is a big fail.

It seems that the problem is the Disk Agent. I have been trying to get it to work for hours. I have tried with 6.0 and 6.11 clients. I've got no hair left ;)

---

### Post by mfburgo on 2010-02-19
Question: on 9.10  when trying to do the push install I am having a problem with the rpm.  The --force-debian option.  Why we would do something to break an installation tool is beyond me but how did you accomplish the push installation on your 9.10 servers without rpm.

Or have I missed something else..


I appreciate your help in this.  On all previous version never had a problem just install rpm and xinetd and all worked fine.   I use the ssh install options for linux host and never had a problem untill they broke rpm.

Thank you...

Mark

---

### Post by rarendes on 2010-02-22
I solved that rpm problem with a shell wrapper that adds the command before. That was a requirement to get the remote push working.

However, the DA doesn't work here. I'm not deep enough into the topic yet to know how to debug that. 

Through the inet.log specified in the inetd.conf I get this line, if I try to browse with the DA:
```
Mon Feb 22 09:34:39 2010 [MY_NTUSERID.DOMAIN@cellmanager.com] : BDF

```

BDF?

---

### Post by rarendes on 2010-02-22
I'm a step further. BDF is a command that the cell manager issues to INET. It basically means "Browse Disk Filesystems" and looks for Mountpoints on the client.

This command fails for us.

You can invoke it on the cell manager:
```
Omniback/bin/omnirsh <hostname> BDF
```

On other clients, that should return the list of filesystems (as paths).

I found that on our linux system, the inet calls a hidden script to give the answer to that call. For me it is in /opt/omni/lbin and is called .util 

In the header, you can remove 2 #'s to activate debugging, it creates a /tmp/
UTIL_<hostname>_<pid>_OB2DEBUG which, at the end, executes the following command to give results:
```
/bin/df -P -t psfs -t ext2 -t SFS -t ext -t minix -t xiafs -t vmfs -t reiserfs -t ext3 -t vfat -t vxfs -t+ fs -t hsmfs -t gfs -t lustre_lite -t 1ds -t ocfs2 | awk {print $6}
```

As you can see, the script fails to recognize ext4 as a filesystem.

If you now change the following
line in .util:

```
    gpl/i386/linux)
       /bin/df -P -t psfs -t ext2 -t SFS -t ext -t minix -t xiafs -t vmfs -t reiserfs -t ext4 -t ext3 -t vfat -t vxfs -t xfs -t hsmfs -t gfs -t lustre_lite -t ocfs   -t ocfs2 2>/dev/null | sed '1d' | awk '{print $6}'
       ;;

```
(see the added -t ext4 there)

.. the browsing of the filesystem works. I need to make sure that the backup of ext4 filesystems work in general, but it looks fine so far.

Have fun.
Roland

---

### Post by Cloud79 on 2010-02-22
Thanks man! Big ups to you! Now you saved me a lot of work!


> **rarendes said:**
> I'm a step further. BDF is a command that the cell manager issues to INET. It basically means "Browse Disk Filesystems" and looks for Mountpoints on the client.

This command fails for us.

You can invoke it on the cell manager:
```
Omniback/bin/omnirsh <hostname> BDF
```

On other clients, that should return the list of filesystems (as paths).

I found that on our linux system, the inet calls a hidden script to give the answer to that call. For me it is in /opt/omni/lbin and is called .util 

In the header, you can remove 2 #'s to activate debugging, it creates a /tmp/
UTIL_<hostname>_<pid>_OB2DEBUG which, at the end, executes the following command to give results:
```
/bin/df -P -t psfs -t ext2 -t SFS -t ext -t minix -t xiafs -t vmfs -t reiserfs -t ext3 -t vfat -t vxfs -t+ fs -t hsmfs -t gfs -t lustre_lite -t 1ds -t ocfs2 | awk {print $6}
```

As you can see, the script fails to recognize ext4 as a filesystem.

If you now change the following
line in .util:

```
    gpl/i386/linux)
       /bin/df -P -t psfs -t ext2 -t SFS -t ext -t minix -t xiafs -t vmfs -t reiserfs -t ext4 -t ext3 -t vfat -t vxfs -t xfs -t hsmfs -t gfs -t lustre_lite -t ocfs   -t ocfs2 2>/dev/null | sed '1d' | awk '{print $6}'
       ;;

```
(see the added -t ext4 there)

.. the browsing of the filesystem works. I need to make sure that the backup of ext4 filesystems work in general, but it looks fine so far.

Have fun.
Roland

---

### Post by rahul.kolan on 2010-06-22
Dear Team , 

   while installing HP Data protector 6 on ubuntu 9.10 facing below problem ...

root@delft:/tmp/hp/rahul/LOCAL_INSTALL# sh omnisetup.sh

  The omnisetup.sh script didn't finish last time
  Client still has to be installed. (omnicf da)

  The omnisetup.sh script can now continue the unfinished installation
  or it can ignore the saved state and start a new one.
  If you choose to ignore, the script will erase the saved state
  and will process only the command line options
  Do you want to continue the unfinished installation? (Y/n)
n
  Ignoring saved state...

  No Data Protector/OmniBack software detected on the target system.

  Install (cc) User Interface (yes/NO/Quit)?
NO
  Install (da) Disk Agent (YES/no/Quit)?
YES
  Install (ma) Media Agent (YES/no/Quit)?
YES
  Install (sap) SAP R/3 Integration (yes/NO/Quit)?
NO
  Install (sapdb) SAP DB Integration (yes/NO/Quit)?
NO
  Install (oracle8) Oracle Integration (yes/NO/Quit)?
NO
  Install (db2) IBM DB2 Integration (yes/NO/Quit)?
NO
  Setup cannot continue, please insert the HP-UX installation CD (CD2)
  and run the installation script again, without options, it will continue.



Help in this regards will be highly appreciated.

---

### Post by Superzaffo on 2010-12-13
I already follow your step for installing the DP agent and all ok.
But the server not responding on port 5555. 
I suppose that the agent don't start .
Why ?
 
Thank you

---

