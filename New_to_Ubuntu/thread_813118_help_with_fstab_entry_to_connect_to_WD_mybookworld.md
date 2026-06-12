---
title: "help with fstab entry to connect to WD mybookworld"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by wangvs80 on 2008-05-30
Could someone please share the string you used in your fstab to map to the Mybookworld? I have tried many fstab entries in both upper and lower case. My current is '//mybookworld/public /media/mountname ntfs defaults 0 0' I already mkdir a mountname directory. The error message when I do 'mount -a' is 'ntfs-3g: Failed to access volume '//mybookworld/public': No such file or directory'

I have two Vista machines that backup regularly to this device using a mapped drive over a wired lan. I can ping the device's IP address so I know I am getting to the network. ubuntu 8.04.

Thanks for any help.
wangvs80 (old school)

Prefer explicit reply from someone who has a WD mybook world NAS (not raid) device configured.  Thanks

- - -
After I downloaded the last batch of updates, the mybookword device showed up in the network places!! Do not know which update 'did it' but it works!  Thanks

---

### Post by Duck2006 on 2008-05-30
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by unutbu on 2008-05-30
I think the WD mybookworld is a samba server.
I suggest going to the [URL="https://help.ubuntu.com/community/SettingUpSamba#head-d20d5087654b50fd3da049ad849b9d3cc36e9098-2
"]Ubuntu SettingUpSamba guide[/URL]

On the right-hand table of contents, click on [chapter 3.1.2 CIFS]("https://help.ubuntu.com/community/SettingUpSamba#head-13e9ab1c815c3a2f9be9fe720b7e2be6d896014a").

 I think that will show you how to set things up.

---

### Post by JohnnyP on 2008-06-04
This is what I use.

//192.168.0.*/public /media/Public smbfs username=******,password=******,auto,user 0 0

Apols if this is Grannie & Egg Sucking but you need to replace the ***'s with your details.

One thing, if you reboot your router and suddenly the drive doesn't mount anymore, it will be because it's been allocated a different IP address.  You can avoid this by giving it a fixed one through the web page.

Best of Luck 

Johnny P

---

### Post by bjorn.aigen on 2012-05-06
Network Storage Device:
WD MyBookWorld, Model#: WD10000H1NC-00
[http://support.wdc.com/product/install.asp?groupid=117&lang=en](http://support.wdc.com/product/install.asp?groupid=117&lang=en)

Example data:
Router: 192.168.0.1
Network storage device IP: 192.168.0.100
Network storage device name: mybookworld
Mount: /media/mybookworld
Host: mybookworld

Hostname settings:
- In /etc/hosts, add the entry 
[FONT=Courier New][COLOR=Navy]192.168.0.100 mybookworld[/COLOR][/FONT]

Mounting settings:
- In /etc/fstab, add the entry:
[FONT=Courier New][COLOR=Navy]mybookworld:/public /media/mybookworld  cifs  rw,exec 0 0[/COLOR][/FONT]
(Note: I've set the options "rw,exec" but you can modify as desired.)

Reload the fstab file
[FONT=Courier New][COLOR=Navy]mount -a[/COLOR][/FONT] 

Router settings:
- Find your router IP
[FONT=Courier New][COLOR=Navy]route[/COLOR][/FONT]
- Access the router e.g. [http://192.168.0.1](http://192.168.0.1)
- Find the address of your network storage device under 'Network Settings' or similar. e.g. [http://192.168.0.100](http://192.168.0.100)
- Reserve this IP address to give it a static IP.

WD MyBookWorld Settings
These should be the default settings but you can check as follows:
- Log in to the network storage device at [http://192.168.0.100](http://192.168.0.100) where the default admin password is <blank>.  
- You can change the password in 'Advanced Mode' and select 'Admin password'.
- Add the workgroup named 'WORKGROUP' under Network->Workgroup.
- Set the device name to 'mybookworld' under 'Device Name'.
- You should see 'Public' and 'Download' under folder shares.
- To reset the device, put a pin in the reset for 4 seconds and wait 3 minutes (See p173 of the user manual).

Browser or Nautilus navigation
[FONT=Courier New][COLOR=Navy]smb://mybookworld/[/COLOR][/FONT]

Launcher:
[FONT=Courier New][COLOR=Navy]nautilus smb://mybookworld[/COLOR][/FONT]

---

### Post by oldos2er on 2012-05-06
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

