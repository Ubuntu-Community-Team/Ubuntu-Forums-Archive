---
title: "Installing netcdf4"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by jamie10 on 2014-03-09
Hello fellow Ubunters!

I am afraid I'm new at this and I'm struggling to install netcdf4 on my Ubuntu 12.04.

I have installed HDF5, all of its dependencies and the netcdf-4.3.1.1.tar.gz file. 

Once I've entered the right directory I execute the following:

LDFLAGS=-L/usr/local/lib CPPFLAGS=-I/usr/local/include ./configure --enable-netcdf-4 --enable-dap --enable-shared --prefix=/usr/local
make
sudo make check install

[FONT=arial]I then get the following fails in the terminal:

FAIL: test_varm3
FAIL: t_auth

See ncdap_test/test-suite.log

Would anyone be able to tell me where I'm going wrong?

Cheers,

Jamie[/FONT]

---

