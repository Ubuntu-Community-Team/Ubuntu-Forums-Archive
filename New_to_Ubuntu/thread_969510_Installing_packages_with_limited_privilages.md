---
title: "Installing packages with limited privilages"
date: 2008-11-03
forum: New to Ubuntu
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

### Post by bwhite82 on 2008-11-03
Its been a while but can't you specify the directory with make?

> make install --directory=/my/install/dir

---

### Post by bodhi.zazen on 2008-11-03
Well, in theory what you are doing should work ...

[http://www.control-escape.com/linux/lx-swinstall-tar.html](http://www.control-escape.com/linux/lx-swinstall-tar.html)

Try ./configure --help

---

### Post by thisxcantxexist on 2008-11-03
After running

make install --directory=/afs/engin.umich.edu/contrib/oof2/ImageMagick-6.4.5

the install proceeds well until it displays

cd PerlMagick && make CC='gcc -std=gnu99' install
make[3]: Entering directory `/afs/engin.umich.edu/contrib/oof2/ImageMagick-6.4.5/PerlMagick'
Warning: You do not have permissions to install into /usr/lib64/perl5/site_perl/5.8.8/x86_64-linux-thread-multi at /usr/lib/perl5/5.8.8/ExtUtils/Install.pm line 114.
mkdir /usr/lib64/perl5/site_perl/5.8.8/x86_64-linux-thread-multi/auto/Image: Permission denied at /usr/lib/perl5/5.8.8/ExtUtils/Install.pm line 176
make[3]: *** [pure_site_install] Error 13
make[3]: Leaving directory `/afs/engin.umich.edu/contrib/oof2/ImageMagick-6.4.5/PerlMagick'
make[2]: *** [install-exec-perl] Error 2
make[2]: Leaving directory `/afs/engin.umich.edu/contrib/oof2/ImageMagick-6.4.5'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/afs/engin.umich.edu/contrib/oof2/ImageMagick-6.4.5'
make: *** [install] Error 2
make: Leaving directory `/afs/engin.umich.edu/contrib/oof2/ImageMagick-6.4.5'

---

