---
title: "need help with permissions/installing"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Arex Bawrin on 2008-10-19
Hi, I'm trying to install a Rapidshare commandline downloader, but I am a bit confused with the directions they give for installing:

```
how to install

download tar archive from here
unpack it into /usr/bin

    $ chmod a+x /usr/bin/modrapi
    $ modrapi configure
```

I tried extracting the file to the /usr/bin directory, but it said I did not have permission. Sorry, I tried searching for something like this before I posted.

---

### Post by BDNiner on 2008-10-19
you need to use the command sudo to extract the archive to the directory 
/usr/bin. Are you using the command line to extract it or the nautilus (the file manager)?

---

### Post by oldos2er on 2008-10-19
In order to have write access to anything outside your home directory, you need admin privileges. In Ubuntu, do this by prepending the command with "sudo."

sudo tar zxvf filename.tar [assumes the tar file is already in /usr/bin].

sudo chmod a+x /usr/bin/modrapi

 etc.

 Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Arex Bawrin on 2008-10-19
Well what if I'm using the nautilus file manager?

---

### Post by Sealbhach on 2008-10-19
You can download a .deb of it from this page:

[http://mundogeek.net/rapidshare-dl/](http://mundogeek.net/rapidshare-dl/)

Maybe that might be better?


.

---

### Post by BDNiner on 2008-10-19
you can launch the file manager with admin rights by typing 
```

gksudo nautilus

```

in a terminal window or in the run box (Alt+F2)

be very carefull when running nautilus as root, if you mistakenly delete something then you could be in trouble.

---

### Post by Arex Bawrin on 2008-10-19
Ok, It'll probably be safer via terminal. Thanks for the help!

---

