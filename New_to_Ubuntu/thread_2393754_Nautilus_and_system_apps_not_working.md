---
title: "Nautilus and system apps not working"
date: 2018-06-07
forum: New to Ubuntu
---

### Post by aeris9x9 on 2018-06-07
Hello. Im new to linux and just today when i clicked on my files icon, it just kept loading and didn't startup. Even the settings was not opening. i tried opening nautilus from the terminal and i got this.
nautilus: symbol lookup error: /usr/lib/x86_64-linux-gnu/tracker-2.0/libtracker-data.so.0: undefined symbol: sqlite3_bind_pointer
Don't know what to do. Please, can somebody help?
Im on ubuntu budgie 18.04

---

### Post by vanadium on 2018-06-07
Here is a bug report with a similar error message, for a gnome desktop: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1773207](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1773207) I found a similar issue for Solus ([https://dev.solus-project.com/T4850](https://dev.solus-project.com/T4850)) and for Manjaro). You could try doing what is suggested in the solus thread and reinstall two relevant packages, which for Ubuntu 18.04 will be libtracker-sparql-2.0-0 and sqlite3. You can do so with "sudo apt install --reinstall libtracker-sparql-2.0-0 sqlite3". 

If this fails to solve the issue, then perhaps try once again but after selecting a different server in "Software and updates". Not sure how likely this is, but there might be a temporary error in your mirror server.

If that also does not work, a more invasive attempt could be to log on on a virtual console (on login screen press Ctrl+Alt+F3 and login to the text terminal, then "purge" nautilus and both mentioned packets (which also should take down budgie-desktop, if not, remove that one manually as well) and then perform a reinstall of the budgie-desktop package,  which automatically should pull in nautilus and all dependencies again.
```

sudo apt purge budgie-desktop nautilus libtracker-sparql-2.0-0 sqlite3
sudo apt install budgie-desktop

```
This may remove a lot of other packages, but all needed for a functional Budgie desktop should be restored after running the second command.

---

### Post by sunnysharan369 on 2018-11-03
I faced this problem too. I fixed it by reinstalling sqlite3 library from the source code. 
Please follow these steps:-

1.) wget [https://sqlite.org/2018/sqlite-autoconf-3250200.tar.gz](https://sqlite.org/2018/sqlite-autoconf-3250200.tar.gz)
2.) tar -xvf sqlite-autoconf-3250200.tar.gz
3.) cd sqlite-autoconf-3250200
4.) ./configure
5.) make 
6.) sudo make install

Thanks

---

