---
title: "Howto : Burn Iso with Right-click in Thunar"
date: 2006-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Sabutay on 2006-09-01
Here is a custom action for the file-manager Thunar. It's useful to burn an iso file with a right-click.

First install burn:
```

sudo aptitude install burn
```

Edit **/etc/burn.conf** for your system(As root)

Open Thunar, *Edit > Configure custom actions*
Click on the add button, and fill it with these informations. 
    
```
Name: Burn Iso
Command: Terminal -T "Burn ISO" -x sudo burn -I -n %f
File pattern: *.iso
Appears if selection contains: Other Files
```

Then save it.

---

### Post by frodon on 2006-09-01
Just for the record, gnome users would be able to do the same installing burn then [nautilus-action]("http://www.grumz.net/")
The command to add would be the same.

Short nautilus-action guide : [http://doc.gwos.org/index.php/Custom_Command_Nautilus](http://doc.gwos.org/index.php/Custom_Command_Nautilus)

Nice guide Sabutay ;)

---

### Post by Sabutay on 2006-09-01
Thanks for the link. Now I can make more custom actions, looking the examples  through your link. Actually, it's possible to create custom actions with Burn  app. Maybe, burn a whole directory,burn a playlist, etc.

---

### Post by tenjin1 on 2007-12-17
also to mount ISO:
(assuming there is directory /media/iso)
```
sudo mount %f -o loop -t iso9660 /media/iso 
File pattern: *.iso
Appears if selection contains: Other Files
```

and to unmount ISO:
```
sudo umount %f /media/iso
File pattern: *.iso
Appears if selection contains: Other Files
```

---

