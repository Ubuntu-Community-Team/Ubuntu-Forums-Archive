---
title: "Backup Notice"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by dee119 on 2015-12-31
):P Hi - I wonder if anyone could tell me what the following 
             message means when my backup program has finished.

             #could not backup /home/myself/.config/nautilus-actions

             Does this mean all my settings in the web browser, and 
             home settings.

             Hope someone understands what I am trying to say. :confused:
             Thanks for any input.

---

### Post by PaulW2U on 2015-12-31
> **dee119 said:**
> ):P Hi - I wonder if anyone could tell me what the following 
             message means when my backup program has finished.

             #could not backup /home/myself/.config/nautilus-actions
It could mean that you are not the owner of the files in "/home/myself/.config/nautilus-actions" directory or is that actually a file?

Are the file(s) in question owned by a user other than you, root maybe?

---

### Post by dee119 on 2015-12-31
):P  Hi and thank you for your reply.

Not sure if I am the owner of the files
or it maybe owned by root. How would I
find out who owns these files?

As I am not the owner of the files, would that
make problems if I had to recover the files 
when or if I had to restore them.

Silly question - but how would I go about
getting rid of the message.

Thanks again for your input. ;)

---

### Post by col48 on 2016-01-01
You can see who owns the files in Nautilus or using a command in a Terminal.  Nautilus is easier to describe...

In the View menu in Nautilus, make sure that 'Show Hidden Files' is ticked (so that you can navigate to the .config folder), that you have selected 'List' view and that the 'Visible Columns' list includes 'Permissions', 'Owner' and 'Group'.  Then navigate down to the folder by clicking down the hierarchy.

_Explanantion:_
'Permissions' - ten letters; **the first** is d for a folder, l (lower case L) for a link, - for a file, **then three sets of three** for owner, group and everybody privileges respectively.  Each group is r for read access (- if no permission) then w for write access (- if no permission) then x for execute access (- if no permission).
'Owner' is straightforward, I hope!
'Group' - name of a group of users who may share rights to files; these users may include behind-the-scenes ones for system use as well as real users.

In my .config file, all the files and folders are owned by me, which is, I think, what I would expect.
To change privileges for a file you own, right-click it in Nautilus, choose 'Properties' and one of the tabs is 'Permissions'.
To change ownership you would need to either use a gksudo command in Terminal to make the change with root privileges or (if the current owner is *not* root) be logged on as the current owner.
The commands to look up are chmod (for privileges) and chown (for ownership)

#############
The backup program might also be unable to do the backup if, for any reason, the file was open (especially if with write access) at the moment it wanted to back it up.  It might also be a corrupt file, for instance.

---

### Post by dee119 on 2016-01-01
Thanks very much for your reply and explanation on permissions.
Will do a bit more research and try to solve this one.  Hopefully
I will be able to come back and say I managed to fix it.
Much appreciated for your time.
Happy New Year 2016 - Dee

---

