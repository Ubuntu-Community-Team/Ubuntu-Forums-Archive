---
title: "Setting up a basic lab with file and print server."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by whickey on 2008-09-17
I am a newbie who has volunteered to help a private grade school set up a computer lab. I have installed Ubuntu Hardy desktop on 2 systems (more to follow when I figure things out). I would like to set one up as a server to handle all user management and file and print services. The students will be doing basics like learning openoffice for report writing and presentations. They will be accessing the internet for research but there is no reason to go through the server for that unless there is an advantage to that.
I have no experience doing this under windows either so instructions must be very basic and not compared to windows.
I have searched the forums for server information but most of what I find is information for web servers or arguments about server verses desktop edition and the need to learn the CLI. Also arguments over using the GUI on a server because of the load. Please! I want to keep the GUI and make this easy to manage for the teachers. Will the load on a server be high enough to need to remove the GUI if I'm only providing file and print services to about 30 users at a time?
Links to a basic file server setup guide anyone?
Thanks in advance... I'm sure more questions will follow.

---

### Post by bodhi.zazen on 2008-09-17
Well, you have a few options . 

I suggest you look at Edubuntu : [http://edubuntu.org/Documentation](http://edubuntu.org/Documentation)


Or Samba : 

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

Once you decide on a protocol / setup let us know if you have questions or problems.

---

### Post by whickey on 2008-09-17
I've browsed through those documents but I'm not sure what I need to use. Will Samba allow me to manage users from the server or just make public shares from the server? I need to secure individual users' files and manage accounts centrally.

I found LDAP mentioned in another thread. Is that where I want to go?

My main goal is to set up a lab so that any user can log into any workstation and access his files and print to a common printer. We currently have all windows PCs mounting a shared drive on a windows server but there are not individual logins and users have access to each other's files. 

I don't have a powerful server so I don't think I want to use LTSP and thin clients. By the way, how can I get my system specs in Ubuntu? I don't even know my processor, memory, or disk space. I set this up on a blank, donated PC.

Thanks again.

---

### Post by bodhi.zazen on 2008-09-17
The easiest method, IMO, is to share your /home directory over nfs and use samba for a network share printer.

You can list your hardware with :

```
sudo lshw -short
```

---

### Post by whickey on 2008-09-17
With NFS, won't I still have to maintain users on each workstation individually? If not, can you provide me with a link to the proper documentation. All I'm finding about NFS is the ability to access the files, not maintain users. (Remember I'm a newbie, I have no networking experience.)

Thanks for the hardware code.

---

### Post by bodhi.zazen on 2008-09-17
no, you have NFS correct. With NFS you share /home

When users log in they then have access to a networked home directory.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by whickey on 2008-09-17
Okay, so how do I manage all users and logins from the server without having to add every user to every PC?
Sorry if I'm not explaining what I need correctly. I'm not sure on some of the terminology.

---

### Post by bodhi.zazen on 2008-09-17
You will have to follow the links I gave you. I have not done this myself.

---

### Post by donatell0 on 2009-02-05
To manage accounts, you should try to setup NIS or LDAP. These are systems to manage logins centrally. Using LDAP is recommended for secure and high volume usage, but the setup is somewhat complicated. NIS on the other hand is much easier to configure.

---

### Post by haddog on 2009-02-15
Whickey. Have you though about using Ubuntu LTSP?

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

I'm current using Ubuntu Hardy 8.04 alternate CD. It comes with LTSP.  Had issues trying to use 8.10. Plus 8.04 has LTS (Long Term Suport) It works out of the box. Use the search function in forums and search for haddog.

Check out my post regarding LTSP Server with WIFI Internet. That will give you an idea of what I am doing. All I have to manage with LTSP is the server and not the workstations. I actually have 5 thin clients plus the server up and running now.

LTSP is pretty simple to setup once you've done it a couple of times. Took me a day or so installing, reading info on the net to get where I think I know what the heck I am doing. I wouldn't say I'm a linux beginner or novice but I am by no means an expert nor do I play one on TV!

---

