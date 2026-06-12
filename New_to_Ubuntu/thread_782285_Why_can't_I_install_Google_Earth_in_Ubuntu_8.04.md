---
title: "Why can't I install Google Earth in Ubuntu 8.04"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ptn107 on 2008-05-04
All I get is this when I attempt to install:

```
phil@phil-desktop:~$ sudo apt-get install google-earth 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package google-earth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package google-earth has no installation candidate
```

I'm running Ubuntu 8.04 64-bit.

---

### Post by damis648 on 2008-05-04
download the install script from the Google Earth website then run as shell script.

---

### Post by Tatty on 2008-05-04
Do you have the medibuntu repo enabled?  

I believe in hardy there is an older version of googlearth available in the multiverse repo, which is called googleearth-package.

Otherwise you will have to enable the medibuntu repo.

---

### Post by spudratic on 2008-05-04
I installed the new one with the flight simulator pretty cool lol. The Medibuntu repo has it  for install.you have to add the repo to your sources list then reload the package manager and search for google earth.for instructions search the forum.

---

### Post by Sinkingships7 on 2008-05-04
Google Earth isn't in the repo's, I think. Get it from [here.]("http://earth.google.com/download-earth.html")

---

### Post by spudratic on 2008-05-04
It is in the medubuntu repo thats where I got it 4.3 is the version

---

### Post by Tatty on 2008-05-04
> **Sinkingships7 said:**
> Google Earth isn't in the repo's, I think. Get it from [here.]("http://earth.google.com/download-earth.html")

It is in the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo

There is a package called googleearth-package in the multiverse repo but having now read its description im not totally sure what this is.

---

