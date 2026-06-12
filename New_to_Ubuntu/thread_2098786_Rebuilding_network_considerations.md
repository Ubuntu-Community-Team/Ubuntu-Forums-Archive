---
title: "Rebuilding network considerations"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by john18 on 2012-12-27
Because I can no longer remember the password that encrypts the wireless  connection between my laptop and router, I am thinking of pushing the  reset on the router and rebuilding my network from scratch.  As it now  stands, this network consists of a three year old Netgear router to  which I have connected with ethernet cables a 5 year old windows desktop  with Vista, a new linux desktop with Ubuntu, a new Brother  printer/scanner and a 2 year old samsung Blueray player.  The blueray  connection is so I can stream Netflix movies into my TV.  In addition,  there is the above mentioned laptop connected wirelessly.  My end goals  are as follows:  
     1.   Ability to print from any computer.
     2.   Ability to share files between any computer.
     3.   Ability to view web content (YouTube) and personal content (photos) on TV.
                   (I believe this is beyond the capabilities of the existing  blueray player                 and that a newer model or different  approach will be needed)
     4.   Ability to operate both desktops from the laptop remotely  
More  generally, my goal is to get my computing centered around linux instead  of windows.  With this in view, I ask if a network such as I have  described is completely generic (independent of the items connected  to it) or must it be set up as a windows network or a linux network  resulting in additional configuration procedures for attachment of  incompatible components?  Any tips regarding this installation will be  appreciated.

Thanks,
John

About me: I am retired and  have built a new computer and installed linux in order to learn both the  hardware and software ends of computing.  I will be looking to find  open source replacements for Autocad and Quicken.  When and if I am  successful at this all computing will be done using Linux for reasons  both philosophic and economic.

---

### Post by Cheesehead on 2012-12-27
Are you thinking about building a new Linux-based router or server for fun?
Or are you asking for ideas on how to reconfigure your existing router?

---

### Post by CharlesA on 2012-12-27
> **Cheesehead said:**
> Are you thinking about building a new Linux-based router or server for fun?
Or are you asking for ideas on how to reconfigure your existing router?

Sounds like he wants to set up a server, but didn't really go into much detail.

TBH, it would be easier to just login to the router's web console and reset the wireless passphrase from there, instead of resetting the whole thing.

---

### Post by john18 on 2012-12-27
With respect to Cheesehead's message, if I can opt to build a linux router, does that imply that I now have a windows router?  If that is the case and the router seems to be the heart of the LAN (as is my impression) than I guess the answer to my original question is that a net work is specific to the operating system you were using when you set it up.  Is that the case?  If so, can I use the Netgear router I now have to reinstall as a linux network so long as start from the linux computer.  Finally, is this silly and in fact I should just try an connect to the network as it is?  This brings me to the Charles A comment.  Are you saying it possible to retrieve the passphrase?  Is logging into the router's web console something I do from the Netgear web site?  How will they know I am who I say I am?  Finally, is the router the server or is the server a seperate thing and if so what is its purpose?
 

 Remember, I am an absolute beginner.  If anyone can recommend some reading that would provide better understanding I would appreciate it.  This is in lieu of the thousand page book stop manuals that just give step by step procedures without any basic explanation.

---

### Post by CharlesA on 2012-12-27
> **john18 said:**
> With respect to Cheesehead's message, if I can opt to build a linux router, does that imply that I now have a windows router?

A router has it's own OS on it and it not limited to Windows or Linux.

> If that is the case and the router seems to be the heart of the LAN (as is my impression) than I guess the answer to my original question is that a net work is specific to the operating system you were using when you set it up.  Is that the case? If so, can I use the Netgear router I now have to reinstall as a linux network so long as start from the linux computer.

Not the case, any networking gear is OS independent.

> Finally, is this silly and in fact I should just try an connect to the network as it is?  This brings me to the Charles A comment.  Are you saying it possible to retrieve the passphrase?  Is logging into the router's web console something I do from the Netgear web site?  How will they know I am who I say I am?

