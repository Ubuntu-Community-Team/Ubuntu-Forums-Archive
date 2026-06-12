---
title: "How to pass options to checkinstall?"
date: 2009-09-16
forum: Packaging and Compiling Programs
---

### Post by ernstblaauw on 2009-09-16
Hi,

Before, I did use the commands
```
make sqlite=true unstable=true
sudo make sqlite=true unstable=true install
```
to install the program.

Now, I want to make a .deb package and tried checkinstall. However, I'm not succeeding in passing the options 'sqlite=true unstable=true' to the package via checkinstall. Does anybody know the correct command? Everytime, it the options are causing an error in checkinstall:

```
checkinstall: unrecognized option '--sqlite=true'
checkinstall: unrecognized option '--unstable=true'
```

or (if I removed the dashes):
```
/var/tmp/tmp.OvHiYxyoYI/installscript.sh: 4: sqlite=true: not found
```

Thanks for your help :-).

---

### Post by andrew.46 on 2009-09-16
Hi ernstblaauw,

> **ernstblaauw said:**
> 
```
make sqlite=true unstable=true
sudo make sqlite=true unstable=true install
```

I have not tested this:

```
sudo checkinstall make sqlite=true unstable=true install
```

does not work? [Documentation on the website]("http://www.asic-linux.com.mx/~izto/checkinstall/docs/README") suggests:

```

  NOTE: If you give no arguments to checkinstall it will run a "make install".
  If you give arguments, the first non-option argument will be used as the
  install command. This is useful when the install command is not "make install"
  but something else like "make install_packages" or "setup" or whatever, i.e. 

  checkinstall make install_packages
  checkinstall make modules_install
  checkinstall install.sh
  checkinstall setup
  checkinstall rpm -i my-package-1.0.i386-1.rpm

```

but I am not sure how to utilise this with your scenario...

Andrew

---

### Post by ernstblaauw on 2009-09-16
Thanks! Indeed, ```
sudo checkinstall make sqlite=true unstable=true install
``` works. I overlooked this item in the manual.

---

### Post by andrew.46 on 2009-09-16
Hi ernstblaauw,

> **ernstblaauw said:**
> Thanks! Indeed, ```
sudo checkinstall make sqlite=true unstable=true install
``` works.


Excellent news :). I shall file this one away for my own personal use as to tell the truth I was also not aware of this syntax for checkinstall and it certainly opens up a few possibilities.

Andrew

---

