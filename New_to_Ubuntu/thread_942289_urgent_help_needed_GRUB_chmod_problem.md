---
title: "urgent help needed GRUB chmod problem"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by ferronica on 2008-10-09
i am getting weired problem, i just double clicked menu.lst and saved it tooo without doing sudo, as normal user. When i checked "ls -l /boot/grub/menu.lst" here is the output --:


student@student-desktop:~$ ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 11:54 /boot/grub/menu.lst
after that i did --- "sudo chmod 755 /boot/grub/menu.lst"
but not effect same output:(:(:(

student@student-desktop:~$ sudo chmod 755 /boot/grub/menu.lst
student@student-desktop:~$ ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 11:54 /boot/grub/menu.lst
student@student-desktop:~$ 

Please help me:(:( i am using ubuntu 8.04 Gnome

---

### Post by REDace0 on 2008-10-09
I'd say try logging in as root and doing the chmod then. Maybe you can't change the permissions because root owns the file? ```
su -
``` will let you temporarily be root in the terminal.

---

### Post by WWSmith36 on 2008-10-09
I find it strange that the permission on the file got changed.  Did you issue a recursive chmod command at some point?  I would also suggest looking for other files that may have had their permissions changed as well.

---

### Post by ferronica on 2008-10-09
sorry i didint get you, i tried to Login as su -

student@student-desktop:~$ sudo chmod -c 755 /boot/grub/menu.lst
mode of `/boot/grub/menu.lst' changed to 0755 (rwxr-xr-x)
student@student-desktop:~$ ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 11:54 /boot/grub/menu.lst
student@student-desktop:~$ sudo chmod -c 755 /boot/grub/menu.lst
mode of `/boot/grub/menu.lst' changed to 0755 (rwxr-xr-x)
student@student-desktop:~$ ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 11:54 /boot/grub/menu.lst
student@student-desktop:~$ sudo chmod -c 000 /boot/grub/menu.lst
mode of `/boot/grub/menu.lst' changed to 0000 (---------)
student@student-desktop:~$ ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 12:32 /boot/grub/menu.lst
student@student-desktop:~$ su
Password: 
su: Authentication failure
student@student-desktop:~$ su
Password: 
su: Authentication failure
student@student-desktop:~$ su
Password: 
su: Authentication failure
student@student-desktop:~$ su -
Password: 
su: Authentication failure
student@student-desktop:~$ su -
Password: 
su: Authentication failure
student@student-desktop:~$

---

### Post by Enternald on 2008-10-09
maybe "sudo -i" may work

---

### Post by REDace0 on 2008-10-09
I believe root in Ubuntu initially doesn't have a password so that you can't log in as root. You have to go to System>Administration>Users and Groups, hit Unlock, and then check root's properties to manually add one before you can log in. Just had to do that on my fresh install here.

---

### Post by ferronica on 2008-10-09
here is the output :(

student@student-desktop:~$ sudo -i
root@student-desktop:~# chmod 000 /boot/grub/menu.lst
root@student-desktop:~# ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 12:32 /boot/grub/menu.lst
root@student-desktop:~# chmod 644 /boot/grub/menu.lst
root@student-desktop:~# ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 12:32 /boot/grub/menu.lst
root@student-desktop:~# chmod 644 -c /boot/grub/menu.lst
mode of `/boot/grub/menu.lst' changed to 0644 (rw-r--r--)
root@student-desktop:~# ls -l /boot/grub/menu.lst
-rwxrwxrwx 1 root root 6078 2008-10-09 12:32 /boot/grub/menu.lst
root@student-desktop:~#

---

### Post by ferronica on 2008-10-09
Bump----

---

