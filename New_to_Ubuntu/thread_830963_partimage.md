---
title: "partimage"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by DBrocks on 2008-06-16
Hey guys.
 
I am working at my school, trying to find an alternative to Norton Ghost that they are using. I stumbled across the G4L live cd a few years back. I also discovered Partimage, which seems better because it only copies the actual data, not all the empty blocks. I have configured a ubuntu server to act as a server for computer images. I know you can use the Partimage CD to run in server mode, but i was wondering if there was a package that exists for Ubuntu SE that can run Partimage in Server Mode without a CD. Thanks in advance!
 
~Dan

---

### Post by Sef on 2008-06-16
Use the terminal, and check the repositories to see if it is there.

```
sudo apt-cache search partimage
```

---

### Post by DBrocks on 2008-06-16
Yeah i got it. Partimaged-server

---

