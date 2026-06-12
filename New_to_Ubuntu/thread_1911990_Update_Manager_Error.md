---
title: "Update Manager Error"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by JeremySchubert on 2012-01-19
Update manager is telling me there are 5 important security packages to download.  But then wont let me download them as 

```
The action would require the installation of packages from unauthenticated sources.
libavcodec-extra-53 libavformat53 libavutil-extra-51 libpostproc52 libswscale2
```

So should I be removing some software from my computer?

---

### Post by Frogs Hair on 2012-01-19
Run the following command in the terminal .```
sudo apt-get update && sudo apt-get upgrade
```
This will update the package information and allow you to install the updates . The message sometimes appearers when the package information is not up to date .

---

