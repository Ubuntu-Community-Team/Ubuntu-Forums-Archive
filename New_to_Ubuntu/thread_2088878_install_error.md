---
title: "install error"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by nycap on 2012-11-27
i get this error after running sudo make install:

```
usrp2.cc:43:5: note:   no known conversion for argument 2 from ‘usrp2::usrp2::sptr {aka boost::shared_ptr<usrp2::usrp2>}’ to ‘int’
usrp2.cc:38:10: note: usrp2::usrp_table_entry::usrp_table_entry(const usrp2::usrp_table_entry&)
usrp2.cc:38:10: note:   candidate expects 1 argument, 2 provided
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from /home/matt/src/gnuradio-3.2.2/usrp2/host/include/usrp2/usrp2.h:22,
                 from usrp2.cc:23:
/usr/include/boost/smart_ptr/shared_ptr.hpp: In instantiation of ‘boost::shared_ptr<T>::shared_ptr(Y*) [with Y = int; T = usrp2::usrp2]’:
usrp2.cc:73:56:   required from here
/usr/include/boost/smart_ptr/shared_ptr.hpp:183:50: error: cannot convert ‘int*’ to ‘usrp2::usrp2*’ in initialization
```

the source compiles but the install is hung up here.  thanks in advance for any ideas.

---

### Post by Monotoko on 2012-11-27
Need a lot more detail here, which program are you trying to install? Have you done "./configure" then "make" and finally "make install"?

---

### Post by nycap on 2012-11-27
the program is gnu radio 3.2.2  here is commands i used in terminal

```
mkdir ~/src; cd ~/src
wget ftp://ftp.gnu.org/gnu/gnuradio/gnuradio-3.2.2.tar.gz
tar zxvf gnuradio-3.2.2.tar.gz
cd gnuradio-3.2.2
./configure
make -j 4 CC=gcc-4.1 CXX=g++-4.1
make check
sudo make install
```

configures and compiles without error but stuck at the install.

---

### Post by oldos2er on 2012-11-27
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=2088544](http://ubuntuforums.org/showthread.php?t=2088544)

---

