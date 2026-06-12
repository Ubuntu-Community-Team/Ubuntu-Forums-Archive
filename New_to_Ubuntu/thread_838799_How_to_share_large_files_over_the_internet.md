---
title: "How to share large files over the internet"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by garyedwardjohnston on 2008-06-23
I want to give someone access to a file (mp4) on my computer and trust the person.

How would I go about doing this?

Thanks :)

---

### Post by superprash2003 on 2008-06-23
many ways.. openssh,apache,ftp etc ..

---

### Post by neurostu on 2008-06-23
SSH is the easiest.

If you know your ip, you can create an account for them that has read access to your files. You can also give them write access if you want.  Then give them the login name and password and they can connect with:
```

ssh user@##.##.##.## <-- IP address

```
then they will be connected to a terminal on your machine.

They can easily transfer files using scp.

---

### Post by Dutch70 on 2008-06-23
Also, check this out,  [http://rapidshare.com/](http://rapidshare.com/)

 But dont take my word for it. I am going to check out the above posted tutorial as well.

Dutch

---

### Post by apswartz on 2008-06-23
I use...
[http://www.yousendit.com/](http://www.yousendit.com/)

---

### Post by Dani Filth on 2008-06-23
Free hosters (like yousendit, rapidshare, mediafire etc) have their limit for the size of files upload - 100MB, I think. So if your file(s) is too big you may want to use other methods. If they allow torrent at your place, using torrent will be an easy option :D

---

