---
title: "Setting up Ftp on ubuntu 14.04"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by cranston on 2015-01-23
i am relatively new to ubuntu/linux. i am trying to setup ftp on my home network which has 2 computers,  LinuxServer, and WindowsClient.  But all I get is the message Connection timed out.

I am connected to the internet via talktalk and have amended the computer address of both computers to be static via the router page to  LinuxServer 192.168.1.11 and WindowsClient as 192.168.1.10. 

I have used nmap and it recognises that WindowsClient exists:  it returns the correct Mac Address.

Please help me

---

### Post by Derrick_Katula on 2015-01-23
i suggest u use SaMBa

SaMBa is an implementation of the SMB protocol, also called the NetBIOS or LanManager protocol. This is a networking protocol used by Windows.  It ships with most of the major Linux distributions, and is available for many different operating systems.

Getting SaMBa running was quite easy for me with the help of the [SMB HOW-TO]("http://www.tldp.org/HOWTO/SMB-HOWTO.html"), and should be equally easy for most folks, so I won&#8217;t go into too much detail. The steps are these:
 
[LIST]
[*]**Get your Ethernet configured.** (A whole separate FAQ!)

[*]**Set up TCP/IP on each of your machines.** By default MS uses their NetBEUI protocol, which Linux doesn&#8217;t understand (yet). You need to install the TCP/IP protocol for Windows (comes on the Windows CD). This is done under Network Properties in the control panel. (See Windows help for details, but I found it self explanatory.) Each machine must have an IP address assigned. All the IP&#8217;s must be on the same subnet (have the same subnet mask). You should use IP&#8217;s that have been reserved for private networks. See the [Networking HOW-TO]("http://www.tldp.org/HOWTO/Net-HOWTO/index.html") for details on this.

[*]**Make all the machines members of the same workgroup.** For the Windows machines you set the workgroup name under Network Properties in control panel. For the Linux machine, you must edit /etc/smb.conf. Make a backup of the example before editing, and change nothing but the workgroup name. The example will serve nicely for starters, and you can add shares later. Read the [SMB How-to]("http://www.tldp.org/HOWTO/SMB-HOWTO.html") for details here.

[*]Finally, you must **load the SMB daemons.** This is covered in detail in the [SMB How-to]("http://www.tldp.org/HOWTO/SMB-HOWTO.html").  Note that some Linux distributions may automatically start these daemons at startup if SaMBa is installed, so you may want to test it before doing this step.  Basically, you edit /etc/inetd.conf (make a backup!) and paste in these lines:
 # SAMBA NetBIOS services (for PC file and print sharing)
netbios-ssn stream tcp nowait root /usr/sbin/smbd smbd
netbios-ns dgram udp wait root /usr/sbin/nmbd nmbd

 
[/LIST]
 Then restart the inetd deamon or (easier) just reboot. (Note: newer distributions may use xinetd rather than inetd.) You should then be able to browse Network Neighborhood on your Windows boxes and see the Linux box there. You still need a username and password to access the Linux machine across the network. By default, Windows will send the same name you used to login to Windows, so you may need to create a new account on one machine so the user names match.

---

### Post by cranston on 2015-01-23
ok i will give ths a go and let you know

---

### Post by cranston on 2015-01-24
i have set up Samba and have can successfully share files between the 2 computers.  however, i still need to setup Ftp on the LinuxServer.  i have successfully set up ftp on Windows Client and can view file on the Linux Server

---

### Post by cranston on 2015-01-24
i have set up Samba and have can successfully share files between the 2 computers.  however, i still need to setup Ftp on the LinuxServer.  i have successfully set up ftp on Windows Client and can view file on the Linux Server

---

### Post by nerdtron on 2015-01-25
> **cranston said:**
> i have set up Samba and have can successfully share files between the 2 computers.  however, **i still need to setup Ftp on the LinuxServer.  i have successfully set up ftp on Windows Client and can view file on the Linux Server**

You can already view files of the linux server? What program are you using on windows? also, what else do you need? But do you mean you still need to setup ftp on the linux server?

---

