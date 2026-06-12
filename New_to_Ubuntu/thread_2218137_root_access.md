---
title: "root access"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2014-04-19
I have just upgraded to Ububtu 14.04 and find that I am not allowed permission to view the root, or even own some programs. Why is this? I'm the only one that uses the computer so who owns these things? Also, where do programs go when you install them? I've installed google earth, but am having some issues with it. I need to edit a file in the folder but have no idea where it is. Any help greatly appeciated.

---

### Post by pfeiffep on 2014-04-19
Are you using nautilus to find the file?
If so I suggest using this line
```
gksudo nautilus
```

---

### Post by migs73 on 2014-04-19
Also some files are hidden (prefixed with a dot . ) to be able to see these just press 'cntrl+H' when in Nautilus.

---

### Post by bapoumba on 2014-04-19
I would recommend to be very careful using a file browser as root.

To the OP, which files are you trying to have a look at ? Any error message ?

---

### Post by HappyAsHellas on 2014-04-19
Apparently I don't have gksudo installed. I was originally trying to find a file named qt.conf in google earth as I cannot see any photos in this application.

---

### Post by bapoumba on 2014-04-19
> **HappyAsHellas said:**
> Apparently I don't have gksudo installed. I was originally trying to find a file named qt.conf in google earth as I cannot see any photos in this application.

How can you tell gksudo is not working ? It is not a package.

---

### Post by HappyAsHellas on 2014-04-19
When I typed gksudo nautilus in the terminal box it replied "gksudo not installed".

---

### Post by grahammechanical on 2014-04-19
If you want to see folders and files files in what is called the root folder/directory then open File Manager and look for Computer in the left panel.

Apparently the Ubuntu developers do not see any reason for users to edit system files. So, since 13.10 gksu has been depreciated. In other words it is not installed. If we try to load Nautilus or Gedit using gksudo we get the message that gksu is not installed and also advice on how to install it. It is simple to do but editing system files can be dangerous.

Root owns many files and folders. For example, /etc is owned by root and root can Create  and Delete files. Others can only access files. I have no problem accessing/seeing the folders and files in my root directory. If I want to edit those files or paste another file into one of the folders, well then, this is a different matter. I need root or administrator privileges and Ubuntu has an easy way of giving me that.

One of the reasons why a lot of work is being done to replace the Xserver is because X has and can give other programs root access. And that could be a security vulnerability.

One of the great things about Linux is the fact that it allows the user to endlessly modify the OS. One of the worse things about Linux is the fact that it allows the user to endlessly modify the OS.

Regards.

---

