---
title: "Connectingt 2 Ubuntu Boxes Via Router?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-09
Setup - Home / Office simple network

Router - BTHomeHub with ethernet and Wifi capabilty connects out to internet via BT phone line and splitter. Those in the UK will know the configuration.

Desktop - Old PIII with 128MB RAM running 7.10 and hard wired to the router with ethernet cable.

Laptop - IBM Thinkpad T23 with PIII processor and 1GB RAM runining 7.10. Wireless connection to router.

Objective - establish file sharing between Desktop and Laptop.

I have searched the forums but cannot find an idiots guide to setting up a simple home network for the above configuration. The best I have been able to find is this:
  [https://help.ubuntu.com/community/InternetAndNetworking#head-121a173dae16b9a1bb0a3e8116f907ade85e648c](https://help.ubuntu.com/community/InternetAndNetworking#head-121a173dae16b9a1bb0a3e8116f907ade85e648c)

which is more focused on internet connection than networking.

Please could any forum member point me in the right direction please?

Thanks in advance.

Mark

---

### Post by mlentink on 2008-05-09
It's a bit unlikely that a fresh install will help the OP.

@Mapes: can your two computers 'see' each other? Can you ping one from another? If you don't know what that means, please say so, it'll makes us know where you're coming from..

---

### Post by mapes12 on 2008-05-09
Thanks folks.

Both boxes have just been re started but I'm not convinced that will solve the issue.

The router assigns class C IP addresses via DHCP with the laptop currently leased (on this session) 192.168.1.72

In a windoze world I can usually see shared folders with a hand under the folder but the GUI in Ubuntu shows nothing.

There are no longer any windoze boxes connected. The configuration is per my first post.

---

### Post by mlentink on 2008-05-09
> **mapes12 said:**
> There are no longer any windoze boxes connected. The configuration is per my first post.

OK, so...
Have you declared any folder on either machine as 'shared'?
You should be able to do so in 8.04 (hardy) by right-clicking any folder in your /home directory (i.e. a folder over which you have any jurisdiction, so to speak), and then slecting 'sharing options'

Because if you have not alreadu done so, Ubuntu will then ask you if it should install Samba for you, which is the Linux pendant of Windows file-sharing (or of coping with a lack of intelligent file-sharing as other would say (and I can't blame them). 

Edit: the last part means there's also an easy way (the right way, if you want to be religious about it) to share files. It'called NFS

---

### Post by mapes12 on 2008-05-09
Hello mlentink

Both boxes are running 7.10 as previously stated. I have run upgrades to 8.04 but have run into problems with screen resolution and sound configuration issues which for my boxes means I have to stay with 7.10 for the time being.

Therfore, I am looking for a 7.10 configuration solution if possible.

Thank you.

---

### Post by mlentink on 2008-05-09
> **mapes12 said:**
> ... 
Therfore, I am looking for a 7.10 configuration solution if possible.


Take  a look here : [http://ubuntuforums.org/showthread.php?t=193408&highlight=file+sharing](http://ubuntuforums.org/showthread.php?t=193408&highlight=file+sharing)
and here: [http://ubuntuforums.org/showthread.php?t=193408&highlight=file+sharing](http://ubuntuforums.org/showthread.php?t=193408&highlight=file+sharing)


This may be abit alien to you if you're highly accustomed to Windows-(SMB)-networking, but you&#314;l find it pretty much trouble free..

---

### Post by mapes12 on 2008-05-11
The DHCP server in the router has assigned the desktop the private address 192.168.1.66. and the laptop 192.168.1.72

I'm on the laptop and have just successfully ping the desktop. How can I "see" the folders on the desktop from here?

---

### Post by mapes12 on 2008-05-12
I've re checked everything to make sure I have done what [this guide]("https://help.ubuntu.com/7.10/internet/C/networking-shares.html") tells me to do.

Then on the laptop I go to Places>Network where I see 3 icons. One is called "Mark" and looks like a PC tower case. The second one is called "Ubuntu" and looks the same. The other is called "Windows Network" and the icon looks like a PC tower case with two client machines attached.

If I click the "Mark" icon the mouse turns to a spinning circle for a while an then a window opens reporting that the The foIder contents could not be dispalyed - Sorry, couldn't display all the contents of "Windows Network: mark".

If I click the"Ubuntu" icon I then arrive at the shared folder icon for this laptop, but the desktop shared folder is no where to be seen.

If I click the Windows Network" icon I am then presented with 3 more icons called "bt" (my router) "Home" (the name of the share) "Workgroup" (usual MS <10 client machine network.

The "bt" icon only takes me to the router "Thomson" icon which reveals nothing when clicked.

The "Home" icon takes me to the "Home" and "Ubuntu" icons as mentioned above. 

The "Workgroup" icon brings up the error window again : The folder contents could not be displayed - Sorry, couldn't display all the contents of "Windows Network: workgroup".

I think I'm getting close but can someone help me get to the bottom of this please??  ](*,)

BTW my username on both machines is mark.

---

### Post by mapes12 on 2008-05-12
I've just thought.

Do I need to change the shared folders permissions and if so what do I change??

---

### Post by mapes12 on 2008-05-12
OK I give up!

I thought Linux was supposed to be the networking defacto. But it appears nobody has a clue how to network even 2 machines over a simple home network.

What a waste of time this OS is turning out to be.............

---

### Post by mlentink on 2008-05-13
Before you draw your final conclusions, did you peruse the threads I gave? You might take a look at [this one]("https://help.ubuntu.com/community/NFSv4Howto") as well...

---

