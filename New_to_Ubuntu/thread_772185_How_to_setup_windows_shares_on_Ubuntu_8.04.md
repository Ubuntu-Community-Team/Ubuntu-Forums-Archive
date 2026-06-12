---
title: "How to setup windows shares on Ubuntu 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by drbk563 on 2008-04-28
How do I setup windows shares on Ubuntu 8.04? I have been trying to see my network drives that exist on a Windows XP computer. I already installed samba on my Ubuntu computer.

Thank You

---

### Post by hammad1337 on 2008-04-28
in terminal:
```
 sudo apt-get install samba 
```

this will install a GUI for setting up samba/windows shares/users on your pc.

To view windows/samba shares, type:
```
 smb://ip.of.share.computer/ 
```
in address bar of any nautilus file manager window and it will show you those shares.

Hope this helps.

BTW, there are already threads with similar problems, so please take time to search before creating a new thread. :)

---

### Post by Michael.Godawski on 2008-04-28
Also always have a look at the official community guides at
[http://www.help.ubuntu.com/community](http://www.help.ubuntu.com/community)
Samba:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29)

---

### Post by Raistlinbuntu on 2008-04-28
> **drbk563 said:**
> How do I setup windows shares on Ubuntu 8.04? I have been trying to see my network drives that exist on a Windows XP computer. I already installed samba on my Ubuntu computer.

Thank You

Upgrading from 7.10 to 8.04 the system uninstall the smbfs support.
You have to reinstall it

 sudo apt-get install smbfs

---

### Post by Yulquen on 2008-04-28
> **drbk563 said:**
> How do I setup windows shares on Ubuntu 8.04? I have been trying to see my network drives that exist on a Windows XP computer. I already installed samba on my Ubuntu computer.

Thank You


I just installed ubuntu 8.04.
I discovered that there are no menu options to create and 
manage local file shares.I tried the command lines mentioned here,but where is this so called samba gui? nowhere.

until real user-friendly file-sharing administration is built 
in, I consider Ubuntu a disaster for new users.having to lurk around forums and playing with the console to do such trivial stuff is really pointless.

---

### Post by A$h X on 2008-04-28
I like how everyone has told you to install samba in order to solve your problem. Just like how samba has NOTHING to do with your problem, all samba does is allow WINDOWS to see your shared ubuntu folders. 

Let's try and sort you out:

Click on the network icon (two monitors) and click on manual configuration.
There enter your password and click on your connection details.

Change it to a static IP, and enter your IP and subnet (usually 255.255.255.0) and gateway (router) IP. 

Next click on the general tab and enter your machine's hostname and in domain, enter the name of your windows network. 

Then click on the hosts tab, and click on add. Enter your machine's IP followed by your hostname fololwed by a dot and the name of your windows network. For example:

> 123.456.78.90 hostname.networkname

Click okay, click close, then reboot just to be sure. Then your windows machines SHOULD appear in places > network automatically. 

If you want to see your ubuntu machine in "my network places" in windows then you need to install samba.

---

### Post by drbk563 on 2008-04-29
When I do what you suggested and I try to do a sudo xxxx command I get an error. The error is "sudo: unable to resolve host xxxx". What can I do to resolve the issue?

Thank You

---

### Post by buntunub on 2008-04-29
Really not sure why all the confusion here. All you need to do is go into Places > Connect to Server. From there just click on the drop down arrow at Service Type: and choose "Windows Share", fill out the appropriate info, and voila! Other than that, you could just click on "Network", in that same Places menu and pick a server from there and it will auto mount.

---

### Post by buntunub on 2008-04-29
> **Yulquen said:**
> I just installed ubuntu 8.04.
I discovered that there are no menu options to create and 
manage local file shares.I tried the command lines mentioned here,but where is this so called samba gui? nowhere.

until real user-friendly file-sharing administration is built 
in, I consider Ubuntu a disaster for new users.having to lurk around forums and playing with the console to do such trivial stuff is really pointless.

Just because you might not have the patience to play around with some of the new system settings, does NOT mean it is not user friendly. It is just not user friendly for you, because you lack patience. Setting up Windows shares on Hardy has never, ever, been easier.

---

