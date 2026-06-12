---
title: "libjack0? wtf is that anyway?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-11-04
hi there.
i need some help with this error which is killing me.

[IMG]http://i37.tinypic.com/2r38cpk.png[/IMG]

can you tell me what is libjack0? how to get it? how to install it if its necesary?

im trying to install audacity but this is givin me hard time. help please-

thanks.

:?

---

### Post by Sarmacid on 2008-11-04
To install it, run```
sudo apt-get install libjack0
```It should prompt you for your password, ask for a confirmation and will download and install.

---

### Post by jsf_pp on 2008-11-04
ok, i did it. i install it but the same thing happens. 

[SPOILER][IMG]http://i34.tinypic.com/8zl5ps.png[/IMG][/SPOILER]

what else can i do to solve this?

thanks.

btw im using ubuntu 7.10 if that helps...

---

### Post by jsf_pp on 2008-11-04
is that impossible?
c'mon guys, cant be that hard.

please help, thanks

---

### Post by Sarmacid on 2008-11-04
Post the output of ```
sudo apt-cache policy libjack0
```

---

### Post by jsf_pp on 2008-11-04
> **Sarmacid said:**
> Post the output of ```
sudo apt-cache policy libjack0
```

ok, here it is:

```
julio@julio-laptop:~$ sudo apt-cache policy libjack0
libjack0:
  Instalados: 0.103.0-6ubuntu1
  Candidato: 0.103.0-6ubuntu1
  Tabla de versión:
 *** 0.103.0-6ubuntu1 0
        500 http://cl.archive.ubuntu.com gutsy/universe Packages
        100 /var/lib/dpkg/status
julio@julio-laptop:~$ 

```

hey, thanks for your help hermano.

---

### Post by lordmyth on 2008-11-04
you should tone down a little

read this:
[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

and do you have a reason for not installing audacity from the ubuntu repositories?
sudo apt-get install audacity

you can also open up synaptic to install programs and dependencies

---

### Post by jsf_pp on 2008-11-04
> **lordmyth said:**
> you should tone down a little

read this:
[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)
[COLOR="Magenta"][SIZE="3"]
and do you have a reason for not installing audacity from the ubuntu repositories?
sudo apt-get install audacity[/SIZE][/COLOR]

you can also open up synaptic to install programs and dependencies

hey bro, thanks. as the sub forum says, im totally n00b at ubuntu. 


i have been lookin for this for weeks! really, i have posted this in spanish, english, in several forums, and had no help at all. 

thanks again, the solution was as easy as type:

```
sudo apt-get install audacity 
```

i was always downloading .deb stupidly.

thank thanks thanks.
bye.

---

### Post by lordmyth on 2008-11-04
try to find 'synaptic' in the menu, or you can just pick the 'install and remove' thing, it's a lot easier than synaptic :)

---

