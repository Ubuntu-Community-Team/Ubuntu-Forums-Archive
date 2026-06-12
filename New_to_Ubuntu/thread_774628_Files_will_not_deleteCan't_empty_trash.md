---
title: "Files will not delete/Can't empty trash"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by gpilkay on 2008-04-29
This is an odd incredibly basic thing that I just can't figure out...I have a new 8.04 install, and I have some files I copied over from a thumb drive.  They were recently moved to the trash.

I can not wipe them from the trash, as it says that it does not have the permissions to do so.  There's a few other old folders that it won't erase either for the same reason. I'm putting this in 'beginner' as it is super basic but totally throwing me.

I know it sounds dumb but can anyone tell me how to delete a file?

---

### Post by floke on 2008-04-29
In the terminal do (as root, so use sudo prefix or su):

chown [yourname].[yourname] -R /home/[yourname]/.local/share/Trash

Should be good to go.

* Edit: This assumes you're using gnome 2.22 **

---

### Post by gpilkay on 2008-04-30
Sorry, it didn't work.  The files in the trash (and one on the desktop using a different path) are still there, saying they will not delete as permission is denied.  I hope I don't have to reload an entire system to get rid of several 'locked' folders full of useless old backups, but if needs be, I will.

Is it perhaps possible to change the 'lock' status (which I have no idea how it was generated anyway) to a normal one so I could wipe them?

---

### Post by Shazaam on 2008-04-30
You can do this...
```
gksudo nautilus
```
to VERY CAREFULLY browse to your /Desktop directory, your .Trash and root's .Trash (control+h to view hidden files) to delete the files in question.
Just remember, when you use this whatever file/folder you delete is gone.

---

### Post by enigmaniac23 on 2008-04-30
Can you just navigate to the trash folder and use sudo to delete them?

```
cd /home/[yourname]/.local/share/Trash
sudo rm filename.file
```

It's likely that you deleted the file originally (put it into the trash) via sudo, giving the file root permissions in the trash (that's where the lock comes from).  Now you can't delete it with your user permissions.

---

### Post by SlappyPappy on 2008-04-30
Dude, no biggie, I had the same thing going on after I had been moving a bunch of files with a flash drive too. In terminal you can do this:

sudo rm -r /home/slappypappy/.Trash/"Old PC Documents"

Now be sure to change slappypappy to your user name and change "Old PC Documents" to whatever the directory that is in your trash you want to get rid of. If I'm not mistaken you need to use the quotes if you have spaces between words describing your directory.

You should be cleared for takeoff. Good luck!   :)

---

### Post by Fran89 on 2008-04-30
Something similar happened to me only the files only appear in Trash:/// not my or root's .Trash folder i cant rename delete or delete no matter how hard i try... :( WHY?! 

(the files were for my Wireless card 8187B, which works fine)...

I uploaded a screenshot of the error, its good to point out that altho the folders have the same name for some reason they are different when i see them in the directory

---

### Post by Fran89 on 2008-05-04
*bump* sorry i dont usually do that but i need to know... im running hardy could it be something with nautilus's new backend?... its just annoying to see files there..it may have also have to do with the files (altho the permisions were mine not root's) anybody with the same problem?


EDIT: managed to delete them.... it seems hadry has another place to store trash the solcion is found here: [http://ubuntuforums.org/showthread.php?t=781859](http://ubuntuforums.org/showthread.php?t=781859)

---

### Post by NeilE888 on 2008-05-17
Just to contribute to the discussion; I had the same problem with a couple of file folders deleted from an external USB drive which sat in the desktop deleted items folder and wouldn't allow complete deletion, and wouldn't allow changing of permissions either - permissions seemed to be the problem. The solution in this case turned out to be that there was a hidden folder called .Trash-1000 in the external drive (CTRL-H to view) and from there I could change file permissions to allow deletion - and once I'd done that I could empty them from the deleted items folder.

I suspect that this was a transient problem which has been solved by recent updates to Hardy ... but just in case ...

---

### Post by Oldsoldier2003 on 2008-05-17
> **NeilE888 said:**
> Just to contribute to the discussion; I had the same problem with a couple of file folders deleted from an external USB drive which sat in the desktop deleted items folder and wouldn't allow complete deletion, and wouldn't allow changing of permissions either - permissions seemed to be the problem. The solution in this case turned out to be that there was a hidden folder called .Trash-1000 in the external drive (CTRL-H to view) and from there I could change file permissions to allow deletion - and once I'd done that I could empty them from the deleted items folder.

I suspect that this was a transient problem which has been solved by recent updates to Hardy ... but just in case ...
.Trash-1000 is the trash bin belonging to user 1000 (the first user created on the system) you will also find a .Trash-0 sometimes, which is roots trash.

---

