---
title: "[SOLVED] Is there a good wifi decryptor avalible in Ubuntu?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by fiestytom on 2008-08-15
My windows partition has an awesome wifi wireless cracker, but i can't seem to find one in Ubuntu.

I'm trying to kick my windows habit, so good links would be appreciated!

---

### Post by iaculallad on 2008-08-15
> **fiestytom said:**
> My windows partition has an awesome wifi wireless cracker, but i can't seem to find one in Ubuntu.

I'm trying to kick my windows habit, so good links would be appreciated!

You could try aircrack or airsnort:

```
sudo apt-get install aircrack
```
or
```
sudo apt-get install airsnort
```

---

### Post by nicedude on 2008-08-15
Are you serious, Windows is your wifi cracker. Thats a pretty good one. Linux is king at wifi cracking and probably always will be.

If you want the best aircrack you have to compile from source, there are 2 new attack types in the newest source that are not in the version in the repositories. And airsnort is not even close to aircrack in ability - as far as scanners go , kismet is the nicest available but airodump ( part of the aircrack suite ) gets the job done.


In fact I have commview for wifi ( 1000$ ) installed on my XP partition along with a automatic WEP cracker ( Authoring company says police only for this automatic plugin ) and it is so weak compared to aircrack that I never use it. If I wanna hack the air then aircrack is the application of choice.

---

### Post by fiestytom on 2008-08-15
I can't install aircrack, it sounds awesome and i want it!!!

heres what i get from terminal:

****@****:~$ sudo apt-get install aircrack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack
****@****:~$ 

i'd like to compile from source, but i don't know where to get a safe package

---

### Post by nicedude on 2008-08-15
Can't find where to get a safe package? How about try the authors of the software ? If you want you can PM me and I will help you further but you must promise to behave yourself with what I teach you as I don't teach people how to bother other people. Penetration testing is another thing though so if you really want to learn, not just hack your nextdoor neighbors wifi router then I will try to guide you.

And aircrack is awesome but takes the proper setup and commands to use, on top of the fact that it is command line only so it isn't a simple GUI based application suite. Its a suite of programs by hackers for hackers. And the reason you can't install with the command you listed is that its package is called aircrack-ng so the command would be 

sudo apt-get install aircrack-ng

But if you seriously want the best then get the source from the source and then PM me when you get stuck and I can help.

JUST ACT RESPONSIBLY

---

