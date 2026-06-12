---
title: "HELP! Cannot access protected share!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by copperdore on 2008-05-31
Hi everyone,

I have just switched over to Ubuntu 8.04 and in all my previous distributions I have used smb4k as my standard way of accessing protected shares. However, this is a really irritating process and I would like the samba share I have been to automount with read-write capabilities. I've been using various distributions of Linux for a couple of years but i'm not very knowledgeable on how to get things like samba to work.

I would like to do this via a gui but if that isn't going to work could some kind-hearted soul give me a bit of a step by step process of how to automount password protected shares, in complete dummy language.

Any help would be greatly appreciated.

Cheers,

Copperdore.

---

### Post by spiderbatdad on 2008-05-31
Just right click on any folder, in your home directory, you want to share and select sharing options. Then just follow the prompts. Shares should be automatic after that. You will see options for allowing guest users...or not, as well as whether to allow others to write to folders.
It should simply work. I have mac and windows users on the same network able to browse all my shares.

If you have protected shares, your username and password must be entered, or check the other machine as it tries to browse the share, note the username; create a user and password on your system for this user, log that user in.

---

### Post by copperdore on 2008-05-31
Thanks spiderbatdad, I didn't know setting up share folders on my computer was that easy. 

What I'm trying to do at the moment is access another share across the network which requires authentication. It's on a fedora machine, which services both Linux and windows computers. I can access this share through smb4k but I can't seem to make it automount it as a normal drive, and i believe this is an authentication issue. Any help anyone can give me would be enormously appreciated.

Thanks again,

Copperdore.

---

### Post by copperdore on 2008-05-31
Hi again, 

Just an addition to that last reply. When I try to mount it through nautilus I get a message saying 

[I]Unable to mount location
Failed to mount windows share[/I]

Thanks again,

Copperdore.

---

