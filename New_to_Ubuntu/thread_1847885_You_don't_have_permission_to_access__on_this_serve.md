---
title: "You don't have permission to access / on this server"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by Luxx on 2011-09-21
When trying to access distrowatch.com I get the following error:

Forbidden
You don't have permission to access / on this server.

At first I thought it might be the website, but I could bring it up fine on a friend's Windows comp.

I have seen threads on this error in the forums and don't understand a single thing they are talking about -- apache servers, files I don't have, permissions I can't even find, etc, etc. I've been using Linux for 6 years, Ubuntu for more than 4, but i feel like a real noob on this one. Please help.

This seems to have happened just yesterday after an update that seemed pretty benign, just a few files, mostly mozilla related.

Much gratitude for any advice to fix this.

---

### Post by sammiev on 2011-09-21
> **Luxx said:**
> When trying to access distrowatch.com I get the following error:

Forbidden
You don't have permission to access / on this server.

At first I thought it might be the website, but I could bring it up fine on a friend's Windows comp.

I have seen threads on this error in the forums and don't understand a single thing they are talking about -- apache servers, files I don't have, permissions I can't even find, etc, etc. I've been using Linux for 6 years, Ubuntu for more than 4, but i feel like a real noob on this one. Please help.

This seems to have happened just yesterday after an update that seemed pretty benign, just a few files, mostly mozilla related.

Much gratitude for any advice to fix this.

Works here so it maybe your ISP provider or have you blocked out some sites yourself?

---

### Post by jvance492 on 2011-09-21
hidemyass.com

can you get there through a proxy?

If so its probably your global IP thats blocked for whatever reason.

Sounds like the rejection is coming from the web server side.

---

### Post by Luxx on 2011-09-21
Um... the other computer is the main comp on the network. I'm actually connecting to the internet through this other computer anyway, so wouldn't it be getting the same rejection?

I can bring up the website on his comp with no 403 errors. And tthe fact that it's looking for access to root (/) seems very Linux specific, doesn't it?

The ISP is obviously not involved and I haven't blocked any websites myself.

---

### Post by Luxx on 2011-11-07
I get the same error message on all DistroWatch pages:

Forbidden
You don't have permission to access / on this server.


Forbidden
You don't have permission to access /dwres.php on this server.

etc.

Seems to be same issue with proxy:

The requested resource could not be loaded.


Only this website, only the one Ubuntu computer on the network, only since updating packages. Still unresolved.

---

