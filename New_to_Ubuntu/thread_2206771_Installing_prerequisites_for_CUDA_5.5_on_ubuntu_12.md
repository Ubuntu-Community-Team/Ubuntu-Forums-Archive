---
title: "Installing prerequisites for CUDA 5.5 on ubuntu 12.04"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by Jack_Liddell on 2014-02-20
I'm a fairly new Ubuntu user and have been trying to get the CUDA toolkit installed for a project. I've been following this guide: [http://pastebin.com/fDpqvSi5](http://pastebin.com/fDpqvSi5) to try and get it installed correctly, but I keep running into an issue when trying to install "freeglut3-dev". I have followed the guide I linked on a fresh Ubuntu 12.04 install up to installing the libraries needed for the CUDA samples.

I tried using:

  ```
 sudo apt-get install freeglut3-dev
```

but get the following error:

```
The following packages have unmet dependencies.
 freeglut3-dev : Depends: libgl1-mesa-dev or
                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Unable to correct problems, you have held broken packages.
```

Any help much appreciated, thanks.

---

