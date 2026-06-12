---
title: "authentication failure"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Necro280 on 2008-06-23
hi, i am trying to install JAva, an it tells me to go to the terminal, type in su, i do,  is asks for password, i type in my password and i get Authentication Failure

---

### Post by tamoneya on 2008-06-23
by default there is a scrambled root password.  Ubuntu developers did this intentionally since it is prefered to use sudo.  instead of doing this:```
su
apt-get update
apt-get upgrade
exit
``` you do this:```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Necro280 on 2008-06-23
Thanks forthe fast post, but im a total noob with linux, do i just enter those one by one in the terminal?

---

### Post by spiderbatdad on 2008-06-23
All java apps you need should be available in the package manager. To become root in ubuntu su is not advised. Use sudo -i. The authentication failure is because the root password is locked by default, and better to keep it locked. sudo -i will give you temporary root login to perform administrative tasks, but java can be installed from the package manager.

---

### Post by django0909 on 2008-06-23
Yep.

---

### Post by Necro280 on 2008-06-23
Wait.. Is it installing Java o_o

---

### Post by Necro280 on 2008-06-23
Why is linux so much more confusing O_O




so... where is this"package manager"

---

### Post by Bubba64 on 2008-06-23
> **Necro280 said:**
> Why is linux so much more confusing O_O




so... where is this"package manager"

System-administration-synaptic  
just type java into the search make sure you are loking for the right package. Java is also installed as part of a add remove package one of the gstreamer ones I think. It may be that if you search with java in add remove a java 6 package is there as well.

---

### Post by Necro280 on 2008-06-24
> **Bubba64 said:**
> System-administration-synaptic  
just type java into the search make sure you are loking for the right package. Java is also installed as part of a add remove package one of the gstreamer ones I think. It may be that if you search with java in add remove a java 6 package is there as well.


not in either

---

### Post by Bubba64 on 2008-06-24
> **Necro280 said:**
> not in either
It may be that java since it is a 3rd party is part of the medibunti repositories search for medibuntu on google for the instructions on how to intsall and the url to install medibunti. Also in add remove you have to have  all available applications showing to get all available applications. Here are some simple instructions to help you,-- install medibuntu first though.
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by Nepherte on 2008-06-24
The java packages are located in the multiverse repository. To enable this repository, just go to system > administration > software resources and check and be sure multiverse is checked.

---

### Post by Bubba64 on 2008-06-24
> **Nepherte said:**
> The java packages are located in the multiverse repository. To enable this repository, just go to system > administration > software resources and check and be sure multiverse is checked.

I have never used kubuntu so I don't know if the medibuntu repositories are built in. I doubt it though it is a 3rd party repository. Here is a site that will tell you how to add this to the apt source list though. These can also just be input in the add 3rd party section of software sources if the apt source list is hard to bring up. Don't forget to add the key besides the free nonfree repositories.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu). :)

---

