---
title: "Loosing shared folders"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by ugmanuk on 2013-06-28
Please help, iam testing Lubuntu in my client server enviroment. When via nautilus i add a shared folder after reset, the conection to the marker is lost. I need to do this on the graphical enviroment to explain this to the final user.

Thanks, and sorry for my awful english.

---

### Post by TheFu on 2013-06-28
I've never used Nautilus, but I use Lubuntu daily. **pcmanfm** is the default file manager.  I don't know if there is a way to tell any file manager to remember a mount "forever" or not. Does the nautilus man page help?

Anyway, if you want to automatically mount remote file storage, why not just use a remote mount feature inside the /etc/fstab?  That way the end-user doesn't need to do anything. The mount is there and available if the machine is running.  For non-Windows file shares, the user/group and other permissions will be retained if the remote server is setup properly.  For Windows, I think even the mount is owned by the user so only 1 user can access the mounted storage - uuuug. Nasty.  Mounting via samba or cifs of a remote Windows share isn't hard.

The type of remote mount needed would be handy to know. What OS is the other machine running and how it is sharing files?  BTW, file sharing isn't really considered client/server to most people.

I hope someone that uses the GUI for this stuff replies.

---

### Post by Morbius1 on 2013-06-28
> When via nautilus i add a shared folder after reset, the conection to the marker is lost.
I'm assuming you mean you created a Samba share of a folder within Nautilus and that after a reboot the share disappears?

After your next reboot immediately run the following command:
```
net usershare info --long
```
That will list all the Samba shares you created in Nautilus and how they are configured.

If that command shows the shares you created then the problem is something else but for now just see if the shares you created actually go away.

[COLOR=#0000cd]* Then again, I may have entirely misunderstood the question.*[/COLOR]

---

