---
title: "HOWTO: Install the latest stable Quod Libet"
date: 2005-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by PsychoTrauma on 2005-12-06
This guide will show you what you need and how to install the latest stable quod libet with support for mp3/mod/flac/mpc.

Open a terminal and type:

```
sudo apt-get install build-essential automake1.9 gstreamer0.8-mad python-pymad python-modplug libmpcdec-dev swig libflac-dev python-dev checkinstall
```

Open a web browser and go to [http://www.sacredchao.net/quodlibet/wiki/]("http://www.sacredchao.net/quodlibet/wiki/") and save pyflac and pymusepack to your home directory.

Open a terminal and type:

```
tar xvfz pyflac-0.0.4.tar.gz
```

```
tar xvfz pymusepack-0.4.tar.gz
```

```
cd pyflac-0.0.4
```

```
make
```

```
sudo checkinstall
```

After you have installed pyflac do:

```
cd ..
```

```
cd pymusepack-0.4
```

```
./setup.py build
```

```
sudo checkinstall
```

After installing pymusepack open your web browser again and go to [ftp://ftp.ubuntu.com/ubuntu/pool/universe/q/quodlibet]("ftp://ftp.ubuntu.com/ubuntu/pool/universe/q/quodlibet") and save quodlibet_0.15-3_all.deb to your home directory.

Open a terminal and type:

```
cd ..
```

```
sudo dpkg -i quodlibet_0.15-3_all.deb
```

After that everything should be installed and you can now enjoy the latest stable quod libet thanks to dapper.

---

