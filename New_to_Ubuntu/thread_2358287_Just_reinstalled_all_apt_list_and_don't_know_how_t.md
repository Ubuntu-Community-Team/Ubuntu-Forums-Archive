---
title: "Just reinstalled all apt list and don't know how to get out of it..."
date: 2017-04-11
forum: New to Ubuntu
---

### Post by Mike Krall on 2017-04-11
Was looking through this:  [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages]("http://askubuntu.com/questions/17823/how-to-list-all-installed-packages")  to find a list of things I had put into 16.04.2.  Used "apt list --installed".  Went on further and generated a complete list of all apt with "dpkg -l" and same list with other code from the linked discussion (don't know which for sure).  Then wanted to go back to short list of things I put in since start up and instead of using "apt list --installed"  I used "apt list installed".  

I have no idea what kinds of complications I generated (or not ???), and if a problem, haven't the slightest idea how to unwind them...  to get back to where "apt list --installed" is a command listing things I can save for use in reinstall, etc.

If you can make time to help, I'd sure appreciate it.

Mike

---

### Post by Dennis N on 2017-04-11
If you use the terminal to do your installs and want to see the packages that you requested with apt or apt-get, and not list dependencies, then use the appropriate command below:

if **apt-get install** 

```
history | grep "apt-get install"
```

if **apt install**

```
history | grep "apt install"
```

example:

```
dmn@Sydney:~$ history | grep "apt-get install"
    4  sudo apt-get install audacious geany
    7  sudo apt-get install libreoffice-style-tango
   13  sudo apt-get install gimp
   19  sudo apt-get install gthumb
   23  sudo apt-get install gcolor2
   28  sudo apt-get install synaptic gparted
   36  sudo apt-get install easytag
   37  sudo apt-get install audacity
   38  sudo apt-get install smplayer
   45  sudo apt-get install htop tree
```

Easy to make a list from this output.

---

### Post by Impavidus on 2017-04-11
**apt list installed** should do nothing more than list all available packages named "installed" and show their status on your system. As it happens, no such packages exist.

---

### Post by Mike Krall on 2017-04-11
Dennis N,

Thank you... I've saved the instructions

Impavidus,

After reading your post I looked around the web a little and came to a better understanding of what I actually did and did not do... thanks for getting me pointed to that.

Mike

---

