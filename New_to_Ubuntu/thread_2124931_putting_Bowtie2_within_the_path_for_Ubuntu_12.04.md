---
title: "putting Bowtie2 within the path for Ubuntu 12.04"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by raw937 on 2013-03-12
I want to put a program called Bowtie2 in the usr/bin path so I can exe it from any where. But, it has many exe parts to it..

---

### Post by Cheesemill on 2013-03-12
Instead of trying to add it to the /usr/bin directory, why don't you just add the directory containing the Bowtie2 executables to your path?

You can do this by adding the following line to your ~/.bashrc file...
```
PATH="/path/to/bowtie2:$PATH"
```

You'll need to re-source your ~/.bashrc for the change to take effect, you can either log out and back in or run...
```
. ~/.bashrc
```

---

