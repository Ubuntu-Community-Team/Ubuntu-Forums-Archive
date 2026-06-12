---
title: "unable to update libboost-graph-dev and libnetcdf-dev"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by ilFonta on 2013-06-06
Hello everybody
every time I try to upgrade my system i get thi message (italian):

I seguenti pacchetti sono stati mantenuti alla versione attuale:
  libboost-graph-dev libnetcdf-dev
0 aggiornati, 0 installati, 0 da rimuovere e 2 non aggiornati.

Translation:
The follow packages have not been updated
0 aggiornati, 0 installati, 0 da rimuovere e 2 non aggiornati.

I also tryed with 
sudo apt-get dist-upgrade, but.... nothing.

Any suggestion?

I use Lubuntu 13.04 64 bit

---

### Post by newb85 on 2013-06-06
You could try
```
sudo apt-get -f upgrade
```

But, if no other error messages were given, then nothing's really broken.  The package manager just has some reason for holding back those upgrades (like perhaps some of the dependencies need upgrades that haven't made it down the pipeline yet).  This isn't really a problem, and will probably go away in a couple days.

---

### Post by ilFonta on 2013-06-07
Thank you. I tryied with your script, but anything change. I'll try to forget this little problem. Thank you so much. Bye

---

