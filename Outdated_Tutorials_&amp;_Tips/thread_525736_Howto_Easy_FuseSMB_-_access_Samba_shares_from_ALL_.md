---
title: "Howto Easy FuseSMB - access Samba shares from ALL programs. - automatic access to win"
date: 2007-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by BuffaloX on 2007-08-14
*** Based on howto by Tazix, modified for Gnome by BuffaloX ***

Tested for Ubuntu x86 6.06 and 7.04 (Gnome)
[B]
Purpose:
To easily access Samba and Windows shares from all X-programs. (Especially mediaplayers.)[/B]
[B]
1: Install samba and fusesmb from repositories:[/B]
Open Synaptic Package Manager
Install libsmbclient, samba-common, smbclient and fusesmb
[B]
2: Give root and user access to fusesmb:[/B]
Select from menu: "System->Administration->users and groups".
Now select "root" then click "properties" and tag "allow use of fusesmb"
Do the same for your user account.
[B]
3: Create a mountpoint:[/B]
In terminal write: sudo nautilus
navigate to the /media folder
create a new folder and rename it to "network" (you can call it something else if you like)
Right click the folder, and select "properties" then select "permissions", for section "group" select the group "users", for section "folder acces" select "read and write". 

**4: Make fusesmb start at boot.**
Select from menu: "system->preferences->sessions" 
Select new
Name: fusesmbnet (can be whatever)
command: fusesmb /media/network

**5: Try it out.**
Reboot to make changes take effect...
Now you (should) have automatic access to windows networks from all programs.
There may be a delay before fusesmb sees your network. So you may have to give it a couple of minutes....
Much better than Gnome way of doing it IMO.

**Rollback:**
If you don't want it anyway, its easily reversible just following the guide again, but replace install/new/create/make with delete/remove/uninstall. Except you may want to keep the samba stuff.

---

### Post by brennydoogles on 2007-08-22
I just have an empty folder with no network access. Any Ideas??

---

### Post by BuffaloX on 2007-08-23
Are you using Ubuntu with Gnome?
Did you remember point 2?
For me I had to give these rights to both root and user, otherwise it doesn't work.

Does your Windows/Samba shares work normally in Nautilus?
(Meaning are you sure you have a woking share to see.

You should see your workgroups, and be able to navigate them as easy as local drives...

---

### Post by brennydoogles on 2007-08-23
> **BuffaloX said:**
> Are you using Ubuntu with Gnome?
Did you remember point 2?
For me I had to give these rights to both root and user, otherwise it doesn't work.

Does your Windows/Samba shares work normally in Nautilus?
(Meaning are you sure you have a woking share to see.

You should see your workgroups, and be able to navigate them as easy as local drives...

Network browsing in Nautilus works fine, and I have all permissions set correctly. Here are screenshots...

---

### Post by BuffaloX on 2007-08-23
OK that looks fine.

I suppose you have a working mountpoint, and read/write permission for user.
Forgetting that gives the "empty folder" symptom.

If that is OK, you could try to check if your Samba share works with xSMBrowser.
Its available in Synaptic. :)
(Just to check if Samba shares work independent of Gnome specific features)
In xSMBrowser click on "Samba Config" to see accessible samba shares.

If both of the above are true, See if all 4 mentioned packages required are installed.

I can't think of anything else right now, so anybody please feel free to chip in. :popcorn:

---

### Post by brennydoogles on 2007-08-23
> **BuffaloX said:**
> OK that looks fine.

I suppose you have a working mountpoint, and read/write permission for user.
Forgetting that gives the "empty folder" symptom.

If that is OK, you could try to check if your Samba share works with xSMBrowser.
Its available in Synaptic. :)
(Just to check if Samba shares work independent of Gnome specific features)
In xSMBrowser click on "Samba Config" to see accessible samba shares.

If both of the above are true, See if all 4 mentioned packages required are installed.

I can't think of anything else right now, so anybody please feel free to chip in. :popcorn:

