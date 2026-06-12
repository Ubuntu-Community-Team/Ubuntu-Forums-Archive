---
title: "Deleting Updates"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by kendor on 2008-09-06
I have just installed ubuntu 8.04 for the very first time and found 974 updates, which if i installed would use up all my download MB for the next 6 weeks can anyone tell me how to delete these and start from scratch,any help will be appreciated as i am a brand new Linux user.

                        regards kendor

---

### Post by iaculallad on 2008-09-06
> **kendor said:**
> I have just installed ubuntu 8.04 for the very first time and found 974 updates, which if i installed would use up all my download MB for the next 6 weeks can anyone tell me how to delete these and start from scratch,any help will be appreciated as i am a brand new Linux user.

                        regards kendor

That would just be a warning popping out, It has not been installed yet. You could ignore it if you want. To remove the cached files from this updates, you could do the command below on your terminal:

```
sudo apt-get clean
```

---

### Post by perlluver on 2008-09-06
974, I only had 263 as of yesterday.  How did you get so many.  This was on a fresh install too.

---

### Post by Elfy on 2008-09-06
> **iaculallad said:**
> That would just be a warning popping out, It has not been installed yet. You could ignore it if you want. To remove the cached files from this updates, you could do the command below on your terminal:

```
sudo apt-get clean
```

He's trying to save bandwidth - if he ran apt-get clean he'd need to download them again to update.

You could change what gets updated - software sources in system >admin menu - update tab (I think) only have security enabled. But I would rather do that after I had a complete update.

That said - I'd be with perlluver - that is a lot of updates, did you have an old hardy disc maybe.


Edit - see this [http://ubuntuforums.org/showthread.php?t=911579](http://ubuntuforums.org/showthread.php?t=911579) - 966 updates on a preinstalled 8.04.

---

### Post by iaculallad on 2008-09-06
> **forestpixie said:**
> He's trying to save bandwidth - if he ran apt-get clean he'd need to download them again to update.

You could change what gets updated - software sources in system >admin menu - update tab (I think) only have security enabled. But I would rather do that after I had a complete update.

That said - I'd be with perlluver - that is a lot of updates, did you have an old hardy disc maybe.


Edit - see this [http://ubuntuforums.org/showthread.php?t=911579](http://ubuntuforums.org/showthread.php?t=911579) - 966 updates on a preinstalled 8.04.

Is the OP not asking on how to "delete these and start from scratch"?

---

### Post by Elfy on 2008-09-06
Yes I think he is - but I'm not sure he knows what he's asking for ;) at somepoint he's going to need to do it and I guess he won't want to donwload them twice.

---

### Post by iaculallad on 2008-09-06
> **forestpixie said:**
> Yes I think he is - but I'm not sure he knows what he's asking for ;) at somepoint he's going to need to do it and I guess he won't want to donwload them twice.

Ok. Got your point, He might as well need aptonCD to do that then :)

---

