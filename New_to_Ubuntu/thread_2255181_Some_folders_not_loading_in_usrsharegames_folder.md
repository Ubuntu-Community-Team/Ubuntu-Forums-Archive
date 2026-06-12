---
title: "Some folders not loading in /usr/share/games folder"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by cakarunkumar on 2014-12-02
Dear Members

I have installed flightgear 3.2 in my ubuntu installation 14.04. However when I load the game from command line by using the following command
```
fgfs --aircraft=777-200LR
```

However the game did not load properly and a long list of errors were generated in teh terminal window, I figured out where the problem is, the game requires some files to be loaded which are located in /usr/share/games/flightgear folder however these files are not readable(even when I tried to check these files manually by browsing to the folder) it shows the following error  "This location could not be displayed. You do not have the permissions necessary to view the contents of “Textures”.". Even I tried to copy the missing files to the folder using command
```
cp -R
``` but that is also not permitting me to edit that folder. Please help me on how to copy these missing files to these folder.

Also FG users please suggest any good launcher app for flightgear 3.2. I prefer FGX but I suppose that is not available for ubuntu. If you have any idea of any repo providing FGX for ubuntu pls post that repo too so that I can use the same.

Thank You
Arun

---

### Post by Impavidus on 2014-12-03
If you have no permission to view the contents of that Textures folder, then flightgear has no permission to read the contents either, as flightgear runs with just your permissions. Give read permission for all on all files in the Textures directory and also execute permission on the directory itself:```
sudo chmod -R a+rX /usr/share/games/flightgear/whatever/Textures
```Chances are that the files are present, but flightgear had just no access to open them.

How did you install flightgear 3.2? PPA or manually? I believe a PPA is available, so that's the preferred way. In the Ubuntu repos you still find 3.0. Anyway, something went wrong in the installation.

---

### Post by cakarunkumar on 2014-12-03
Thank you. That has worked

---

### Post by cakarunkumar on 2014-12-04
And forget to mention. Yes I have installed it from ppa it is available in launchpad page of saiarcot

---

### Post by Impavidus on 2014-12-04
Great. Can you mark this thread as solved? Click thread tools (top of the page) -> mark as solved.

I also used that PPA to install the latest flightgear on 12.04. When switching to 14.04 I reverted to the official repos, but now that 3.2 is available I may move back to the PPA.

---

### Post by cakarunkumar on 2014-12-04
Marked as solved. And welcome to FG 3.2

---

