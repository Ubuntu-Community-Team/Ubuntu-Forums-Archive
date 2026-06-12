---
title: "fwbackups on ubuntu server"
date: 2015-11-19
forum: New to Ubuntu
---

### Post by andy-tehinternets on 2015-11-19
I'm new to linux and Ubuntu and have just set up an Ubuntu server at home. I hope this is in the right forum.

 I would like to run automated backups and have tried to use fwbackups using these instructions [http://www.diffingo.com/oss/fwbackups/documentation/installation](http://www.diffingo.com/oss/fwbackups/documentation/installation)

I installed the dependencies listed at the top of the page and then did the following:
```

tar xfj fwbackups-1.43.4.tar.bz2
cd fwbackups-1.43.4
./configure --prefix=/usr
make
su -c "make install"

```
Everything is ok until 'make'

I get the program 'make' is not currently installed.

So I did apt-get install make... and try again and get 

"make: *** No targets specified and no makefile found. Stop."

So I tried the specific Ubuntu:

'make && sudo make install'

and get
"make: *** No targets specified and no makefile found. Stop." again 

Any help appreciated.,

Thanks[/FONT]
[FONT=arial][/FONT]

---

### Post by Vladlenin5000 on 2015-11-19
Hi and welcome.

You need to run *make *from the folder where you extracted it. Are you sure you're in the correct folder?

---

### Post by andy-tehinternets on 2015-11-19
Thanks... 

I checked and tried again.

I am in   /etc/fwbackups-1.43.4    

when I try the make command but I still get > make: *** No targets specified and no makefile found. Stop. 

I can see in /etc/fwdbackups-1.43.4/ there are 'Makefile.in' and 'Makefile.am'  is one of these supposed to be the target? 

Thanks

A bit more info:

'./configure --prefix=/usr'    completes all checks but there are 2 errors >  configure: error: in `/etc/fwbackups-1.43.4':   and> configure: error: no acceptable C compiler found in $PATH

---

### Post by cariboo on 2015-11-19
Have you got build-essential installed? It's in the repositories

---

### Post by andy-tehinternets on 2015-11-19
Thanks cariboo that was the solution I came accross

I did: apt-get install build-essential  

This time ./configure --prefix=/usr  completed with no errors

*make *worked after that although it did throw up 1 error that a file already existed. I removed this and ran 
'make && sudo make install' again. 

Everything seems ok, 

Thanks.

---

### Post by sandyd on 2015-11-19
> **andy-tehinternets said:**
> Thanks cariboo that was the solution I came accross

I did: apt-get install build-essential  

This time ./configure --prefix=/usr  completed with no errors

*make *worked after that although it did throw up 1 error that a file already existed. I removed this and ran 
'make && sudo make install' again. 

Everything seems ok, 

Thanks.

By the way, if you want to clean up files created duringa make failure, you can run
```

make clean
```

---

### Post by andy-tehinternets on 2015-11-23
Thanks Sandyd I've done that. 


I'm unable to get fwbackups to start. When I type fwbackups I get this:

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 48, in <module>
    from fwbackups import interface
  File "/usr/lib/python2.7/dist-packages/fwbackups/interface.py", line 23, in <module>
    import gtk.glade
ImportError: No module named glade



I've clearly done something wrong. 

Any help appreciated.

---

### Post by sandyd on 2015-11-23
> **andy-tehinternets said:**
> Thanks Sandyd I've done that. 


I'm unable to get fwbackups to start. When I type fwbackups I get this:

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 48, in <module>
    from fwbackups import interface
  File "/usr/lib/python2.7/dist-packages/fwbackups/interface.py", line 23, in <module>
    import gtk.glade
ImportError: No module named glade



I've clearly done something wrong. 

Any help appreciated.

You're missing python-glade2
```

sudo apt-get install python-glade2
```

---

### Post by andy-tehinternets on 2015-11-23
Thanks, that has cleared that error up. 

Unfortunately I'm still getting an error when trying to connect the Windows PC that is to be backed up. 

*'A connection to 192.168.0.50 could not be established. Error: No suitable address family for 192.168.0.50...'*

I'm putting the ip address for host as I am using it on a local network should I be using something else?

---

### Post by sandyd on 2015-11-23
Odd.

Are the computers on the same subnet?

What does
```

ip addr
```
output?

---

### Post by andy-tehinternets on 2015-11-24
This is the output from ip addr

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group defaul                                              t
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP gr                                              oup default qlen 1000
    link/ether 00:19:d1:4f:31:55 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.50/24 brd 192.168.0.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::219:d1ff:fe4f:3155/64 scope link
       valid_lft forever preferred_lft forever



Thanks

---

### Post by andy-tehinternets on 2015-11-25
OK I've made a bit of a mess of this. 

I thought I had installed all the packages required [http://www.diffingo.com/oss/fwbackups/documentation/installation](http://www.diffingo.com/oss/fwbackups/documentation/installation) 

but I checked and they are not installed. I couldn't find them via apt-get install even after adding relevant lines to the sources file, so I had to download the gz.tar packages. I have read this is not the best way to do it. 

So I need to know what are the correct lines to add to sources.list in order to be able to get the packages, gettext, dcron, PyGTK, pycrypto, paramiko 

Thanks

---

