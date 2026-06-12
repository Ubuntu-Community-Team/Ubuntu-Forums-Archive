---
title: "nmap installation errors"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by jba6511 on 2008-08-09
i am trying to install nmap 4.68 from source. I know it is in the repositories but would like the updated version. Running ./configure 2>configerrors and then less configerrors produces the following:

config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting

make seems to run fine and then when I run sudo checkinstall or sudo make install I get the following:

[PHP]blake@deviant:~/nmap-4.68$ sudo make install
./shtool mkdir -f -p -m 755 /usr/local/bin /usr/local/share/man/man1 /usr/local/share/nmap
mkdir: cannot create directory `/usr/local/bin': File exists
make: *** [install-nmap] Error 1
[/PHP]

[PHP]./shtool mkdir -f -p -m 755 /usr/local/bin /usr/local/share/man/man1 /usr/local/share/nmap
mkdir: cannot create directory `/usr/local/bin': File exists
make: *** [install-nmap] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

[/PHP]

Any ideas?

---

### Post by nicedude on 2008-08-11
Use the 4.68 Deb package located at the Debian Linux software download address below to install it instead of trying to compile. I am not sure why but apparently it might not just compile cleanly on Ubuntu so use of the deb file below is what is recommended at the Nmap homepage and there must be a reason although I don't know it.

[http://packages.debian.org/unstable/nmap](http://packages.debian.org/unstable/nmap)

Hope this helps

nicedude

---

### Post by iaculallad on 2008-08-11
In your terminal:

```
sudo apt-get install nmap
```

---

### Post by rizitis on 2008-08-11
Alternative, if you want, you can install  zenmap.
```
sudo apt-get install zenmap
```

---

### Post by jba6511 on 2008-08-12
thanks i will give the deb a try. As I stated previously i did not want to grab nmap from synaptic as it is an older version.

---

### Post by jba6511 on 2008-08-16
> **nicedude said:**
> Use the 4.68 Deb package located at the Debian Linux software download address below to install it instead of trying to compile. I am not sure why but apparently it might not just compile cleanly on Ubuntu so use of the deb file below is what is recommended at the Nmap homepage and there must be a reason although I don't know it.

[http://packages.debian.org/unstable/nmap](http://packages.debian.org/unstable/nmap)

Hope this helps

nicedude

Thanks nicedude, package installed without any issues. Nice pic of ricky as well.

---

