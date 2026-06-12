---
title: "CLI to GUI .............?????"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by adym333 on 2012-03-11
[COLOR=red][B][COLOR=Black]sudo apt-get install --no-install-recommends ubuntu-desktop

[/COLOR][/B][COLOR=Black]i am  using ubntu 11.10 server ................. after entering above comnd got all the installation done but aftr  running whole processes ............ still not able to get GUI for  ubuntu server ....????

did tried Ctrl +Alt + (F1/F2/F3/F4 ....)........!!!!!!!!!!!!!!!!!!

help required .....!!!.....:sad::sad:[/COLOR][/COLOR]

---

### Post by 3rdalbum on 2012-03-11
```
sudo service lightdm start
```

Should start the Ubuntu GUI, if you have it.

Why did you do no-install-recommends, by the way?

---

### Post by adym333 on 2012-03-11
[SIZE=4]**@3rdalbum**[/SIZE]


**[http://www.noobslab.com/2011/07/graphical-user-interface-on-ubuntu-11.html](http://www.noobslab.com/2011/07/graphical-user-interface-on-ubuntu-11.html)**

I followed the material given on above link ........

---

### Post by adym333 on 2012-03-11
thnks fr promt reply ........................



sudo service lightdm start 


after entering above cmnd screen have become blank .........only cursor blinking ....!!!!!!..:(

---

### Post by Paqman on 2012-03-11
> **3rdalbum said:**
> 
Why did you do no-install-recommends, by the way?

Exactly, using this on ubuntu-desktop will mean you'll miss out on a huge number of packages. Basically you'll miss out on everything with a green diamond on [this list]("http://packages.ubuntu.com/oneiric/ubuntu-desktop"). A lot of that stuff is pretty essential.

If you want a lightweight Gnome desktop I'd suggest installing:
```
sudo apt-get install xorg lightdm gnome-core gnome-themes
```

Then:
```
sudo service lightdm start
```

---

### Post by AleeRaza on 2012-03-11
--no-install-recomends ubuntu-desktop will not work on 11.10.
So you have to install desktop using :
sudo apt-get install ubuntu-desktop :p

---

### Post by adym333 on 2012-03-11
> **Paqman said:**
> Exactly, using this on ubuntu-desktop will mean you'll miss out on a huge number of packages. Basically you'll miss out on everything with a green diamond on [this list]("http://packages.ubuntu.com/oneiric/ubuntu-desktop"). A lot of that stuff is pretty essential.

If you want a lightweight Gnome desktop I'd suggest installing:
```
sudo apt-get install xorg lightdm gnome-core gnome-themes
```Then:
```
sudo service lightdm start
```

tried both of the above cmnds still comes the blk screen after applying second cmnd ...........im using ubuntu server 11.10..................... !!!!!!!!!!!!!!...........:(

---

### Post by adym333 on 2012-03-12
tried both of the cmnds u told but ...........still comes the blk screen after applying second cmnd ...........im using ubuntu server 11.10..................... !!!!!!!!!!!!!!.....help......:sad:

---

### Post by adym333 on 2012-03-12
**problem still unsolved ....... !!!!...........???????**

---

### Post by Paqman on 2012-03-12
Try installing gdm and doing:
```
sudo service gdm start
```

---

### Post by mastablasta on 2012-03-12
imagine that... after one minute....
 
Anyway try giving some hardware informaiton specifically what graphics card do you have and is it working?
**sudo apt-get install ubuntu-desktop**
**[B]or**
**sudo apt-get install xubuntu-desktop   :-)**
[/B]if you want someting light try one of the windows manager (e.g. IceWM, Openbox) instead of full desktop.

---

### Post by sudodus on 2012-03-12
> **AleeRaza said:**
> --no-install-recomends ubuntu-desktop will not work on 11.10.
So you have to install desktop using :
sudo apt-get install ubuntu-desktop :p
Maybe it helps to purge, update-upgrade and reinstall
```
sudo apt-get purge ubuntu-desktop
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install ubuntu-desktop

```

---

### Post by adym333 on 2012-03-12
**@sudodus**

i dont need ubuntu desktop .......... i am using ubuntu server 11.10 and want to go in GUI mode from CLI ......... ???????

---

### Post by sudodus on 2012-03-12
> **adym333 said:**
> **@sudodus**

i dont need ubuntu desktop .......... i am using ubuntu server 11.10 and want to go in GUI mode from CLI ......... ???????
Maybe you should install LXDE, which has a much smaller foot-print, but anyway, I suggest that you purge what was installed with the command in your first post.

---

### Post by QIII on 2012-03-12
Perhaps someone is misinterpreting what "GUI" means to you.  The link you provided specifically refers to ubuntu-desktop, yet you say you don't want ubuntu desktop, but "GUI".

Perhaps you could explain that -- without the extended ellipses and multiple question marks.

---

### Post by matt_symes on 2012-03-12
Hi

> **QIII said:**
> Perhaps someone is misinterpreting what "GUI" means to you.  The link you provided specifically refers to ubuntu-desktop, yet you say you don't want ubuntu desktop, but "GUI".

Perhaps you could explain that -- without the extended ellipses and multiple question marks.

^^^This. 

I am also confused as to what the OP wants. After all, Webmin is a "GUI".

Kind regards

---

### Post by mastablasta on 2012-03-12
perhaps it would be better if they want a GUI to server to use a distribution such a Zentyal which is server based on 10.04 with a GUI yet not a desktop: [http://www.zentyal.com/](http://www.zentyal.com/)
[http://www.zentyal.com/en/server/download/](http://www.zentyal.com/en/server/download/)
 
Is perhaps this what is required here?

---

### Post by adym333 on 2012-03-12
what I am tryin to have is GUI(Graphic usr intrfce) in ubuntu server 11.10 .... .........like RHEL 6...... will be checking out Zentyal .....

---

### Post by QIII on 2012-03-12
The desktop environments suggested ARE GUIs.

You were given instructions on how to start them from the command line after installing them.  Did you do that?

---

### Post by sudodus on 2012-03-12
> **adym333 said:**
> what I am tryin to have is GUI(Graphic usr intrfce) in ubuntu server 11.10 .... .........like RHEL 6...... will be checking out Zentyal .....
Do you want the GUI on the console, or do you want it at remote login from another computer, like for example ```
ssh -X
``` or both?

---

