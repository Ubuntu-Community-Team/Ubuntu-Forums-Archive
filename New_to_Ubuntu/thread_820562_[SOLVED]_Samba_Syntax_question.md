---
title: "[SOLVED] Samba Syntax question"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Sprogg2001 on 2008-06-06
Im trying to mount a network share but I am getting an error message


the command and output is as follows

```

sudo mount -t smbfs //192.168.1.66/big 1 (d)  /mnt/lan/desktop/big 1 (d)
bash: syntax error near unexpected token `('
```

it seems that the program does not like the fact that there are "()" in the name of the folder does anyone know how I get around this? The name is for the root of a network drive so its not like I can just mount another folder?

any suggestions?

---

### Post by spiderbatdad on 2008-06-06
```
sudo mount -t smbfs "//192.168.1.66/big 1 (d)"  "/mnt/lan/desktop/big 1 (d)"
```Have you tired that?

---

### Post by Sprogg2001 on 2008-06-06
slicker then snot! thank you spiderbatdad it worked

---

### Post by Sprogg2001 on 2008-06-06
Uh oh, just when things were going so well Ive hit the wall again ](*,)

after creating a .smbcredentails file as below

```

username=mywindowsusername
password=mywindowspassword

```

this is the command I have placed in my fstab file

```

"//192.168.1.66/big 1 (d)" "/mnt/lan/desktop/big 1 (d)" smbfs credentials=/home/username/.smbcredentials
```

save and close 

when I reload fstab  with sudo mount -a I get a [mntent]: line 11 in /etc/fstab is bad

What am I doing wrong?

---

### Post by spiderbatdad on 2008-06-06
Are you running 8.04? If so, setting up a network share is incredibly easy.
Set the permission, recursively on the folder you want to share: chmod -R 766 ~/Pictures  (for example).

Launch nautilus with admin rights: gksu nautilus.
Navigate to the folder /home/user/Pictures.
Right click the folder and select "sharing options."
Check all appropriate boxes, including allow guests, if you don't want other network users to be required to log into your account.

Its that easy. Pictures would then be read/write accessible via the local network...unless you are running a host-based firewall. You would need to configure the firewall settings, in that case.

---

### Post by sisco311 on 2008-06-06
In the fstab:
> //192.168.1.66/big**\040**1**\040**(d)    /mnt/lan/desktop/big**\040**1**040**(d) smbfs credentials=/home/username/.smbcredentials

\040 = ascii code of space(in octal)

---

### Post by Sprogg2001 on 2008-06-06
Im trying to auto mount a ntfs shared drive on boot

according to all the howtos I've read this means ensuring you can mount the drive manually from terminal and then editing /etc/fstab to mount the chosen directory at boot.

using the command 

```
sudo mount -t smbfs "//192.168.1.66/big 1 (d)"  "/mnt/lan/desktop/big 1 (d)"
```

works from the terminal to manually mount the network drive 


but adding the below to my fstab file does not work

```
"//192.168.1.66/big 1 (d)" "/mnt/lan/desktop/big 1 (d)" smbfs credentials=/home/username/.smbcredentials,gid=1234 0 0
```

---

### Post by Sprogg2001 on 2008-06-06
Thank you sisco311

it needed a little tweaking to work but I got it to mount using
```

//192.168.1.66/big\0401\040(d) /mnt/lan/desktop/big\0401\040(d) smbfs credentials=/home/username/.smbcredentials
```

thanks for all the help.

I have another question though? (please dont shoot! I'm new at all this!) 

I use hardy on a laptop, and my network connection is wireless and because of the stupid hardware maker I have to type FN + F10 to get wirless to turn on after bootup. 

So wont this mean that the fstab mount will fail at bootup and I will manually have to mount -a to get it to work after there is a network connection available?

---

### Post by spiderbatdad on 2008-06-06
That sounds likely. One possibility might be to make a small script to check that the lan connection is established then run the mount...add the script to the sessions manager.
Just throwing out an idea...

---

