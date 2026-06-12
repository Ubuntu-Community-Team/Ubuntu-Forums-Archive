---
title: "jingo811's awk problems, need help pls?"
date: 2008-02-04
forum: Programming Talk
---

### Post by jingo811 on 2008-02-04
I'm trying to learn awk and reading from this beginners guide.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_06_02.html#sect_06_02_03](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_06_02.html#sect_06_02_03)
I understand what it is trying to do but I can't make it work in terminal.  Got any tips for me?
```
ls -l | awk '/\<(a|x).*\.conf$/ { print $9 }'
```

---

### Post by pmasiar on 2008-02-04
I told you before that you should learn Python instead! :-) Awk is even worse than Perl. Good luck!

---

### Post by wdk on 2008-02-04
Try it without using the -l switch

The reason it doesn't appear to work is that the expression is trying to find an "a" or an "x" at the beginning of the entire 8 column string returned by the -l switch, which of course will always begin with "-" (or "d" for directories)

Also, printing column $9 won't actually work (at least in ubuntu--my familiarity with other flavors is limited). try $8 instead:

```

ls -l | awk '/\.conf$/ { print $8 }'

```

again, remove the -l switch to chop off all the preceding columns and match at the beginning of the filename

Good luck!

---

### Post by jingo811 on 2008-02-04
Tnx wdk that explained a lot.  You don't happen to know how to use the "reg expression thingy" so that I only get *.conf files starting with letter A and U?
It doesn't work for me also what's the $ sign doing after conf like so conf$?
```

bill@gates:/etc$ **ls | awk '/\.conf$/ { print $1 }'**
adduser.conf
brltty.conf
ca-certificates.conf
debconf.conf
deluser.conf
fdmount.conf
hdparm.conf
host.conf
inetd.conf
kernel-img.conf
ld.so.conf
lftp.conf
libao.conf
logrotate.conf
ltrace.conf
mke2fs.conf
netscsid.conf
nsswitch.conf
pam.conf
pnm2ppa.conf
popularity-contest.conf
resolv.conf
scrollkeeper.conf
sysctl.conf
syslog.conf
ucf.conf
uniconf.conf
updatedb.conf
usplash.conf
vnc.conf
wodim.conf
wvdial.conf
bill@gates:/etc$ **ls | awk '/\<(a|u)\.conf$/ { print $1 }'**
bill@gates:/etc$ 

bill@gates:/etc$ **ls | awk '/\<(a|u).*\.conf$/ { print $1 }'**
bill@gates:/etc$ 

```

> **pmasiar said:**
> I told you before that you should learn Python instead! :-) Awk is even worse than Perl. Good luck!
If I would program for fun or business then I'd choose Python in a heartbeat.  But you know school is forcing us to learn Bash, awk, sed, etc. because we're supposed to become "great" Linux administrators when we have graduated :-)

---

### Post by pmasiar on 2008-02-04
maybe you can for fun solve all problems in Python and show your teacher. 

it is well known that many teachers (not all - not those reading this forum of course :-) ), without the pressure from competitive marketplace, can teach same old stale crap for years. Ie in our community college there is "Intro to programming" - in COBOL :-(

---

### Post by jingo811 on 2008-02-04
hehe that's even older than relic :)

---

### Post by wdk on 2008-02-04
I'm glad you found my previous post helpful

The "\<" command is specific to gawk, which you are probably not running if you are using a default (or pretty close) installation of Ubuntu. 

Try replacing "\<" with "^", which should work with all awk implementations.

^ - matches text at the beginning of the string
$ - matches at the end of the string

This site may be useful to you:
[http://www.math.utah.edu/docs/info/gawk_5.html]("http://www.math.utah.edu/docs/info/gawk_5.html")

(The site is gawk oriented, but should be useful anyway) 

Good luck!

---

### Post by jingo811 on 2008-02-04
Tnx wdk for the regex link gonna read it right away!

> [LIST]
[*]Both Perl and awk share the reputation of being incomprehensible, **even to the actual authors of the programs that use these languages**. So document your code!
[/LIST]
source: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_06_04.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_06_04.html)

They should really tell ppl that more often :)

---

### Post by ghostdog74 on 2008-02-04
> **jingo811 said:**
> Tnx wdk that explained a lot.  You don't happen to know how to use the "reg expression thingy" so that I only get *.conf files starting with letter A and U?

you should also get to know about shell expansion. For your case , 
```

ls -l [AU]*.conf

```

---

### Post by jingo811 on 2008-02-05
Tnx ghostdog that was even better and cleaner than the awk way of thinking.

---

