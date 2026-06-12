---
title: "How to change permission"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Garrion on 2008-08-26
Hey there everybody. I am a total newb at this, so be nice ^^

In any case, i have a problem. i have a fresh installation of ubuntu right, and i was having some problems with mounting my windows partition so i went to this website [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Unmounting%20a%20partition%20to%20prevent%20unwanted%20access](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Unmounting%20a%20partition%20to%20prevent%20unwanted%20access)

to do the whole auto mount thing. Now uh... i can't write anything in my windows main partition T-T says something about not having privileges. I tried checking out other forums and all, and they were very confusing to me. Can anyone help me change the permission for both of my windows partition? this is what my fstab looks like

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=1c33024f-efac-4b3f-9d92-e9097e1e60f2     /               ext3        defaults,errors=remount-ro    0   1
# /dev/disk/by-uuid/320D-180E
UUID=320D-180E       /media/drv0       vfat         defaults      0   0


# /dev/sda4
UUID=365e7942-852f-4f97-a971-9c623d469094      none            swap        sw          0   0


#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 vfat rw,user,fmask=0111,dmask=0000 0 0

---------------------------------------------------

can someone please help me? T-T it would be much appreciated..

---

### Post by jgrabham on 2008-08-26
> **Garrion said:**
> Hey there everybody. I am a total newb at this, so be nice ^^

In any case, i have a problem. i have a fresh installation of ubuntu right, and i was having some problems with mounting my windows partition so i went to this website [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Unmounting%20a%20partition%20to%20prevent%20unwanted%20access](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Unmounting%20a%20partition%20to%20prevent%20unwanted%20access)

to do the whole auto mount thing. Now uh... i can't write anything in my windows main partition T-T says something about not having privileges. I tried checking out other forums and all, and they were very confusing to me. Can anyone help me change the permission for both of my windows partition? this is what my fstab looks like

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=1c33024f-efac-4b3f-9d92-e9097e1e60f2     /               ext3        defaults,errors=remount-ro    0   1
# /dev/disk/by-uuid/320D-180E
UUID=320D-180E       /media/drv0       vfat         defaults      0   0


# /dev/sda4
UUID=365e7942-852f-4f97-a971-9c623d469094      none            swap        sw          0   0


#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 vfat rw,user,fmask=0111,dmask=0000 0 0

---------------------------------------------------

can someone please help me? T-T it would be much appreciated..

Right, if you poen a terminal then type > sudo chown username /media/xyz
where 'username' is your login name and 'xyz' is what your partition is mounted as, look in the /media/ folder to find out.

---

### Post by drubin on 2008-08-26
> **jgrabham said:**
> Right, if you poen a terminal then type 
where 'username' is your login name and 'xyz' is what your partition is mounted as, look in the /media/ folder to find out.

It would be better to use 
```
sudo chown **-R** username /media/xyz 
```

The -R tells it to include subdirectories.  **R**ecursively

---

### Post by jgrabham on 2008-08-26
> **rubinboy said:**
> It would be better to use 
```
sudo chown **-R** username /media/xyz 
```

The -R tells it to include subdirectories.  **R**ecursively

Oops, knew that as well, I'm an idiot sometimes *looks embarrassed*.

---

### Post by drubin on 2008-08-26
> **jgrabham said:**
> Oops, knew that as well, I'm an idiot sometimes *looks embarrassed*.

I am sure you did know it, It was more for the OP because I am also relatively sure they didn't. :) 

Every one forgets things.

Prime example why posting support  questions should be done in the forums and not PM'S. We got each others backs. :)

---

### Post by Garrion on 2008-08-26
Well, i tried the sudo sudo chown username /media/xyz  doesn't work

did the -r thing, and i got a LOT of lines popping up. all of it had : operation not permitted.

---

### Post by halitech on 2008-08-26
did you substitute username for your Ubuntu username ?

---

### Post by Garrion on 2008-08-26
Oh also forgot, the windows partition are all in fat32 format. hope that helps.

---

