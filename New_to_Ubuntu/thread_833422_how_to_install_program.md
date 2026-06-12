---
title: "how to install program"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Rax. on 2008-06-18
heres what i want to install on ubuntu 8.04:
[http://www.geexbox.org/~schroeterm/splash-sky](http://www.geexbox.org/~schroeterm/splash-sky)
how to do that?

---

### Post by the_doc on 2008-06-18
What is it you are downloading, ISO/package/source/binaries etc?

---

### Post by Rax. on 2008-06-18
just downloading that: [http://www.geexbox.org/~schroeterm/splash-sky](http://www.geexbox.org/~schroeterm/splash-sky)
should be binary or what?

---

### Post by cariboo on 2008-06-18
In a Applications-->Accessories-->Terminal navigate to where you downloaded the file, for example if it is on your desktop then

```
cd ~/Desktop
```

Once your are in the correct directory you have to make the file executable to do this type:

```
chmod +x splash-sky
```

To run it

```
sudo ./spalsh-sky
```

Good luck

Jim

---

### Post by Rax. on 2008-06-18
wont work :s
```
ragnar@ragnar-desktop:~$ cd ~/Desktop
ragnar@ragnar-desktop:~/Desktop$ chmod +x splash-sky
ragnar@ragnar-desktop:~/Desktop$ sudo ./spalsh-sky
[sudo] password for ragnar: 
sudo: ./spalsh-sky: command not found
ragnar@ragnar-desktop:~/Desktop$ 

```

---

### Post by the_doc on 2008-06-18
Yeah, looks like a binary at 16K, is it on your desktop?  CD to wherever you downloaded it.

---

### Post by Rax. on 2008-06-18
yep. its in desktop

---

### Post by cpetercarter on 2008-06-18
A typo perhaps?

./splash-sky, not ./spalsh-sky

---

### Post by the_doc on 2008-06-18
> **Rax. said:**
> wont work :s
```
ragnar@ragnar-desktop:~$ cd ~/Desktop
ragnar@ragnar-desktop:~/Desktop$ chmod +x splash-sky
ragnar@ragnar-desktop:~/Desktop$ sudo ./spalsh-sky
[sudo] password for ragnar: 
sudo: ./**spalsh**-sky: command not found
ragnar@ragnar-desktop:~/Desktop$ 

```

You spelled in wrong!

---

### Post by TeoBigusGeekus on 2008-06-18
> **rax. said:**
> wont Work :s
```
ragnar@ragnar-desktop:~$ Cd ~/desktop
Ragnar@ragnar-desktop:~/desktop$ Chmod +x Splash-sky
Ragnar@ragnar-desktop:~/desktop$ Sudo ./[color="red"]spalsh-sky[/color]
[sudo] Password For Ragnar: 
Sudo: ./spalsh-sky: Command Not Found
Ragnar@ragnar-desktop:~/desktop$ 

```

Typo!!!

---

### Post by Rax. on 2008-06-18
i dont get it. what type? file name is "splash-sky" all letters are lowercase and i typed it exactly like file name

---

### Post by TeoBigusGeekus on 2008-06-18
No you didn't...
If your post was the exact output of the command line, then you typed
```
spalsh-sky
```
instead of
```
splash-sky
```

---

### Post by kaboodle_fish on 2008-06-18
The GeeXboX website shows this as being a distro 

Are you trying to install an application found in that distro in Ubuntu?

---

### Post by Rax. on 2008-06-18
thats not part of geexbox distro. [http://www.geexbox.org/forum/viewtopic.php?t=8992](http://www.geexbox.org/forum/viewtopic.php?t=8992)

copy pasted file name now..
```
ragnar@ragnar-desktop:~/Desktop$ sudo ./splash-sky
Usage: ./splash-sky -s [-u unit] -n [cfgfile]
ragnar@ragnar-desktop:~/Desktop$ 

```
also tryed -s, -u and -n but nothing :$
```
ragnar@ragnar-desktop:~/Desktop$ sudo ./splash-sky -s
/proc/splash: No such file or directory
ragnar@ragnar-desktop:~/Desktop$ sudo ./splash-sky -u
./splash-sky: option requires an argument -- u
Usage: ./splash-sky -s [-u unit] -n [cfgfile]
ragnar@ragnar-desktop:~/Desktop$ sudo ./splash-sky -n
Usage: ./splash-sky -s [-u unit] -n [cfgfile]


```

---

### Post by the_doc on 2008-06-18
That file is a binary that has several options that require several parameters.  You don't need to install it, but you do need to go to the geekbox wiki/FAQ/forum and find out how to use it.

If you don't know how to use it then how do you know you need it?

---

### Post by Rax. on 2008-06-18
i need it to make bootsplash for my htpc that uses geexbox. in geexbox wiki/forum theres nothing about installing or using splash-sky
[http://www.geexbox.org/wiki/index.php/How_to_create_a_theme#Bootsplash](http://www.geexbox.org/wiki/index.php/How_to_create_a_theme#Bootsplash)

---

### Post by the_doc on 2008-06-18
> **Rax. said:**
> thats not part of geexbox distro. [http://www.geexbox.org/forum/viewtopic.php?t=8992](http://www.geexbox.org/forum/viewtopic.php?t=8992)
[/code]

Further down that thread is a post linking to a wiki that's a tutorial for creating a theme, I suppose that program is to be used in conjunction with that.

---

### Post by the_doc on 2008-06-18
> **Rax. said:**
> i need it to make bootsplash for my htpc that uses geexbox.

It looks like bootsplash has been superseded by **splashy** maybe they have better documentation?

[http://splashy.alioth.debian.org/wiki/](http://splashy.alioth.debian.org/wiki/)

---

### Post by Rax. on 2008-06-18
thanks everyone who wasted theyr time. dont need to install that.
```
./spash-sky -s -f bootsplash-800x600.cfg > bootsplash-800x600.dat


``` works.

---

### Post by cariboo on 2008-06-18
Sorry, thats my fault, sometimes i forget to speel check:).

Another thing I would suggest is just don't blindly paste some of these instructions, check to see if there are spelling errors and if you don't understand the instructions please ask for clarification.

Jim

---

