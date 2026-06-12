---
title: "Unrecognized mount option &quot;jqfmt=vfsv0&quot;"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by Oneeyd on 2012-06-27
To start I am extremely new to Linux. I installed Ubuntu 12.04 LTS the other day. My end goal is to have a server that me and some friends can use to mess around with some app development and I wouldn't mind learning about MySQL, nginx (or any web server stuff), and whatever else I can learn or get into along the way. I decided to go ahead and make a Ubuntu server using only command line to jump right in. I followed "The perfect server guide" and everything seemed to work fine except when I edit fstab adding in "usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0" I get an error when attempting to "mount -o remount/". 

"Unrecognized mount option "jqfmt=vfsv0" or missing value 
mount: / not mounted or bad option

Any help on this would be greatly appreciated.

---

### Post by Gone fishing on 2012-06-27
Maybe a typo

You should have
```
usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0
```

not

```
usrjquota=**quota**.user,grpjquota=**quota**.group,jqfmt= vfsv0
```

I also cheat and setup using ssh and on another box with Firefox and a gui and then paste in the commands saves typos.

---

### Post by Oneeyd on 2012-06-27
I feel a little dumb, it was a typo.

---

### Post by Gone fishing on 2012-06-27
Sorry about feeling dumb.:lolflag:

Please mark as solved - also why not set up from another box (could even be Windows if you use putty - though I don't know why you would want to use that OS) and SSH into the server and then you can copy and past from Firefox straight into the terminal of your server through the SSH connection.

---

