---
title: "[SOLVED] Permissions"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by anderskitson on 2008-08-01
I have a whole drive where the permissions for each folder is set to root, I want to set them to myself, I can go in and right click on each folder and do it that way, is there a way to change permissions on the whole drive?

---

### Post by Darkade on 2008-08-01
Is this your installation hard drive? I ask because it is not wise to change all the permissions of the system files.
Why do you want to change the permissions and to which folder?

---

### Post by howlingmadhowie on 2008-08-01
open a terminal, cd to the directory and then enter:


sudo chown -R your_username:your_username .

and then your password

---

### Post by dca on 2008-08-01
I would recommend only files/directories in /home/myusername are set to that...  Everything outside, no...

---

### Post by Paqman on 2008-08-01
> **anderskitson said:**
> I have a whole drive where the permissions for each folder is set to root, I want to set them to myself, I can go in and right click on each folder and do it that way, is there a way to change permissions on the whole drive?

The file manager you're using (Nautilus) will only be running as a user, so won't have permission to modify files owned by root.

You can get around this by temporarily running Nautilus as root. Hit Alt F2 and enter:
```

gksu nautilus

```
Don't forget to close Nautilus as soon as you're done modifying things!

---

### Post by decoherence on 2008-08-01
> **Darkade said:**
> Is this your installation hard drive? I ask because it is not wise to change all the permissions of the system files.
Why do you want to change the permissions and to which folder?

I just want to re-iterate this. If this is the drive you're running ubuntu from, changing the permissions in this way will break things. You should only ever do this on a separate partition that contains only your user data. If that's the case, I'd go with howlingmanhowie's suggestion for being fast and easy. Just MAKE SURE YOU CD TO THE RIGHT DIRECTORY before you run the command or better yet, explicitly specify the path

sudo chown -R your_username:your_username /media/<name of your disk>

---

### Post by Paqman on 2008-08-01
> **decoherence said:**
> I just want to re-iterate this. If this is the drive you're running ubuntu from, changing the permissions in this way will break things.

+1

Sorry, I just assumed you were referring to a seperate data partition. If that isn't the case, DO NOT change the permissions.

---

### Post by anderskitson on 2008-08-01
wow alot of replies, um its just folders i copied to a new hardrive that kept the permissions, so nothing important

---

### Post by anderskitson on 2008-08-01
> **Paqman said:**
> The file manager you're using (Nautilus) will only be running as a user, so won't have permission to modify files owned by root.

You can get around this by temporarily running Nautilus as root. Hit Alt F2 and enter:
```

gksu nautilus

```
Don't forget to close Nautilus as soon as you're done modifying things!

thats what i was doing when i was right clicking and changing permissions

---

### Post by anderskitson on 2008-08-01
> **howlingmadhowie said:**
> open a terminal, cd to the directory and then enter:


sudo chown -R your_username:your_username .

and then your password

Thanks Exactly what I wanted

---

### Post by Paqman on 2008-08-01
> **anderskitson said:**
> thats what i was doing when i was right clicking and changing permissions

If use the button at the bottom marked "Apply permissions to enclosed files" you can chmod/chown the whole disk. It works the same as "chown -R" in the command line.

---

### Post by anderskitson on 2008-08-01
The funny thing is I was doing that and it wasn't changing them

never mind that works too, I just had to close it then go back and click apply for some reason

---

