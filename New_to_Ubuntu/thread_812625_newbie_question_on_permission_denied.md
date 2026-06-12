---
title: "newbie question on permission denied"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by user2000 on 2008-05-30
hi,

if i get a permission denied error i have to use sudo in terminal which is fine with me. but suppose i am using the normal graphical interface e.g. Places -> Computer and then i try to move a file or edit a file. it gives an error saying permission denied. how do i remove that permission denied error? i dont want to use terminal all the time.

thank you very much.

---

### Post by Inxsible on 2008-05-30
> **user2000 said:**
> hi,

if i get a permission denied error i have to use sudo in terminal which is fine with me. but suppose i am using the normal graphical interface e.g. Places -> Computer and then i try to move a file or edit a file. it gives an error saying permission denied. how do i remove that permission denied error? i dont want to use terminal all the time.

thank you very much.If you are going to move a file anywhere but your home folder, it is going to give you permission denied since that's how Linux is made. It only allows the user to modify the home files.

you can use the terminal and sudo to copy/move files to any place other than the home. - Highly Recommended.

you can also open the file browser in root mode and copy/move files - Not recommended at all.

---

### Post by k@e on 2008-05-30
To have all permissions in the graphical file management tool use this command:

```
gksudo nautilus
```

Be careful when messing with system files. There is a good reason why a non-super user does not have full permissions.

---

### Post by hyper_ch on 2008-05-30
what do you want to copy/move where`?

---

### Post by sam_delta on 2008-05-30
as sayd in the previous post, click ALT+F2 and type "gksudo nautilus", youll have full permissions you can even make a quick launch icon in the panel to that command, and each time you press it, youll get a full permissions file manager

BUT permissions are there for a reason, you shouldnt be messing with system files on a regular basis, you should save your normal files under the home folder, which you can read write with no problems

sam

---

### Post by x88a on 2008-05-30
```
sudo nautilus
```

---

### Post by MaxVK on 2008-05-30
As a newcomer to Ubuntu and Linux myself I fully understand the frustration when you are trying to move files about, but when I first got here I read all the dire warnings about not running the file manager as root, and got down working out how the OS works (To some extent at least).

The people here know what they are about and its worth listening to them.

Your OS is secure because it has these restrictive permissions, so if you do go for "sudo nautilus" be very, VERY careful what you do, and don't use it unless it is absolutely necessary.

---

### Post by user2000 on 2008-05-31
thankyou everyone for your replies. actually am running apache and the directories are /var/www and /usr/lib/cgi-bin which i am interested in.  think i will have to change them to the home folder for further use. also i tried to install ubuntu on a 4gb usb stick but after installation i got a grub error 2. :( i wish it worked out of the box like the live cd. damn. any ideas on what can be done? 

thank you again

---

