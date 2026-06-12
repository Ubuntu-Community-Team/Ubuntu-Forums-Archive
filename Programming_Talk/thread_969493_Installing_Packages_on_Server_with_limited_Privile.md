---
title: "Installing Packages on Server with limited Privileges"
date: 2008-11-03
forum: Programming Talk
---

### Post by thisxcantxexist on 2008-11-03
I'm trying to install the ImageMagick package as well as a program called OOF2 on a server at my university. I have been given privileges to install in the folder /afs/engin.umich.edu/contrib/oof2

when trying to install ImageMagick i run the commands

./configure
make install

during the make install it tries to install to /usr/bin/local/...... which i do not have privileges to so the install fails

i have tried the -prefix= and the -exec-prefix= options on the configure however the make install still tries to install to /usr/bin/local

how can i limit the install to my folder /afs/engin.umich.edu/contrib/oof2 so i will have privileges to install it?

For the oof2 install i have to run
python setup.py build
python setup.py install

is there similar options for these commands that will allow me to limit the install to the folder /afs/engin.umich.edu/contrib/oof2?

---

### Post by jamescox84 on 2008-11-03
Its a double dash ('--', not '-') for the prefix option:
```
./configure --prefix=/home/james/ImageMagick
```
For the python package try:
```

python setup.py build
python setup.py install --prefix=/home/james/oof2

```
I was only able to try the ImageMagick bit but it worked, unprivilaged.  As for oof2 it seemed to crash during build, and seems I have no intention of using it, and I assume you already have it built, I'll leave it there.

Hope this helps!

---