I have checked all of the above to no avail, but i did see something interesting while browsing. I created a text document in /media/network to test my write privs, and when I went to delete it I was told that I could not move it to the trash, but had to delete it straightforward. That seems very similar to how you delete something on a networked computer. How can I tell which workgroup I am a part of??

---

### Post by BuffaloX on 2007-08-23
Did xSMBrowser show any samba shares?

To see your own workgroup select from menu:
System -> administration -> shared folders.
The name of your workgrup is in: "General properties".

Note:
This does not affect your ability to browse samba shares with fusesmb.

---

### Post by brennydoogles on 2007-08-23
> **BuffaloX said:**
> Did xSMBrowser show any samba shares?

To see your own workgroup select from menu:
System -> administration -> shared folders.
The name of your workgrup is in: "General properties".

Note:
This does not affect your ability to browse samba shares with fusesmb.

Here is what I get in xsmbrowser:

Have I screwed up somewhere??

---

### Post by BuffaloX on 2007-08-23
No I don't think you screwed up.
It looks perfectly alright,
I don't know why fusesmb doesn't work for you.
I'll have to look into it more closely.

The only possible problem I can think of now, is if something in Ubuntu desktop makes fuseSMB not work correctly.

I'll try to double-check the guide on a newly installed system ASAP, but it may be a couple of days because I don't have a test system available ATM.

PS
You could try to start fusesmb in a terminal. To see if it returns anything usable.
Note that you cannot use already mounted mount-points.
So either make a new one, or disable autostart of fusesmb and reboot.

---

### Post by brennydoogles on 2007-08-23
ok, so here is the command that helped get it straightened out: ```
fusesmb /media/network/ -o nonempty
```

I don't know why, but it works now. Thanks!

---

### Post by BuffaloX on 2007-08-24
Great that it works. :)

I don't know why you need the extra parameters?
If others report similar results, I will add it to the how-to.

---

### Post by evaldas on 2007-08-25
I also had the same problem, that the folder was empty. Then I started looking for a problem, and while googled, after some time the network name appeared in the folder :) So I guess you just need to wait some time.

I have another question: how to unmount the folder?
And how to access password protected shares (like c$ or d$) with fusesmb? With smbmount (mount -t smbfs) there's no problem, I just add -o username=***,password=***. But how to do that with fusesmb?

---

### Post by brennydoogles on 2007-08-25
> **evaldas said:**
> I also had the same problem, that the folder was empty. Then I started looking for a problem, and while googled, after some time the network name appeared in the folder :) So I guess you just need to wait some time.

I have another question: how to unmount the folder?
And how to access password protected shares (like c$ or d$) with fusesmb? With smbmount (mount -t smbfs) there's no problem, I just add -o username=***,password=***. But how to do that with fusesmb?

try it in terminal with the same parameters and see if it works!! I ended up adding the required parameters to the entry in sessions, and it worked out well. Hope that helps!!

---

### Post by BuffaloX on 2007-08-26
> **evaldas said:**
> I also had the same problem, that the folder was empty. Then I started looking for a problem, and while googled, after some time the network name appeared in the folder :) So I guess you just need to wait some time.

I have another question: how to unmount the folder?
And how to access password protected shares (like c$ or d$) with fusesmb? With smbmount (mount -t smbfs) there's no problem, I just add -o username=***,password=***. But how to do that with fusesmb?

Thanx for the feedback.
I have added the possible delay to the how-to.
I remember having problems with C$ way back with Windows NT 4.0, 
So your post called back some ancient memories. :)
You could "unhide" the shares by making a new share without the $ sign added.

---

### Post by D10 on 2007-08-28
You may need to edit your fusesmb.conf file it is located in ~/.smb.

I know if I bring my xubuntu laptop to work I have to change the username and password for our doamin.

Right now I can't remeber how the file is layed out,  but the man page for fusesmb.conf has an example of a basic file. change the username to [COLOR="Red"]**"<domain or win pc name>"\username**[/COLOR] no qoutes.

Hope that helps

---

### Post by Gonkerd on 2007-09-06
Could somebody explain why the reboot is neede in step 5? Is this to get the user settings right???

---

