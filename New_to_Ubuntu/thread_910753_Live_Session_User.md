---
title: "Live Session User"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by blendmaster on 2008-09-04
Hello!

So I've been away from Ubuntu for a while... it stinks.

Lol, anyway, I've got a new install on my flash drive. The install is essentially the 8.04 live cd (not much has been changed yet to set my drive apart from the cd). I'm having two user accessibility issues.

My first is that my user doesn't need a password to access sudo. Although security probably won't be an issue, I still like keeping my data well under control and safe. What method(s) can be used to force a password prompt when accessing sudo for my user?

My second is that I am still able to switch to the live session user and use it to unlock user administration privileges. How would I be able to delete the live session user?

On a side note, it appears I am logged into "user"@ubuntu. If memory serves, "user" is obviously the user while "ubuntu" is the group. I'm pretty sure I should be logged into "user"@"user", as that is what I had always been before. "ubuntu" also appears to be the live session user group, so there may be a correlation. Again, this is assuming I remember everything correctly.

Please excuse my renewed "noobishness" and "wall of text".

Thank you!

---

### Post by iaculallad on 2008-09-04
> **blendmaster said:**
> Hello!

So I've been away from Ubuntu for a while... it stinks.

Lol, anyway, I've got a new install on my flash drive. The install is essentially the 8.04 live cd (not much has been changed yet to set my drive apart from the cd). I'm having two user accessibility issues.

My first is that my user doesn't need a password to access sudo. Although security probably won't be an issue, I still like keeping my data well under control and safe. What method(s) can be used to force a password prompt when accessing sudo for my user?

- When you're finished installing the LiveCD on your HDD, you're users are automatically prompted with password in order for them to access the sudo/gksudo/gksu + intended command(s).

> **blendmaster said:**
> My second is that I am still able to switch to the live session user and use it to unlock user administration privileges. How would I be able to delete the live session user?

- The live session user is automatically removed once you install the LiveCD permanently on your HDD.

> **blendmaster said:**
> On a side note, it appears I am logged into "user"@ubuntu. If memory serves, "user" is obviously the user while "ubuntu" is the group. I'm pretty sure I should be logged into "user"@"user", as that is what I had always been before. "ubuntu" also appears to be the live session user group, so there may be a correlation. Again, this is assuming I remember everything correctly.

- Ubuntu is the/your computer name.

> **blendmaster said:**
> Please excuse my renewed "noobishness" and "wall of text".

Thank you!

---

### Post by blendmaster on 2008-09-04
Thanks for the reply!

I followed [this tutorial]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") to install Ubuntu on my flash drive (not my HDD).

Instead of actually installing it, it essentially replicates the live cd on the drive. Therefore, it leaves the usual live session user there (what I assume).

I had to create my own user manually and add it to the "admin" group through use of the "adduser" command.

---

### Post by sisco311 on 2008-09-04
The default user name on the live cd is *ubuntu.*
You can delete a user with the *userdel <username> *command.

How did you create the new user?
Did you set up a password for it?

EDIT: You can use the GUI to manage users and groups: System --> Administration --> Users and Groups

---

### Post by blendmaster on 2008-09-04
Okay, so I'm remembering some of the primary traits which define Debian based Linux now (feeling quite dumb for even posting this now).

My only problem now is in trying to delete user "ubuntu". I'll try rebooting once more but the terminal answers my deluser with a "user is logged in" (yes, I logged out of user ubuntu... supposedly). Dunno what's up with that, but I'll surely figure it out.

Thanks for the support!

---

### Post by blendmaster on 2008-09-04
User "ubuntu" seems to log in automatically at start-up:

[IMG]http://i210.photobucket.com/albums/bb258/blends3d/terminal.jpg[/IMG]

This is what command "w" shows.

Remember it tells me "ubuntu" is logged in, so I can't delete it. I'm afraid to forcefully log "ubuntu" out, as it may cause serious issues (though I'm doubtful of that).

Is this related to the drive being a "live-cd"?

PS: Sorry for the double-post btw.

---

### Post by Ben63 on 2008-12-18
Hi,

I have the same problem and cannot find any documentation for it ;
How can I get rid of the "live session user" or at least remove him the sudo rights?

Thanks

---

### Post by eric stockman on 2009-09-12
To change the login-screen :
   first: create  a new user : that's you ( System -> administration -> Users & Groups )
   second:- give a right click on the "live session user" button (above right )
          - chose option "Setup Login Screen"
          - fill in Security as appropriate 
Good luck

---

### Post by nenn on 2009-12-15
> **eric stockman said:**
> 
give a right click on the "live session user" button (above right )
          

Hi!
It's not clearly where to look for giving such a click.
Could anybody post a prtscreen of this operation?

---

