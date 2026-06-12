---
title: "NAS Permission problem"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by il pepe on 2012-07-17
Hi,
I installed a NAS (Lacie) on my network.

I would like to use it as a storage for multimedia, as well as for backups...

On my ubuntu computer I'm able to mount the disk using fstab (making it a permant mount). 
This is the code i use:
//xxx.xxx.x.xxx/MyShare /home/xxx/Mounts/Lacie cifs user=xxx,password=xxx,file_mode=0777,dir_mode=0777    0    0

The problem now is that i don't have any rights in this folder. It is still under root...
I tried chmod, which didn't work (but mayby that is because my other computer is syncing)

Have i missed something here?

I'm using the same account to log in (lacie software) so the computers can see the same folders.
So i can see the disk, i can even rsync it (as superuser) but i'm not able to create files as a normal user. any tips?

---

### Post by Jacobonbuntu on 2012-07-17
I am definitely not a permissions expert, but this is how I did it, works perfectly. As you can see I have a password stored in my root directory (with a gksu-command - link in one of my quicklists, to change it if I want), according to [URL="http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/"]this manual
[/URL]
my fstab entry:
//192.168.0.104/werkmap_documenten/documenten\040Jacob /home/jacob/Netwerkmap cifs auto,iocharset=utf8,uid=jacob,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

---

### Post by il pepe on 2012-07-17
and then Jacob is your login for linux?

---

### Post by Tony Flury on 2012-07-17
> **Jacobonbuntu said:**
> I am definitely not a permissions expert, but this is how I did it, works perfectly. As you can see I have a password stored in my root directory (with a gksu-command - link in one of my quicklists, to change it if I want), according to [URL="http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/"]this manual
[/URL]
my fstab entry:
//192.168.0.104/werkmap_documenten/documenten\040Jacob /home/jacob/Netwerkmap cifs auto,iocharset=utf8,uid=jacob,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
+1
I think my exact details are slightly different(i have my NAS drive mounted directly in "/goflex") but i had the same permissions issues and the only way i could solve it was using a credentials file. I will post the config later if that would help.

---

### Post by il pepe on 2012-07-17
I know that trick.
I think you should put your credentials in your ./home directory, as it is saver there, as far as i know.

I didn't think this would help and was a bit lazy, will check it out very soon....

---

### Post by Jacobonbuntu on 2012-07-17
> **il pepe said:**
> I know that trick.
I think you should put your credentials in your ./home directory, as it is saver there, as far as i know.

I didn't think this would help and was a bit lazy, will check it out very soon....

nonono!
never store your credentials in a location that can be viewed or accessed without your password. my password as well as user name are in the credentials file in /root!!

---

### Post by il pepe on 2012-07-17
indeed, it is solved now.
Still weird, i guess.
Moving the credentials to another file is important for safety reasons, didn't think of it for solving the problem...
Anyway, fixed now. Thanks a lot!

---

### Post by il pepe on 2012-07-17
> **Jacobonbuntu said:**
> nonono!
never store your credentials in a location that can be viewed or accessed without your password. my password as well as user name are in the credentials file in /root!!

now i'm lost.
They say at this page:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
to set it in your /home?

---

### Post by Jacobonbuntu on 2012-07-17
> **il pepe said:**
> now i'm lost.
They say at this page:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
to set it in your /home?

Ah, I see what they do, they store the file in /home, but take away all "natural" priveleges from files, stored in /home, so you won't be able to acces the file without root permissions. I think it is a bit a complicated alternative to simply storing the file in your root directory. Normally, at home is the least safe location :) , as your /home directory can simply be viewed by other users that might log in.

---

