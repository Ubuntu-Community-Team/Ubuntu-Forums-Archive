---
title: "SSH with file browser interface?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by cheatos on 2012-06-01
Hi,

so I have to sort the filesystem on a remote machine but I don't want to do this via the terminal. Is there a possibility of doing that with some program where you have the usual folder structures (i.e. any file manager like windows explorer, ...) so I can see the folders unfold and can move them around?

Off Topic:
I certainly miss that in my lubuntu system, too as it doesn't have the folder hierarchy on the left side but the "favorite" folders. If there's a way to change that, just let me know

Thanks for your help!

---

### Post by lechien73 on 2012-06-01
I have ssh server installed on my Mythbuntu media centre, and the Thunar file manager.

I can connect remotely by typing:

```
ssh -X user@ip.address thunar
```

This opens the Thunar file manager with the remote file structure. It was a plain vanilla install, so I didn't have to install anything other than ssh server.

Is that what you were looking for?

---

### Post by The Cog on 2012-06-01
nautilus is capable of making ssh/sftp connections to another pc. Google for "nautilus sftp" for lots of articles about it.

P.S.
It might be under File->Connect to server, but I can't remember exactly, I haven't used nautilus for a couple of years.

---

### Post by Paqman on 2012-06-01
> **cheatos said:**
> Hi,

so I have to sort the filesystem on a remote machine but I don't want to do this via the terminal. Is there a possibility of doing that with some program where you have the usual folder structures (i.e. any file manager like windows explorer, ...) so I can see the folders unfold and can move them around?


Sure, if you're using Ubuntu you can just use Nautilus (the normal file manager). Go to File > Connect to server > change "type" to SSH and enter the details.

---

### Post by spiky001 on 2012-06-01
Hi

You will have to install ssh server on the other machine, Then you can open nautilus, then open address bar Ctrl+l type ```
ssh://username@ipaddress 
```

---

### Post by cheatos on 2012-06-03
All your posts,
I' ll try it with nautillus.
Am i right that pcmanfm doesn't have the ability to connect via ssh?

---

### Post by amauk on 2012-06-03
Also have a look at sshfs
Fuse filesystem for mounting a directory on a remote machine over SSH

---

### Post by cheatos on 2012-06-03
Thanks for all your advice, I'm pretty busy at the moment but as soon as I'm done with testing the different ideas I'll come back and mark this as solved or ask more questions ;)

---

### Post by cheatos on 2012-06-06
Okay, so here I am again to mark this as solved as Nautilus was prettty much all I wanted.

Thanks for your help guys! You are awesome.

---

### Post by Ahunt on 2012-06-30
Thank you so much for this information! I too was having problems with sshfs and found this thread which enabled me to set SFTP via Nautilus - a nice solution!

---

### Post by crymsonfyre on 2012-07-31
Hi everyone, I am kinda a newbie still with Ubuntu. I have been trying to fix my connect to server issue for a while now. I have absolutely no options under connect to server anymore? all i have on there is connect to service type and then custom location? I wish to be able to search through files by folder with ssh under there? I dont know what I did? Ive been trying to think back what changes I made but not a clue? Please anyone I would appreciate the help!?

---

### Post by Kelvari on 2012-07-31
Assuming you're able to ssh into the computer, you could try the following setup:```
ssh -X user@host
```to let you use Nautilus (or whatever file browser you have on that machine).

---

### Post by CharlesA on 2012-07-31
> **crymsonfyre said:**
> Hi everyone, I am kinda a newbie still with Ubuntu. I have been trying to fix my connect to server issue for a while now. I have absolutely no options under connect to server anymore? all i have on there is connect to service type and then custom location? I wish to be able to search through files by folder with ssh under there? I dont know what I did? Ive been trying to think back what changes I made but not a clue? Please anyone I would appreciate the help!?
Please create a new thread, instead of posting in old ones.

Thanks.

---

