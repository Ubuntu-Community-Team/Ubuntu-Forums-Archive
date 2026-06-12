---
title: "Could we get in the next release : /usr/bin/system-config-authentication ?"
date: 2010-01-25
forum: Packaging and Compiling Programs
---

### Post by frenchn00b on 2010-01-25
Hello

That could be pretty cool to get this great gui : [http://www.yolinux.com/TUTORIALS/images/system-config-authentication_LDAP-1.gif](http://www.yolinux.com/TUTORIALS/images/system-config-authentication_LDAP-1.gif)

Ubuntu, made for humans:popcorn::popcorn:

thank you very much the ubuntu team development !


link; [https://fedorahosted.org/releases/a/u/authconfig/](https://fedorahosted.org/releases/a/u/authconfig/)

---

### Post by frenchn00b on 2010-01-25
:~/Downloads/authconfig-6.0.1
```
./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.    -g -O2 -Wall -Wunused -Wuninitialized -Wimplicit -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wcast-align -I/usr/include/python2.5 -Wall -g -O2 -Wall -Wunused -Wuninitialized -Wimplicit -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wcast-align -MT acutilmodule.lo -MD -MP -MF .deps/acutilmodule.Tpo -c -o acutilmodule.lo acutilmodule.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -g -O2 -Wall -Wunused -Wuninitialized -Wimplicit -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wcast-align -I/usr/include/python2.5 -Wall -g -O2 -Wall -Wunused -Wuninitialized -Wimplicit -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wcast-align -MT acutilmodule.lo -MD -MP -MF .deps/acutilmodule.Tpo -c acutilmodule.c  -fPIC -DPIC -o .libs/acutilmodule.o
acutilmodule.c:22:20: error: Python.h: No such file or directory
acutilmodule.c:27: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;initacutil&#8217;
acutilmodule.c:29: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
acutilmodule.c:48: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
acutilmodule.c:84: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;acutil_methods&#8217;
acutilmodule.c:91: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;initacutil&#8217;
make[2]: *** [acutilmodule.lo] Error 1
make[2]: Leaving directory `/ho
```


system-config-authentication comes from Fedora/RHEL/CentOS, and can
quickly configure a workstation to authenticate via ActiveDirectory
domain and Kerberos.  This would make an excellent addition to Hardy, as
it would open the doors for domain-authenticated workstations and
servers.

---

