---
title: "fastest way for fresh install (as in saving the most apps/settings)"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-11-02
I have a computer that I use for work and play.  It is usually updated to the most recent Ubuntu version.  The problem is that doing a fresh install is a pain!  I now have a separate /home partition, so that saves me some effort (no transferring to external HD and back) but there is still a lot of work in installing, configuring so many applications.  Is there an easier way?  Specifically is there a way to save the installed programs and other stuff?  

Thanks
JTS

---

### Post by scragar on 2008-11-02
```
**## let's store the currently installed packages to a text file**
sudo dpkg --get-selections > ~/Desktop/my-packages.txt
[b]## do what you want with the text file during the install, once your new system is installed restore the packages like so:
## first, we tell dpkg what we want[/b]
sudo dpkg --set-selection < my-packages.txt
**## then we install them**
sudo apt-get -f install
```
hope that helps.

---

### Post by jimmy the saint on 2008-11-02
hey thanks man, Ill give that a shot.  Since the configuration files are in the /home directory, that will be great.  I just need to remember to backup my repo list too so the versions are current.

---

### Post by handydan918 on 2008-11-02
> **jimmy the saint said:**
> hey thanks man, Ill give that a shot.  Since the configuration files are in the /home directory, that will be great.  I just need to remember to backup my repo list too so the versions are current.

Ummm, when you do a fresh install you will have fresh repos, too. If you use a backed-up /etc/apt/sources.list, you will run into issues.

---

### Post by jimmy the saint on 2008-11-02
hmmm.  good catch on the repos.  I didn't think about that.  Well, most of the third party ones that I use will only require a change from hardy to intrepid.  Still a little work, but less than adding them all over again.  less to type if nothing else!  Thanks for catching that.  I'd have gone through thinking I was saving 15 minutes, and had nothing but drama!

---

### Post by handydan918 on 2008-11-02
That's what the community is all about. 

And APT is all about the repos...

---

