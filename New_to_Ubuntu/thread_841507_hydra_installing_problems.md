---
title: "hydra installing problems"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Til_Valhall_vi_drar! on 2008-06-26
Hi, i need hydra to crack my router (http-get). i have made a 
perl script that will write a textfile like this:

------------------------------

a
b
c
..
..
z
aa
ab
ac
..
..
az
bz
...
...
aaa
...
zzz
aaaaaa
zzzzzz

------------------------------

(well you get it, it will contain all words...)

which im going to use as a passwordfile.


im so noob that i can't get the text inn here because it says i its 14 images with it, so i put it on my webserver: [http://193.91.189.30/h.txt]("http://193.91.189.30/h.txt")



im sure i have libssh v0.11!

i edited the Makefile and removed -lpq and -DLIBPOSTGRES

(i was instructed to from a previous try.





as far as i can see, there is no problems with the compiling.


when i now look in the directory the "pw-inspector" file is there and is executable and are working fine, but the file "hydra" is empty.

what should i do? what packages do i need?

(this is my first post and my english isn't so good, and btw i have only been using ubuntu for a halv year (i am a noob xD).)

---

### Post by dracayr on 2008-06-26
```
hydra-ssh2.o: In function `start_ssh2':
hydra-ssh2.c:(.text+0x44): undefined reference to `options_new'
hydra-ssh2.c:(.text+0xac): undefined reference to `options_set_wanted_method'
hydra-ssh2.c:(.text+0xc4): undefined reference to `options_set_wanted_method'
hydra-ssh2.c:(.text+0xd3): undefined reference to `options_set_port'
hydra-ssh2.c:(.text+0xdf): undefined reference to `options_set_host'
hydra-ssh2.c:(.text+0xee): undefined reference to `options_set_username'
hydra-ssh2.c:(.text+0x13f): undefined reference to `ssh_error_code'
```

those are lots of errors.. the compiling didn't co well at all... are you sure that you have libssh v0.11 installed?

dracayr

---

### Post by Til_Valhall_vi_drar! on 2008-06-26
i installed this: [http://193.91.189.30/libssh/libssh_0.11-1_i386.deb]("http://193.91.189.30/libssh/libssh_0.11-1_i386.deb")


so im very sure i have the correct version... how do i check it??

sorry for being such a noob, thanks for replying btw.

---

### Post by Til_Valhall_vi_drar! on 2008-06-26
FIGURED IT OUT:

i had installed libssh and libssh-dev with apt-get, and now i uninstalled them: sudo apt-get -y --force-yes remove libssh libssh-dev

and then run dkpg -i [that libsshpackage-v0.11.deb]

anyway, thanks for your time!!

---

