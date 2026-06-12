---
title: "[Howto] Create a Headless VMWare 2.0.2 Server with Ubuntu Server 9.10"
date: 2010-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Thund3rstruck on 2010-04-01
**INTRODUCTION**

The following guide is a step-by-step walkthrough for creating a headless (no monitor, keyboard, mouse) VMWare Server based on Ubuntu Server 9.10 (Karmic Koala) running VMWare Server 2.0.2-203138 (i386). 

**Hardware**

*NOTE: The hardware being used for this guide is a 32-bit Dell Optiplex 760 with Intel(R) Core(TM)2 Duo CPU E8500 @ 3.16GHz and 4GB DDR2 RAM. The purpose of this hardware is to test the concept. For optimal results I recommend using an x64 computer with: 4-CPU/Core and at least 8GB of ram, though I cannot guarantee this guide will work with any configuration other than the one demonstrated.*

**Host Operating System**

For this guide I have selected to use Ubuntu Server v9.10 as the host operating system. Due to some of the troubles I encountered setting this up, it appears that Ubuntu isn't supported directly by VMWare but I decided to fight through the trouble since Debian based Linux is the only Linux I have any skill (very limited) using.



**BACKGROUND**

In my opinion, virtualization is the most profound advancement in computing technology since the birth of the hobbyist PC movement in the 1980's. Virtualization technology allows you to run complete computer systems within other computer systems for the purposes of development, testing, or proofing concepts. For old timers like me who have racks of servers and workstations and testing a new service or solution involves building out a new machine from bare metal, virtualization represents a monumental leap forward in terms of productivity and efficiency. 

Once you buy off on virtualization, you soon realize that a dedicated machine to host your virtual machines is an absolute necessity.

**Project Goals**

For this project the goal is to build a virtualization host server with the smallest footprint possible for the exclusive purpose of hosting virtual machines, either created manually with MSDN-downloaded operating system discs, pre-built windows virtual machines, or linux virtual applicances we can drag and drop onto the server. The server needs to run unattended, needs to not require a keyboard, monitor, or mouse, it needs to provde a simple way to transfer new (or existing) virtual machines to it and it needs to provide a web user interface for managing the virtual machines. 

There are a lot of VM technologies out there today but I am going to use VMWare as it is the technology certified for use on my company's enterprise and it's the industry standard. 

The reason we are building out a Linux host instead of using VMWare's free HyperVisor OS (ESXi) is because Linux supports nearly every possible system configuration where ESXi only supports a limited subset of hardware configurations.



**WALKTHROUGH**

**Step 1: Install Host OS**

