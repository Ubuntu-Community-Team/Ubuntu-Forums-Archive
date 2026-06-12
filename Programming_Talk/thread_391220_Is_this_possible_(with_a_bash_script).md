---
title: "Is this possible (with a bash script)"
date: 2007-03-22
forum: Programming Talk
---

### Post by acorn22 on 2007-03-22
I only know a little bash scripting basics so I wouldlike to know if the following things are possible in a script.

1. install .debs from a specific place.
2. run make/make install
3. sudo cat ...
4. reboot the system

I'm assuming I'll have to run the script from root, but is there a way to make it just ask? Also can I package the script with other files (the mentioned .debs) into one file somehow?

I am a web developer, not a bash scripter. Please keep your explanations semi-understandable ;)

---

### Post by kerry_s on 2007-03-23
1. dpkg -i /path/to/*.deb
2. I would say, this ones going to take work. You'll need to check if make was successful without errors and dependency's satisfied before you can do make install.
3. cat as root, yes
4. shutdown now -r

I would probably stick a script like that in /etc/rc.local were everything would be run as root at computer startup. So just write up the bash script, stick it in /usr/bin make it executable. Then have it start at boot, of course make sure you put the appropriate checks, like maybe check the folder for deb's and if deb's are found then run the script otherwise just exit.

---

### Post by cwaldbieser on 2007-03-23
> **kerry_s said:**
> 2. I would say, this ones going to take work. You'll need to check if make was successful without errors and dependency's satisfied before you can do make install.

Wouldn't
```

make && make install

```
do the trick?

---

### Post by angelmartinezn on 2007-03-23
Everything you can do in console mode, you can do it in a script.


check out this manual:

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)


Good Luck,

---

### Post by xtacocorex on 2007-03-23
For compiling source packages, I have set up an alias to run the commands:
```
alias buildsrc="./configure && make && sudo make install"
```
I actually have a huge list of aliases in .bash_aliases and have that referenced in my .bashrc file.

---

### Post by Ramses de Norre on 2007-03-23
You might want to look into auto-apt, it can install needed dependencies automatically from the output of ./configure.

---

