---
title: "python- pytables and hdf5"
date: 2011-11-03
forum: Programming Talk
---

### Post by abraxas334 on 2011-11-03
Hi,
I am trying to install pytables, but I need hdf5 installation. The error I get when I try to run setup for pytables is:

 ERROR:: Could not find a local HDF5 installation.
   You may need to explicitly state where your local HDF5 headers and
   library can be found by setting the ``HDF5_DIR`` environment
   variable or by using the ``--hdf5`` command-line option.

I am not sure how I install/ check set the right variables. I am not even sure if hdf5 is installed.
I have downloaded the libraries, but I can't seem to find a configure or make script. Also I would first like to check if it is already installed or not.

Thanks for any help regarding this:

---

### Post by MadCow108 on 2011-11-03
why do you want to install it yourself? whats wrong with the package?
```
apt-cache search pytables
python-tables - hierarchical database for Python based on HDF5
```

---

