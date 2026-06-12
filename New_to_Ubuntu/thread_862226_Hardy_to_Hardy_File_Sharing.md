---
title: "Hardy to Hardy File Sharing"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Anthony M on 2008-07-17
I have been having a heck of a time sharing files between my two computers on my wireless network.  I have read tutorials regarding Samba, but they all seem to be how to share from Ubuntu to Windows or vice versa.  

I simply need to be able to share files from one Ubuntu box to another.

Right clicking "Share Opions" in Nautilus prompted me to install Samba, so I did.  The folder is now shared but I cannot see it over the network...

Can anyone point me in the right direction?

---

### Post by chalewa on 2008-07-17
well samba will work with hardy to hardy sharing...

if you right click and hit sharing options and enable sharing and all those fun things then you should be able to see it across your network running hardy or windows.

---

### Post by Anthony M on 2008-07-17
> **chalewa said:**
> well samba will work with hardy to hardy sharing...

if you right click and hit sharing options and enable sharing and all those fun things then you should be able to see it across your network running hardy or windows.


Is there anything I need to enable on the receiving computer in order to "see" the shared folder?

Right now, when I open Places>Network I see "Windows Network", which is empty...

Thanks!

Edit: What I am trying to share is "My Music" directory.  Should it work by simply right clicking on it and sharing?

---

### Post by chalewa on 2008-07-17
> **Anthony M said:**
> Is there anything I need to enable on the receiving computer in order to "see" the shared folder?

Right now, when I open Places>Network I see "Windows Network", which is empty...

Thanks!

no, there shouldn't be anything that you need to do in order to see the shares. 

have you tried to simply restart both of the computers?

---

### Post by bodhi.zazen on 2008-07-17
See this post :

[http://ubuntuforums.org/showpost.php?p=5400935&postcount=11](http://ubuntuforums.org/showpost.php?p=5400935&postcount=11)

---

### Post by Anthony M on 2008-07-17
I dont know why, but this isnt working on my machine.  I can set the files to be shared but cannot view the over the network.  I have tried sharing to/from both the 8.04 computers and neither works.  

Yes I have rebooted. lol

Could someone tell me what specfic packages I need installed for this type of file sharing, just to be sure?

Thanks!!

---

### Post by drs305 on 2008-07-17
> **Anthony M said:**
> 
Could someone tell me what specfic packages I need installed for this type of file sharing, just to be sure?

The packages I have installed and work with the link provided by bodhi.zazen are samba, samba-common, smbclient, and smbfs. I don't know specifically if these are all required but they are currently installed on my machine and samba works without problems.

---

### Post by Anthony M on 2008-07-17
This is frustrating, I have booted into windows and it is simply point and click and be done with it.  

In Ubuntu, all I see in my "Network" folder after sharing the files is "Windows Network" which is empty.

---

### Post by drs305 on 2008-07-17
From the link provided to set up samba:
```

On the server, go to "Places -> home"
Right click on any directory (folder) DO NOT SHARE YOUR HOME DIRECTORY.
[B]From the menu select "sharing options" -> install samba from the next set of pop up menus.
[/B]Log out and back in.

```

The step in bold should create a network visible when you go to Places, Network. Your network should be named the same as the computer name. If this isn't working, you might try uninstalling samba (complete removal) and reinstalling it, then running the entire set of instructions again. It takes only a minute or two to run the entire procedure.

---

### Post by Anthony M on 2008-07-17
I have tried completely removing samba and reinstalling.  The problem  is not sharing the folder, but viewing it on the network.  Even booting the client machine into XP, I can view the shared Ubuntu folders.  But not so with the Ubuntu client.

---

### Post by septekin on 2008-07-17
Would you like to give "Share through: Unix networks (NFS)" a try?

---

### Post by Anthony M on 2008-07-19
Turns out the ONLY way I have found to view the network is with smb4k.  it is a KDE application, but works decently.  
My only gripe is that I havent yet figured out how to have it auto-moount on reboot. 
 
I dont know why Nautilus will not see my network share...

---

### Post by Bog_Warrior on 2008-07-19
I created a link to the share and saved it on the other users desktop.  I am not sure if this is the prescribed way of doing it, but it works for sharing for all users on one computer.  I have not set up my network yet, but I hope to get it going with this, and other threads.

---

