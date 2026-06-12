---
title: "Install GroupWise 8.0.1 on Ubuntu 8.10"
date: 2010-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by cybermatthieu on 2010-07-09
I had problems installing GroupWise 8.0.1 on my Ubuntu 8.10 64 bit install.

I couldn't "alienate" the rpm:
```

dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

```

All I did was to follow the steps showed in this post:
[http://ubuntuforums.org/showthread.php?t=1420744]("http://ubuntuforums.org/showthread.php?t=1420744")

Basically, I had to specify the -g flag of alien :
```
-g, --generate
           Generate a temporary directory suitable for building a package
           from, but do not actually create the package. This is useful if you
           want to move files around in the package before building it. The
           package can be built from this temporary directory by running
           "debian/rules binary", if you were creating a Debian package, or by
           running "rpmbuild -bb <packagename>.spec" if you were creating a
           Red Hat package.
```

Go in the directory generated.
```
cd novell-groupwise-client-8.0.1HP
```


Then change the architecture in the control file from i386 to amd64.
```
sudo vim debian/control
```
Change the line from :
```
Architecture: i386
```
to
```
Architecture: amd64
```

Then build the package with:
```
sudo ./debian/rules binary
```

And the last step is to install the package:
```
cd ..
sudo dpkg -i novell-groupwise-client_8.0.1HP-89146_amd64.deb

```

Hope this helps a few ;)

Matt

---

