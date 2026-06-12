---
title: "How to install Firefox 2.0.0.17 in Ubuntu 8.10?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by mignihc on 2008-11-08
Dear all,

I reall \y need firefox 2.0.0.17 to be install since quite a few of my plugin can only be use in firefox 2.0.0.17.

Will like to know how can I install it to Ubuntu 8.10 by auto/manual?

Also do I need to uninstall any package?

Thanks.

Sincerely New Noob,
mignihc

---

### Post by bscbrit on 2008-11-08
[http://packages.ubuntu.com/hardy/i386/firefox-2/download](http://packages.ubuntu.com/hardy/i386/firefox-2/download)

If you go to this link it will allow you to download firefox-2.  You will note that it is from a Hardy repository and not intended for Intrepid.  However, I have checked and all the dependencies are met.  It does install.

HOWEVER:

It might not continue to work if you upgrade other parts of the system.

It might need the .mozilla directory deleting from your user area so that it can create a new one that is compatible with version 2.

There are no guarantees that it will not have adverse effects on other software.


If it were me, and if I really need version 2, I would install it and take the risk but I can take no responsibility for how it behaves on your system or the potential for loss of your data.


Incidentally, can you tell me which extensions do not work for you?  It might be easier to upgrade the extensions.

---

### Post by thilinamb on 2008-12-20
This is possible with a small trick. I was able to install FF2 without any conflicts with FF3(default FF version for Ubuntu 8.10).

First you need to modify the source list, so that it refers to the package sources of Ubuntu Gusty. Before changing that do not forget to keep a copy of the current sources list. Following command will make a copy of the current sources list and save it as sources.list.backup

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Now start modifying the content of the original sources.list.

```
sudo gedit /etc/apt/sources.list
```

Now replace the content of this file with the following list

```
deb http://archive.canonical.com/ubuntu hardy partner
deb http://br.archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://br.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb http://packages.medibuntu.org/ hardy free non-free
```

Now get a update and install FireFox 2

```
sudo apt-get update
sudo apt-get install firefox-2
```

Once the above commands are successfully completed FF2 will be installed and it will be ready to install. But changing the package sources to an older version will make the system unstable. So replace the modified sources list with the original one.

```
sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list
```

Now get a update for the package sources.

```
sudo apt-get update
```

More on this can be found in this [[COLOR="Red"]blog post[/COLOR]]("http://thilinamb.wordpress.com/2008/12/18/how-to-switch-back-to-mozilla-firefox-2-in-ubuntu-810/").

Cheers. :)

/ thilina.

---

