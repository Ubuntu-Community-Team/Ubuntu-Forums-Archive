---
title: "How to write to /etc and other files in a Makefile"
date: 2012-04-17
forum: Packaging and Compiling Programs
---

### Post by josephmills on 2012-04-17
hello there all I am trying to package up a well package and am having troubles with the Makefile. I need to mkdir to etc and I keep on getting permissions troubles. What is the work around for this. example of my make file 
```
#!/usr/bin/make
install: 
	mkdir -p /etc/zpanel
	mkdir -p /etc/zpanel/configs
	mv $(CURDIR)/ubuntu_11_10/ /etc/zpanel/configs
	mkdir -p /etc/zpanel/panel
	mkdir -p /etc/zpanel/docs
	mkdir -p /var/zpanel
	mkdir -p /var/zpanel/hostdata
	mkdir -p /var/zpanel/hostdata/zadmin
	mkdir -p /var/zpanel/hostdata/zadmin/public_html
	mkdir -p /var/zpanel/logs
	mkdir -p /var/zpanel/backups
	mkdir -p /var/zpanel/temp
	install -m 755 $(CURDIR)/setso /usr/bin
	install -m 755 $(CURDIR)/zppy /usr/bin
```

I am real new to making a makefile. 

also how to cp -r something in a make file 

```
#!/usr/bin/make
install: 
	cp $(CURDIR)/ubuntu_11_10/* /etc/zpanel/configs
	
```

??


Thanks for your time.


This is my plan 

make the make file that makes the new dirs and prep for dh_make 
run dh_make alter the debian folder 
build package

---

### Post by bregma on 2012-04-17
> 
```
#!/usr/bin/make
install: 
	mkdir -p /etc/zpanel
	mkdir -p /etc/zpanel/configs
	mv $(CURDIR)/ubuntu_11_10/ /etc/zpanel/configs
	mkdir -p /etc/zpanel/panel
	mkdir -p /etc/zpanel/docs
	mkdir -p /var/zpanel
	mkdir -p /var/zpanel/hostdata
	mkdir -p /var/zpanel/hostdata/zadmin
	mkdir -p /var/zpanel/hostdata/zadmin/public_html
	mkdir -p /var/zpanel/logs
	mkdir -p /var/zpanel/backups
	mkdir -p /var/zpanel/temp
	install -m 755 $(CURDIR)/setso /usr/bin
	install -m 755 $(CURDIR)/zppy /usr/bin
```

(1) use a variable for basic directories so they can be changed and (2) prefix with the DESTDIR variable.
```
#!/usr/bin/make

prefix = /usr
sysconfdir = /etc
pkgdir = /var/zpanel

install: 
	mkdir -p $(DESTDIR)/$(sysconfdir)/zpanel
	mkdir -p $(DESTDIR)/$(sysconfdir)/zpanel/configs
	cp -r $(CURDIR)/ubuntu_11_10/ $(DESTDIR)/$(sysconfdir)/zpanel/configs
	mkdir -p $(DESTDIR)/$(sysconfdir)/zpanel/panel
	mkdir -p $(DESTDIR)/$(sysconfdir)/zpanel/docs
	mkdir -p $(DESTDIR)/$(pkgdir)/zpanel
	mkdir -p $(DESTDIR)/$(pkgdir)/hostdata
	mkdir -p $(DESTDIR)/$(pkgdir)/hostdata/zadmin
	mkdir -p $(DESTDIR)/$(pkgdir)/hostdata/zadmin/public_html
	mkdir -p $(DESTDIR)/$(pkgdir)/logs
	mkdir -p $(DESTDIR)/$(pkgdir)/backups
	mkdir -p $(DESTDIR)/$(pkgdir)/temp
	install -m 755 $(CURDIR)/setso $(DESTDIR)/$(prefix)/bin
	install -m 755 $(CURDIR)/zppy $(DESTDIR)/$(prefix)/bin
```

Now, to test, you would run 'make install DESTDIR=/tmp/puppy' and examine what gets put into /tmp/puppy.  To install o your local system, run 'sudo make install'.  When dpkg-buildpackage is run, assuming a minimal dh-based debian/rules file, it will effectively run 'make install DESTDIR=debian/tmp'.

---

### Post by josephmills on 2012-04-17
Thank You so much for the examples and also the book on irc. 
[http://oreilly.com/catalog/make3/book/ch11.pdf](http://oreilly.com/catalog/make3/book/ch11.pdf)

Marking as solved.

---