### Post by Yulquen on 2008-04-29
> **buntunub said:**
> Just because you might not have the patience to play around with some of the new system settings, does NOT mean it is not user friendly. It is just not user friendly for you, because you lack patience. Setting up Windows shares on Hardy has never, ever, been easier.


its easy to view share located on a windows computer,
but none of the replies here have said anything about
how to create LOCAL shares, that is visible on a windows computer.

i tried the sudo apt-get install samba as described above,
it installed successfully, but wheres the gui???
not in any of the menus.please enlighten me.

I generally do not lack patience, but I do not want to waste
hours trying to accomplish something that takes 5 seconds
on a different platform.

---

### Post by PokerJoker on 2008-04-29
> **buntunub said:**
> Really not sure why all the confusion here. All you need to do is go into Places > Connect to Server. From there just click on the drop down arrow at Service Type: and choose "Windows Share", fill out the appropriate info, and voila! Other than that, you could just click on "Network", in that same Places menu and pick a server from there and it will auto mount.

Lovely, but something must be wrong in Hardy. I have a Gutsy server running as fileserver, set up samba. My XP-notebook, after setting up the networkdrives once ages ago, keeps seeing the shares no problem. After upgrading my dekstop from gutsy to hardy-beta it lost the shares. It can't find my windows workgroup, no matter which tool i use. Networkplaces finds "Windows network", but when opening/clicking icon nothing shows, where in gutsy it showed my windows workgroup.

smbclient only lists shares when using ip-address instead of servername, still i can't connect even when using mount on cli. (need to look up the different errors/warnings i get on my desktop when i get home, server doenst show errors in smbd or nmbd logs)
A long time cli freak, i've gone and went lazy with ubuntu :lolflag:

---

### Post by drsox1899 on 2008-04-29
I agree with the last post.  Something has happened in 8.04 that is different to 7.10 wrt Samba etc.

I have a Server with a number of shares, shared through Samba.  On my 7.10 PC I can connect to all of them.  On my 8.04 experimental PC I can connect to those without passwords but NOT to those with passwords.

I've followed the Stormbringer HowTo at : [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) in both cases, plus installing smbfs in case I missed something.

What's changed in 8.04 ?

UPDATE : I also can't see the 8.04PC from the 7.10PC, but I can see the 7.10PC from the 8.04PC

---

### Post by A$h X on 2008-04-29
> **drbk563 said:**
> When I do what you suggested and I try to do a sudo xxxx command I get an error. The error is "sudo: unable to resolve host xxxx". What can I do to resolve the issue?

Thank You

