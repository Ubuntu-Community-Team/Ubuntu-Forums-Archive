---
title: "Can't install the One Drive Client in Ubuntu"
date: 2019-09-12
forum: New to Ubuntu
---

### Post by stephanielira on 2019-09-12
I am trying to syncronize OneDrive in Ubuntu throw the following codes and i am receiving the error message bellow when i type the command "make":
```
git clone [https://github.com/skilion/onedrive.git](https://github.com/skilion/onedrive.git)
cd onedrive
make
sudo make install
```

Error message: 
```
dmd -g -ofonedrive -O -L-lcurl -L-lsqlite3 -L-ldl -J. src/config.d src/itemdb.d src/log.d src/main.d src/monitor.d src/onedrive.d src/qxor.d src/selective.d src/sqlite.d src/sync.d src/upload.d src/util.d
make: dmd: Command not found
make: *** [Makefile:29: onedrive] Error 127
```
How can i correct this?

---

### Post by oldos2er on 2019-09-12
Did you install dmd?

---

### Post by GrouchyGaijin on 2019-09-16
For what it is worth in the past I spent a lot of time trying to get the various incarnations of the OneDrive script from github to work.
On occasion things would work well for a few days and then files would be skipped and the syncing was simply not reliable.
In the end I gave up trying to sync OneDrive with my Linux machine.

---