### Post by BuffaloX on 2007-09-06
It's sufficient to just restart X.
You can even skip that, by mounting fusesmb in terminal.
But that way, you wouldn't know if you entered everything correctly for your session start.
It's simply the easiest way to check everything works, and I wanted to make this how-to as simple as possible.

---

### Post by BuffaloX on 2007-09-07
> **evaldas said:**
> 
I have another question: how to unmount the folder?
And how to access password protected shares (like c$ or d$) with fusesmb? With smbmount (mount -t smbfs) there's no problem, I just add -o username=***,password=***. But how to do that with fusesmb?

For further options type "fusesmb -h" in terminal,

unmounting,
Only way for me is to kill fusesmb.

About your problem with c$ or d$,
Did you find a solution yourself?
I don't think fusesmb supports automatic login with alternate user-name and password.

---

### Post by kakao on 2007-09-08
> **evaldas said:**
> 
I have another question: how to unmount the folder?

as with any fuse based fs: $fusermount -u mountpoint

> **evaldas said:**
> 
And how to access password protected shares (like c$ or d$) with fusesmb?

I installed the fusesmb package for feisty and it comes with man-pages for fuser.conf (do man fusesmb.conf on the command line, there are good examples at the very bottom): in your ~/.smb/fusesmb.conf file you can add something like
```

; Default username and password
[global]
username=user
password=totallysecret

```

or for certain servers or shares do:
```

; Share-/Server-specific settings
;[/SERVER/SHARE]
;[/SERVER]
username=yourusernamehere
password=totallysecret

```

Adapt to your local set-up. E.g. SERVER could be an ip like 192.168.1.23, but don't end neither SERVER nor SHARE with a slash ('/'). But keep in mind that passwords (as far as I know) are send over the samba network in naked plain text.

Hope it helps.
Cheers.

---

### Post by airflow on 2007-09-16
Hi!

