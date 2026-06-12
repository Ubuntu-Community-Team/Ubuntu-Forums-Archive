---
title: "what is this add-apt-repository used for?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by kevincmaker on 2011-12-29
Hello! 

I am a newbie to ubuntu and i just want to know about this command "add-apt-repository"... why is this used? Also, please someone explain each component of the following command :
```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

Thanks in advance :)

---

### Post by drackololord on 2011-12-29
Lol, soooooooooooo easy dude

sudo = admin permission
add= to add it lol
apt=  *Advanced Packaging Tool*
repository= the "garage" of the web lists you download your ubuntu Gnu/linux software, so it can be updated automatically or manually
gnome 3= Introduction of [GNOME Shell]("http://en.wikipedia.org/wiki/GNOME_Shell")
ppa=[Personal Package Archives]("https://launchpad.net/ubuntu/+ppas")
gnome= *GNU Network Object Model Environment*, pronounced gah-NOHM

and

```
add-apt-repository
```

to add the repository to your lists, so you can download-update whatever you want,
and dont forget your private key, perhaps it could ask you for it


:popcorn:

---

### Post by plucky on 2011-12-29
> **kevincmaker said:**
> Hello! 

I am a newbie to ubuntu and i just want to know about this command "add-apt-repository"... why is this used? Also, please someone explain each component of the following command :
```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

Thanks in advance :)

Read [Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

PPA's are described lower down the article.

Good Luck

---

### Post by kevincmaker on 2011-12-29
> **drackololord said:**
> Lol, soooooooooooo easy dude

sudo = admin permission
add= to add it lol
apt=  *Advanced Packaging Tool*
repository= the "garage" of the web lists you download your ubuntu Gnu/linux software, so it can be updated automatically or manually
gnome 3= Introduction of [GNOME Shell]("http://en.wikipedia.org/wiki/GNOME_Shell")
ppa=[Personal Package Archives]("https://launchpad.net/ubuntu/+ppas")
gnome= *GNU Network Object Model Environment*, pronounced gah-NOHM

and

```
add-apt-repository
```to add the repository to your lists, so you can download-update whatever you want,
and dont forget your private key, perhaps it could ask you for it


:popcorn:


Then, i we want to add any package to the repository, we r using that command..... am i right?? :P

---

### Post by mcduck on 2011-12-29
> **kevincmaker said:**
> Then, i we want to add any package to the repository, we r using that command..... am i right?? :P

No, the repository is the web server that maintains and provides the packages. Unless you are the maintainer, you don't add any packages to repositories, you install packages *from* them. ;)

And not using that command either. :)  That command adds the repository and it's signing key to your system's configuration files, so you can then install packages from that repository using Ubuntu's package management tools (like the Software Center, Synaptic Package Manager or apt-get)

---

### Post by kevincmaker on 2011-12-29
> **mcduck said:**
> No, the repository is the web server that maintains and provides the packages. Unless you are the maintainer, you don't add any packages to repositories, you install packages *from* them. ;)

And not using that command either. :)  That command adds the repository and it's signing key to your system's configuration files, so you can then install packages from that repository using Ubuntu's package management tools (like the Software Center, Synaptic Package Manager or apt-get)

OMG! I'm such a noob! :D Thanks for that mcduck! Now i have understood..... U guys r really polite... I have started liking ubuntuforums.org ...:popcorn:

---

