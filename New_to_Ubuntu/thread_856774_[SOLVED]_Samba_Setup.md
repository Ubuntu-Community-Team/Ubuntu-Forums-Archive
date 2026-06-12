---
title: "[SOLVED] Samba Setup?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by VorlonShadow on 2008-07-11
I posted this message earlier, but it seems to have disappeared.

I want to set up a folder that will be shared by windows users.  I have Samba set up and running on my Ubuntu 8.04 server.  I've edited the smb.conf file, and added a shared resource in there, but I don't believe I've got it set up correctly.  I've got two questions:

1.  How can I tell what the user names are that I have added to my Samba User file?
2.  How do I make sure my shared resource is set up for read/write access by Windows users?

Thanks,
Jesse

---

### Post by rbc on 2008-07-11
1. Good question. I have no idea, but I am going to keep searching. And if you find out first, please post back. I would love to know myself.
2. I found three ways:
-Right click on the share, selct Properties then go to the Share tab. Make sure the "Allow others to write...." box is checked. 
-The shares should be the last things in the smb.conf file. Make sure there is a line that says, "writeable = yes" in there (without the quotes)
-Test it. Go to a Windows computer and try to copy or save something to it.

---

### Post by shp on 2008-07-11
To make it writeable us just add "writeable = yes" under the share names

all the users should be in a smbpasswd file which is probably somewhere in /etc/samba

---

### Post by VorlonShadow on 2008-07-12
I wasn't sure if my user was there, so I just ran smbpasswd and added it. It didn't complain, so I figure the user is now there.

On the other issue, I think I have it set correctly, but not sure that I have permissions set right.  When I go to Windows I can see the folder, but when I double-click on it, it asks me to log in.  So, I type in the user name and password that I added to Samba, and it doesn't accept it.  It just loops me right back around and asks again.

Does this user need to be a valid user in Linux as well?  if so, how do I add it?

If this is a permissions thing, I have Ubuntu 8.04 server installed, so I don't have a GUI running. Whatever I do, I'll need to do through a command prompt.  How do I ensure that I have the permissions set correctly for the folder?

Thanks,
Jesse

---

### Post by superprash2003 on 2008-07-12
once you add a samba user, you need to add the user in the smbusers file.. did you do that?

---

### Post by VorlonShadow on 2008-07-12
No.  In fact, that file didn't even exist.  I did a little research, and I've uncommented the "security=user" part of the smb.conf file, and added "username map = /etc/samba/smbusers to the file.

I then added the following lines to smbusers:
jesse="JesseCastleberry"

I restarted Samba, and I appear to be able to get in now.

Thanks for your help.

Jesse

---

