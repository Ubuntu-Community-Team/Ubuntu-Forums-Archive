---
title: "[SOLVED] File Sharing using Samba over a Home Network"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by getitright on 2008-10-25
Can any one help me with setting up file sharing using Samba on a home network?

The state of play is that I have a desktop connected by ethernet cable to a router/modem and a laptop connected wirelessly. The laptop is configured in Roaming Mode and the laptop with a fixed IP. Both are running Ubuntu and both can access the net. I am able to ping each machine from the other and can access each machines folders and files using SSH. I have installed and configured Samba but am unable to share folders and files using Samba.

Whenever I seek information on the web all I seem to get is that setting up file share using Samba is easy. Having tried unsuccessfully, for a couple of weeks, I am beginning to doubt my ability in setting up a "simple application". In order to protect my sanity or at least boost my confidence, I need advice please.

---

### Post by techstop on 2008-10-25
Have you read this guide?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

There's a link on that page to this guide;

[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

---

### Post by Nepherte on 2008-10-25
How are you accessing the network shares? Have you tried typing smb://ipaddress/sharename in nautilus directly?

There might also be a reason logged somewhere in /var/log. It's a file named samba.log or smb.log or something. I forgot the actual name.

Can you also post your smb.conf file?
```
cat /etc/samba/smb.conf
```

---

### Post by vanadium on 2008-10-25
If you only have Linux machines and you have ssh up and running anyway, you might connect your computers using sshfs. This works very well for me. This is the guide I used. [http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)
It is probably easier to setup than samba.

I have no experience with setting up samba myself. However, just a tip: if you want to continue with samba, you should probably inform on what you already did (what procedure you used) and how your current setup is. Then, experienced people can see what you are missing. As you put your question now, there is no sensible way to answer your issue than to link to guides that are all over the net.

---

### Post by getitright on 2008-10-25
Thanks vanadium.

Your suggestion re:-sshfs looks good.

If I follow the sshfs procedure do I have to install ssh on either or both machines or just install sshfs.

---

### Post by bodhi.zazen on 2008-10-25
Well, first get samba working on a wired network then try it wireless. For security reasons some wireless routers will block you from connecting with samba. Do a google search on samba and wireless.

---

### Post by vanadium on 2008-10-25
You mentionned ssh works, so that is already installed. You only need to add sshfs on the client computer. All instructions in the link apply to the client side (it is assumed you can already connect to the server with ssh).

---

### Post by getitright on 2008-10-31
> **vanadium said:**
> You mentionned ssh works, so that is already installed. You only need to add sshfs on the client computer. All instructions in the link apply to the client side (it is assumed you can already connect to the server with ssh).

Vanadium followed your advice. File sharing now working great.

---

