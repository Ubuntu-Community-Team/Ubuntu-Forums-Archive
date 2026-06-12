---
title: "Smbmount"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by Balf on 2012-01-23
peter@peter-desktop:~$ smbmount "\\\\Sylvia\\Documents" "\\home\\peter\\share"

This is what I get:

mount error: could not resolve address for Sylvia: No address associated with hostname
No ip address specified and hostname not found

Can anyone tell me why this doesn't work. I have spent all morning Googling and trying different syntax.

If I mount the folder in "Places" and look at the properties of a folder in //Sylvia/documents I get        smb://sylvia/documents/     as the location. (it is on a win XP with no password)

/home/peter/share exists on my Ubuntu 10.04

I am trying to mount the shared folder automatically!

---

### Post by Cheesemill on 2012-01-23
Unless you are running an internal DNS server you probably have to use the IP address instead of the name for Sylvia. For example:
```
smbmount "\\\\192.168.1.10\\Documents" "\\home\\peter\\share"
```

Obviously using the correct IP for Sylvia.

---

### Post by Nick_Kats on 2012-01-23
Furthermore, you can always check the IP of the desired PC from your router's administration page.;)

---

### Post by Morbius1 on 2012-01-23
>  If I mount the folder in "Places" and look at the properties of a folder  in //Sylvia/documents I get        smb://sylvia/documents/     as the  location. (it is on a win XP with no password)You are in fact mounting the remote share from "Places" but the location you see is the location of the remote share not the location of the mount point.

Your mount point is located here: **/home/peter/.gvfs/documents on sylvia**

[COLOR=Blue]*You will have to enable "view hidden files" in Nautilus to see the ".gvfs" folder if you have not already done so.*[/COLOR]
>  I am trying to mount the shared folder automatically!     If you can live with the mount point in .gvfs then by far the easiest way to have this share automount is to use Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by satanselbow on 2012-01-23
Or use cifs

```

//path/of/share   /mount/folder   cifs   username=windowsuserid,password=windowspassword,uid=1000,_netdev,rw,nofail   0 0

```

You can leave out username/password if share is on an insecure xp box.

You will need a folder to mount the share to - I tend to create it under /mnt (you will have to chown it to your account) although it can be pretty much anywhere ;)

**rw** gives you read/write permissions and **nofail** prevents your linux box grinding to a halt if the xp machine is not available ;)


More good info here: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by Morbius1 on 2012-01-23
It's true that the "gvfs-mount smb://" method used by Nautilus, Connect to Server, and Gigolo do not inherently allow you to put a mount point anywhere you want you can always use a symbolic link:

```
ln -s /home/peter/.gvfs/"documents on sylvia" /home/peter
```And to rename it to what you originally wanted:
```
mv /home/peter/"documents on sylvia" /home/peter/Share
```

There is no right way or better way here - only alternate ways.

---

### Post by Balf on 2012-01-31
Thank you all for your replies.  It seems that Gigolo is the tool for me!
Peter :P

---

