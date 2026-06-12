---
title: "Do we have to create .fonts directory?"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-03
I was running fc-cache and i noticed in the output:
```

...
/home/glenn/.fonts: skipping, no such directory
...

```And a quick check of my home directory:
```

drwx------  2 glenn glenn      4096 Jun  2 18:45 .filezilla
-rw-------  1 glenn glenn 119531741 Apr 22 20:59 Flight Of Apollo 11.ogv
drwxr-xr-x  2 glenn glenn      4096 Jun  3 23:12 .fontconfig

```Do we have to create the .fonts directory in out home directory. I would have thought that would have been installed during setup?

---

### Post by Plueonic on 2012-06-03
Yes, and that's where you install fonts for a single user. The system wide fonts folder path is /usr/share/fonts/

---

### Post by mcduck on 2012-06-03
If you want to install fonts for your current user only (As opposed to installign tem system-wide), then yes, you need to create that directory.

On the other hand if you don't need to install fonts, or prefer having them available for all users, then there's no reason to create that directory.

---

### Post by Senior_Buckethead on 2012-06-03
Thanks for that.

I was just wondering since when fc-cache is running, its obviously looking for that directory, hence the error message. 
I'm installing my fonts in  /usr/share/fonts/, even though I'm the only user.

Glenn.

---

### Post by Plueonic on 2012-06-03
It's not an error message as it is just ignoring the directory since it doesn't exist.

Where you install the fonts depends on how you want its availability to be to other users. Since you're the only user on the system, it really doesn't matter where you install them, but IMO copying stuff to a directory in your home folder is generally easier :)

---