You normally would login to the web interface on the router to do that. What model of router is it? You can find documentation for a netgear at their website: [http://www.netgear.com/](http://www.netgear.com/)

> Finally, is the router the server or is the server a seperate thing and if so what is its purpose?

A server would be a separate thing. I have a home server, myself, and it handles quite a few tasks.
 

> Remember, I am an absolute beginner.  If anyone can recommend some reading that would provide better understanding I would appreciate it.  This is in lieu of the thousand page book stop manuals that just give step by step procedures without any basic explanation.

Do you want to set up a home server to store your files and act as a print server, or do you want to get a router that you can hook a USB drive to and do it that way?

---

### Post by audiomick on 2012-12-27
> **john18 said:**
>  My end goals  are as follows:  
     1.   Ability to print from any computer.
     2.   Ability to share files between any computer.
     3.   Ability to view web content (YouTube) and personal content (photos) on TV.
(I believe this is beyond the capabilities of the existing  blueray player and that a newer model or different  approach will be needed)
     4.   Ability to operate both desktops from the laptop remotely  

Hi John.

Points 1, 2 and 4 can be realised in a windows only, a linux only and a mixed network. For point 3, you only have to have a TV that will take input from a computer. What you are after can be realised, once again, with windows or Linux.

The router, if it is properly built, is a network device that does not even know what OS is running on the computers that are connected to it. It talks ethernet protocol, which is absolutely independent of any particular OS. I personally reckon Linux machines behave better in networks, but I might be biased.

A server is a machine somewhere in the network that supplies content to other machines in the network. This can be a dedicated computer, but in your case, you could likely use one of your existing machines as a server. You only really need a dedicated machine when there is a real lot of traffic happening. For a household where one or two people want to look at a film or a few photos, the machine can most likely handle a few other tasks too. 
For what you describe, you would need a machine with an internet connection (to get the you tube stuff) on which your photos are stored and which has the TV connected to it as a monitor.

If you have a real lot of photos, you might want to think about an NAS. That means Network attached Storage, and is basically a box with several hard drives in it, a network connection, and just enough operating system to allow other machines on the network to access the drives it is administrating.
[http://en.wikipedia.org/wiki/Network-attached_storage]("http://en.wikipedia.org/wiki/Network-attached_storage")

Is the printer a network printer? It sounds like it, or it is connected to a dedicated USB printer connection on the router like mine. Either way, you can access that from windows or from Linux. It is a network resource, and is available to anything connected to the network.

It occurs to me to comment on your question about whether you have a "linux network or a windows network". You have a network. There is a Windows machine and a Linux machine in your network. The ethernet protocol is, as already mentioned, not OS specific. You choose which OS you want to run and connect the machines to your network, which will then deal with them.

This is getting long, so I will finish for now, but I will keep an eye on the thread. ;)

---

### Post by BertN45 on 2012-12-27
Whatever you do, if you need a wireless connection, you first have to set a new pass phrase for your Netgear router. How to do it you can find in the documentation of the router. It also should mention the ip address,  default user name and password to be used to log in to the router. 
In general you have to type in in the browser address line the ip address whick looks like 192.168.xxx.1 or 192.168.xxx.254. A login screen should appear now.

Only if you cannot log in this way I would reset the router, but then you have again to log in with the default user name and password. You have to find the Netgear screen, where you can choose the passprase. In general nowadays everybody is using WPA-PSK for home networks.

After this operation both windows and linux systems should be able to connect to your router and to each other again using wired or wireless network. Sharing a folder in Ubuntu is a peace of cake, you go to the folder you like to share and right click and select "sharing options" and use Windows Shares. If you want to connect to any other system (Windows or Linux), use "Connect to Server" from the file menu of the file manager Nautilus.

Keep for the ease of connecting: username, password and workgroup name the same on all systems. There is a small easy to use GUI tool to refine the share and add more users. You can find it in the Ubuntu Software Center, called Samba, a samba configuration tool to refine the access to your Windows shares.

I do not think there is a good alternative for Autocad and Quicken in Linux, but you could do what many persons are doing, install Virtualbox and run e.g. Windows XP as a Virtual Machine under Ubuntu. I have done the same to be able to run e.g. Google Sketchup. Windows 7 Ultimate had the same type of facility to run XP in a Virtual Machine. Virtualbox is more general, you can run any i386 OS from MS-DOS till Windows 8 or Ubuntu or OpenSuse etc. in a Virtual Machine.

---

### Post by audiomick on 2012-12-27
> **BertN45 said:**
> 

Keep for the ease of connecting: username, password and workgroup name the same on all systems.

Not for "ease of connecting". If there is a windows machine involved, file sharing will be via Samba. For that to work, the machines have to all be in the same workgroup.

---

### Post by BertN45 on 2012-12-27
> **audiomick said:**
> Not for "ease of connecting". If there is a windows machine involved, file sharing will be via Samba. For that to work, the machines have to all be in the same workgroup.
I heard that before and I always kept the names the same, but I already had the feeling, that it did not really matter.

Now I tried it and I can connect to a samba share with a different workgroup name. I have the feeling samba nowadays ignores the workgroup name, when connecting. In the browser it still uses the name for organizing the display.

---

### Post by audiomick on 2012-12-28
> **BertN45 said:**
> 
Now I tried it and I can connect to a samba share with a different workgroup name. I have the feeling samba nowadays ignores the workgroup name, when connecting. In the browser it still uses the name for organizing the display.

Ok, that is news to me. When I set mine up a couple of years back, it was imperative to have the same workgroup.

---

