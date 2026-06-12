---
title: "Shared Folder Ownership Problem"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by BirdZerk on 2011-11-27
I have 2 computers running Ubuntu, the computer I use has 10.04 (gnome2) and the other was just upgraded to 11.10 (gnome3). I created a shared folder on the 11.10 computer which I have no problem accessing or creating folders and files.  The problem I am having is in the ownership, some of the items I create are locked from the other user and some of the items they create are locked from me.  This shared folder does not need any restrictions at all, it is a work folder for both of us to collaborate on projects.  This restriction is really slowing us down.  How do I remove this ownership restriction?

---

### Post by Lars Noodén on 2011-11-27
Make sure there is a group that both accounts belong to.  Then make the directory belong to the group.  Then make sure that the sticky bit is set for group:

```

chmod g=rwxs */path/to/directory*

```

---

### Post by BirdZerk on 2011-11-27
Is there a howto I can read and follow?  I created a group on the 11.10 computer and added that user to it, but do not know how to add myself on the 10.04 computer or the shared folder.  Thanks for the help so far.

---

### Post by Lars Noodén on 2011-11-27
The closest to a HowTo that I could find is this one:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Morbius1 on 2011-11-27
"Shared Folder" as in Samba?

Nautilus > right click a folder > Sharing Options ... type of share?

---

### Post by Jacobonbuntu on 2011-11-27
Hi BirdZerk,

You probably made a shared folder in nautilus, which is rather limited in setting controls. your problem is I believe that the creation mask for new documents is not right, so (new) documents are owned by only the creator. with the chmod command, you change things for *existing* files, but not for newly created ones :)

how to set up a server (shared folder) you can find here
[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)
it is a good and not too difficult howto

on the client-side this is a pretty good description:
[http://www.mattvanstone.com/2007/11/...-in-ubuntu-v3/]("http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/")
if you do not use a password just leave the user- and password empty in the .cifscredentials-file that is mentioned in the last howto

we just "finished" a similar problem in this thread (not exactly the same, but the same cause):
[http://ubuntuforums.org/showthread.php?t=1887181&page=1](http://ubuntuforums.org/showthread.php?t=1887181&page=1)

---

### Post by Morbius1 on 2011-11-27
Well, if it's a samba share and he created it using Nautilus ( and accessing it from the remote machine through Nautilus ) then by far the easiest way around this problem is to add one line to the [global] section of smb.conf on the machine with the share:
```
force user = your-user-name
```[COLOR=Blue]*Change your-user-name to your local login user name.*[/COLOR]

And restart samba:
```
sudo service smbd restart
```When the remote user accesses the share ( after authentication if you set it up that way or as a guest ) he will be converted to you as far as that share is concerned. All future files saved will have you as owner. On the client end accessing the share through nautilus mounts the share with all the requisite permissions necessary automatically. But it does have a crappy mount point:
> /home/user-name/.gvfs/share-name on server-name

---

### Post by Jacobonbuntu on 2011-11-28
> **Morbius1 said:**
> Well, if it's a samba share and he created it using Nautilus ( and accessing it from the remote machine through Nautilus ) then by far the easiest way around this problem is to add one line to the [global] section of smb.conf on the machine with the share:
```
force user = your-user-name
```[COLOR=Blue]*Change your-user-name to your local login user name.*[/COLOR]

And restart samba:
```
sudo service smbd restart
```When the remote user accesses the share ( after authentication if you set it up that way or as a guest ) he will be converted to you as far as that share is concerned. All future files saved will have you as owner. On the client end accessing the share through nautilus mounts the share with all the requisite permissions necessary automatically. But it does have a crappy mount point:


although it looks logical what you say, it seems not to work...
I changed my /etc/samba/smb.conf the way you suggested (I have a good working situation as described, but wanted to test). After that, I had no rights to my own share any more.  I do not have the theoretical knowledge to clarify (yet), but that's the result. I changed it back to the way I had it :)

---

### Post by Morbius1 on 2011-11-28
Unfortunately I'd need a lot more information to see how you are currently set up to determine why it didn't work which would probably be considered a hijacking of this topic. If you would like to start a separate topic with the output of the following commands I'd love to see why it didn't work for you:
```
testparm -s
``````
net usershare info --long
```And also state where exactly you added the "force user" line.
I'd also like to see the Linux ownership and permissions of the target shared folder.

---

### Post by Jacobonbuntu on 2011-11-28
> **Morbius1 said:**
> Unfortunately I'd need a lot more information to see how you are currently set up to determine why it didn't work which would probably be considered a hijacking of this topic. If you would like to start a separate topic with the output of the following commands I'd love to see why it didn't work for you:
```
testparm -s
``````
net usershare info --long
```And also state where exactly you added the "force user" line.
I'd also like to see the Linux ownership and permissions of the target shared folder.


I would love to! and thanks a lot for doing me the favour :)
This is a subject that I would love to get a hold on. So far I manage mainly by using good manuals building stones, combined with a little understanding. Although everything works well in my situation, fine-tuning of the network structure is one of my knowledge goals.
I have to run today, but will open a new thread tomorrow and will send you a message.

thanks once again!
Jacob

---

