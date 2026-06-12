---
title: "Howto: Google Talk voice support on Ubuntu"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by finferflu on 2006-08-29
Hi, I've just been able to use the Google Talk voice service on Ubuntu using Tapioca.

I've already found a post with an how-to, but the link to the file was not working, and moreover, it was more complicated than this.

For this howto I'm referring to [http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide#Installing_packages_with_apt-get.2Faptitude](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide#Installing_packages_with_apt-get.2Faptitude)

If you are using Dapper Drake, add this to your /etc/apt/sources.list:

```
deb http://extindt01.indt.org/VoIP/apt dapper main
```

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo aptitude update
```

(obviously press Enter), then type:

```
sudo aptitude install tapiocaui0.3
```

and Tapioca will be installed in your system.

Now, you just need to run it: you can either find it in Applications > Internet > Tapioca, or run it from the terminal typing **tapiocaui**.

To log in with your Google Talk account you just need to type your username and password at the prompt.

Hope you find this useful :)

---

### Post by randomthings on 2006-09-01
Hi , I tried it but i got :
" E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? "
and Tapioca didn't installed .

---

### Post by finferflu on 2006-09-01
Maybe you had something else open, like Synaptics, or another apt-get or aptitude process running while trying to run the command...

Try again and make sure any other package manager utility is not running...

---

### Post by Dinerty on 2006-09-12
Works great, thanks for the guide

---

### Post by aie on 2006-09-17
the sound quality is very low..

---

### Post by Z13 on 2006-11-05
I wonder if you managed to install Tapioca VoIP 0.3.9 on Edgy too.

As a note, my machine is AMD64.

Thank you.

---

### Post by finferflu on 2006-11-05
Well, if there's nothing on the official website, I'm not able to install it.. sorry.
I'll let you know as soon as I get some information.

---

### Post by McLogic on 2006-12-04
> **finferflu said:**
> [...]and Tapioca will be installed in your system.

Now, you just need to run it: you can either find it in Applications > Internet > Tapioca, or run it from the terminal typing **tapiocaui**.

To log in with your Google Talk account you just need to type your username and password at the prompt.

The installation worked fine. I launched Tapioca from the menu and put in my username and password, but then got this error:
```
**Error**
A network error has ocurred during login. Check your network settings.
```

Occurred is spelled ocurred in the dialogue box, and the only hit on this text and tapioca is someone with the same issue, and no resolution on the hi-weed (Chinese ubuntu clone) site. This is a PITA, please help if you can.

I have no trouble using Skype on the same network. 

I [first posted]("http://ubuntuforums.org/showthread.php?t=302363") this issue on the Feisty Fawn Discussions, but realized this had little or nothing to do with Feisty.

---

### Post by finferflu on 2006-12-04
Just to be sure, did you insert your username as username@(gmail or googlemail).com ?

---

### Post by McLogic on 2006-12-05
> **finferflu said:**
> Just to be sure, did you insert your username as username@(gmail or googlemail).com ?

Yes, and I can login to gtalk on the same computer with the same account info using Gaim.

---

### Post by finferflu on 2006-12-05
That's very weird, but at the moment I can't offer you any help, since I can't install it, for there is no current version for Edgy Eft, so I can't test it or play with it...

I'll try my best to find an Edgy Eft package and I'll be back to help you!

---

### Post by debiannerd on 2007-01-01
> **McLogic said:**
> Yes, and I can login to gtalk on the same computer with the same account info using Gaim.

what's your NAT setup? which router do u use? any ports blocked!

start the program and run netstat -a

get back

---

### Post by finferflu on 2007-02-14
> **Z13 said:**
> I wonder if you managed to install Tapioca VoIP 0.3.9 on Edgy too.

As a note, my machine is AMD64.

Thank you.

I've just found this: [http://download.ubuntu.pl/_Edgy_Eft/tapioca/](http://download.ubuntu.pl/_Edgy_Eft/tapioca/)
I don't know if it suits your requirements, but it can come useful to somebody anyway..

---

### Post by Z13 on 2007-02-14
> **finferflu said:**
> I've just found this: [http://download.ubuntu.pl/_Edgy_Eft/tapioca/](http://download.ubuntu.pl/_Edgy_Eft/tapioca/)
I don't know if it suits your requirements, but it can come useful to somebody anyway..

Yep.. it seems it's for i386.

---

### Post by Homie Bongo on 2007-03-19
You can install TapiocaUI on Feisty Herd 5 as well. Downloading the .debs for Edgy ([http://www.dcc.ufam.edu.br/~boa/edgy/](http://www.dcc.ufam.edu.br/~boa/edgy/) ) and hunting for many packages in Adept I got it finally working too.

---

