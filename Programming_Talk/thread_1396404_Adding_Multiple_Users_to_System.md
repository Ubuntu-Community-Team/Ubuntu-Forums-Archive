---
title: "Adding Multiple Users to System"
date: 2010-02-02
forum: Programming Talk
---

### Post by Meghnaad on 2010-02-02
Hello I was asked to add multiple users to system with some random password I can not use perl ( I don't know perl )
I can only use bash So I came up with following script 

```
#!/bin/bash

for i in `seq 1 80`
do
	pass=$( apg -n 1 -m 6 -x 8 -M ncl )
	user=$( sed -n "${i}p" names )
	sudo useradd -m $user -g exam -d /home/$user -s /bin/bash -p `echo "$pass" | mkpasswd -s`
	echo "$user,$pass" > out.dat
	echo "Added $user,$pass" >&2
done
```

The Script Accepts user names stored in "names" file
ganerates a random password with "apg" and Stores usernames and passwords in "out.dat" ( I know before adding a user i should check if user with same name exists or not, but i'm planning to do it later )

Well My Problem is all goes well but when i tried adding 80 users the script took well more than 10 mins. 
I've a decent Machine and also from man page of "apg" I've found that "apg" is the reason why my script executes slowly (well at least I believe that )

can you help me speeding up the script ?

---

### Post by lloyd_b on 2010-02-02
> **Meghnaad said:**
> Hello I was asked to add multiple users to system with some random password I can not use perl ( I don't know perl )
I can only use bash So I came up with following script 

```
#!/bin/bash

for i in `seq 1 80`
do
	pass=$( apg -n 1 -m 6 -x 8 -M ncl )
	user=$( sed -n "${i}p" names )
	sudo useradd -m $user -g exam -d /home/$user -s /bin/bash -p `echo "$pass" | mkpasswd -s`
	echo "$user,$pass" > out.dat
	echo "Added $user,$pass" >&2
done
```

The Script Accepts user names stored in "names" file
ganerates a random password with "apg" and Stores usernames and passwords in "out.dat" ( I know before adding a user i should check if user with same name exists or not, but i'm planning to do it later )

Well My Problem is all goes well but when i tried adding 80 users the script took well more than 10 mins. 
I've a decent Machine and also from man page of "apg" I've found that "apg" is the reason why my script executes slowly (well at least I believe that )

can you help me speeding up the script ?

Hmmm - this sounds suspiciously like a homework problem (in the real world, for "run once" programs you generally don't worry about how fast it is).

That said - unless you need "pronouceable" passwords, you can use "/dev/urandom" along with a few other standard commands to generate random strings very quickly:```
pass=`cat /dev/urandom | tr -dc _A-Z-a-z-0-9 | head -c8`
```will give you an 8 character string (modify the "-c" parameter after the 'head' command to change the string length.

Lloyd B.

---

### Post by Meghnaad on 2010-02-03
It's not Home Work Problem.
I work for a training Institute and we need to add and delete users on regular basis 
Yes I've no problem if the script executes for a couple of hours but I was just Interested in speeding things up

and I am also trying this thing up in perl !

and as soon as i reach office i'll try this trick and let you know how it works !

---

### Post by Meghnaad on 2010-02-03
@ lloyd_b :p
Thank you now My Script is executing faster......

:popcorn:

---

