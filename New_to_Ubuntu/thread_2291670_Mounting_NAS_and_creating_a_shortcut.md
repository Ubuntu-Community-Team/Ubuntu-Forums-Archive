---
title: "Mounting NAS and creating a shortcut"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by AKZMonster on 2015-08-22
I'm slowly getting worse at Linux every minute...

When I first installed Lubuntu and opened the file browser (pcmanfm), I read a post about accessing your NAS by typing smb://<IP>/ into the address bar and I did it and it worked fine. Since attempting to create a shortcut, it no longer works. I get errors. I am trying to create a folder shortcut to that location on my Lubuntu machine and now I can't even access the NAS anymore.

So far I've installed LAMP, samba, cifs-utils, and vsftpd.

Ultimately, I'm trying to get functionality out of my hikvision IP cam. It sucks. It doesn't work. The only thing that works on it is the FTP transfer. But my NAS is a kd20 and does not support FTP. My Lubuntu machine does support FTP and it works but the harddisk on my Lubuntu machine is small and so I need to send the files to my NAS via my Lubuntu machine. I know, I know, it's exhausting to read, how exhausting do you think it is to have all these problems, I just need to get the camera functioning for now. I can perfect my system later.

[Please help]("http://i46.tinypic.com/24wr8so.png") me someone.

I've googled the crap out of these issues. Reddit won't respond. Please dear god will someone help me! I know I'm a ducking moron but I've read post after post of ideas that just don't work. Please Please help! I'll answer any questions and try anything you can think of. Thanks so much for reading this far!!

Okay I'm assuming this will not get many/any responses but I tried here first... 

when I type:
```
mount –t cifs –o username=username,password=password //<IP>/<path> <shortcutpath>
```
I get:
```
mount error(5): Input/output error
```

---

### Post by Bucky Ball on 2015-08-22
The absolutely easiest way I've found is to install Gigolo from Synaptic package manager> launch it> Actions> Connect> Connect to the IP of your NAS> that will put an entry into the left pane of PCmanFM for your NAS or you can access the NAS directly from Gigolo.

Once the NAS is mounted you can close Gigolo. You could then copy the address Gigolo is using for the NAS and make a desktop launcher for it using that with a little experimentation. :)

---

### Post by AKZMonster on 2015-08-22
WAAAAAT?!?! hahaha

It's working! I restarted my machines many times last night and no luck with accessability. Today is a different story. Awesome. Thanks for That Bucky!! Now that my IP cam is storing successfully to my NAS I can get back on the road of having fun with Lubuntu.

I only have one question still. So, when I read through the various closed posts pertaining to NAS mounting, I see that many people write the mounting instruction directly to /etc/fstab. My understanding is that if I don't do this then I will have to mount the NAS manually every time I restart.

Am I correct in that assumption?

---

### Post by sandyd on 2015-08-22
> **AKZMonster said:**
> WAAAAAT?!?! hahaha

It's working! I restarted my machines many times last night and no luck with accessability. Today is a different story. Awesome. Thanks for That Bucky!! Now that my IP cam is storing successfully to my NAS I can get back on the road of having fun with Lubuntu.

I only have one question still. So, when I read through the various closed posts pertaining to NAS mounting, I see that many people write the mounting instruction directly to /etc/fstab. My understanding is that if I don't do this then I will have to mount the NAS manually every time I restart.

Am I correct in that assumption?

This is correct unless you are running the NAS mount command at startup using another method.

---

