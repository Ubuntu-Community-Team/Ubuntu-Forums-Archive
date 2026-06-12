---
title: "A question about linux"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by gatorbowls on 2008-06-08
In linux, when you remove a program is it fully removed.. what I mean is..in windows when ever you removed a program there would be stuff left over, than you would need to run a registery program to remove what ever it left... or delete it manually..
does the same apply to linux?

---

### Post by dje on 2008-06-08
To completely remove a program (including config files) do the following in a terminal:
```
sudo apt-get autoremove --purge *program_name*
```
or in synaptic mark the program for complete removal

if you dont do the above then the program will be removed but dependencies and config files will remain

hope that helps,
dje

---

### Post by hlekat on 2008-06-08
can the --purge option delete depended files ?

---

### Post by dje on 2008-06-08
the autoremove removes dependencies and the --purge option removes config files ;)

dje

---

### Post by Paqman on 2008-06-08
Synaptic can completely remove packages too. Just right click and select "remove completely". That'll also get rid of any config files in your /home.

---

### Post by gatorbowls on 2008-06-08
Wow, seems pretty easy.

---

### Post by Thanoulis on 2008-06-08
It may occasionally be a configuration file left in your $HOME, but you can safely remove it as well.

---

### Post by Prospero2006 on 2008-06-08
the --purge will not delete dependencies if those depencies are required for other programs.

It does delete your configuration files

When you download something from the repositories, it saves the deb to 

/var/cache/apt/archives

--purge also makes a point of eliminating this hard copy.

---

### Post by RequinB4 on 2008-06-08
I would note that if you have the space, leaving the configuration files in your $HOME might be a good idea.  For instance, if I for some reason get rid of compiz, I may want to leave my custom settings intact (~/.compiz), so that if I wake up the day after and realize i shouldn't have deleted it, I can simply re-install it and it'll use my old settings.

---

