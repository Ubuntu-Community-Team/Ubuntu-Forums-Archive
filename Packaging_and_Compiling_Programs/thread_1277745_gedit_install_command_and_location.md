---
title: "gedit install command and location"
date: 2009-09-28
forum: Packaging and Compiling Programs
---

### Post by community nerd on 2009-09-28
What is the install command for gedit to install a deb package.And how would i locate the package to install if it would be changed in someone on someone elses computer.

---

### Post by korin43 on 2009-09-29
First run:
```
sudo aptitude update
```

If you just want to install gedit, do:
```
sudo aptitude install gedit
```

I'm not sure about your second question, but if you want to update it, you can do:
```
sudo aptitude upgrade
```

These two commands will work on any computer running Ubuntu, so you don't need to download the deb file yourself.

If you're not comfortable with the terminal, you can also do this by going to the menu (the ubuntu icon menu), clicking system, then administration, then synaptic package manager. Just type "gedit" in the quick search box and hit enter. In the list below it, you should be able to find a package called gedit. Click the checkbox (and choose "mark for installation"), then click apply on the toolbar.

---

### Post by community nerd on 2009-09-30
No i am asking for the command to put in my script oto i nstall a deb package.

---

### Post by community nerd on 2009-09-30
does anyone know? say i am compiling a package with a deb file in it, what would i put in the script to install the package. and how would i put the location in the script so that if i move the package to another computer it would still be able to find it.

---

### Post by dinxter on 2009-10-01
> **community nerd said:**
> does anyone know? say i am compiling a package with a deb file in it, what would i put in the script to install the package. and how would i put the location in the script so that if i move the package to another computer it would still be able to find it.

I'm not sure I quite follow what you're trying to do here, but...
The command to install a deb file

sudo dpkg -i <package name>

though you could make that gksudo if aiming for an X environment

as for using a path that transfers to another computer, thats difficult to say, it depends on where the script will be and where the deb will be, if the deb file is expected to be in an 'absolute' position on all computers then you can use the usual directory structure, /var/cache/<package name>, etc wherever it is. if the deb file is expected to be somewhere relative to your script then you will probably want to build up the directory path using things like like 
~/  script users home directory
./    current directory
../   parent directory
and so on

---

### Post by community nerd on 2009-10-01
I am intending to put the deb file in the zip file with the install script.

---

### Post by dinxter on 2009-10-01
obviously the last post still applies, if the script refers to the right package using the relative path before you zip it all up, then it'll still be correct when you unzip all your files somewhere else

---

### Post by community nerd on 2009-10-01
Thankyou. I could never successfuly write a program in windows. I almost broke my laptop when i saw that Bill Gates was the richest man in the world. I actively support ubuntu. I have it on 4 laptops and one desktop. Love it. Thankyou all.

---

### Post by dinxter on 2009-10-02
One of the first things people notice is that linux is free, what they later learn to love is that there's the best part of 40,000 packages in ubuntu repositories that you can get the source for with one command
$sudo apt-get source <package>
That's 40,000 (not counting the countless others not in the repositories) opportunities to learn/fix/contribute, and of course the chance to add your own useful programs to the collection for others to enjoy :)

---

### Post by community nerd on 2009-10-02
How do you get 40,000 packages for openoffice? Not so sure i understand?

---

### Post by dinxter on 2009-10-02
$sudo apt-cache stats
Total package names: 48258 (2,316k)
  Normal packages: 39372
  Pure virtual packages: 298
  Single virtual packages: 2485
  Mixed virtual packages: 273
  Missing: 5830

almost 40,000 separate packages that you can install from ubuntu's repositories, don't know where you get openoffice from!

---

### Post by community nerd on 2009-10-02
Oh sorry didnt understand you.

---

