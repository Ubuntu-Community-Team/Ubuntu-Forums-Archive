---
title: "Network with Windows PCs"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by burnsmicro on 2011-12-05
This seems to be another topic that has been beaten to death. Yet, here I  bring it up again. Perhaps I have run into a Ubuntu-11.10 "feature".

I installed "***system-config-samba***" (now known as Samba) through the Software Center and followed the instructions in [Connect Ubuntu 11.04 and Windows Systems via Samba–Part One]("http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/") and Two.

The  result is the Windows PCs can access each other and the Ubuntu-11 PC  without any problems, but while the Ubuntu-11 PC can see the Windows  PC's (Network -> Browse Network -> Windows Network -> Workgroup  -> 2-Windows-PCs. But, when I go to open either of these PCs, I get a  pop-up: "Unable to mount location" instead of a pop-up asking for name  and password.

Any thoughts as to what I am missing?

---

### Post by gordintoronto on 2011-12-05
You might be making it too complicated. I have never installed "system-config-samba," but I routinely access shared folders on other computers.

I start the file manager ("Home Folder" in the launcher), select Browse Network, then double-click on "Windows Network," "Workgroup," the computer I want to access, then the folder. Using 11.10, I notice that I am asked for a username and password twice along the way, to get files from my wife's Windows 7 system. 

But not when I access my Ubuntu 10.10 desktop, perhaps because I set up the same username and password on all my computers.

---

### Post by mapes12 on 2011-12-06
Hi

Below is a HowTo I wrote a while ago for accessing XP. Not sure about Win 7 but some of it may be of help:-

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

### Post by burnsmicro on 2011-12-06
Thanks Goditoronto,

> **gordintoronto said:**
> I start the file manager ("Home Folder" in the launcher), select Browse Network, then double-click on "Windows Network," "Workgroup," the computer I want to access, then the folder. Using 11.10, I notice that I am asked for a username and password twice along the way, to get files from my wife's Windows 7 system.

In my dreams...

I just removed Samba from my Ubuntu-11.10 PC to "make it less complicated". 

Without Samba or CIFS, the Windows PCs can no longer see the Ubuntu-11.10 PC on the LAN, let alone access files on it. 

Interestingly, my U-11 PC can see (Browse Nework) other PCs on the LAN ..including itself. But it cannot see shared folders on any of these ..not even itself ..with or without Samba.

My sense is there are a bunch of hidden dependencies that make each U-11 PC act differently when it comes to networking. What works for you may not work for me...

---

### Post by burnsmicro on 2011-12-06
Thanks Mapes12
> **mapes12 said:**
> PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then &quot;Remove mount point after unmount&quot; = tick
- Then &quot;File Manager&quot; tab - add Nautilus

Then in the left hand pain right click the globe and select &quot;Scan&quot;

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.
    : 
If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.



Hmmmmmm... this sounds promising, but I have a long way to go.

First of all, it seems PyNeighbourhood has changed quite a bit since you used it.

I managed to mount a shared folder from an XP PC in my Home directory and, in so doing, clobbered Thunderbird. No success connecting with the Vista PC.

..And theUbu11.10 PC is not visible to the Windows PC any more.

After closing PyNeighbourhood, I cannot open it again.

This is starting to look quite worrysome.

---

### Post by burnsmicro on 2011-12-06
Hi Mapes12

> **mapes12 said:**
> If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. 
    :
If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.


Can I ask you a few questions:

[LIST=1]
[*]Could I ask you to elaborate on what you mean by "Limited Account" and "Administrator permissions"?
[*]Did you have to use another Samba or CIFS program to make your Ubu visible to the Windows machines?
[*]Do you have a network printer? How do you get it to show up in PyNeighborhood?
[*]How do you make the changes stick? That is, so you do not have to fire up PyNeighborhood after every reboot?
[/LIST]

Thanks,

RF

---

### Post by azmyth on 2011-12-06
```
[Name]
path = /to/ubuntu/share
hosts allow = 192.168.0. <- only use if you want to limit on home network
browseable = yes
guest ok = yes
read only = no
```

You can add something like this to your /etc/samba/smb.conf and then restart. Then go to Windows and add a network drive and then add \\IPofUbuntu\to\ubuntu\share

Windows will prompt for password enter it and you should see your files

---

### Post by burnsmicro on 2011-12-08
Thanks Azmyth

The Windows PC's have no problem accessing Ubu11.10 PC files.

My problem is Ubu11.10 PC cannot see the Windows PCs. 

So, I am still stuck trying to figure out how to access the Windows PCs from my Ubu11.10 PC.

I think this has to do with setting up a Samba client. But, coming from windows, the Ubu [instructions on this]("https://help.ubuntu.com/community/Samba/SambaClientGuide") are unintelligible for me.

The BAD news is the printer is attached to a Windows machine.

The other BAD news is I am no closer to solving this than I was 4 days ago.

---

### Post by mastablasta on 2011-12-09
it might be that simply a package is missing. or a share "group" is not created. i agree. it's kind of not made out of box as it should be.
 
additionally sometimes it looks like it will fail but then you wait a bit and suddenly it displays the files. kind of strange.
 
anyway system config samba is not samba. it's a samba configuration tool that can make a real mess of original samba config if you don't know what you're doing.

---

