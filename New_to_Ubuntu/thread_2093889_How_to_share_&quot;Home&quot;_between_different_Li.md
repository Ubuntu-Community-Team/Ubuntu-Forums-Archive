---
title: "How to share &quot;Home&quot; between different Linux distros?"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by asifnaz on 2012-12-12
I have ubuntu as only OS on my computer . Now I decide to dual-boot it with fedora . How to share home between both of them..?

---

### Post by rnerwein on 2012-12-12
> **asifnaz said:**
> I have ubuntu as only OS on my computer . Now I decide to dual-boot it with fedora . How to share home between both of them..?
hi
expect you have your home of ubuntu on /dev/sda6 and your /home on fedora on /dev/sda9 .
then in ubuntu you can mount fedoras (/home) /dev/sda9 on ubuntus /mnt or the ubuntu /dev/sda6 (/home) on /mnt in fedora.
best is if you get on both systems the same UID and GID for your users. then will have no problems with permissions (the names of the users doesen't matter).
cheers

---

### Post by asifnaz on 2012-12-12
Thank you for reply . Should I prefer mounting home on Ubuntu or fedora ..?

---

### Post by audiomick on 2012-12-12
If you do not have your Ubuntu /home on  a separate partition, here are instructions to do that. I always install with a separate /home partition.
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")


If you do have a separate /home partition, I believe you would be able to mount this partition to /home in Fedora during the install. I haven't done this, but I believe it should be possible. If you set up the same user on both installs, they should then, as far as I know, both use the same /home/user folder.

So, it is, as far as I know, possible. Despite this, I would not recommend doing it. It is ok to use the same /home/user folder for two installs of the same version of the a particular Linux distribution. Even sharing a /home/user between an older and a newer version of a Linux distribution is generally not that dangerous. The more different the two installs are, however, the more likely you are to have problems sharing a /home/user folder. Ubuntu and Fedora are quite different. One is Debian based, the other Red Hat.

If you want to have files available to both systems, you are better off to set up a Data partition. It is no big deal to change the default save path of your programs to go there, or just use "save as" to save to there. 

If you are really ambitious, you might want to look into sym-links from the /home/user folder of the respective installs to your data partition.

---

### Post by ibjsb4 on 2012-12-12
I can't see that working either and also think a data partition would be a better way to go.  The home folder also contains configuration files and I think that would cause conflicts between the two.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by CaptainMark on 2012-12-12
The way I've found works best for me is:

/dev/sda1 contains distro1's root directory (20gb),

/dev/sda2 contains distro1's home directory (210gb),

/dev/sda3 contains  distro2's root directory (20gb) which has symlinks for each main folder within its home folder pointing to /dev/sda2

/dev/sda4 contains swap space

This works well for me as I only have 7 main directories in my home directory so it doesn't take long to symlink them across from distro2 like so:
```
mount /dev/sda2 /mnt/home
ln -s /mnt/home/Music ~/Music
```

EDIT: I suppose I should have mentioned that you need to permanently mount /dev/sda2 at /mnt/home with fstab this was just a quick scribble

---

### Post by GordThompson on 2012-12-12
> **audiomick said:**
> If you do not have your Ubuntu /home on  a separate partition, here are instructions to do that. I always install with a separate /home partition.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This has been a topic of curiosity for me lately. Many of my friends are becoming increasingly interested in Linux for their home machines and are asking me for advice. I've been reluctant to tell them that they need to do "custom" installs, including repartitioning for a separate /home partition, because I don't want them to get frightened off ("That's too technical; I'll just stick with Windows.") and I also don't want to have to do all of their installs for them. ;)

On reading some of the comments in the Linux Mint forums I gathered that they tend to recommend a separate /home partition because the preferred way to upgrade Mint is to do a clean install of the new version. OTOH, I gather that Ubuntu supports (recommends?) in-place upgrades that preserve the existing files in /home.

So, if a user has a backup regimen that includes their entire /home hierarchy, and if they don't want to dual-boot or share their /home with multiple Linux installs, is there still a significant advantage to creating a separate /home partition?

Thanks in advance for any and all advice.

Gord 
(I've supported Linux servers for years, but I'm still a rookie on the desktop side.)

---

### Post by audiomick on 2012-12-12
> **GordThompson said:**
>  is there still a significant advantage to creating a separate /home partition?

I can't say definitively. I only have to deal with my machines and one other belonging to a friend of mine. But only a couple of weeks ago I had to re-install on the one other, and having had set it up initially with a separate /home saved me the bother of copying back the backup I made before the re-install. Not for the first time, I might add. Sure, you can keep backups, and copy back files and what not. If you can just re-mount the /home, then all of that is still there, along with all your config files and everything else. 

The down side is, if there is anything odd in there, it gets carried over. This also applies to my friend's machine. Her daughter must have tried connecting a mobile phone to it at one point. This left an icon on the desktop that is orphaned and wont let itself be removed. Because of this, and because I think it is just time for a clean out, I will be doing a complete fresh install for her next version upgrade, and copying back all her data files but no config files other than firefox and evolution into the newly formatted /home partition.

Anyway, we shouldn't hijack the thread, actually...

---

### Post by asifnaz on 2012-12-12
> **CaptainMark said:**
> The way I've found works best for me is:

/dev/sda1 contains distro1's root directory (20gb),

/dev/sda2 contains distro1's home directory (210gb),

/dev/sda3 contains  distro2's root directory (20gb) which has symlinks for each main folder within its home folder pointing to /dev/sda2

/dev/sda4 contains swap space

This works well for me as I only have 7 main directories in my home directory so it doesn't take long to symlink them across from distro2 like so:
```
mount /dev/sda2 /mnt/home
ln -s /mnt/home/Music ~/Music
```EDIT: I suppose I should have mentioned that you need to permanently mount /dev/sda2 at /mnt/home with fstab this was just a quick scribble

Nicly explained . I will defiantly give it a try and ask here if need help . Thank you for you reply

---

### Post by SeijiSensei on 2012-12-12
The most important difference between Ubuntu and Fedora in terms of sharing /home is that RedHat-flavored distros begin numbering users at 500 while Debian-flavored distros start at 1000.  Since filesystem permissions are attached to the numeric user and group IDs, they need to be consistent across the distros.  I usually replace the regular users on RH machines with the list from Ubuntu so my username works correctly in both places.  You can edit /etc/passwd and /etc/group to accomplish this, but do not simply replace one file with the other.  There are a variety of "system" users on each platform, and they may not have comparable UIDs and GIDs.

The easiest solution is to install Fedora and let it create /home in its own partition.  Then you can edit its /etc/passwd and /etc/group replacing the users at 500 and above with those from Ubuntu.  (To do this easily, create a "mount point" in Fedora called /mnt/ubuntu, then mount the Ubuntu partition there.  You'll have access to all your Ubuntu files.)  Run chown and chmod on Fedora's /home to match.  

If you want to do a test run to see if the two distros can share the same partition, try this:

```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu # replace sda1 with the appropriate partition
cd /home
sudo rsync -av username /opt   # backs up /home/username
sudo rm -rf username/*
cd /mnt/ubuntu/home
sudo rsync -av username /home

```

This will transfer the contents of /home/username in Ubuntu to /home/username in Fedora.  Now log out and log back in to see what works and what doesn't.  If you have problems, use "rm -rf /home/username/*" then reverse the rsync command above to copy back what you backed up to /opt.

If it works, edit /etc/fstab in Fedora to mount the home partition at boot.

---

