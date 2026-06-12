---
title: "[SOLVED] temp gauge on gnome panel?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-06-30
in gutsy i downloaded a temp gauge that goes on the gnome panel (from synaptic)

but now i cant find it, and i cant even remember what it was called

can anyone help me out?

---

### Post by Marshal0505 on 2008-06-30
> **tjwoosta said:**
> in gutsy i downloaded a temp gauge that goes on the gnome panel (from synaptic)

but now i cant find it, and i cant even remember what it was called

can anyone help me out?

search query "computer temperature" yields alot of results in synaptic.

for instance: [http://computertemp.berlios.de/](http://computertemp.berlios.de/)

---

### Post by silkstone on 2008-06-30
sensors-applet from synaptic. Then you can add it to your panel.

P.S. Once installed, it will show in the 'Add to Panel' list as 'Hardware Sensors Monitor'.

---

### Post by dje on 2008-06-30
```
sudo apt-get install sensors-applet
```
is the one i use, it gives me cpu and hdd temp on my inspiron 1501

hope that helps,
dje

---

### Post by tjwoosta on 2008-06-30
thanks guys 


thats the one i was looking for

---

### Post by steveneddy on 2008-07-01
What am I missing? I used to be able to monitor the temps of the CPU with this little applet and with gkrellm, but I guess I don't have the correct libs installed.

Anyone know what additional libs I need to install to get this working?

Thanks.

---

### Post by tjwoosta on 2008-07-01
do you have lm-sensors installed?

```
sudo apt-get install lm-sensors
```

---

### Post by steveneddy on 2008-07-01
> **tjwoosta said:**
> do you have lm-sensors installed?

```
sudo apt-get install lm-sensors
```

Yeah - I got all that. I forgot that you have to install the linux modules to get this working right.

```

sudo sensors-detect

```

I can't believe I forgot that.

Oh well, ran the script and restarted and all is well in Steven Eddy Land.

Thanks - :D

---

