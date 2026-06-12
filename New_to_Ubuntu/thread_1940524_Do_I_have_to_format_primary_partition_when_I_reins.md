---
title: "Do I have to format primary partition when I reinstall ubuntu 11.10?"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by acimi66 on 2012-03-13
I have run into some issues with this install and I simply want to re-install it.

Is it necessary to re-format or delete the primary partition /root when re-stalling ubuntu 11.10?

---

### Post by Paqman on 2012-03-13
Yep. Back up any data before installing.

---

### Post by acimi66 on 2012-03-13
So, just to be clear...
reboot with CD
when I get to "what to you want to do" click "something else".
With the partition set-up click on primary and delete.
Do i then need to ADD NEW and make it "primary ext3".

Does that sound  about right?

thanks for your patience.

---

### Post by Paqman on 2012-03-13
No need to do manual partitioning at all actually. One of the automatic options will be to wipe the previous install and replace it.

The only time you'd need to do manual partitioning is if you have other partitions and/or operating systems on the drive. If thats's the case:
[LIST]
[*]Boot into the install disk
[*]Pick "something else..."
[*]Mark the partition you want to install to as filesystem EXT4, mount point /, and tick the box for "format".
[/LIST]

There's no need to delete and add the partition. Just tell it to format the existing one. EXT4 is an upgraded version of EXT3, and is the default filesystem for the current version of Ubuntu.

---

### Post by grahammechanical on 2012-03-13
You do not need to delete the partition. Is the size correct? Do you want to enlarge it or shrink it? You can do that.

Otherwise just tell the installer to install Ubuntu into that partition by setting the mount point to /

You can format if you wish. You can set the file format to ext3 if that is the existing file format but I think that if you change it to ext4 from ext3 then it will need a format.

If you do not format then the Ubuntu system files will be replaced but not the files in the /home folder. User configuration files are stored in the /home folder. So, if the issue is with configuration conflicts you may find that the fresh install has not solved the problem.

On the other hand the applications, such as Libreoffice and the browser and email programs will not loose their settings.

You can also use the same swap partition. Just mount it as swap.

Regards.

---

### Post by acimi66 on 2012-03-14
Yeah, thanks for the responses.

i have had some software conflicts with my sound system,web browser and broadcasting to an icecast2 server. I feel, in newbie attempt to download the right stuff, I've made things progressively worse.

I guess I'm thinking a new install will clean the slate, but you are right it might not actually solve the conflicts.

Thanks for the advice.

---

### Post by The Cog on 2012-03-14
If you use the custom partitioning, you can specify the / partition but choose not to format it. In this case, the installer tries to delete all the contentious directories (/var, /usr, /etc and so on ) before going on to install the OS. I think it leaves /home untouched, but I'm not really sure so you should have a backup just in case. Of course if /home was on a separate partition there should be no problem at all.

---

### Post by acimi66 on 2012-03-14
With windows I could not even think of doing this.

---

