---
title: "Where did the data in my folder go after I renamed it?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Paradoxfox93 on 2008-08-25
Okay so the folder i use for Frostwire I have named Shared it's on my /data partition.  It's been giving me problems lately because it's owner is root.  I can't chown the &!7$# so I looked up chmod and how to use it.  I ended up going with sudo chmod 760 so I could make modifications to it.  I changed the name to Shared1 so I could create a new Shared folder (Which I apparently should have done after I move it...)  And now everything in the folder is gone.  Futhermore my lost+found is locked without read permission by owner:root.  Help, please! I have 60gigs worth of data in there!!!!!!!!!!

---

### Post by graben3 on 2008-08-25
I don't fully understand the part where you said you renamed your folder to Shared1 so you could create a new Shared folder... Why is this ? Didn't you only wanted a Shared folder that belongs to your user ????

I'm thinking perhaps you don't have permissions to see the files in that folder Shared1 folder.

Try opening a terminal window and type :

sudo nautilus

Then, you will see files as root... is your folder still empty ?

---

### Post by Paradoxfox93 on 2008-08-25
Yes, Thank you!! yeah the folder itself just causes me problems so i thought it'd be easier just to make a new folder than figure out why i can't chown it.

---

### Post by graben3 on 2008-08-25
If the :

sudo nautilus

does not show you any files, you might want to try also :

sudo chown -hR yourusername /path/to/your/folder
sudo chmod -R 755 /pathtoyourfolder

However it is possible that you just deleted those files instead of renaming the folder of something like this... Have a look at the 

<yourusername>.trash directory on the same drive your Shared folder is to see if your data is in the trash

---

### Post by graben3 on 2008-08-25
I need to see the permissions on your shared folder.

Can you open a terminal window and do this :

cd /path/to/your/Shared1
ls -l

And tell me what you see for the Shared1 directory. Should look like this :

drwxr-xr-x 18 yourusername yourusername     4096 2008-05-11 10:54 Shared1

---

### Post by Paradoxfox93 on 2008-08-26
Oh I should clarify. the Sudo Nautilus did the trick. i was able to get the folder and the files without a problem.  I backed them up on an external hard drive.  From Sudo Nautilus I was able to edit access and such.  Thanks for the help.  Knowing this puts a few other questions I'd been investigating to rest at the same time!

---

