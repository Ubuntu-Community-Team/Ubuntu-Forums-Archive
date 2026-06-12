---
title: "Installing GCC"
date: 2007-06-19
forum: Programming Talk
---

### Post by perlude on 2007-06-19
Some background: 
I'm new user of Ubuntu. For 6 years I'm using Slackware and Mandrake/Mandriva.

By default Ubuntu Feisty doesn't install packages that we need to compile programs such as GCC. In Mandriva I simply selected Development Packages if we want to compile programs using GCC etc. What packages that we need in order to compile using C or C++ in Ubuntu?

Thanks.

---

### Post by Canis familiaris on 2007-06-19
Just copy and paste this command in terminal:
```
sudo aptitude install build-essential
```
This will install gcc, g++, etc. with other developmental packages

---

### Post by perlude on 2007-06-19
Great! Fast answer :)

I try this at home, I don't have internet connection at home, I surf from internet cafe. I have DVD repo though, so I hope I can do this without net connection.

Thanks a lot.

---

### Post by LaRoza on 2007-06-19
You will have to add the DVD as a source before using it to get the program.

Go to Synaptic-> add third party sources-> add cd, even if it is a dvd. If you installed from that dvd, it may already be added.

---

### Post by Canis familiaris on 2007-06-21
No internet connection? This is problematic!!!
Then insert the ubuntu install cd:
```
sudo apt-cdrom -m add
```
and then 
```
sudo aptitude install build-essential
```

---