### Post by Garrion on 2008-08-26
yes i have

---

### Post by jgrabham on 2008-08-26
> **Garrion said:**
> yes i have

Could you run ```
ls /media/
``` and post the output for us please?

---

### Post by drubin on 2008-08-26
> **halitech said:**
> did you substitute username for your Ubuntu username ?

> **Garrion said:**
> Well, i tried the sudo sudo chown username /media/xyz  doesn't work

did the -r thing, and i got a LOT of lines popping up. all of it had : operation not permitted.

Another way of giving this command out to users is 
```
sudo chown -R `whoami` /media/xyz
```

This way it will fill in their username, or if they change it to their real username it will still work :)

---

### Post by shane19174 on 2008-08-26
Doesn't that -R have to be uppercase as well? (I ask partly for my own benefit, but maybe the problem lies there?)

---

### Post by Garrion on 2008-08-26
cdrom  cdrom0  drv0  drv1  sda1  sda2  tdm

is what that ls /media/ shows me. and uh... -r 'whoami'?

---

### Post by Garrion on 2008-08-26
haha the whoami line doesn't work too. i keep getting operation not permitted =\

---

### Post by drubin on 2008-08-26
> **jgrabham said:**
> Could you run ```
ls /media/
``` and post the output for us please?

ls gives very little details could you rather use the -lah params.
```
ls -lah /media/
```

This way we are listing details about them (-l) all of them (a) and in a nice size format (h).

Could you also please post the out put of this command. 
```
df -h
```

---

### Post by Garrion on 2008-08-26
total 84K
drwxr-xr-x  8 root root 4.0K 2008-08-27 01:23 .
drwxr-xr-x 22 root root 4.0K 2008-08-25 03:58 ..
lrwxrwxrwx  1 root root    6 2008-08-25 05:21 cdrom -> cdrom0
drwxr-xr-x  2 root root 4.0K 2008-08-25 05:21 cdrom0
drwxr-xr-x 36 root root  16K 1970-01-01 07:30 drv0
drwxr-xr-x  2 root root 4.0K 2008-08-25 07:54 drv1
-rw-r--r--  1 root root    0 2008-08-27 00:38 .hal-mtab
-rw-------  1 root root    0 2008-08-27 00:10 .hal-mtab-lock
drwxr-xr-x 36 root root  16K 1970-01-01 07:30 sda1
drwxrwxrwx 16 root root  32K 2008-08-27 01:26 sda2
drwxr-xr-x  2 root root 4.0K 2008-08-25 07:42 tdm


hope this helps

---

### Post by Garrion on 2008-08-26
total 84K
drwxr-xr-x  8 root root 4.0K 2008-08-27 01:23 .
drwxr-xr-x 22 root root 4.0K 2008-08-25 03:58 ..
lrwxrwxrwx  1 root root    6 2008-08-25 05:21 cdrom -> cdrom0
drwxr-xr-x  2 root root 4.0K 2008-08-25 05:21 cdrom0
drwxr-xr-x 36 root root  16K 1970-01-01 07:30 drv0
drwxr-xr-x  2 root root 4.0K 2008-08-25 07:54 drv1
-rw-r--r--  1 root root    0 2008-08-27 00:38 .hal-mtab
-rw-------  1 root root    0 2008-08-27 00:10 .hal-mtab-lock
drwxr-xr-x 36 root root  16K 1970-01-01 07:30 sda1
drwxrwxrwx 16 root root  32K 2008-08-27 01:26 sda2
drwxr-xr-x  2 root root 4.0K 2008-08-25 07:42 tdm


hope this helps

---

### Post by drubin on 2008-08-26
> **shane19174 said:**
> Doesn't that -R have to be uppercase as well? (I ask partly for my own benefit, but maybe the problem lies there?)

Yes it should be an upper case **R**.

---

