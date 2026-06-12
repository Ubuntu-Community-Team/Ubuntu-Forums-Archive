---
title: "problem installing gimp on trusty"
date: 2015-04-16
forum: New to Ubuntu
---

### Post by Johnathan_Bar_-_Da on 2015-04-16
Hi , I am running 14.04 trusty. It seems the only way to install gimp image manipulation program is to get it from the kesselgulasch ppa. I entered the commands in the terminal exactly as given , 
like this: sudo add-apt-repository ppa:otto-kesselgulasch/gimp                                                                                                                                                                                                                                   sudo apt-get update
              sudo apt-get install gimp

After authenticating, I received...  Error : need a single repository as argument

I am not a programmer and know nothing about software. If you can tell me what is going on , please explain it for a beginner... Thanks in advance

---

### Post by Dennis N on 2015-04-16
> **Johnathan_Bar_-_Da said:**
> Hi , I am running 14.04 trusty. It seems the only way to install gimp image manipulation program is to get it from the kesselgulasch ppa. I entered the commands in the terminal exactly as given , 
like this: sudo add-apt-repository ppa:otto-kesselgulasch/gimp                                                                                                                                                                                                                                   sudo apt-get update
              sudo apt-get install gimp

After authenticating, I received...  Error : need a single repository as argument

I am not a programmer and know nothing about software. If you can tell me what is going on , please explain it for a beginner... Thanks in advance

Gimp is in the Ubuntu Software Center and repositories, so you don't need a PPA. Just type **gimp** in the Software Center search box. It is version 2.8.10 for Ubuntu 14.04. The PPA offers 2.8.14 (also to be used in 15.04). Do you need 2.8.14?

If so, to use that repository use three separate commands:

```
sudo apt-add-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

```

---

### Post by Impavidus on 2015-04-16
Gimp 2.8.10 is in the trusty repository, so no need to use a PPA. Unless you really want version 2.8.14. I guess there is a problem because you now have multiple repositories providing the same package and the package manager can't make out which is the most recent.

---

### Post by buzzingrobot on 2015-04-17
> **Johnathan_Bar_-_Da said:**
> ...I entered the commands in the terminal exactly as given , 
like this: sudo add-apt-repository ppa:tto-kesselgulasch/gimp                                                                                                                                                                                                                                   sudo apt-get update sudo apt-get install gimp...


If you happened to enter all that as a single command, the "add-apt-repository" command likely read everything on the line as a PPA address.  I.e., it read ```
"ppa:tto-kesselgulasch/gimp sudo apt-get update sudo apt-get install gimp" 
```as the designation of the PPA.

If you want to do it that way, you need to separate each individual command.  You can use a ';', like so:

```
sudo apt-add-repository ppa:tto-kesselgulasch/gimp ; sudo apt-get update ; sudo apt-get install gimp
```

...or you can use '&&':

```
sudo apt-add-repository ppa:tto-kesselgulasch/gimp &&  sudo && apt-get update && sudo apt-get install gimp
```

The ';' says continue with the next command after the previous command completes, regardless of its success.  '&&' says continue if the previous command completed successfully.

The package manager should locate and retrieve the most recent package available in your list of sources.

---

### Post by Johnathan_Bar_-_Da on 2015-04-18
Hi ya Buzzingrobot ! Thank you for your help and prompt reply. Your post was the most educational of the replies I received. I am on the road to Ubuntu enlightenment,thanks again

---

### Post by Johnathan_Bar_-_Da on 2015-04-18
Thanks Dennis. the answer was really silly, as it so often seems to be...I was putting " gimp " into the Dash , and nothing really was happening , although I did find out about the
band Gimp Fist's two albums...but when I waited and used a bit of patience, the Software Center icon appeared, and now I have it on my machine. I live in South Africa , and my 
internet speed some days is SSSSS ...SS..LLLLL...ooooooooooo...oooo..WWWWW

---

### Post by GrouchyGaijin on 2015-04-18
> **Johnathan_Bar_-_Da said:**
> ...the answer was really silly, as it so often seems to be...I was putting " gimp " into the Dash , and nothing really was happening ...

Don't sweat it - EVERYONE has made mistakes that seem "silly".  If you don't know, you don't know and frankly if you are very new to Linux in general entering the name of the software you want to install into the Dash seems plausible.  One of the things you will find that makes Ubuntu different from the traditional view of Linux users is that by and large Ubuntu Forum users are friendly and helpful.

Welcome to the group!

---

