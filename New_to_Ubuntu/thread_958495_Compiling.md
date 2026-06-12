---
title: "Compiling"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by P13808 on 2008-10-25
I have the freeciv source code, but I cannot figure oput how to compile it.

---

### Post by snova on 2008-10-25
You shouldn't have to compile it yourself. Freeciv is in the repositories, so you can install it from the package manager. I think it's the freeciv-client package.

But if you really want to, it should come with instructions inside the archive in a file usually called INSTALL.

---

### Post by OutOfReach on 2008-10-25
Generally, it's
```

./configure
make
sudo make install

```

But as snova said, it is best to read a README or INSTALL file and follow the instructions there.

---

### Post by WRDN on 2008-10-25
> **OutOfReach said:**
> Generally, it's
```

./configure
make
sudo make install

```

But as snova said, it is best to read a README or INSTALL file and follow the instructions there.

It is recommended you use "checkinstall" rather than "make install" now, because, if the former is used, an entry is added to Synaptic, allowing for easy removal. The checkinstall program must be installed first though:

```
sudo apt-get install checkinstall
```

---

### Post by P13808 on 2008-10-25
I have no internet access to use the reposititory(on another machine right now) so the rep[ository is a bit out of reach.

---

### Post by john.hall on 2008-10-25
> **P13808 said:**
> I have no internet access to use the reposititory(on another machine right now) so the rep[ository is a bit out of reach.

What about downloading the .deb and using dpkg?  Maybe transfer via a flash drive or something.

[http://www.getdeb.net/app.php?name=FreeCiv](http://www.getdeb.net/app.php?name=FreeCiv)

---

### Post by OutOfReach on 2008-10-25
> **WRDN said:**
> It is recommended you use "checkinstall" rather than "make install" now, because, if the former is used, an entry is added to Synaptic, allowing for easy removal. The checkinstall program must be installed first though:

```
sudo apt-get install checkinstall
```

Of course, I was showing the 'traditional' way of compiling that would work for all Linux distros.

---

### Post by snova on 2008-10-25
I would suggest the same thing, but minus getdeb.net. I have nothing against them, but it's probably for the better to use the official repositories. Go to packages.ubuntu.com and search for the ones you need. Make sure to get dependencies (Freeciv has a separate package for its game data, in particular).

Have you considered getting the repositories on disk? It's a suitable method if you don't have an Internet connection. (Might want to wait until Intrepid, though.)

---

