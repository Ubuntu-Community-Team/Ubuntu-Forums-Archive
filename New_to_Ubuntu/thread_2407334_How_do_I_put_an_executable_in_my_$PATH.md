---
title: "How do I put an executable in my $PATH ?"
date: 2018-12-03
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-12-03
I have installed both Texmacs and Sagemath, Now Texmacs has a plugin for sagemath, as described here, at the bottom of the page: [https://wiki.sagemath.org/TeXmacs](https://wiki.sagemath.org/TeXmacs) 



texmacs-sage.tar.gz contains a folder which has an executable called tm_sage ... how to I put this executable into my $PATH ?

---

### Post by freemedia2018 on 2018-12-03
Add the folder it is in to:

```
PATH=$PATH:/texmacs/path/to/add; export PATH;
```

To .profile

I don't usually do that though, I would personally just say:

```
sudo ln -s /filepath/to/binary /bin/nameofbinary
```

---

### Post by Impavidus on 2018-12-03
I would use a symlink too, although I'd put it somewhere else:```
sudo ln -s /path/to/tm_sage /usr/local/bin/
```If you only want to install this for one user, you can also create it in your home directory:```
ln -s /path/to/tm_sage ~/.local/bin/
```First make sure the ~/.local/bin directory exists.

---

### Post by mc4man on 2018-12-03
> **Impavidus said:**
> I would use a symlink too, although I'd put it somewhere else:```
sudo ln -s /path/to/tm_sage /usr/local/bin/
```If you only want to install this for one user, you can also create it in your home directory:```
ln -s /path/to/tm_sage ~/.local/bin/
```First make sure the ~/.local/bin directory exists.

Why ~/.local/bin? 
~/bin is by default in a users $PATH ( once created and sourced or after a reboot

---

### Post by Impavidus on 2018-12-04
It seems that ~/.local/bin is in my path, and I didn't put it there myself, so I assumed it's there by default. Maybe it's a leftover from a previous Xubuntu install, as I've kept my /home partition for quite a while now.

---

### Post by mc4man on 2018-12-04
> **Impavidus said:**
> It seems that ~/.local/bin is in my path, and I didn't put it there myself, so I assumed it's there by default. Maybe it's a leftover from a previous Xubuntu install, as I've kept my /home partition for quite a while now.
I've pretty much only used Ubuntu where the 'default' would be

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:

```
/home/username/bin would be auto added to front once created, likely latest Ubuntu by default adds /snap/bin to end.

---

### Post by automate-stuff on 2018-12-13
OK, New question: 

I want to create linkers for every file inside a folder in some other folder.....How do i do it ?

---

