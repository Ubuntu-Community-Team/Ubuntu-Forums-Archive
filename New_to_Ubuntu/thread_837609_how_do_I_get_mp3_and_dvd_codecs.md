---
title: "how do I get mp3 and dvd codecs?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by nashphyl on 2008-06-22
I installed gutsy gibbon on my computer (the second time0 after i got bored with XP. This time, however, I cant install VLC under the "add/remove" section under the "Applications" drop down menu. When I try to download it, ubuntu tells me "the list of applications is not available" then i click on a refresh button and i see a series of bars filling up as if it is downloading the program but then nothing happens and I dont have VLC. Anyone know how i can either get vlc or install the codecs so i can watch dvds and mp3s?

---

### Post by thisiam on 2008-06-22
sudo apt-get install vlc from terminal will install it for you.

Edit: this command might help aswell
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by oldos2er on 2008-06-22
> **nashphyl said:**
> I installed gutsy gibbon on my computer (the second time0 after i got bored with XP. This time, however, I cant install VLC under the "add/remove" section under the "Applications" drop down menu. When I try to download it, ubuntu tells me "the list of applications is not available" then i click on a refresh button and i see a series of bars filling up as if it is downloading the program but then nothing happens and I dont have VLC. Anyone know how i can either get vlc or install the codecs so i can watch dvds and mp3s?

 Can you post the output of cat /etc/apt/sources.list ?

---

### Post by nashphyl on 2008-06-22
I copy and pasted the commands you gave me into the terminal and this is what ubuntu told me: 

E: Couldn't find package vlc


what gives?

---

### Post by Pjotr123 on 2008-06-22
This how-to is meant for 8.04, but is largely the same as for 7.10:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

But I really advise installing 8.04. Much better.  :-)

---

### Post by steveneddy on 2008-06-22
You don't have the correct sources listed.

Open 

System --> Administration --> Software Sources

and check every box on the first page/tab.

Open a terminal and type

```
sudo apt-get update
```

let it run, then type

```
sudo apt-get upgrade
```

let it run, then type

```
sudo apt-get install vlc
```

If the package manager doesn't know to look in the alternate repositories, you can't get the good extras.

:popcorn:

EDIT:

Also [read this.]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")

---

### Post by azurepancake on 2008-06-22
> **nashphyl said:**
> I copy and pasted the commands you gave me into the terminal and this is what ubuntu told me: 

E: Couldn't find package vlc


what gives?

Edit: Steveneddy's method is actually the better idea. Try that first and see how it works!

You should open up a terminal session and type the following command..

```
cat /etc/apt/sources.list
```

This will output the contents of your sources.list file, which is where links to the repositories are stored and used by apt-get program. You should then copy and paste the output of the previous command to a post in this topic.

According to VLC's website, apt-get uses the 'universe mirror' to download and install VLC.

---

