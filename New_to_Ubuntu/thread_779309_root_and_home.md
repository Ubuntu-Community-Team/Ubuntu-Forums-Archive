---
title: "/root and /home"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by tentel on 2008-05-02
When I installed Ubuntu, I did it according to a how to.

It told me to make three partitions, a swap and two ext3s
it told me to make one of the ext3 to have a mount point /home, and the other one to just have /

How do I know that this worked and my files are on one partition, and my os on the other?


it didn't ask me to select what goes where or anything.




thanks
-Tim

---

### Post by mlentink on 2008-05-02
Are your files in your home directory? Can you see them?
Try downloading a file. Does it show up in your own user directory?

If all seems perfectly normal, it is.

You can always check by booting up with a Lice-CD and mounting the separate partitions independently of another.

---

### Post by forestpixie on 2008-05-02
open a terminal and use this command - home should show up on a seperate partition

```
mount
```

this is how mine show up
/dev/sda4 on /home type ext3 (rw)
/dev/sda1 on / type ext3 (rw,errors=remount-ro)

obviously your partitions are likely different

---

### Post by Monicker on 2008-05-02
> **tentel said:**
> When I installed Ubuntu, I did it according to a how to.

It told me to make three partitions, a swap and two ext3s
it told me to make one of the ext3 to have a mount point /home, and the other one to just have /

How do I know that this worked and my files are on one partition, and my os on the other?


it didn't ask me to select what goes where or anything.




thanks
-Tim


Just type "mount" in a terminal session.  You should see one partition mounted to /, and another partition mounted to /home.

---

### Post by wermeulen on 2008-05-02
Or type "df", gives you size information as well. For example, if I run it:
```
wermeulen@home:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             52015036   2482968  46910664   6% /
varrun                 1024160       100   1024060   1% /var/run
varlock                1024160         0   1024160   0% /var/lock
udev                   1024160        56   1024104   1% /dev
devshm                 1024160       188   1023972   1% /dev/shm
lrm                    1024160     38176    985984   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda6            376345508   1000912 356377860   1% **/home**
/dev/sda5             52015036    184272  49209360   1% /storage
gvfs-fuse-daemon      52015036   2482968  46910664   6% /home/vincent/.gvfs

```
You see that I have three paritions (/dev/sda1, /dev/sda6 and /dev/sda5) and /home is on the second one.

---

### Post by tentel on 2008-05-02
eek
I can't seem to make heads or tails of this:

tim@tim-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tim)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=tim)


I have a lot of partions on my hard drive.

one for vista
one for hp recovery
one for Mcafee backup
ubuntu /home
ubuntu /
and ubuntu swap




I can't tell which is which though.


this is what df gives me:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             11626784   2348332   8692484  22% /
varrun                  972356       104    972252   1% /var/run
varlock                 972356         0    972356   0% /var/lock
udev                    972356        76    972280   1% /dev
devshm                  972356        44    972312   1% /dev/shm
lrm                     972356     38176    934180   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda7             29334236    294648  27561208   2% /home
gvfs-fuse-daemon      11626784   2348332   8692484  22% /home/tim/.gvfs
/dev/scd0              7747684   7747684         0 100% /media/cdrom0



so i'm not usre...

the one that is a little over 11 gb is what I made as / , but it looks like that one is /home, not /root.






-Tim

---

### Post by nhandler on 2008-05-02
> **tentel said:**
> eek
I can't seem to make heads or tails of this:

tim@tim-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tim)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=tim)


I have a lot of partions on my hard drive.

one for vista
one for hp recovery
one for Mcafee backup
ubuntu /home
ubuntu /
and ubuntu swap




I can't tell which is which though.




-Tim

It is set up correctly. /dev/sda6 is mounted at /, and /dev/sda7 is mounted as /home.

---

### Post by tentel on 2008-05-02
alright cool.


thanks everyone.

I just wanted to make sure that everything was alright.

I didn't want to get my whole system set up perfectly and then find out that i couldn't reinstall the os if needed.


-Tim

---

### Post by couzin2000 on 2008-05-02
I don't believe you're required to know what goes where.

What this looks like is that you were recommended to make a separate partition for your [FONT="Courier New"]/home[/FONT] folder, which holds all your "My Documents" stuff (if you're coming from a Windows background like me).

What you can do is, once you're in Ubuntu, open a terminal (**Applications > Accessories > Terminal**) and type at the prompt ```
mount
```
What you should see is a bunch of lines that tell you what devices are "mounted" where.
The [FONT="Courier New"]/[/FONT] folder is the root folder, where everything starts -- kinda like "C:\".
The [FONT="Courier New"]/home[/FONT] folder is your My Documents folder. Linux almost always has the same config from one distro to the next, so this is almost always true. Go into **Places > Computer**, and you'll see all this. 
Mounting a partition#2 into [FONT="Courier New"]/home[/FONT] is simple: in terminal, type:```
sudo mount /dev/sdb1 /home
```
My drive is "sdb1", but yours might well be "hda" or "hdb"... lookup your [FONT="Courier New"]/media[/FONT] folder and take a look at what you have in there, and use the name of that second partition instead.

If you see that you get an error message, I suggest you take a look at this here: **[https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")**. Should explain how the [FONT="Courier New"]mount[/FONT] command works.

My recommendation to you is that if you are really bent on using this way of setting up, you may wish to take a look at what's *really* hidden inside your current [FONT="Courier New"]/home[/FONT] folder. When you decide to mount [FONT="Courier New"]/home[/FONT] to somewhere else, you'll most likely have to copy whatever is currently in [FONT="Courier New"]/home[/FONT].
To see what's hidden, go to **Places > username** (at the top). When the folder is open go to **View > Show hidden files**.

Hope this helps!

---

