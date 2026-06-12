---
title: "[SOLVED] I need help installing a program"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Hoonakwa on 2008-08-31
Hi,
 New user and I need help installing a program called Zone minder. I downloaded the file zoneminder_1.23.3-2_1386.deb. I have no clue what to do with it. I extracted the file to my desktop, but I cant find the install icon anywhere. I probley am looking for something that isnt in linux only a windo$ type file. Any help would be appreciated. I would love to get this prg. working on my system.

---

### Post by Gone fishing on 2008-08-31
In general install using apt or synaptic. 

System > Administration > Synaptic Package Manager

If you enable the repositories (tick boxes) and search for zoneminder Synaptic will download and install.

If you have downloaded the .deb file right click and select Open with GDebi Package Manager.

---

### Post by original_jamingrit on 2008-08-31
If it's a .deb file that you don't see in the repositories, then just go ahead and double-click on it.

It should tell you whether or not it requires you to install any additional required applications, and might do that for you.

But as gone fishing says above me, check the repositories first, since it is better to download programs through there rather than websites.

---

### Post by Sef on 2008-08-31
> But as gone fishing says above me, check the repositories first, since it is better to download programs through there rather than websites.

Sometimes the repositories have an older version that does not have a feature needed or a bug that has been fixed in a later version.

---

### Post by jemate18 on 2008-08-31
> **Hoonakwa said:**
> Hi,
 New user and I need help installing a program called Zone minder. I downloaded the file zoneminder_1.23.3-2_1386.deb. I have no clue what to do with it. I extracted the file to my desktop, but I cant find the install icon anywhere. I probley am looking for something that isnt in linux only a windo$ type file. Any help would be appreciated. I would love to get this prg. working on my system.

To install a .deb file, you dont have to extract its contents. do this.

suppose you have the zoneminder_1.23.3-2_1386.deb on your desktop,
follow this steps.
1. Application -> Accessories -> Terminal
2. Type
```
sudo su [password]
```
3. go to your Desktop directory
```
cd /home/[name]/Desktop
```
4. Type
```
dpkg --install zoneminder_1.23.3-2_1386.deb
```
or
```
dpkg -i zoneminder_1.23.3-2_1386.deb
```

Make sure you are root to be able to run dpkg -i or --install
 
I hope this helps. Mark this thread SOLVED if you have done it and give thanks to those who helped you.

jemate18

---

### Post by gjoellee on 2008-08-31
> **Hoonakwa said:**
> Hi,
 New user and I need help installing a program called Zone minder. I downloaded the file zoneminder_1.23.3-2_1386.deb. I have no clue what to do with it. I extracted the file to my desktop, but I cant find the install icon anywhere. I probley am looking for something that isnt in linux only a windo$ type file. Any help would be appreciated. I would love to get this prg. working on my system.

when you have a .deb file just launch it and install it. Extracting it will just take more disc space:mad:

---

### Post by ashmew2 on 2008-08-31
Just double click the .deb file , and in the new window that opens click Install Package. Its simple if u try ;)

---

### Post by jemate18 on 2008-08-31
> **Hoonakwa said:**
> Hi,
 New user and I need help installing a program called Zone minder. I downloaded the file zoneminder_1.23.3-2_1386.deb. I have no clue what to do with it. I extracted the file to my desktop, but I cant find the install icon anywhere. I probley am looking for something that isnt in linux only a windo$ type file. Any help would be appreciated. I would love to get this prg. working on my system.

Did you tried my instructions in my post above?

Was it successful?

Mark this thread SOLVED if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button

jemate18

---

### Post by Hoonakwa on 2008-08-31
OUTSTANDING HELP PEOPLE.
 Just another reason LINUX and UBUNTU rules. No way anyone associated with windo$ would be that helpful. Im not shure how to mark this as solved, but it most certainly is solved. Thanks again to all who answered.

---

### Post by 7raTEYdCql on 2008-08-31
you can also use the terminal. 

```
 dpkg -i (filename).deb
```
Remember to change to the diretory where the deb is located using the cd command.

---

### Post by Hoonakwa on 2008-08-31
OK guys,
 It installed I think but I cant get the program to run. I did not install anything under my applications menu. The other programs I installed did. I can see a lot of .php files and other stuff accosiated with zoneminder but I dont know where to start the program.

---

### Post by Gone fishing on 2008-08-31
The reason I mentioned Synaptic is that the idea of repositories and downloading software in this manner is not only very convenient, it is also alien to Windows users and using apt or Synaptic is the way most of us get software.

I went for right clicking the deb file and selecting open with GDebi as it seemed likely that Hoonakwa was having the file extract rather than install on double click and this seemed easier than using the command line.

---

### Post by Gone fishing on 2008-08-31
I imagine it can be started by opening a terminal and typing zoneminder. However, In the repositories (synaptic) found:

> MythZoneMinder
view status and display footage recorded with zoneminder
MythZoneMinder interfaces with Zoneminder, a CCTV solution.
You can view the status of ZoneMinder and watch live camera shots and
recorded surveillance footage.

---

### Post by jemate18 on 2008-08-31
> **Hoonakwa said:**
> OUTSTANDING HELP PEOPLE.
 Just another reason LINUX and UBUNTU rules. No way anyone associated with windo$ would be that helpful. Im not shure how to mark this as solved, but it most certainly is solved. Thanks again to all who answered.

Check this link this will show you how to mark the thread as SOLVED
```
https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads
```

AS for saying "thanks" to the useful posts and those who help you, just click the "medal icon" right below each user's post or reply -> on the lower right.

Marking a thread as SOLVED allows other user search to be more easy and finding answers to their problems. As for the "THANKS" it usually feels better for those who helped to have an incremental or more "THANKS" status.

Cheers!

jemate18

---

