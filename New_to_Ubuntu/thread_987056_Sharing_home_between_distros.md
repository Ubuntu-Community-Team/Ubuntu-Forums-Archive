---
title: "Sharing /home between distros"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by LittleKoy on 2008-11-19
I've been using Ubuntu for more than a year. Since my linux-skills/knowledges developed, and I'm going to but new computer, I would like to go out and explore the linux world (aka, trying various distros). 

My usual fs structure is the following:

A partition mounted as / = Ubuntu OS
A partition mounted as /home = you can guess ;)

Now, my question is: can I split into several partitions my "OS partition" and make all distros share the same /home? Would they mess it?

---

### Post by philinux on 2008-11-19
I would suggest a shared data partition and let each distro manage their own home.

---

### Post by bubba_169 on 2008-11-19
Sharing a /home can get messy as different distros use different default setting for their applications. All of these setting are stored in your home. Using a data partition as suggested would be your best bet!

---

### Post by amac777 on 2008-11-19
If you do share the /home partition across several distros, I would recommend you use a different username for the users on the different distros to keep their respective home directories separate from one another. 

The reason is each distro might not have the same versions of programs and therefore sharing the settings for a same-named user (stored in the user's home directory) might mess up the settings for a different version on the other distro.

---

### Post by LittleKoy on 2008-11-19
I'm glad I asked ^^

So, suppose I have several "data directories" inside my home, for example Anime, Movies, Music, Work, etc.. I can I share those among the users, while keeping homes separated?

---

### Post by ShodanjoDM on 2008-11-19
Aside from the Desktop and configuration (a.k.a hidden) folders, I think it's safe to share other folders, specifically if they're only contains multimedia files.

As for me, I am sharing several hidden folders between my Arch and Ubuntu accounts, but they're just saved games and my mail client's inbox (both use the same version of the mozilla thunderbird, though).

---

### Post by LittleKoy on 2008-11-19
Sorry, I typed it wrong, I was asking how can I do that... A separated partition mounted as /home/username/data?

---

### Post by philinux on 2008-11-19
I would have a partition /data all on its own.

---

### Post by Paqman on 2008-11-19
Sharing a /home partition between distros is absolutely fine, provided you use different user names on each distro (as amac777 says).

I've had my machine set up this way for years, with no issues at all.

---

### Post by ShodanjoDM on 2008-11-19
Hmm, well, I'll try to explain as best as I can with my example:

Partition 1: Ubuntu
Partition 2: Arch
Partition 3: home --- : a. Ubuntu account
                        b. Arch account

Inside home partition, there are two accounts, one for Ubuntu and the other for Arch. I shared Music, Wallpapers, saved games and thunderbird's inbox folder inside the Ubuntu home to Arch home folder. Then I make sure that both accounts can access those folders by checking their permissions' settings.

Hope that helps.

---

### Post by Dedoimedo on 2008-11-19
Hello,
Either different usernames or a common data partition.
For the sake of simplicity, a data partition sounds like a better idea. You may even consider a filesystem that other operating systems can read (e.g. windows).
Dedoimedo

---

### Post by kpkeerthi on 2008-11-19
I'd mount the Data partition to /media/Data. Then create a symlink to it in your /home
```

cd ~
ln -s /media/Data Data

```

---

