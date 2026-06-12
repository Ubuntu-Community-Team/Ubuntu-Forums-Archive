---
title: "Packaging a binary: &quot;No rule to make target 'clean'&quot;?"
date: 2009-04-20
forum: Packaging and Compiling Programs
---

### Post by Ubuntiac on 2009-04-20
Hi there,

I'm packaging a blender game I'm making. Blender already creates a working binary executable, so I don't need to compile anything.

Now I'm just trying to create the simplest deb I can using this guide:
[http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source](http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source)

dh_make --createorig seems to work fine, but then dpkg-buildpackage -rfakeroot gives me:
```
make[1]: Entering directory `/home/user/Desktop/tuxworld-0.1'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/user/Desktop/tuxworld-0.1'
make: *** [clean] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2
```

The rules file in the debian folder includes:
```
clean: 
	dh_testdir
	dh_testroot
	rm -f build-stamp configure-stamp

	# Add here commands to clean up after the build process.
	$(MAKE) clean
	rm -f tux_runtime
	dh_clean 
```

I have autotools-dev, fakeroot, dh-make and build-essential installed.

Any ideas would be really appreciated! :D

---

