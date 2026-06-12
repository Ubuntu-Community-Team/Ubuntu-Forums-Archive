---
title: "Does iridium browser work with 22.04 ?"
date: 2022-08-03
forum: New to Ubuntu
---

### Post by Innernet on 2022-08-03
Hi.  
Tried and was not found it among the available software repository.  Is there a magic process ?

---

### Post by Perfect Storm on 2022-08-03
You could try convert  the Fedora Linux .rpm package to .deb with alien command
Or try search for a PPA if any are availble.

[https://dl.iridiumbrowser.de/fedora_36/](https://dl.iridiumbrowser.de/fedora_36/)

```

sudo apt install alien

```

then

```

cd /to/package/distionation
alien --to-deb file_name.rpm
chmod +x file_name.deb
sudo apt install ./file_name.deb

```

---

### Post by grahammechanical on 2022-08-04
The Iridium web site does not list a version that will run on Ubuntu. I have found these instructions. Whether they will work for Ubuntu 22.04 I cannot say. It is your decision. I have seen instructions for Ubuntu 18.04 but not for Ubuntu 20.04. It could be that the Iridium developers are no longer providing a Debian (deb) packaged version.

[https://websetnet.net/how-to-install-iridium-browser-on-ubuntu/](https://websetnet.net/how-to-install-iridium-browser-on-ubuntu/)

Regards

---

### Post by ActionParsnip on 2022-08-04
[https://ubunlog.com/en/iridium-browser-thought-privacy/](https://ubunlog.com/en/iridium-browser-thought-privacy/)

Seems there is a repo for it. Seems to be yet another chromium based browser

---

