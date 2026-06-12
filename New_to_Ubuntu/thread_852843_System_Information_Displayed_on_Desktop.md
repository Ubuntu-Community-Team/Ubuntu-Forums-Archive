---
title: "System Information Displayed on Desktop"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-07-08
[http://www.compiz-themes.org/content/preview.php?preview=2&id=73972&file1=73972-1.png&file2=73972-2.jpg&file3=&name=SlicknesS+Emerald](http://www.compiz-themes.org/content/preview.php?preview=2&id=73972&file1=73972-1.png&file2=73972-2.jpg&file3=&name=SlicknesS+Emerald)

I want to have system info displayed on my desktop similar to what's in the image there. How can I go about doing this?

Thanks,
SMRT

EDIT: nvm, figured it out

---

### Post by webofunni on 2008-07-08
The sysmonitor screenlet < [http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/](http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/) > will provide that ;-)

---

### Post by tjwoosta on 2008-07-08
actually in that picture they are using conky with a custom .conkyrc

```
sudo apt-get install conky
```

then make a .conkyrc file

```
sudo gedit ~/.conkyrc
```
then just copy and paste someones .conkyrc into it and save 
(you may need to edit some small things like using wlan0 instead of eth0 for network monitor and stuff)

to make conky open press alt-f2 and type conky in the box

to make conky run at every login  go to system-preferences-sessions (click add and put conky in the command box)

here is a thread where people have been posting there .conkyrc files for all to use
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by aktiwers on 2008-07-08
That looks a lot like Conky :)

Try it out, you can use this post for inspiration and tips:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

