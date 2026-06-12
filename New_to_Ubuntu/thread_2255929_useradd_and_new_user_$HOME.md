---
title: "useradd and new user $HOME"
date: 2014-12-08
forum: New to Ubuntu
---

### Post by wannbenixdude on 2014-12-08
Im taking an Essentials class. adduser from the class perspective doesnt exist. 

I was asked on a quiz "Does adduser create the users home directory by default? True or False

I answered False and performed the following tests after the quiz  

> 
$ sudo useradd bob
$ getent passwd bob
bob:x:1003:1003::/home/bob:

$ sudo ls -l /home
total 4
drwxr-xr-x 22 chris chris 4096 Dec  8 14:29 chris

$ sudo useradd mary -d /home/mary
$ getent passwd mary
mary:x:1004:1004::/home/mary:
$ sudo ls -l /home
total 4
drwxr-xr-x 22 chris chris 4096 Dec  8 14:29 chris
$ 
$ sudo mkdir /home/mary
$
$ uname -r
3.13.0-40-generic
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
$


I understand that the defaults can be modified as discussed in the man page. 

My question is Why is my answer incorrect when the "useradd bob" clearly doesnt create /home/bob ?  Not even when is use the "-d" switch  with "useradd mary" is the /home/mary directory created. I dont understand. Any help is appreciated. 
:confused:#-o](*,)


Thanks Regards 
Chris

---

### Post by deadflowr on 2014-12-08
adduser and useradd are two different things.
And yes adduser adds a user home directory.
From "man adduser"

>  adduser will create a home directory subject to DHOME, GROUPHOMES,  and  LETTER&#8208;
       HOMES.   The  home  directory  can  be overridden from the command line with the
       --home option, and the shell with the --shell option. The home directory's  set-
       group-ID bit is set if USERGROUPS is yes so that any files created in the user's
       home directory will have the correct group.




---

### Post by nerdtron on 2014-12-08
In Ubuntu:
Adduser is like a front-end to the old useradd command. And yes it does create a home directory complete with the default folders inside (well, taht depends on the /etc/adduserconf). But leaving the defaults in Ubuntu, this is true.

In Centos, adduser just points to useradd, so they are basically the same.

---

### Post by bab1 on 2014-12-08
To add to what @nerdtron has said, *_adduser_ *is a Debian friendly perl script that conforms to the "Debian way" of doing things.  That's why the CentOS *_adduser_* is just a link to the original ***useradd***.  You can look at the perl code yourself at [I]/usr/sbin/adduser
[/I] with this command```
cat /usr/sbin/adduser
```

---

### Post by grahammechanical on 2014-12-08
> [COLOR=#000000]My question is Why is my answer incorrect when the "useradd bob" clearly doesnt create /home/bob ?[/COLOR]

What explanation did the class instructor give? I think that we learn more from getting answers wrong than from getting them right but we do need to understand why the correct answer is correct. And that is the responsibility of the class teacher.

Regards.

---

### Post by wannbenixdude on 2014-12-10
The instructor is stumped herself. 

Please note that the Essentials class doesnt go into the front end adduser. I do know that adduser does in fact setup /home/$USER by default. 

Im supposed to NOT know about that front end from a class perspective. ... remember Im an Essential guy :)

According to my tests on Ubuntu and Centos ... Im correct. **By default **useradd does ***not ***create /home/$USER. Id will however if the -m switch is added.

---

### Post by steeldriver on 2014-12-10
What does

```

useradd -D

```

say? what are the contents of the /etc/default/useradd file?

---

### Post by bab1 on 2014-12-10
> **wannbenixdude said:**
> The instructor is stumped herself. 

Please note that the Essentials class doesnt go into the front end adduser. I do know that adduser does in fact setup /home/$USER by default. 

Im supposed to NOT know about that front end from a class perspective. ... remember Im an Essential guy :)

According to my tests on Ubuntu and Centos ... Im correct. **By default **useradd does ***not ***create /home/$USER. Id will however if the -m switch is added.

It's important to note which distribution of Linux you are using when the question is asked.  The Debian family is different from the Redhat in many of these details.  The question can't really be answered without knowing which distribution is being used.  The tools *useradd* and *adduser* are not part of the Linux kernel.  The tools are implemented differently on a distribution wide (i.e. Debian, Ubuntu or Redhat, CentOS) basis.  Your response to the instructor's question could have correctly been "what distro are we talking about?".

---

