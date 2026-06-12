---
title: "Backup strategy"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by bercy on 2012-11-24
Hi,

I rent dedicated servers.

When I get a new server, the provider installs a fresh install of (let's say) Ubuntu 12, and then I do a bunch of configuration (install software with apt-get, add some shell scripts, and install custom software of my own).

How do I make a backup of this first server, so that I can then get a second server installed with a fresh Ubuntu, on which I could "apply" all the custom changes I made on the first server just by copying files over, but without overwriting whatever has to do with network configuration, computer name, etc.. of the new server ?

Tks.

---

### Post by ibjsb4 on 2012-11-24
Take a look at clonezilla

[http://clonezilla.org/clonezilla-SE/](http://clonezilla.org/clonezilla-SE/)

---

### Post by bercy on 2012-11-24
> **ibjsb4 said:**
> Take a look at clonezilla

[http://clonezilla.org/clonezilla-SE/](http://clonezilla.org/clonezilla-SE/)


Thanks for your reply.

I read the documentation there, correct me if I'm wrong, but this solution is for making a COMPLETE disk image, which means that the network config and computer name of the source computer would be on that image.  If I were to overwrite a fresh install of Ubuntu with that image, wouldn't I end up with 2 exact copies, meaning two computers set up with the same name / IP ?

I guess the information I'm looking for is this : I know where I'm installing my custom software.  What I don't know is : where does Ubuntu make changes on the disk when one installs packages through apt-get ?

I would like to make a backup of those directories, but also avoid backing up files that are not affected by apt-get...

---

### Post by ibjsb4 on 2012-11-24
Ok

[http://ubuntuforums.org/showthread.php?t=1379965](http://ubuntuforums.org/showthread.php?t=1379965)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=script+to+install+packages+to+multiple+servers&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=script+to+install+packages+to+multiple+servers&as_qdr=all&sa=Google+Search&lang=en)

---

