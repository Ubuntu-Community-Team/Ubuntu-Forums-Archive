---
title: "Synaptic Gone Missing!!"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-19
Boy oh boy.... nothing is working today.

And I already tried Update manager and software  center. They both deliberately avoid to install synaptic.

---

### Post by lucazade on 2011-09-19
gksu software-properties-gtk
enable all repos
update repos
and retry to install sympaptic

---

### Post by Blasphemist on 2011-09-19
I just installed from the software center, and used, synaptic today on one of my oneiric partitions.

---

### Post by drs305 on 2011-09-19
Do you have the universe repository enabled and have you updated the repository listings? It was recently moved.

---

### Post by ventrical on 2011-09-19
> **lucazade said:**
> gksu software-properties-gtk
enable all repos
update repos
and retry to install sympaptic

Thats the right stuff!!

Thanks Lucazade!

---

### Post by ventrical on 2011-09-19
> **Blasphemist said:**
> I just installed from the software center, and used, synaptic today on one of my oneiric partitions.


 In alpha testing I had near perfect installs- seemed like the completed project. Software Center and UM worked just great. Now , however, I have more bugs and crashes than seemingly perfect installs.

---

### Post by 23dornot23d on 2011-09-19
I get a segmentation fault when I now try to run synaptic ..... have for last two days

just to show the error - would normally start without priveleges this way .... (sudo) **[COLOR=Red]shows nothing[/COLOR]** or running it from the menu .. and entering a
password when asked ..... 

> 
keith@keith-MS-7181:~$ synaptic
Segmentation fault
keith@keith-MS-7181:~$ 

Upgraded and re-installed .....   still the same ..... 
( was hoping it was something minor - will watch and wait )

Looked at the repos using the commands above ..... the repos appear to be set up alright ....
other than one where I have a invalid key now .....

I upgraded synaptic as it was the old search option on it that takes ages ...... this was a
upgrade and not a fresh install ....... but as long as aptitude works I can update and upgrade my system ...... 

So to clarify aptitude is still working for me  ..... just Synaptic Seg Faults .....

Disabled the universe repository ...... too ..... but I did get the message coming up running without privileges before it seg faults

> 
keith@keith-MS-7181:~$ synaptic
Segmentation fault
keith@keith-MS-7181:~$ gksu software-properties-gtk
glibtop: Non-standard uts for running kernel:
release 3.0-0-generic=3.0.0 gives version code 196608


(software-properties-gtk:15942): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
'
keith@keith-MS-7181:~$ synaptic
Segmentation fault
keith@keith-MS-7181:~$ 

Maybe will do a fresh install .... was trying to keep this one going .... though .....

Ubuntu Software Center worked ..... just installed KompoZer ok ......

---

### Post by ventrical on 2011-09-19
> **drs305 said:**
> Do you have the universe repository enabled and have you updated the repository listings? It was recently moved.

 Yes, thankyou . I just did that. I had a really weird installation where I had to manually install the 3.0.0.9 kernel because it would not <install selected software> but, after I entered the code suggested by Lucazade it got all turned around in a hurry.

 Thanks for your help and suggestions.

---

### Post by CaptainMark on 2011-09-20
> **ventrical said:**
> In alpha testing I had near perfect installs- seemed like the completed project. Software Center and UM worked just great. Now , however, I have more bugs and crashes than seemingly perfect installs.

i know how you feel, even two weeks ago it seemed almost ready to roll out, now im getting major breakage left right and centre, did someone push the wrong button

---

