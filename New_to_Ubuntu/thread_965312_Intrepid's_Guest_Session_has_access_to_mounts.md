---
title: "Intrepid's Guest Session has access to mounts?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-31
I just installed Intrepid (8.10) on my laptop and I went to check out the new "Guest Session" feature which is supposed to be a locked down session, yet as a Guest I was able to access my mounted drives, I could even read, write, delete, and execute files from those mounts also...

Isn't the "Guest Session" supposed to be secure: 
> The User Switcher panel applet (package fast-user-switch-applet) now provides an extra entry for starting a Guest session (by Martin Pitt). This creates a temporary password-less user account with restricted privileges: the account cannot access any users' home directories, nor permanently store data. This is sufficiently safe to lend your laptop to someone else for a quick email check. - [http://www.ubuntu.com/getubuntu/releasenotes/810overview](http://www.ubuntu.com/getubuntu/releasenotes/810overview)

Not safe enough IMO :(

---

### Post by firefeather on 2008-10-31
I think it depends on the way those mounts are mounted; I cannot access any mounts through the Guest Session unless they were mounted by the user in the Guest Session (i.e. plugging in a flash drive, etc.).

---

### Post by ajgreeny on 2008-10-31
I imagine this will depend on the fstab file which is loaded long before the user gui.  You may need to set that file to restrict users to only have whatever limited access you wish to other partitions.  Just out of interest, can the guest user also read the user files of the first user, even if guest can't write to them?

I'm sure there must be a way to get the restricted file access you want quite easily, but can't help further I'm afraid.  I have yet to really look at 8.10, just downloaded with ktorrent, which seemed much faster than transmission.

---

### Post by nhasian on 2008-10-31
I dont have a thumbdrive to test, but i would hope that Guests could launch their own apps as well as save data to their thumbdrive using a guest account.  Can anyone confirm?

---

### Post by coldcoffee on 2008-10-31
I have similar questions on these lines. I do want other accounts to be able to use applications that are on the computer, but I don't want them to be able to see any other folders except the ones that are on the home directory for that account. I am sure there has to be a way to do this. After all, isn't that one of the things about Linux? The ability to create these accounts and to only have access to certain things.

I mean sure, I can restrict folder access and such, but what a pain to go around setting up all these permissions. Is there not a simple way to set up accounts to where they can run media players, word processing and other apps, but be limited to only being able to see the folders in the home directory for that account. I have a guest account too. I can see all the other directories in all the other accounts too though.

Edit: I am using Hardy though and not Intrepid.

---

### Post by firefeather on 2008-10-31
> **ajgreeny said:**
> Just out of interest, can the guest user also read the user files of the first user, even if guest can't write to them?

Nope, access is denied to the guest user. I double checked yesterday.

---

### Post by firefeather on 2008-11-01
> **coldcoffee said:**
> I have similar questions on these lines. I do want other accounts to be able to use applications that are on the computer, but I don't want them to be able to see any other folders except the ones that are on the home directory for that account. I am sure there has to be a way to do this. After all, isn't that one of the things about Linux? The ability to create these accounts and to only have access to certain things.

I mean sure, I can restrict folder access and such, but what a pain to go around setting up all these permissions. Is there not a simple way to set up accounts to where they can run media players, word processing and other apps, but be limited to only being able to see the folders in the home directory for that account. I have a guest account too. I can see all the other directories in all the other accounts too though.

Edit: I am using Hardy though and not Intrepid.

I'm pretty sure all of this is available on the Guest access feature of Intrepid. It would be difficult for me to know where to start to implement that on Hardy, however.

---