### Post by Garrion on 2008-08-26
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              10G  3.0G  6.5G  32% /
varrun                121M  120K  121M   1% /var/run
varlock               121M     0  121M   0% /var/lock
udev                  121M   48K  121M   1% /dev
devshm                121M  232K  121M   1% /dev/shm
gvfs-fuse-daemon       10G  3.0G  6.5G  32% /home/shahril/.gvfs
/dev/sda1              28G   17G   12G  60% /media/drv0
/dev/sda1              28G   17G   12G  60% /media/sda1
/dev/sda2              18G   17G  1.1G  94% /media/sda2

haha forgot this one. soprry ^^0

---

### Post by jerome1232 on 2008-08-26
I thought fat32 doesn't support permissions and that it was all determined on mounting for fat32. IE an fstab like follows should make it writeable by all users

**/dev/sda1 /media/sda1 vfat auto,users,rw,exec,umask=000 0 0**

---

### Post by Garrion on 2008-08-26
Hey guys, uh... if i don't reply, i am asleep. Haha its 3 AM here and i got class at 8 AM so... I'll stay up as late as i can and check this post out frequently. haha i really hope someone can help solve this problem =/ its getting annoying not being able to write your own data into it.

---

### Post by Garrion on 2008-08-26
oh really? its not supported? i thought ubuntu supports fat32?

---

### Post by halitech on 2008-08-26
it does support fat32 but it's different then NTFS or any of the *nix file systems in the way it is designed.

check this out

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

look for the section on fat32 drives

---

### Post by Garrion on 2008-08-26
Hrmm... so how then? should i change the formatting or something? that's gonna take a lot of work, and if possible.. would like to avoid it ^^0 but will do it if you think its wise.

---

### Post by halitech on 2008-08-26
check my previous post, I edited it with a link to a way of mounting fat32 drives

---

### Post by jerome1232 on 2008-08-26
I meant fat doesn't support permissions, linux can write to it just fine :)

---

### Post by Garrion on 2008-08-26
i see. will do ^^ thanks for the link

---

### Post by Garrion on 2008-08-26
Hmm.. if i were to follow it. does this means i need to edit my fstab? if yes. ... uh.. i'm not sure how to do it...

---

### Post by halitech on 2008-08-26
just make sure you back it up first
from the terminal
```
sudo cp /etc/fstab /etc/fstab-backup
```

you would use
```
gksu gedit /etc/fstab
```

that will open it in gedit so you can edit the file easily

---

### Post by Garrion on 2008-08-26
alright thanks. i'll tell you what happens tomorrow ^^ too tired to think straight, and i got an early class tomorrow. hahaha see you all and hope this works. Thanks for all of your time everyone!

---

### Post by jerome1232 on 2008-08-26
so according to psychocats tut it would look like this

