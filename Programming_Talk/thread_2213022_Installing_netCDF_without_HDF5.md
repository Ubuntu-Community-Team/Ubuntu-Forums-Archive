---
title: "Installing netCDF without HDF5"
date: 2014-03-24
forum: Programming Talk
---

### Post by alma2 on 2014-03-24
Hello everyone,
I'm a beginner on Ubuntu, and I ran into a problem with installing netCDF via terminal. I'm trying to install it without HDF5, and using this command:
./configure --prefix=/usr/local/netcdf
make check install
the problem is, the process is running, but in the end netcdf is not install. 
Can anybody help me?
Thank you

---

### Post by cariboo on 2014-03-27
This is nowhere near an Absolute Beginner question, moved here so that you may get better help.

---

### Post by monkeybrain20122 on 2014-03-27
After running the configure script there are two commands, not three
```
make
sudo checkinstall
```

'checkinstall' is one word without space and obviously the program checkinstall has to be installed in your system first (sudo apt-get install checkinstall). The checkinstall command is invoked with sudo because it needs root privilege to write to /usr/local

---

### Post by alma2 on 2014-04-23
Thank you guys, this was really helpfull. I will try to install it now, hopefully without no problems.

---

