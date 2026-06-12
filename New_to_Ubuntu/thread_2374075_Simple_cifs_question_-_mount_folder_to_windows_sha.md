---
title: "Simple cifs question - mount folder to windows share"
date: 2017-10-12
forum: New to Ubuntu
---

### Post by joetheshmo on 2017-10-12
Total newb to linux. looking to setup a lubuntu box for torrenting/get used to linux.
I have the share on windows setup, user1 has full perms on the share and ntfs

I have added cifs to the linux box. I added this line to /etc/fstab

**//server1/data /home/user1/media cifs username=user1,rw,users 0 0 **

On reboot I see the mount, can browse it, but I just cant seem to write to it. I read somewhere that I have to change owner of this folder as it will be root. Is that correct ?

I tried 

sudo chown -R User1:User media
sudo chmod -R 774 media

Stilll no luck - anyone help - - T'is driving me nuts.

J./

---

### Post by joetheshmo on 2017-10-12
OK, seen this in another post.

[B][COLOR=#000000]adding the following line in /etc.rc.local[/COLOR]
[COLOR=#000000]
Code:
[COLOR=#417394]mount[/COLOR] /var/media/pi[/COLOR]
[/B]

If I run that mount command manually it works, but I cant find the rc.local file ? anyideas?

---