See here: [http://ubuntuforums.org/showthread.php?t=772617](http://ubuntuforums.org/showthread.php?t=772617)

---

### Post by dccrens on 2008-04-29
Seems like something related to Samba is broke in Hardy. I have a Gutsy desktop that I set up and I can see my shares from a windows box no problem. I can also see shares from the Gutsy box when I am on the windows xp box. I also have a Gutsy laptop that was setup and working the same way. I upgraded only the laptop to Hardy. All looked like it went smoothly. But, now I can no longer see any shares from the laptop. I have reinstalled and reconfigured Samba on the laptop including fixing the "hostname/hosts" issue. Still no luck. Anyone have samba working in Hardy? What am I missing?

---

### Post by drsox1899 on 2008-04-29
> **A$h X said:**
> See here: [http://ubuntuforums.org/showthread.php?t=772617](http://ubuntuforums.org/showthread.php?t=772617)

Seems like a good idea, but I seem to have an empty file for nano etc/hosts.

What else should I be doing ?

Thanks

On looking at this a second time it seems to refer to another issue ?  Am I correct ?

---

### Post by buntunub on 2008-04-29
I did notice a strange bug with /etc/hosts on the one system I did a strait upgrade on (there were no problems at all on my fresh install boxes). It attached my domain on to the end of my user account - Username.domain - like so, which created havoc with ownerships such that I was unable to do anything system level related. Fixing that was cake (remove the .domain), and after that, I simply did a sudo /etc/init.d/samba restart, and off to the races from there! All my Windows boxes (XP and Vista) have no trouble whatever mounting smb shares off my Linux machines, and my Linux machines have no trouble whatever mounting shares off my Windows machines.

There was indeed some big changes in Hardy with how Networking is setup. Not with the file systems, but with the layouts. I think they put heavier emphasis on FUSE or something like that, but Samba is much tighter integrated now into the core of the OS. There was no more "Shared Folders" GUI in System Admin, I think because they figured there was no more need for it since Samba is now much more tightly bound to Hardy, seems to me anyway.

---

### Post by drsox1899 on 2008-04-29
> **buntunub said:**
>  I simply did a sudo /etc/init.d/samba restart, and off to the races from there! 

I did that on my 7.10 PC and now I can access my 8.04 PC - so thanks.
I still can't access my protected server shares from 8.04 !

---

### Post by ivze on 2008-04-29
Well, creating a share is simple.
I am using a freshly-installed 8.04.
1. Find a folder you wish to share.
2. Right-click on it-> press 4-th item from the bottom (somethhing like "common access", don't know, because i have a ru-localized version).
You will see a nice gui. It will, probably, ask you to install samba. Do it.
3. Now, there is a little bug to overcome. You will need to reboot after installing samba. (Seems, that it is caused by some access right trouble with sambashare group). 
4. Now, open the same gui, configure the share.

For me, this works fine. Sure, for you it will do so. =)

---

### Post by drsox1899 on 2008-04-29
> **ivze said:**
> Well, creating a share is simple.
I am using a freshly-installed 8.04.
1. Find a folder you wish to share.
2. Right-click on it-> press 4-th item from the bottom (somethhing like "common access", don't know, because i have a ru-localized version).
You will see a nice gui. It will, probably, ask you to install samba. Do it.
3. Now, there is a little bug to overcome. You will need to reboot after installing samba. (Seems, that it is caused by some access right trouble with sambashare group). 
4. Now, open the same gui, configure the share.

For me, this works fine. Sure, for you it will do so. =)

If you are referring to my problems - the shares I want to access are on a NAS box running UNIX and sharing through SAMBA.  Can't get the same access.

Also, just to test, I Right-Clicked on a local folder and can't see the "Common Access".

The Options are : (top to bottom)

Open
Open in New Window
Open with Other Application
Cut
Copy
Paste into Folder (greyed out)
Make Link
Rename
Move To Trash
Send to
Create Archive
Encypt
Sign
Sharing Options
Properties

Folder Sharing opens a routine sort of dialogue.

I'm already in the sambashare group

---

### Post by buntunub on 2008-04-29
Your running Unix on the NAS, so why not just use ssh, fuse, or nfs? ssh works fine on Windows too and is a cinch to setup. I dont run a NAS with UNIX file sharing with Samba so I cant test setups, but Hardy's built in file sharing systems ~should~ work fine. My suggestion though is that you file a bug on this to the Ubuntu Bugzilla and follow this up there so that, if there really is a bug, it can be chased down there with a developer and fixed.

---

### Post by drbk563 on 2008-04-30
The suggesting of just going to the "Connect Server" section and filling the proper information does not even help. I also tried the "Network" section and that does not work either. I get an error message which is : "Couldn't display "network:///". Whatelse do I need to do. I cannot see my windows machine.

---

### Post by NickelGuy on 2008-04-30
> I get an error message which is : "Couldn't display "network:///"

Same problem here

---

### Post by NickelGuy on 2008-05-01
Nevermind installing the "samba" package resolved the problem.

---

### Post by drbk563 on 2008-05-01
I reinstalled samba, and I still cannot see my windows xp share drive. I also removed the domain from the network section. Is there something which I have to do the the smb.conf file?

Thank You

---

### Post by drbk563 on 2008-05-01
ok. I finally got it working by adding again the domain under system -- administration -- network. However, if I try to do sudo xxxx. I get an error message back "sudo: unable to resolve host victor-laptop". How can I correct this? Also if I restart ubuntu I lose the domain name config from the network section.

Thank You

---

### Post by Saabuntu on 2008-05-01
Newbie question here....

How do you mount a samba share from your Windows box?  I have a share with all my MP3's on my XP box but I want to play them in Amarok on my Laptop.  I connect to the share just fine but how do I mount it to my Ubuntu box so I can add it to Amaroks catalog??





> **buntunub said:**
> I did notice a strange bug with /etc/hosts on the one system I did a strait upgrade on (there were no problems at all on my fresh install boxes). It attached my domain on to the end of my user account - Username.domain - like so, which created havoc with ownerships such that I was unable to do anything system level related. Fixing that was cake (remove the .domain), and after that, I simply did a sudo /etc/init.d/samba restart, and off to the races from there! All my Windows boxes (XP and Vista) have no trouble whatever mounting smb shares off my Linux machines, and my Linux machines have no trouble whatever mounting shares off my Windows machines.

There was indeed some big changes in Hardy with how Networking is setup. Not with the file systems, but with the layouts. I think they put heavier emphasis on FUSE or something like that, but Samba is much tighter integrated now into the core of the OS. There was no more "Shared Folders" GUI in System Admin, I think because they figured there was no more need for it since Samba is now much more tightly bound to Hardy, seems to me anyway.

---

### Post by smokey_58au on 2008-05-01
> **buntunub said:**
> Really not sure why all the confusion here. All you need to do is go into Places > Connect to Server. From there just click on the drop down arrow at Service Type: and choose "Windows Share", fill out the appropriate info, and voila! Other than that, you could just click on "Network", in that same Places menu and pick a server from there and it will auto mount.
Thanks heaps.  This fixed my problem and was much easier than I was trying to make it seem.  Now to get my XP laptop to open (it sees it ok) my Ubuntu share!

---

### Post by John_T on 2008-05-30
I have similar problems to those described by a couple of other users.  My problems began after an in place upgrade from 7.10 to 8.04

I can no longer browse my network shares.  The shares are on another Ubuntu machine.  Other machines (still running 7.10 and Windows) can still browse the shares as always, only the upgraded machine has issues.

When I got to network places, the appropriate machine shows up in the Nautlus window.  I double click the machine icon and the various shares appear.  However, when I double click on a share, instead of browsing the share, I get a dialog like this:

[IMG]http://img401.imageshack.us/img401/1280/01openingourmusicvl2.png[/IMG]

("ourmusic" is the name of the share in this instance)
It eventually times out and says:

[IMG]http://img266.imageshack.us/img266/9452/02couldntopenen3.png[/IMG]

It also adds an icon to the desktop, as for a portable device mount.

Things I have tried:
Reinstalling samba
Reinstalling smbfs
Updating the domain in network settings
rebooting

Any ideas would be much appreciated.

Edit: I just tried browsing by IP address instead of host name, and that seems to work properly.  This rings a bell, I think it may be something to do with smb.conf I opted to keep my samba.conf during the upgrade, maybe that's where I'll look next.

---

### Post by jbailey22 on 2008-06-13
We have a Network drive that is ntfs and we can connect to it, read files and pull files from it, but when it comes to writing to the drive we can't do it. Here is the command I used to mount it: 

smbmount //servername/sharename /localmnt -o username=userid,password=passwd

Any thoughts on what we can do? Thanks.

---

### Post by anton on 2008-06-13
Anybody having difficulty accessing their Windows shared folders from Ubuntu 8.04 should take note of this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

### Post by jbailey22 on 2008-06-13
Thanks for the bugreport link. So my question is, is there a clean cut way to get write access now, without having to do any hack patches?

---

### Post by anton on 2008-06-13
You should be able to access the shares by entering the complete path (e.g. smb://server/share) in the address bar.  Alternatively, open a KDE session (if you have KDE installed) - it's only the Nautilus browser that's affected by the bug.

---

### Post by mrcanard on 2008-07-05
> **A$h X said:**
> I like how everyone has told you to install samba in order to solve your problem. Just like how samba has NOTHING to do with your problem, all samba does is allow WINDOWS to see your shared ubuntu folders. 

Let's try and sort you out:

Click on the network icon (two monitors) and click on manual configuration.
There enter your password and click on your connection details.



Thanks for the hint.
For whatever reason (maybe a recent update) my wired network connections were changed to roaming.
After changing them back I can see and interface with my DS-106 NAS again.

---

### Post by hortimech on 2008-07-07
Can I throw my thoughts on this in to the discussion? I just installed Ubuntu-server 8.04 on my server and installed and setup samba on it.
No matter what I tried, I could not connect from my laptop running 8.04, I even tried from a terminal, no success, just got this "mount error 13 = Permission denied". After much googling, without success, I had a thought, can I connect from windows? The answer was NO, so I again did a bit of thinking, the thought I got was 'firewall?', but I had not installed a firewall but a search of synaptic showed that the installation process had. Removed the firewall from the server and the XP client connected straight away, aha progress.
Still could not connect from  8.04, either from nautilus or a terminal, removed the firewall from the 8.04 laptop and entered this in a terminal:

sudo mount.cifs //192.168.0.10/data /mnt/data cifs user=root
got asked for the root password and entered this and I was in:)

I then unmounted the share and tried again with a normal user:

sudo mount.cifs //192.168.0.10/data /mnt/data cifs user=username
[sudo] password for username: 
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

As you can see no go as a normal user, I still cannot connect from nautilus, my thoughts are the connection MUST be done as root and as a normal installation doesn't have a root user, you cannot connect.

Anybody have any ideas how to fix it fully?

---

### Post by astralliquid on 2008-07-08
Hello.. i knew nothing about linux and this is my first post here. Unbuntu 8.04 is my first truly usable linux. Just sharing my experience connecting to my windows to unbuntu and vice-versa from a non-techie point of view.

1) installed fresh unbuntu 8.04
2) googled around to find my nvidia driver and found this
(Takes about an hour here)
[LIST]
[*]open Applications->Assesories->Terminal
[*]type sudo apt-get update
[*]type sudo apt-get install nvidia-glx
[*]type sudo apt-get upgrade
[/LIST]
3) Install the nvidia driver, rebooted and got my laptop running with nice 1024 resolution

