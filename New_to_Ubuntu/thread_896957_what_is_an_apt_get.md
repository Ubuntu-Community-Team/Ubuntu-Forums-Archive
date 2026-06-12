---
title: "what is an apt get?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by ggfile on 2008-08-21
Hey there...

I have been using Ubuntu for a short time and normally install programs with either the "add-remove" feature and use update manager to keep programs up to date.  Recently, Gnutella advised me that my program was out of date and to download and install the new version.  I downloaded the new version but was unable to get it installed so I posted a forum message for help.  This is the reply that I got...

Do this bit once..
"apt-get build-dep gtk-gnutella" (this will install all the bits required to build the source.

cd into the source directory and do
"fakeroot debian/rules binary"

This will build a debian package for you in the directory above the source dir.
dpkg -i <the .deb file it creates> and you are done.

To update you cd into the source dir and do "svn up" then
"fakeroot debian/rules binary".
cd ..
"dpkg -i <the .deb file it creates>"

rinse..lather..repeat..


...  I hate to say this but this is Greek to me.  what do they mean by apt get?  How do I do this?  what is CD?   fakeroot?  Supposedly this is supposed to be easy?  I am using the latest vsn of Ubuntu!

---

### Post by k3lt01 on 2008-08-21
apt is a command line package manager. Ubuntu uses apt (Debian does to and thats why Ubuntu does) to organise packages. Programs are stored in packages for easy control.

apt-get is the command line (cli) way of getting packages. So if you want to dowload and install a new package you type the appropriate command using 
```
 sudo apt-get install (name of program you want to download and install)
```
and that installs it for you. It will tell you what other packages you need to install as well as many packages work together. This "working together" is called Dependencies. When you read through the code the cli puts out and you agree to continue you type Y for yes, or if you choose not to continue you type N for no and that's it.

Hope that helps.

I would suggest you read through the Ubuntu Documentation for more info as it puts it in a much better way than I do but don't hold back from asking questions.

---

### Post by rampageoberon on 2008-08-21
These are commands used in the bash shell (so gnome-terminal in ubuntu).

To find out more about apt-get and aptitude run the following line in terminal. Apt-get is used to install/remove/modify... packages from the ubuntu repositories.
```
man apt-get
```

"cd" means pretty much change directory again in the terminal. The steps you describe above are very easy indeed as all they require is a copy and paste into the terminal. (Applications -> Accessories -> Terminal)

Hope that helps

---

### Post by kansasnoob on 2008-08-21
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Sealbhach on 2008-08-21
> **ggfile said:**
> 

...  I hate to say this but this is Greek to me.  what do they mean by apt get?  How do I do this?  what is CD?   fakeroot?  Supposedly this is supposed to be easy?  I am using the latest vsn of Ubuntu!

I've been using Ubuntu since April of this year and I was exactly in the same boat as you are now. None of these things are difficult, they only seem so because they are new and different.

Most of the time, you won't need to use commands at all, if you don't want to. But you'll find as you go on that you will want to find out how to do things - it's the fun part of Linux, it really is!:)


.

---

### Post by taqkavar on 2008-08-21
nvm

---