```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=1c33024f-efac-4b3f-9d92-e9097e1e60f2 / ext3 defaults,errors=remount-ro 0 1
# /dev/disk/by-uuid/320D-180E
UUID=320D-180E /media/drv0 vfat iocharset=utf8,umask=000 0 0


# /dev/sda4
UUID=365e7942-852f-4f97-a971-9c623d469094 none swap sw 0 0


#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat iocharset=utf8,umask=000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by drubin on 2008-08-26
> **halitech said:**
> .....

Try list things in order they should happen in often when you are coping things other people have told you you do them in the order you see them. Often you do not read the whole thing (I include my self).

---

### Post by halitech on 2008-08-26
good point, I added it as an after thought. I have corrected the order :)

---

### Post by Garrion on 2008-08-27
Uh... i don't understand what rubin boy said... but i did as psychocats showed. Still no permissions =P

---

### Post by trash on 2008-09-15
> **jerome1232 said:**
> I thought fat32 doesn't support permissions and that it was all determined on mounting for fat32. IE an fstab like follows should make it writeable by all users

**/dev/sda1 /media/sda1 vfat auto,users,rw,exec,umask=000 0 0**

umask=000 worked like a charm:)

---

### Post by trash on 2008-09-15
I spoke to soon, now i can read and delete but can't write a file/video... i suspect another problem since delete is actually writing(as far as i know). I may just reformat it ext3 since i have no windows machines but it still would be nice to figure this out!

Garrion, did you get anywhere with this problem?

---

### Post by Mornedhel on 2008-09-15
> **trash said:**
> [...] delete is actually writing(as far as i know).


Minor correction : deleting files depends on the *directory* write permission.

Straight from Wikipedia :


[LIST]
[*]The *read* permission, which grants the ability to read a file. When set for a directory, this permission grants the ability to read the **names** of files in the directory (but **not** to find out any further information about them, including file type, size, ownership, permissions, etc.)
[*]The *write* permission, which grants the ability to modify a file. When set for a directory, this permission grants the ability to modify entries in the directory. This includes creating files, deleting files, and renaming files.
[*]The *execute* permission, which grants the ability to execute a file. This permission must be set for executable binaries in order to allow the operating system to run them. When set for a directory, this permission grants the ability to traverse its tree in order to access files or subdirectories, but not see files inside the directory (unless *read* is set).
[/LIST]

---

### Post by trash on 2008-09-15
> **Mornedhel said:**
> Minor correction : deleting files depends on the *directory* write permission.

Straight from Wikipedia :


[LIST]
[*]The *read* permission, which grants the ability to read a file. When set for a directory, this permission grants the ability to read the **names** of files in the directory (but **not** to find out any further information about them, including file type, size, ownership, permissions, etc.)
[*]The *write* permission, which grants the ability to modify a file. When set for a directory, this permission grants the ability to modify entries in the directory. This includes creating files, deleting files, and renaming files.
[*]The *execute* permission, which grants the ability to execute a file. This permission must be set for executable binaries in order to allow the operating system to run them. When set for a directory, this permission grants the ability to traverse its tree in order to access files or subdirectories, but not see files inside the directory (unless *read* is set).
[/LIST]

DOH!!! Got any ideas why my user/client side can delete a file created by the user on the server but not write a file to the server? (btw both server and client have the same user/password so it should be even easier than it is right now lol)

---

### Post by Mornedhel on 2008-09-15
> **trash said:**
> DOH!!! Got any ideas why my user/client side can delete a file created by the user on the server but not write a file to the server? (btw both server and client have the same user/password so it should be even easier than it is right now lol)

Well it *could* be the directory permission thing.

To give an example (some formatting to make things clearer) :

```

# Create a directory.
~/argh$ mkdir urgh
# Make it r-x.
~/argh$ chmod 500 urgh
~/argh$ ls -l

[...]
dr-x------  2 luser luser 4096 2008-09-15 20:28 urgh
[...]

~/argh$ cd urgh
# Create an empty file.
~/argh/urgh$ touch foo

touch: cannot touch `urgh/foo': Permission denied

# As root, create an empty file and give its ownership to our user "luser"
~/argh/urgh$ su
~/argh/urgh$ touch foo
~/argh/urgh$ chown luser foo
~/argh/urgh$ logout

# Confirm luser owns file, can write to it. At this point luser still hasn't write permissions to directory "urgh"...
~/argh/urgh$ ls -l

-rw-r--r-- 1 luser root 0 2008-09-15 20:31 foo

# ... but he's not trying to *create* a file, just to write to it.
~/argh/urgh$ echo "I have write permission" > foo
~/argh/urgh$ cat foo

I have write permission


```However, this doesn't explain why you can delete the file. In the above example, "luser" can't delete urgh/foo. What kind of server is it ?

Also, having the same username on your server and client does not mean it's the same user. They just happen to share a name.

Third edit : A group problem, possibly.

---

### Post by trash on 2008-09-15
It's a 'simple' nfs, which i had working when the share was on the same drive as the server... since i added a second drive i am now mounting that 2nd drive on the server then sharing it and i'm thinking that its what is causing the problem.(everything mounts without error)
I personnaly think nfs should deal with the permissions better but since i am really not sure where the problem is i guess i shouldn't lay blame hehe. I may try ext3 tonight and see if it's any better.
Thanks!

---

