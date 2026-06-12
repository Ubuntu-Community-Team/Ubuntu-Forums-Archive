---
title: "Lubuntu boot partition full?"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by LYJ7trm on 2014-04-11
Trying to update the Lubuntu base and I get an error msg saying the boot partition is almost full.

It says to empty the Trash (done) and run sudo apt-get clean (done) but I still can't update.

I can't manually delete anything from the /boot directory.  What should I do?

---

### Post by Dreamer Fithp Apprentice on 2014-04-11
> **LYJ7trm said:**
> Trying to update the Lubuntu base and I get an error msg saying the boot partition is almost full. . . .

I can't manually delete anything from the /boot directory.  What should I do?You shuold be able to. Did you try as root? You can start a file browser as root by opening a terminal and entiering```
sudo pcmanfm
```If you want to do it that way, probably you want to delete the older kernel files. Common practice would be to delete all but the 2 newest.

Or you could do this:```
sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname  -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^  ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
sudo apt-get autoremove
sudo apt-get clean

```

Or go to:
[https://startpage.com](https://startpage.com)
and enter:
full boot partition

Then click the icon that looks like a magnifying glass.
I just did that. The first 9 entries (not counting the 3 ads) look like they should all have at least one method of doing this. Choose your pick.

---

### Post by Impavidus on 2014-04-11
Don't manually delete the files. This will confuse the package manager. The dpkg command is safe.

Assuming you run Lubuntu 13.10 you can simply use```
sudo apt-get autoremove
```

---

### Post by Dreamer Fithp Apprentice on 2014-04-12
> **Impavidus said:**
> Assuming you run Lubuntu 13.10 you can simply use```
sudo apt-get autoremove
```Are you saying "sudo apt-get autoremove" ALONE will remove the old kernels, etc.? That the dpkg command is redundant? If so, is that a recent change?

---

### Post by Impavidus on 2014-04-12
Yes, sudo apt-get autoremove alone will remove old kernels and yes, it's a recent change. It works on 13.10 (and 14.04 I assume), not on older versions, but older versions of Lubuntu are unsupported anyway.

---

### Post by Dreamer Fithp Apprentice on 2014-04-15
> **Impavidus said:**
> Yes, sudo apt-get autoremove alone will remove old kernels and yes, it's a recent change. It works on 13.10 (and 14.04 I assume), not on older versions, but older versions of Lubuntu are unsupported anyway.Thanks, Impavidus. Interesting.  That's a pretty big change, considering autoremove didn't use to do anything like that. I bet it's been written into a lot of scripts
where that behaviour wouldn't be desired. In fact, I'll have to go through all my own. I don't like to remove old kernels too quickly. I presume if they added that to it's function, they at least added some sort of safety check to make sure it doesn't purge the running kernel or the new kernel that hasn't been booted yet on a system that has just been upgraded. But I like to keep the old kernels aroung longer than that. If it weren't for you I wouldn't know my scripts may have a nasty surprise action. Frankly I think that is worse than ill-considered on the part of whoever made that change - it's darned arrogant. If you add a substantial action to old command that has the possibility of breaking scripts, you ought to add it as the action of a new option, not just assign a new meaning to an old command.

---

### Post by Impavidus on 2014-04-16
Packages that have been installed manually and many packages installed by default during installation of Ubuntu are marked as manually installed. The remaining packages, those that have been installed as dependencies of other packages that were installed, are marked as automatically installed. When no package depending on a specific automatically installed package remains, the automatically installed package becomes autoremovable.

New kernel images and headers are installed by updating a metapackage. This updated metapackage has new dependencies, pulling in the new kernel package. The old kernel package is no longer depended on, which would cause it to be autoremovable. To prevent this, because it is indeed useful to keep an old kernel, the installation script ensures that the kernel packages are marked as manually installed, even though they are really automatically installed.

The change is, as far as I know as I don't run 13.10 myself, that the installation script of the new kernel checks for old kernels. It keeps one old kernel and marks the older ones as automatically installed, whereafter they become autoremovable. So the change is in the package installation script, not in apt-get autoremove.

In synaptic you can manually mark packages as manually or automatically installed. I'm sure it can be done by command line too.

And it's quite common for new releases to break old scripts. I've had to rewrite my wallpaper switcher a few times. But that's why these changes happen at a new release, not at a normal update.

---

### Post by Dreamer Fithp Apprentice on 2014-04-18
Thanks again, Impavidus, for such a thorough and interesting mechanistic eplanation.  That makes a lot more sense than just changing the meaning of the command. And the mechanism described won't break anything of mine. One old one that won't go away until I tell it to is quite good enough. As a Ukrainian chap I once knew used to say "I give them back their honor".

---

