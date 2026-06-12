---
title: "Problem with my first package"
date: 2009-10-16
forum: Packaging and Compiling Programs
---

### Post by MartinEve on 2009-10-16
Hi all,

I have written a program under the GPL 3, which is hosted on launchpad.

I successfully setup all my build routines, pbuilder ran without a problem and the output looked good. However, upon running an apt install from my ppa, the binary is not installed into anywhere accessible.

Having read the guide, I see that it is not allowed for the build rule to perform any command that allows root privileges.

My question is, then: how and where should one put install logic? By this I mean, for example, copying the compiled binary to /usr/bin/ and, upon remove, getting rid of it because, at present, this is not happening.

If more information is required, the project is available at [https://launchpad.net/ala](https://launchpad.net/ala)

Apologies if I have missed something, I did my best to read the guides but I am entirely new to packaging under Debian/Ubuntu and I think the current guide makes some assumptions about basic knowledge of packaging.

Best,

Martin

---

### Post by Bachstelze on 2009-10-16
> **MartinEve said:**
> 
My question is, then: how and where should one put install logic? By this I mean, for example, copying the compiled binary to /usr/bin/ and, upon remove, getting rid of it because, at present, this is not happening.

In the install rule. ;)

[https://wiki.ubuntu.com/PackagingGuide/Complete#rules](https://wiki.ubuntu.com/PackagingGuide/Complete#rules)

---

### Post by MartinEve on 2009-10-16
Bah, I apologize - I must have been severely tired to miss that!

Many thanks for the reply; I will repackage tomorrow :)

---

### Post by MartinEve on 2009-10-17
Hiya,

I'm afraid I'm still encountering a problem.

I added this rule to debian/rules in my package folder:

```

install: build
	dh_clean
	dh_installdirs

	# Add here commands to compile the package.
	$(MAKE) install

```

which I figure should do what I want based on my makefile.

However, after doing my debuild -S command, I am unable to complete the pbuilder test:

```

dh_clean                                              
dh_installdirs                                        
# Add here commands to compile the package.           
/usr/bin/make install                                 
make[1]: Entering directory `/tmp/buildd/ala-1.0b'    
make[2]: Entering directory `/tmp/buildd/ala-1.0b'    
make[2]: Leaving directory `/tmp/buildd/ala-1.0b'
make[2]: Entering directory `/tmp/buildd/ala-1.0b/ala'
make pre-install-local-hook prefix=/usr
make[3]: Entering directory `/tmp/buildd/ala-1.0b/ala'
make[3]: Leaving directory `/tmp/buildd/ala-1.0b/ala'
make install-satellite-assemblies prefix=/usr
make[3]: Entering directory `/tmp/buildd/ala-1.0b/ala'
make[3]: `install-satellite-assemblies' is up to date.
make[3]: Leaving directory `/tmp/buildd/ala-1.0b/ala'
mkdir -p '/usr/lib/ala'
mkdir: cannot create directory `/usr/lib/ala': Permission denied
make[2]: *** [install-local] Error 1
make[2]: Leaving directory `/tmp/buildd/ala-1.0b/ala'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/tmp/buildd/ala-1.0b'
make: *** [install] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env
    -> removing directory /var/cache/pbuilder/build//9137 and its subdirectories

```

As you can see, the install rule is not liking the privileged mkdir.

Am I missing something? Surely privileged commands are allowed in the install rule, even if not in the build rule...

Have I put this in the wrong place?

Any help much appreciated.

Martin

---

### Post by Bachstelze on 2009-10-17
You must define at least [font=monospace]prefix[/font] like in the example I showed you, so that the file *does not* get installed in /usr (since you don't have permission to write to it), but in a special location so that the package can be built afterwards.

---

### Post by MartinEve on 2009-10-18
Many thanks - working now :)

I'm sorry I misunderstood you - I thought that the logic I supplied in the install rule should *perform* the install, not just a build that will then be moved.

Martin

---

