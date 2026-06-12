---
title: "MOUNT --bind Wrong using... help me"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by Altanmur on 2013-09-11
[COLOR=#404040][FONT=Roboto]Hello everyone!

I want to symlink on ftp. I used MOUNT --BIND.
SYNTAX:
   mount --bind olddir newdir
But I did :
   mount --bind newdir olddir
   or
   mount --bind ~/www /var/www

binding is complete and empty that is not binding the my think

then replace place dirs

   mount --bind /var/www ~/www

then both empty

checking mount list

$ mount

/home/user/www on /var/www type none (rw,bind)
/var/www on /home/user/www type none (rw,bind)&#65279;

my /var/www is replace the empty.

How can i recovery my projects in  /var/www ?

-------------------------------------------------------------------
testing another directories

I did same testing dirs

do UNMOUNT is working and remove the MOUNT LIST. 
BUT /var/www is EMPTY

Where is my web sites ? help me [/FONT][/COLOR]

---

### Post by TheFu on 2013-09-11
I have no idea - I'd look in /lost+found for orphaned files or just restore from a backup. 

I've never used mount --bind before.  I just use regular symlinks for like the last 20+ yrs.
**ln -s /var/www /someplace/else/anywhere**

Still, mount --bind or --rbind is interesting. Thanks for bringing it up.

---

### Post by Werne on 2013-09-11
Like TheFu said, look in lost+found, they might be there.

By the way, is there a logical reason for mounting $HOME/www into /var/www, then mounting /var/www back into $HOME/www?:confused: As far as I get, once you mount $HOME/www to /var/www, files will be present in both and any changes done to any of the two directories will be reflected in both of them since the /var/www is actually $HOME/www mounted to that folder. I have a lot of bound folders and it always worked that way for me.

And I never used the --bind option, I use mount -o bind to mount folders (or just add it to /etc/fstab). As far as I understand, --bind and -o bind are the same, so that shouldn't be the issue unless you messed up something in the process (or worse, made a typo).

---

