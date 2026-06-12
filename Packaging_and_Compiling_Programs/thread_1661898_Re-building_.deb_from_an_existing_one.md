---
title: "Re-building .deb from an existing one"
date: 2011-01-07
forum: Packaging and Compiling Programs
---

### Post by gnagnibu on 2011-01-07
[FONT=Verdana]Hello everybody.
I have to rebuild Zabbix server .deb file because the original was no compiled with ssh support and I want to create a new package, with a different name from the original.

I've downloaded source code with

apt-get source zabbix

and next checked the dependencies with 

apt-get build-dep zabbix

Netx, I've modified zabbix-1.8.2/debian/rules

CONFFLAGS_SERVER  = --host=$(DEB_HOST_GNU_TYPE) \
[/FONT][FONT=Verdana]                    --build=$(DEB_BUILD_GNU_TYPE) \
                    --prefix=/usr \
                    --mandir=\$${prefix}/share/man \
                    --infodir=\$${prefix}/share/info \
                    --enable-server \
                    --with-jabber \
                    --enable-ipv6 \
                    --with-net-snmp \
                    --with-openipmi \
                    --with-ssh2

Now, with

fakeroot debian/rules binary

I'm going to rebuild the package, but with the same name.
How to use a custom name for the new modified package?[/FONT]

---

### Post by MadCow108 on 2011-01-07
the package name is defined in debian/control under:
Package: name

a simpler way to build the package would be (it includes all fakeroot ... steps + more)
debuild -us -uc
or
dpkg-buildpackage -us -uc

-us -uc skips signing of package

---

### Post by gnagnibu on 2011-01-10
Ok, I've tried it.
I've modified control file in section called "Package" 

.. 
Package: zabbix-server-mysql-ssh-support
...
Package: zabbix-server-pgsql-ssh-support

and compiled it with "debuild -us -uc" but the new package aren't right.
They are only 65Kb , while the original are about 600Kb...
I think that changing only section "Package" isn't the right way...

---

### Post by MadCow108 on 2011-01-10
oops I forgot you also have to rename all files in debian which have the old name to the new name

But I just realized there is a much simpler way:
built with debuild -us -uc -nc (no clean) or fakeroot debian/binary

then there should be a debian/tmp or debian/packagename directory
in there is a DEBIAN directory with the control file.
There you rename the package and then do fakeroot dpkg --build tmpdir to create the package

---

### Post by mc4man on 2011-01-10
Not sure why you'd want to change the actual package names, you're building the same set, -  just configured differently.
Plus there are alot of additional files in /debian that would need to be adjusted and depends to adjust ect.

Better to either make a new entry in /debian/chanelog or adjust the existing top entry (what you do for yourself doesn't have to be totally 'correct'

 appending to the current package name/version with a +<whatever> should be fine.

Ex. new entry
> zabbix (1:1.8.2-1ubuntu1+nmu1) maverick; urgency=low

  * Added ssh2

 -- Doug Mc <mc4man@nowhere.com>  Mon, 10 Jan 2011 11:49:04 -0400


---

### Post by gnagnibu on 2011-01-13
Great guys!!

Modifying debian/changelog did the trick!

So, I added to debian/changelog:

zabbix (1:1.8.2-1ubuntu1+ssh1) maverick; urgency=low                                                                                                                         
 
   * Compiled with SSH Agent support:
 
 -- Vecchi Giovanni <my_email>  Tue, 13 Jan 2010 12:20:04 +0100

and next
debuild -us -uc -nc
Thanks to all, bye!

---

