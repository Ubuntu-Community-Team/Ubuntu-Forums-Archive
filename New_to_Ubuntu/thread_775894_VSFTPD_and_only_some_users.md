---
title: "VSFTPD and only some users?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by dag0 on 2008-04-30
I just installed vsftpd. Have edited the vsftp.conf and don't alow anonymous logins. The folder ftp is in /home directory and I want to add only 2 users to this folder and jail them only to stay only in /home/ftp.

I tried to add user1 user2 on a previous install of ubuntu but they had access to rest of the computer(only read). I also want those 2 user to use password for login also...How do I do this?
Just a newbie, an old newbie so its little hard to learn...Not a youth anymore :lolflag:


Dag

---

### Post by superprash2003 on 2008-04-30
considering you are a newbie.i prefer you install proftpd and gproftpd..gproftpd is the GUI(Graphical User Interface) for proftpd.Therefor you can configure your ftp server graphically and dont have to worry about editing conf files..it would be easier!!

---

### Post by Monicker on 2008-04-30
Disregard previous info I gave about chroot_local_user , this is more appropriate for you, since you only want to jail 2 users:


[I]chroot_list_enable

    If activated, you may provide a list of local users who are placed in a chroot() jail in their home directory upon login. The meaning is slightly different if chroot_local_user is set to YES. In this case, the list becomes a list of users which are NOT to be placed in a chroot() jail. By default, the file containing this list is /etc/vsftpd.chroot_list, but you may override this with the chroot_list_file setting.[/I]

---

### Post by dag0 on 2008-04-30
> **superprash2003 said:**
> considering you are a newbie.i prefer you install proftpd and gproftpd..gproftpd is the GUI(Graphical User Interface) for proftpd.Therefor you can configure your ftp server graphically and dont have to worry about editing conf files..it would be easier!!

Thanks alot superprash2003..
This was so much easier :) And it works...


Best Regards
dag0

---

### Post by dag0 on 2008-04-30
> **Monicker said:**
> Disregard previous info I gave about chroot_local_user , this is more appropriate for you, since you only want to jail 2 users:


[I]chroot_list_enable

    If activated, you may provide a list of local users who are placed in a chroot() jail in their home directory upon login. The meaning is slightly different if chroot_local_user is set to YES. In this case, the list becomes a list of users which are NOT to be placed in a chroot() jail. By default, the file containing this list is /etc/vsftpd.chroot_list, but you may override this with the chroot_list_file setting.[/I]

Thanks for tips Monicker.

I did go for gproftpd, looks more simple for me...

But thanks anyway :)  I'll use your tip later when I'm gonna try out vsftpd when I get more experience with Ubuntu.


Best Regards
dag0

---

### Post by Monicker on 2008-04-30
> **dag0 said:**
> Thanks for tips Monicker.

I did go for gproftpd, looks more simple for me...

But thanks anyway :)  I'll use your tip later when I'm gonna try out vsftpd when I get more experience with Ubuntu.


Best Regards
dag0

I may give gproftpd a whirl myself.  It looks kinda slick.  :)

---

