---
title: "Added Microsoft account, can't see Onedrive"
date: 2021-01-01
forum: New to Ubuntu
---

### Post by Trelo on 2021-01-01
So I did a fresh install of 20.10 and added my Google and Microsoft accounts.  Now on home I can automatically see my Google drive files ready to be mounted and opened but the same is not true for Onedrive.  How do I add it? 
Thanks in advance.

---

### Post by mrdc76 on 2021-01-01
OneDrive is not supported. I think there might have been a commercial product for this purpose.

---

### Post by llamakc on 2021-01-01
The package onedrive is in the Universe repository. Start with installing that

```
sudo apt install onedrive
```

And then in a terminal enter ```
onedrive
```

---

### Post by Trelo on 2021-01-01
> **llamakc said:**
> The package onedrive is in the Universe repository. Start with installing that

```
sudo apt install onedrive
```

And then in a terminal enter ```
onedrive
```

Thanks I did that but now it's asking me 

Enter the response uri:

How do I proceed from here.  Thanks in advance.


EDIT:  Oh I managed.  It's trying to download the whole lot of files tho, is there any way I can just see the files and download what I need when I need it?  My SSD is not big enough to download my whole onedrive.

---

### Post by howefield on 2021-01-01
Have you tried

```
onedrive --help
```

This will give you all the available options.

If this doesn't work out for you, I'd suggest using rclone to mount your Onedrive as if it were a local drive, viewable from the file manager. A little bit of setting up but nothing difficult.

---

