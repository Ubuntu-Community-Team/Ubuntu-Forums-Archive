---
title: "Few file removal questions"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-06-05
Okay I had wine installed, but uninstalled it via packet manager and selected complete removal. But it did not delete everything I wanted it to. So I did a search for everything call 'wine' in home and nothing came up. I then did a search in the file system and found all the stuff before in the screen shot. I then tried deleting some of it and it wont let me.

I then wanted to know if it was fine to delete all the files inside of: /var/cache/apt/archives ? In there it just contains all the .deb files that are taking up quite a lot of space. I tried deleting some and it wont let me. How do I do so?

Lastly I installed a few games. They were called ArmyOps(Americas Army) and Enemy territory. I downloaded them and installed via terminal but curious how I can COMPLETELY remove these games as well?

Thanks a lot!

---

### Post by iaculallad on 2008-06-05
Look if there's an uninstall script on the directory where you installed your ArmyOps and Enemy Territory.

---

### Post by Paqman on 2008-06-05
Everything outside of your /home folder is owned by root. That means you don't have permission to delete them as a regular user. That's a really good thing, it's what stops malware from being able to infect your system.

Generally, deleting stuff outside /home is bad unless you know exactly what it is. You can clear out /var/cache/apt/archives if you want, though. It's the cache of the .deb files downloaded by the package manager.

Two ways you can do this:

1) The terminal.
```

sudo rm -rf /var/cache/apt/archives

```
The sudo prefix is what will let you gain root privileges temporarily and do the deleting. Always be careful when deleting stuff as root. Double check you've got the right folder.

2) Nautilus (the file manager)
You'll need to run Nautilus as root. Hit Alt-F2 and type:
```

gksu nautilus

```
Make sure you close Nautilus as soon as you've finished whatever you need to do as root.

As for the games you installed, it really depends on how you installed them. If they were .deb files you can just use Synaptic. Anything else could be a bit of a fiddle. Maybe they have uninstall scripts? Have you checked their websites?

---

### Post by Xiong Chiamiov on 2008-06-05
Apt will store old files you've downloaded incase you want to install them again.  To remove them, use
```

sudo aptitude autoclean

```
or 
```

sudo aptitude clean

```
Type "aptitude help" in the terminal for more information.

The easiest way of getting rid of wine is to remove it through the package manager, then delete the hidden folder in your home directory:
```

rm -r ~/.wine

```

If you installed things through the package manager, then removing them is easy.  If you compiled them, it's also easy if you still have the folder you compiled from.  If you ran a .bin script, or some such, then you'll have to hope they wrote an uninstall script too.

---

