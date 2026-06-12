---
title: "Alien Arena not opening"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by piyushshri on 2011-11-16
I downloaded Alien Arena yesterday from Ubuntu Software Center. I was installed correctly on 11.10. I added a shortcut to launcher. Today when I clicked on that, it didn't start.
Then I typed "alien-arena" in the terminal. I showed up this message:
```
piyushshri@piyushshri-desktop:~$ alien-arena
ln: creating symbolic link `/home/piyushshri/.config/alien-arena/data1': Permission denied
using /home/piyushshri/.config/alien-arena/arena for writing
Could not exec default.cfg
Could not exec config.cfg
Console initialized.
--------- [Loading Renderer] ---------
Master server at 69.136.224.226:27900
Sending shutdown to 69.136.224.226:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx

```Please help me running the game.

---

### Post by LowSky on 2011-11-17
looks like a permissions problem to the folder in question.

start the file manager using sudo

```
gksu nautilus
```


go to that folder, right click on it and make sure the permissions are set so anyone can edit the folder/files.

try to load the program see if that works.

---

### Post by -LynX- on 2011-11-17
> **piyushshri said:**
> I downloaded Alien Arena yesterday from Ubuntu Software Center. I was installed correctly on 11.10. I added a shortcut to launcher. Today when I clicked on that, it didn't start.
Then I typed "alien-arena" in the terminal. I showed up this message:
```
piyushshri@piyushshri-desktop:~$ alien-arena
ln: creating symbolic link `/home/piyushshri/.config/alien-arena/data1': Permission denied
using /home/piyushshri/.config/alien-arena/arena for writing
Could not exec default.cfg
Could not exec config.cfg
Console initialized.
--------- [Loading Renderer] ---------
Master server at 69.136.224.226:27900
Sending shutdown to 69.136.224.226:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx

```Please help me running the game.

Someone has already opened a bug on this. To solve this run alienarena as root twice. After that you can run alien arena as normal user.

---

### Post by qunungnauraq on 2011-11-21
After running alien arena as root twice it will now play, but I cannot change and save settings. Also the other aliens do not appear.

---

### Post by idoerg on 2012-02-16
You need to add the user to group "games"
sudo gkpasswd -a username games

---

### Post by BuMRK on 2012-02-17
Better workaround than sudo, remove the symlink and create a folder there.

rm -v ~/.config/alien-arena
mkdir -p ~/.config/alien-arena

---

