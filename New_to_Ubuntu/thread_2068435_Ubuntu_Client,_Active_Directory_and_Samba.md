---
title: "Ubuntu Client, Active Directory and Samba"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by 4th Dimension on 2012-10-09
So, I have and Windows Server serving as Active Directory and providing my Windows computers and their users with centralized authentification. I also have an FreeNAS box that serves as simple fileserver. The users use the variety of shares from that FreeNAS fileserver, all of which are protected by apropriate file right based on AD groups and users.
It provides the ability to the users to roam around computers without needing to copy files because they all are stored on central location. So allready my system is a frankenstanian amlgman of Linux, Windows and scripts.

So now I need another Linux box in order to install a software to manage our library. I succsesfully installed that software on Ubuntu 11.10.

Next I used the Winbind tutorial to succesfully join this computer to AD, so prospective librarian can use hers AD login to log in into Ubuntu. (there are still teeming dificulties with that. mostly because Ubuntu doesn't seem to know about AD untill I log one of Ubuntu users).

Now I want to make icons on dekstop that would lead the librarian to her shares on the fileserver.
I tried mounting the shares via:

mount cifs -t //fileserver/shareName /home/DomainName/userName/Desktop/Share1 -o user=username%passwd

and command in most cases works. But when I try to open that directory where I mounted the share, Ubuntu says I dont' have permisions to enter such resource.

I should note that I CAN access those shares by opening file manager (nautilus ?) and going into network places -> fileserver -> choosing the Share I want (complication is that some of the shares are hidden), or changing the adress bar to point to one of the shares.
The Nautilus would then prompt me for password (would fill in allready the username and domainname), and I would succsesfully access the share.

I would like to note that this nautilus approach would be way too finicy and complicated for our librarian, which is why I'm trying to mount the shares in folders on desktop. Or maybe put shortcuts there.

My question is basically how do I do this so it's as foolproof and simple for user?

---

### Post by newb85 on 2012-10-09
Absolute Beginners' Section?  This seems more like a Networking & Wireless question.  ;)

---

### Post by Gone fishing on 2012-10-09
I wonder if its time to do away with Windows server and run a box with ldap and samba - samba doing the windows roamings and with ladp doing the authentication both for samba and FreeNAS and linux boxes.

---

### Post by 4th Dimension on 2012-10-10
Well, as to my forum choice, it's because I'm not excatly an Linux veteran. I can usually find my way by folowing tutorials but I lack deep understanding of the platform. So when it comes to linux you need to use simple and short words with me.

As to the suggestion, I would rather my librarian uses only the authorization and has to walk to another windows box to use the fileserver, than have to reengineer my ENTIRE system and all computers from sctrach. Including rewriting all scripts in shell.

So replacing Windows Server is NOT a solution since it is esential to the operation of all other computers and their users. Not to mention the time needed to make the change when I would have NO central way of authorizing users.

So other than rebasing the entire sysem to Linux, are there any other possible solutions. Or better yet what was wrong with my initial approcah, why was I getting the message that I couldn't access that share.

---

### Post by 4th Dimension on 2012-10-15
Can someone move this to Wireless & Networking in hope that somebody there might be able to help me. Also this is the command I used to mount the share:
```
sudo mount -t cifs //fileserver/*SHARE* /mnt/testShare -o user=*DOMAIN*/*user*%*password*

```

And when I try to open testShare I get the following error:
**The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "testShare".

---

### Post by audiomick on 2012-10-15
> **4th Dimension said:**
> Can someone move this to Wireless & Networking ...

You might be able to get this done by using the "report abuse" button to "report" yourself with a polite request to the moderators.


As for this
> **4th Dimension said:**
> 
And when I try to open testShare I get the following error:
**The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "testShare".

You could try
```
sudo gedit /path/to/testshare
```
wherby you obviously have to use the correct path name. That will open the file testshare in an instance of the editor gedit with root privileges. Be careful that you don't accidently change anything in there.

Alternatively, you could start the file manager with root privileges
```
gksudo nautilus
```
and use that to look at the file. Since the instance of the file manager has root privileges, you should be able to open the file in the editor from there.

---

