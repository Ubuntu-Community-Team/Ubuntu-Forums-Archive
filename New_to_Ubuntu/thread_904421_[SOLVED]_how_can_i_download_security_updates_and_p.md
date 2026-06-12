---
title: "[SOLVED] how can i download security updates and packages?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-29
is it possible to download the security updates and all packages outside xubuntu os? i have a slower connections (dialup) and downloading all the updates took too long, as well as the all packages. I am just thinking if it is possible i rent to internet cafe and download all the packages and burn it to cd, then install it to xubuntu?

---

### Post by hyper_ch on 2008-08-29
it is, if you do:

```

sudo apt-get update && sudo apt-get upgrade

```

It will list all packages that are currently installed on your system and that have upgrades available.

So then you can go with that list to the inet cafe and manually download all those packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . Be sure that you select there the right version (hardy, gutsy, ....).

Then copy them all to the apt cache folder

```

sudo cp *.dep /var/cache/apt/archives/

```

And then run
```

sudo apt-get upgrade

``` again. It will not try to download those packages first because you already have them :)

---

### Post by Oldsoldier2003 on 2008-08-29
it sounds like APTonCD is what you are looking for. [http://www.sourceforge.net/projects/aptoncd](http://www.sourceforge.net/projects/aptoncd)

Edit: Hyper_ch has posted an excellent alternative. If you only want specific updates his method is more efficient and will cost less bandwidth.

---

### Post by hyper_ch on 2008-08-29
or take the easy route as oldsoldier says :)

actually, don't the .debs already need to be downloaded for aptoncd?

---

