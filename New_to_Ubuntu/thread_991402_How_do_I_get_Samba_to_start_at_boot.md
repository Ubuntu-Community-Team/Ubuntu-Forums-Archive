---
title: "How do I get Samba to start at boot?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Mighty_Moose on 2008-11-23
Hey guys, 

I've asked a few questions here before with excellent results so far, so thank you :)

I never had this problem with my old Ubuntu box, but on my new one, it seems it won't start Samba when I boot up, or reboot the machine. "Folder sharing service (samba)" is checked in my services settings options, but it doesn't seem to make any difference.

I will preface, I had an issue with Samba earlier, so I did an 'apt-get remove samba', and then reinstalled it. Have I screwed things up by doing that?

I'm just looking for a way to get Samba to start when I boot up the machine. Any suggestions?

---

### Post by doas777 on 2008-11-23
you could try purging the package or using --reinstall, but as for your question, you should be able to start samba with 
```
sudo /etc/init.d/samba start
```

good luck,
franklin

---

### Post by Mighty_Moose on 2008-11-23
That command works for me already (although connecting my Vista machine through samba is a hassle, but that's a different issue...), so that's not a problem. The fact that every time I shut down or restart my machine and have to enter that command is  what's a real pain. I've heard that it can be setup so the samba server is started automatically at boot, but I don't know how to do that.

---

### Post by doas777 on 2008-11-24
well if you can wait until login, you could add the command to System -> Preferences -> Sessions.

---

### Post by Mighty_Moose on 2008-11-25
I'd really prefer it to be started at boot. Is there any way to do that?

---

### Post by doas777 on 2008-11-25
I'm certian there is, but i'm not the guy to ask. google around a bit for "ubuntu service start" or some such, and you should find the answer you seek.

good luck,
franklin

---

