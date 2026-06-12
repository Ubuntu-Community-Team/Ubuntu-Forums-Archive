---
title: "Openxchange on Ubuntu"
date: 2005-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jts on 2005-08-02
This is for Hoary.  Can a moderator move it as such?

I was able to get OpenExchange up and running on Ubuntu recently.  Okay, still working out a few kinks, but for the most part I was able to complete the instructions for Sarge ([http://gpl.netixia.com/openxchange/openxchange-sarge-howto.html](http://gpl.netixia.com/openxchange/openxchange-sarge-howto.html)) and find the gotchas that need to be changed for Ubuntu.  I still need to tweak OpenLDAP policies here and there and fix a few webpage links, but I can still login to OpenExchange and play with all of the features.

This install is not for those that are completely new to Linux and/or Ubuntu.  It requires a little knowledge of compiling programs and understanding shell scripts.

For the most part, the SARGE install works pretty well except for the following gotchas.

Gotcha # 1.) Do NOT install slapd (openldap) from Synaptic.  It is far too old, and not worth the headache (Package people, can we get a later version?).  Grab the latest version from the OpenLDAP website.

Unpack and configure like the following.
./configure --enable-bdb --enable-aci --enable-crypt

Note: If you use the default install location, you will need to make sure you substitute the new location of your ldap, for the tutorials location of ldap.  Mine was installed to: /usr/local/etc/openldap/


Gotcha #2.)  Tomcat also needs some JAVA options (which I found from a forum).  I put these in my .bashrc file (root) along with the other options found in the first section of the tutorial called: "Update your .profile"
JAVA_OPTS=" -Dopenexchange.propfile=/usr/local/openxchange/etc/groupware/system.properties"

Gotcha #3.) Make sure you have the following module loads in your slapd.conf file:
# Load dynamic backend modules:
 modulepath	/usr/local/libexec/openldap
 moduleload	back_bdb.la
 moduleload	back_ldap.la
 moduleload	back_ldbm.la
 moduleload	back_passwd.la
 moduleload	back_shell.la

Gotcha #4.) Persistance.  Never give up!  I have made it and so can you!  It was a bit rough going and frustrating when posting to other mailing lists, only to be told to go pound sound (in nicer terms).    I've said it once and I'll say it again, that's what distinguishes Ubuntu with other distributions.  I've gotten solid usable advice in the Ubuntu forums and I'll try to help out when I can.

---

### Post by nocturn on 2005-08-03
The Hoary version is rather old (april 2004), but the next version came too late for Hoary (april 6, days before Hoary came out).
I'm sure Breezy will have the latest one.

Dates are based on Freshmeat announcements.

---

### Post by manoj.ganla on 2005-11-12
Hi,
    I tried installing open-xchange using the steps given in the link..but i'm facing the following problem..after i excute the command:
./configure \
--prefix=/usr/share/openxchange \
--with-mailjar=/usr/share/javamail/mail.jar \
--with-activationjar=/usr/share/jaf/activation.jar \
--with-jdomjar=/usr/share/jdom/build/jdom.jar \
--with-xercesjar=/usr/share/xerces/xercesImpl.jar \
--with-jsdkjar=/usr/share/tomcat5/common/lib/servlet-api.jar \
--with-jdbcjar=/usr/share/jdbc/pg74.215.jdbc3.jar \
--with-dbpass=octane \
--with-runuid=www-data --with-rungid=nogroup \
--with-domain=localdomain \
--with-organisation="Octane Mobile" \
--with-basedn="dc=localdomain,dc=org" \
--with-rootdn="cn=Manager,dc=localdomain,dc=org" \
--with-rootpw=octane --enable-webdav


/root/open-xchange-0.8.0-6/config/missing: Unknown `--run' option
Try `/root/open-xchange-0.8.0-6/config/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for java... /usr/bin/java
checking for jikes... no
checking for jar... /usr/bin/jar
checking for ant... /usr/bin/ant
checking for javah... /usr/bin/javah
checking for sudo... /usr/bin/sudo
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

this is what i get....

CAN SOMEONE HELP ME PLEASE

---

### Post by jts on 2005-11-12
Do you have C++ installed?  Doesn't look like it from your output.

Make sure you install G++ installed.

My $0.02.
Also, OpenXchange is not for the faint at heart as it does not have an easy to use install program (a la Synaptic).  I eventually had it setup and working, but there was still a lot of things that needed debugging.  For a simple install project, I eventually tossed it and looked for a different solution that better fit my needs ([http://www.vtiger.com/)](http://www.vtiger.com/)).

---

### Post by jts on 2005-11-14
manoj,  thanks for the message, but I think you will need to check out the openexchange forums and/or their newsgroups for better, more directed help.

Vtiger is a Customer Relationship manager and a standalone product.  Its basically an entire web-only system.  It has two install scripts, one for windows and one for Linux.  The windows one is very easy to install.  The linux one is a bit trickier, but if you read the Install manual its a breeze.

Hope this helps.

---

