---
title: "Samba Shares with Windows98SE"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by jamillikan on 2008-10-06
I give up!  I'm nearly ready to thrown in the towel with Hardy Heron.  I have tried everything I can think of but each time I try to map the share in Windows98SE and it asks for the password, I enter the password I created with the command:

smbpasswd -a USERNAME

and EVERY TIME it tells me it is incorrect.

This was easily accomplished with Feisty & Gutsy, but here it seems impossible.  If ANYONE knows how to resolve this issue TODAY, please let me know; otherwise, I'm throwing in the towel and moving back to Gutsy.  I don't want to, mind you, but I'll be forced to as I must share a folder in /home/pauline/mydata with Windows98SE.

Thanks for reading my rant.

Joe

---

### Post by indytim on 2008-10-06
I don't know if this will specifically address your 98SE problems, but I just used the reference to build a new SAMBA share in 8.04 to XP.  Outstandingly easy and worked "out of the box".  In the event that you are not aware of the app, see the 2nd thread in the link.

[http://ubuntuforums.org/showthread.php?t=938154&highlight=samba]("http://ubuntuforums.org/showthread.php?t=938154&highlight=samba")

Good Luck,

IndyTim

---

### Post by superprash2003 on 2008-10-06
in your terminal type cat /etc/samba/smbusers  .. if you see the USERNAME you created there in the output, then its fine, otherwise you have a problem there..

---