4) Applications->Add/Remove
5) Searched for "Samba" and installed "Samba, create, modify and delete Samba Shares
6) System->Administration->Network->General Tab and give the same domain name as my windows workgroup
7) System->Administration->Samba and Add Share
8) My windows machine can see my linux folder and files!

9) Places->Home Folder and click on Network Servers, I can see my windows machines
10) Double clicked on a window pc, 
11) The location shows smb://windowsservername/ but cannot see the share folders
12) Add folder name smb://windowsservername/thesharedfoldername, press enter
13) My linux can see my windows folder and files!

I am not sure what your problems are but I am contented with this setup. I listed a few extra steps not related to windows share because i do not know if those steps made it different for my experience.

I might have also missed a few steps but I will be doing the exact same thing on another pc. Will update the steps if there are any request. If not, hope this helped.

---

### Post by Paddy Landau on 2008-07-08
> **Yulquen said:**
> wheres the gui?

[LIST=1]
[*] System -> Administration -> Synaptic Package Manager
[*] Search for system-config-samba
[*] Install.
[/LIST]
 Now:
System -> Administration -> Samba

---

### Post by hortimech on 2008-07-09
After much googling I found the the thing that allows nautilus to connect to smb shares is a program called gnome-vfs. Could not find this in synaptic, but did find gvfs, gvfs-backends, gvfs-bin and gvfs-fuse. All of these were installed apart from gvfs-bin, this is the binaries for gvfs. I installed this and nautilus now seems to work. I can browse my windows network, I am not saying this is the cure, but it might be worth trying.

---

### Post by JeremiahC on 2008-12-31
Extremely old post, but I'd like to share what worked for me. I'm using Ubuntu Intrepid 8.10, and was also receiving permission errors. 

What I had to do was go to System->Administration->Users and Groups, and create a user with the same UN/PW as the windows system that I wanted to have access, I also made sure to add that user my my user group, and I had previously edited that user group to have access to mount/umount.

Next i went to samba System->Administration->Samba select the share and click properties or double click, then go to the users tab and check the box next to the user you just made. 

Make sure that you have added any firewall exceptions necessary.

Finally I went and edited my fstab to show the ip address of the windows computer, and netbios name resolution was extremely slow for some reason. Ex: //192.168.1.102/D /media/heather cifs username=USERNAME,password=PASSWORD,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

---

