---
title: "Configuration question"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-23
I've been going through a pdf ebook called Ubuntu Hacks and it mentioned the following trick:

Lazy like a fox
If you spend a lot of time working on the command line, you can make things easier for yourself by
creating shortcuts for the common commands. Add these lines to your ~/.bashrc:
alias  agi='sudo apt-get install'
alias  agu='sudo apt-get update'
alias  ags='apt-cache search'
alias  agsh='apt-cache show'
alias  agr='sudo apt-get remove'
alias  agd='sudo apt-get dist-upgrade'
Then you won't need to type the whole command. To do a search, for example, just type ags foo
and enter your password if required. Laziness is a virtue!


How do I access this "~/.bashrc" feature? Thanks.

---

### Post by Technoviking on 2008-05-23
1. Backup your .bashrc
```
cp .bashrc .bashrc.bak
```
2. Edit ~/.bashrc
```
In Ubuntu, type in terminal:
gedit ~/.bashrc

In Kubuntu, type in terminal
kate ~/.bashrc
```
3. Add lines to bottom of file
```
alias agi='sudo apt-get install'
alias agu='sudo apt-get update'
alias ags='apt-cache search'
alias agsh='apt-cache show'
alias agr='sudo apt-get remove'
alias agd='sudo apt-get dist-upgrade'
```
4. File -> Save, File-> Exit

---

### Post by Kevbert on 2008-05-23
The alias file is in your home folder (but it's hidden).  If you open terminal and enter 
```
sudo gedit .bashrc

```
you can add as many shortcuts as you like.
The book is quite useful.  You are aware that you can view this online for free for 45 days (see inside back cover).
The other book I have is 'The Official Ubuntu Book' which complements the Hacks book well (it may not be for the latest version of Ubuntu but most things work as expected).

---

### Post by mlissner on 2008-05-23
Also, those hacks won't be effective until the .bashrc file is run, which only happens when you run it manually, or restart your terminal the first time. So don't forget to do that once you're done making changes.

Also, from what I understand, you should use aptitude, not apt-get. Also, why ags for apt-cache search. Why not acs? Hmmm...

---

### Post by Technoviking on 2008-05-23
> **Kevbert said:**
> The alias file is in your home folder (but it's hidden).  If you open terminal and enter 
```
sudo gedit .bashrc

```

You don't need sudo rights to edit your own .bashrc. Don't use sudo useless you need to.

---

### Post by hyper_ch on 2008-05-23
also nice:
```

alias l='ls -al'

```

---

### Post by wariskampar on 2008-05-23
where did you find the ebook. Mind to share?

---

### Post by Kevbert on 2008-05-23
> **wariskampar said:**
> where did you find the ebook. Mind to share?

On the last page of Ubuntu Hacks there is a web address and coupon code.  This code only lasts for 45 days.  The address is: [http://www.oreilly.com/go/safarienabled]("http://www.oreilly.com/go/safarienabled")
After this you can no longer access the book online.  It's not really much use as you can't download all the contents.:(

---

