---
title: "samba hardy heron"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by anderskitson on 2008-07-28
I was having some major issues with samba, so I reinstalled ubuntu but nothing seem to get fixed. I can share a folder, and all my windows machine can browse and see it. But when I browse in my workgroup in nautilus I can't see any of there shared folders. I also cant get my printing to work. It will browse see the correct share name of the computer and printer, but It will fail to print. Any help?

I am using a fresh install of hardy and samba, all other machines are xp home. I had this all working at one point, but I am pretty sure its on ubuntus end.

---

### Post by superprash2003 on 2008-07-28
to access windows shares, go to the terminal and type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine.To setup network printer go to system->admin->network->printing and set it up..
For Reference : [http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

---

### Post by Thelasko on 2008-07-28
Unless you are determined to configure samba through the terminal, I recommend installing the [system-config-samba]("http://packages.ubuntu.com/gutsy/admin/system-config-samba") package through synaptic.  I find it very intuitive.

A few things to keep in mind:
1.  User names and passwords in Samba are not the same as usernames and passwords for you Ubuntu system. (although you can make it that way if you like.)

2.  Do you have any firewall software installed on your Ubuntu machine?  Firewall software will make your samba shares invisible to the network if they aren't configured properly.  Also note, Firestarter has issues with Samba.  The uncomplicated firewall is more compatible.  If the command line is a bit intimidating, some kind folks created a [GUI for it]("http://gufw.tuxfamily.org/index.html").  However, the GUI is not officially supported by Ubuntu and therefore USE AT YOUR OWN RISK!

---

### Post by anderskitson on 2008-07-28
I am at work now but I will try these when I get home

---

### Post by anderskitson on 2008-07-28
> **superprash2003 said:**
> to access windows shares, go to the terminal and type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine.To setup network printer go to system->admin->network->printing and set it up..
For Reference : [http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html](http://prash-babu.blogspot.com/2008/07/how-to-connect-to-network-printer-in.html)

Hey this worked perfect, any idea why it didn't work in the nautilus graphical interface

---

### Post by anderskitson on 2008-07-28
I still cant print though, and no I have no antivirus stuff setup

---

### Post by Thelasko on 2008-07-29
> I have no antivirus stuff setup 
You want antivirus on the linux machine?

---

### Post by JoneYee on 2008-07-29
> **anderskitson said:**
> I still cant print though, and no I have no antivirus stuff setup

Make sure the printer is shared on the host (print server).  That was my oversight when I was trying to do the same.

---

### Post by anderskitson on 2008-07-29
sorry when the thelasko asked me about firewall software for some reason when i replied i wrote antivirus. Yes its shared i can print from 4 other machines in the house.

---

### Post by JoneYee on 2008-07-29
Well I went digging, this is the dock that I used to get around my printing problems.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Tteddo on 2008-07-29
> **Thelasko said:**
> 
2.  Do you have any firewall software installed on your Ubuntu machine?  Firewall software will make your samba shares invisible to the network if they aren't configured properly.  Also note, Firestarter has issues with Samba.  The uncomplicated firewall is more compatible.  If the command line is a bit intimidating, some kind folks created a [GUI for it]("http://gufw.tuxfamily.org/index.html").  However, the GUI is not officially supported by Ubuntu and therefore USE AT YOUR OWN RISK!

After I upgraded to Hardy my Samba quit sharing. I can see the shared folders from the other machines, but I get access denied. I have 2 other hardy machines that samba works fine on. I have the same smb.conf with permissions wide open too. I don't see anything resembling a firewall that was installed, but what would I look for? Could a firewall have been installed during the upgrade?

---

### Post by Thelasko on 2008-07-29
I doubt a firewall was installed during the upgrade.  Ubuntu doesn't do things like that unless you tell it to.  Since you have Ubuntu on other machines, you should be able to test it by running a portscan from one of the other machines to one of the machine in question (I think its in system>administration>network tools, you need the IP address of the problem machine).  If I remember correctly ports 137, 138, and 139 should be open for samba.  445 might be required for printing.

---

### Post by Tteddo on 2008-07-29
> **Thelasko said:**
> I doubt a firewall was installed during the upgrade.  Ubuntu doesn't do things like that unless you tell it to.  Since you have Ubuntu on other machines, you should be able to test it by running a portscan from one of the other machines to one of the machine in question (I think its in system>administration>network tools, you need the IP address of the problem machine).  If I remember correctly ports 137, 138, and 139 should be open for samba.  445 might be required for printing.

Ah hah! 137 and 138 aren't open! That explains it. They are not commented out in services, what's the config file to turn that on?

Edit: I tested another machine that is working, and it is the same though.

---

### Post by Thelasko on 2008-07-29
Sorry, I'm not a network administrator, but I think communicating with port 139 tells the machine to open ports 137 and 138.  [From wikipedia:]("http://en.wikipedia.org/wiki/NetBIOS")
> Session mode lets two computers establish a connection for a "conversation", allows larger messages to be handled, and provides error detection and recovery. In NBT, the session service runs on TCP port 139.
The fact that 139 is open suggests that a firewall isn't your problem.  Especially if the results of a port scan are the same as the results on a working computer.

Also, I should note that if all of your computers use Linux, you don't have to use samba.  Samba is only necessary for communicating with windows machines.  I think you can use cups on port 631.  It has been a while but I think you can even manage it through your browser by going to [127.0.0.1:631]("127.0.0.1:631") from the print server.(from another machine enter the IP address with :631 at the end)

I have never had two Ubuntu machines on my network, so your circumstances are new to me.

---

### Post by Tteddo on 2008-07-29
Ok, thanks for your help. I still have 1 windows machine so I need samba. I used that machine as a web server for development and am working around that while I figure it out.
It's strange because I am using the exact same configuration on all 3 machines and that one just won't play nice!

---

### Post by Efros on 2008-07-29
Samba on Hardy is transitionally broken I believe, at least within nautilus at least. I have had innumerable issues with it since installing Hardy. I have resigned my self to being unable to browse shares from nautilus and keeping a mental note of the shares I have on my different machines along with their IP numbers. Used to work pretty well under Gutsy.

---

