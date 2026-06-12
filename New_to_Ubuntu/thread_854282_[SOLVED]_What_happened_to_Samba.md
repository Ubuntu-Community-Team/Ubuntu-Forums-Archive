---
title: "[SOLVED] What happened to Samba??"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-07-09
I just did a fresh install of Ubuntu 8.04.1 Desktop Edition. I go to my home folder and create another folder and try to share it. It asks me to install the packages which I did. The I right click it and select Sharing options. I put the share name to Jamesr and the folder name to James. I check Share this Folder and Allow other people to write in this folder. When I click Create share I get this Nautilus needs to add some permissions to your folder "James" in order to share it. The folder "James" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically? 
I click Add the permissions automatically and I get net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
I never had a problem with this before. Also what is the command so you can change the SMB password? Last thing is when I look at my Ubuntu server is windows it shows it as Ubuntu-Server server (Samba, Ubuntu) (Ubuntu-server). Is their anyway I can change that?

---

### Post by plucky on 2008-07-09
> **jamesrfla said:**
> I just did a fresh install of Ubuntu 8.04.1 Desktop Edition. I go to my home folder and create another folder and try to share it. It asks me to install the packages which I did. The I right click it and select Sharing options. I put the share name to Jamesr and the folder name to James. I check Share this Folder and Allow other people to write in this folder. When I click Create share I get this Nautilus needs to add some permissions to your folder "James" in order to share it. The folder "James" needs the following extra permissions for sharing to work:
  - write permission by others
Do you want Nautilus to add these permissions to the folder automatically? 
I click Add the permissions automatically and I get net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
I never had a problem with this before. Also what is the command so you can change the SMB password? Last thing is when I look at my Ubuntu server is windows it shows it as Ubuntu-Server server (Samba, Ubuntu) (Ubuntu-server). Is their anyway I can change that?

You need to logout and log back in again before you set up the share on the folder.

Good Luck

---

### Post by jamesrfla on 2008-07-09
Yeah I should of reboot. It is amazing what miracles happen after a reboot. Now it Works. I still need to know that command to change the SMB password and how to change the Ubuntu description in My network places in windows

---

### Post by issih on 2008-07-09
By default I believe ubuntu now sets the smb name to match the hostname and synchronises the smbuser password with your login ones.

These things are changeable of course, but thats how things are by default.

have a look at the man page for smbpasswd and also look at /etc/samba/smb.conf where a lot of things are set up like the workgroup and network name.

A lot of these things can be configured through gui apps if you install something like the package system-config-samba:

```
sudo apt-get install system-config-samba 
```

That allows you to tweak most of these things in a nice easy way.

Hope that helps

---

### Post by jamesrfla on 2008-07-09
Yeah I looked at /etc/samba/smb.conf and it looks easy for me to edit. These conf files seem to very easy to find and edit what you want. I'll take a close look into that file. But ill go ahead and get that utility as long as it isn't a startup program or uses any of my ram when I'm not using the utility.

---

### Post by issih on 2008-07-09
Nope just a little front end to editing the file really.

Nice and simple

---

### Post by jamesrfla on 2008-07-09
Thanks issih and plucky for all your help!! :guitar:

---