[LIST]
[*]Download and burn the Ubuntu Server v9.10 ISO image: [http://www.ubuntu.com/getubuntu/download-server]("http://www.ubuntu.com/getubuntu/download-server")
[*]Boot the host machine from the CD
[*]At the welcome screen, Hit F4 and select *Minimal System Install*
[*]Follow the onscreen prompts to complete the install. Be sure not to install anything but the base system. 
[*]Do not allow automatic updates. Many updates will break VMWare server. 
[/LIST]

**Step 2: Install VIM (optional)**

*I personally prefer VIM over nano so I install vim. You can skip this if you use another text editor.*

```
sudo apt-get install vim-nox
```

**Step 3: Update Installation**

This step will make sure we are using the most up to date system. This is important because we don't want to update this server once its running. 

```

sudo apt-get update
sudo apt-get upgrade

```

**Step 4: Setup Networking**

The following step will configure the server to have a static IP address so we will always know what IP address to connect to. 

```

# Backup network settings
sudo cp /etc/network/interfaces /etc/network/interfaces.old
sudo vim /etc/network/interfaces

# Edit network config. Edit lines:
auto eth0
iface eth0 inet dhcp

# and change them to match your network:
auto eth0
iface eth0 inet static
address 192.168.2.5 # change this to your IP
netmask 255.255.255.0 # for all class 'C' subnets
gateway 192.168.2.252 # change this to your router IP
broadcast 192.168.2.255 # change this to your upper subnet range

# Save the file, and then restart networking: 
sudo /etc/init.d/networking restart

```

**Step 5: Install SSH**

The following step will configure the server to run the OpenSSH Server. This will allow us to disconnect the monitor and use remote machines to log into the Linux terminal.  

```

# Install SSH
sudo apt-get install openssh-server openssh-client

```

You'll want to go ahead and install the PuTTY SSH Client (on your windows workstations) so they can connect to the server over SSH to manage it: [http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")

*At this stage, you can disconnect and unplug your monitor. Using PuTTY from a remote machine, you can do the rest of the setup remotely. *


**Step 6: Install FTP Server**

The following step will configure the server to run the vsftpd file transfer service. Running FTP allows us to easily download and upload files (virtual machines) to and from the server.  

```

# Fetch/Install FTP daemon
sudo apt-get install vsftpd

# First, you’ll want to make a backup copy of the vsftpd.conf file:
sudo cp /etc/vsftpd.conf /etc/vsftp.conf.old

# Next, open up a text editor to make changes to the vsftpd.conf file:
sudo gedit /etc/vsftpd.conf

# Change anonymous_enable=YES To this: anonymous_enable=NO

# Uncomment/Change these settings:
anonymous_enable=NO
local_enable=YES
write_enable=YES

# Restart the vsftpd service with this command:
sudo /etc/init.d/vsftp restart

```

The configuration above will allow local user accounts to log into the server over FTP and give them access to their home directory.


**Step 7: Install Samba (Optional)**

The following step will configure the server to run the samba service. Running the samba service allows windows machines to UNC into the server using the \\ServerName\ShareName path. Samba isn't very efficient for transferring large files but its a nice feature to have for smaller files.   

```

# Fetch/Install Samba packages:
sudo apt-get install samba smbfs

# Next, configure homw shares:
sudo vim /etc/samba/smb.conf

# Change the workgroup line:
workgroup = [YourWindowsWorkgroup]

# Next, uncomment the security line and add another as follows:
security = user
username map = /etc/samba/smbusers

# Find the share definitions section and match the following:
[homes]
comment = Home Directories
browseable = yes
read only = no
create mask = 0755
directory mask = 0755

# Save the file and then set up the samba user password:
sudo smbpasswd -a <WindowsUserName>

# Create /etc/samba/smbusers mapping
sudo vim /etc/samba/smbusers

# add the username to /etc/samba/smbusers
system_username = "WindowsUserName"

# Restart the Samba service:
sudo /etc/init.d/samba restart

```

You should now be able to access access the server from your windows PC: \\ServerName\Username.


**Step 8: Install VMWare Server 2.0.2.x**

The following step will configure the server to run the VMWare server. This is the ultimate goal of the project. 

```

# Install pre-requisites
sudo apt-get install linux-headers-`uname -r` build-essential xinetd

# If previous VMWare is installed (or previous install failed) delete bad files
sudo rm -rf /usr/lib/vmware/modules/
sudo rm -rf /usr/lib/vmware/modules/binary

# Download VMWare Server tarball
http://www.vmware.com/download/server/getserver.html

# SSH, Samba, or FTP the tarball to your Linux server
\\ServerIp\UserName

# Create directory for virtual machines
mkdir ~/virtualMachines

# Move tarball into virtual machine directory
mv *.gz ~/virtualMachines

# Extract & delete tarball
cd virtualMachines
tar -xzvf VMware-server-2.0.2-203138.i386.tar.gz
rm *.gz

# Download/unpack repair script (works for VMWare Server v.2.0.1 & v2.0.2)
cd vmware-server-distrib
wget  http://www.ubuntugeek.com/images/vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz
tar -xzvf vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz
	
# Run installer perl script
# Accept all defaults, Do not run the /usr/bin/vmware-config.pl script when prompted:
sudo ./vmware-install.pl

# Run the repair script
sudo sh vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh
sudo rm -rf /usr/lib/vmware/modules/binary

# Run the config script
sudo /usr/bin/vmware-config.pl

# Accept all defaults, when prompted for an administrative user enter your user name:
# The current administrative user for VMware Server  is ''.  Would you like to specify a different administrator? [no] yes
YourLinuxAdminUserAccount

```


**Using VMWare Server**

You should now have a working VMware server running on your host. From a computer on the network, connect to it:

[https://ServerIpAddress:8333](https://ServerIpAddress:8333)

You will receive certificate errors which will require you to add the certificate and the site into the list of 'Trusted Sites'. 

Use your Linux admin account to log in.


*I have performed all these procedures twice on my tower to ensure their accuracy. I hope I can spare someone out there the pain I suffered trying to get this working correctly. *

---

### Post by hanscees on 2010-10-03
> **Thund3rstruck said:**
> **INTRODUCTION**

 **Step 8: Install VMWare Server 2.0.2.x**

The following step will configure the server to run the VMWare server. This is the ultimate goal of the project. 

[code]
# Install pre-requisites
sudo apt-get install linux-headers-`uname -r` build-essential xinetd

# If previous VMWare is installed (or previous install failed) delete bad files
sudo rm -rf /usr/lib/vmware/modules/
sudo rm -rf /usr/lib/vmware/modules/binary

# Download VMWare Server tarball
http://www.vmware.com/download/server/getserver.html

# SSH, Samba, or FTP the tarball to your Linux server
\\ServerIp\UserName

# Create directory for virtual machines
mkdir ~/virtualMachines

# Move tarball into virtual machine directory
mv *.gz ~/virtualMachines

# Extract & delete tarball
cd virtualMachines
tar -xzvf VMware-server-2.0.2-203138.i386.tar.gz
rm *.gz

# Download/unpack repair script (works for VMWare Server v.2.0.1 & v2.0.2)
cd vmware-server-distrib
wget  http://www.ubuntugeek.com/images/vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz
tar -xzvf vmware-server.2.0.1_x64-modules-2.6.30.4-fix.tgz
    
# Run installer perl script
# Accept all defaults, Do not run the /usr/bin/vmware-config.pl script when prompted:
sudo ./vmware-install.pl

# Run the repair script
sudo sh vmware-server.2.0.1_x64-modules-2.6.30.4-fix.sh
sudo rm -rf /usr/lib/vmware/modules/binary

# Run the config script
sudo /usr/bin/vmware-config.pl

# Accept all defaults, when prompted for an administrative user enter your user name:
# The current administrative user for VMware Server  is ''.  Would you like to specify a different administrator? [no] yes
</i>

Thanks, I will follow this howto. Two questions: What does the repair script do?  Why not use winscp instead of ftp and such?   Hans-Cees

---

