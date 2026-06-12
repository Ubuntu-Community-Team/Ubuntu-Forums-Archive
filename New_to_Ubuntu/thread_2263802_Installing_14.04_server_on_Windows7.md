---
title: "Installing 14.04 server on Windows7"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by Murray_Summers on 2015-02-03
I have purchased a refurbished W7 (Intel) with 1TB disk and I'd like to set it up as a dual-boot with Ubuntu. The disk is supplied with 2 partitions already on it (recovery and normal boot) and I have already shrunk the normal boot partition and added and formatted a 3rd 250GB partition for Ubuntu, Server version. What is my best way to proceed given this configuration?

---

### Post by mastablasta on 2015-02-03
how did you format the partition? it should use a Linux file system and you can't get that format in windows. 

it might be better to leave it as unformatted disk space and format it later during install. server version is command line only. you boot from install disk and then install it (follow the prompts). you can set partitions and all during install. install looks very similar to this. you get a command prompt in the end. 

I am not sure what would be the benefit of having server version installed in dual boot (servers are usually on all the time). if you want to do some testing or  to try it it out it is easier and faster to just install it in virtualbox or similar.

if you want something similar to Windows SBS (small business server) then have a look at Zentyal. you can install that server with desktop or just a webgui interface (where you control server over a browser). it is based on Ubuntu and officially supported by Canonical I believe.

---

### Post by Murray_Summers on 2015-02-03
Excellent reply and interesting questions raised - thank you. I wanted to install the server version because I intend to use the Ubuntu box primarily as an internal server for testing my PHP development work being carried out on remote LAN workstations (I would also set up Apache and MySQL, of course). Since it is just me doing the testing, I don't need scalable capabilities! Would desktop be a better choice for this application? In addition, while I am modestly comfortable with command line work, I am replacing an older box with 12.04 installed and I do like the convenience of the visual UI.

Finally, given that I have already created the partition and formatted it with NTFS, should I just remove that partition and then recreate it without formatting (i.e., as just available space)?

---

### Post by Murray_Summers on 2015-02-03
OK - so I removed the volume that Windows mounted in that partition  leaving it as empty space. The desktop installation process found that  empty space which I will use for the installation, but it's asking what  kind of file system (EXT4 is selected), what mount point to use (?) and  where to put the swap space. Can you help me with those please?

---

### Post by yancek on 2015-02-03
> but it's asking what  kind of file system (EXT4 is selected), what mount point to use (?) and  where to put the swap space

ext4 is the default on most current Linux systems, leave it.  When you have selected the unallocated space to highlight it there should be a plus sign (+) below that window, select that and you should get an Edit partition window.  Set the partiton size, check the Format box, click the down arrow to the right of the entry box to the right of Mount point and you will see a number of options.  The first would be a forward slash /, select that for the root.  Don't use the entire unallocated space for the root filesystem, leave 2-4GB or whatever you want for swap.  Same process to add it.  Doesn't really matter where you put swap in my experience as it is rarely used.

---

### Post by mastablasta on 2015-02-04
for testing and development it's faster and easier to install in virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox) . you just use server image and install to full virtualdisk

dedicate max (GB hard disk and for server 512MB ram assigned to it will be plenty). another option is to use prepare image like those on Bitnami stack or Turnkey Linux (uses Debian). then no need to install anything. just select passwords, setup the vbox to access server via browsers and you are good to go. for example LAMP stack preinstalled virtual machine: [https://bitnami.com/stack/lamp/virtual-machine](https://bitnami.com/stack/lamp/virtual-machine)

their other stacks: [https://bitnami.com/stacks](https://bitnami.com/stacks)

turnkey Linux is a bit more user friendly if you ask me, but the issue is the use Debian and have too many old applications. but sometimes they are good enough and it's fast to set it up.

dualboot means you will have either server or your windows working not both at the same time. while with virtualbox you have you own virtual server. you can open it to others in LAN. best thing about this option - save snapshot, try something break it completely, make a mess.... then select restore snapshot and you are back where you started in seconds.

---

### Post by Murray_Summers on 2015-02-04
Thanks both of you. With your help, I was able to get my 14.04 installed and operational. I know it's a cop out, but I just selected to install it ALONGSIDE W7, and everything was much simpler - installation went smoothly and it's now functional.

---

