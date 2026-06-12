---
title: "python: can't open file 'setup.py': [Errno 2] No such file or directory"
date: 2016-02-01
forum: New to Ubuntu
---

### Post by Sky_Dog on 2016-02-01
Hello,

I run "python setup.py install" but I get the following log:

**python: can't open file 'setup.py': [Errno 2] No such file or directory**

I had run before the following command, but they didn't help:
[B]pip install --upgrade pip
python setup.py build
sudo apt-get install python-pip python-dev
sudo apt-get install python-setuptools[/B]

Any idea what to do to run successfully python setup.py build"

Regards
S.

---

### Post by Vladlenin5000 on 2016-02-01
> **Sky_Dog said:**
> Any idea what to do to run successfully python setup.py build"

Run it from with the directory where the setup.py is...

---

### Post by Sky_Dog on 2016-02-02
thanks a lot :-)

---