First, thanks for the howto. I like this method of accessing smb-shares much more than the ubuntu-generic style (mainly because some applications can't handle this method).

Secondly, I want to add a piece of information which cost me about two hours of hassling around: Make sure that your server-name does not contain any dots (e.g. don't name your server fp.ath.cx like me). While it works with Windows-clients and also with Ubuntu's native method of accessing shares, it does not work with fusesmb.

Bye,
airflow

---

### Post by BuffaloX on 2007-09-16
@airflow
Thanks for the tip. :)

@kakao
Coming to the rescue! thank you :popcorn:

---

### Post by dysolve on 2007-09-19
thanks for the guide.. I was about to move all my mp3's to my linux box. but this saves a lot of hassle. my only problems now is I can see my shared folders on my winblows machines but I can not see any of the files in the folders.. any body have any ideas?
thanks
David.

---

### Post by airflow on 2007-09-29
Hi all,

I have another little problem with fusesmb, perhaps you can give me a
hint about it.

I tested fusesmb so far that it worked good for me. As the next step, I
wanted to add fusesmb to the auto-start programs of gnome (modify
session). When I start gnome, fusesmb is started automatically with the
same rights as before. Interestingly, when I do this, it does not work
anymore. While the detection of shares still works, it is impossible for
me to access them.

The debug-log says "Connection timed out". I couldn't see any
errormessages on the server-side.

LOOKUP /HETZENDORF/FP-ATH-CX/web
   NODEID: 8
   unique: 387, error: 0 (Success), outsize: 136
unique: 388, opcode: OPENDIR (27), nodeid: 8, insize: 48
   unique: 388, error: -110 (Connection timed out), outsize: 16

After a while of testing and playing around, I have an idea of what the
problem could be: During the start-up period of gnome, the system does
not have it's IP from the LAN. I still have to give my password for the
keyring-manager to log onto my secured wireless network. After that i
associate and get my IP. At this time, fusesmb has already been started
by gnome and perhaps listens at the "wrong IP" (I can only assume, as
the debug-output doesn't give me that info). fusesmb.cache works,
because it is restarted periodically.

I would like to have fusesmb constantly running in the background
scanning for shares and showing them to me, regardless to which networks
I'm currently connected to. Is there a possibility to achive this
(without having to stop and start the service each time I move)?

Thanks for your help,
airflow

---

### Post by phillip2 on 2007-10-29
I have the same problem -- fusesmb prints out "test", I get an empty directory and nothing else. 

xsmbrowser is working fine, nothing else. 

I had it all working fine with feisty and for sometime with gutsy. Now, nothing. 

Confusing.

---

### Post by phillip2 on 2007-10-29
Tell a lie. It just takes ages to mount. Starts working after a while.

---

### Post by foxy123 on 2007-12-19
Does anyone know if there is an option to display utf8/non-latin file and dir names?

---

### Post by peabody on 2008-01-15
> **phillip2 said:**
> Tell a lie. It just takes ages to mount. Starts working after a while.

The practicality of this software is pretty lame if it takes more than 10 minutes to get it up and running.  I've tried everything suggested in this thread, but I still can't get this to work.

**Edit: Success!  My problem was my nmbd process had died because my network connection had been brought down (i'm on a laptop, so I move from network to network).  Restarting the smb service did the trick.  It took me a while to try this because I had actually tried just 'reload'-ing it, but that apparently doesn't jump start nmbd.  fusesmb apparently needs nmbd to work.**

---

### Post by humilleitor on 2008-01-28
I had the same problem several times: randomly, I couldn't access the network shares. I got the same message: "conncection timed out". I guessed it could depend on how busy my network was, and modem. So, I tried stopping a download  that was on progress, and... there it was! That solved the problem for me.
Of course, the question is "why does fusesmb wait so little?, why is it so impatient?" That I don't know. I guess there must be some way of configuring it to wait a little bit longer in case the network is slow. Maybe somebody else can help with that.

---

### Post by coolmanlg on 2008-05-23
Thanks for the tutorial. I have installed fusesmb but I noticed that its showing just two computers on my network. Using other smb file browser, I can see the other computers. What could be wrong pls?

---

### Post by Jandark on 2008-06-29
Hi,
Sometimes I had a problem, and didn't show all client's  ! :)

---

### Post by Cushie on 2009-02-06
I have managed to get so far with setting up Samba in Xfce4-Ububtu 8.10.  I can see the other windows computer and the files therein but cannot access the files.  I have set the 'share' in windows but on my Xubuntu I cannot change the recommended settings in Apps/System/Users & Groups, the properties of /media/network file for my username read write, group read only, others read only. I can change the setting but it does not stick!

Happily from the windows computer I can see and access the files but cannot write (copy over) new files.

Would appreciate your suggestions to fix this, and a guide to affect (chmod) so that I do not get into a big mess!.

---

### Post by rapchee on 2009-03-20
i cant acces some servers - actually it seems that only windows 2003 servers. is this a bug?

---

### Post by eniacpx on 2009-03-22
I'm confused, what functionality will this add over just using the built in smb:// browsing functionality of Nautilus?

---

### Post by foxy123 on 2009-03-23
> **eniacpx said:**
> I'm confused, what functionality will this add over just using the built in smb:// browsing functionality of Nautilus?

Thunar, which is default in XFCE does not support it and to install Nautilus on Xubuntu will mean to have almost full Gnome installation, what some people would like to avoid.

---

### Post by rapchee on 2009-03-23
> **eniacpx said:**
> I'm confused, what functionality will this add over just using the built in smb:// browsing functionality of Nautilus?
with this you can browse the network as if it was part of the file system, (like /media/network/workgroups/ etc.) and thus all applications (for example the terminal) can have acces to files over samba shares. only a limited number of applications support Nautilus's way of browsing.

---

### Post by eniacpx on 2009-03-23
> **rapchee said:**
> with this you can browse the network as if it was part of the file system, (like /media/network/workgroups/ etc.) and thus all applications (for example the terminal) can have acces to files over samba shares. only a limited number of applications support Nautilus's way of browsing.

Maybe I'll give it a shot, though I just created a symlink in my home directory called "Network" that points to my ~/.gvfs directory, this gives all my apps, including the terminal, access to any share I have opened in Nautilus, though I do have to open the share in Nautilus before it will work, maybe this will save me a step.

---

