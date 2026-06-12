---
title: "How to use QQ(OICQ) in Ubuntu"
date: 2005-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by wxm505 on 2005-05-21
OICQ which is called QQ is a internet chat client.
It is a windows based software.
There are more than 10 millions of people use it
everyday. It is a good news that you can use it in 
Ubuntu.
It is quite simple , there are two ways to get installation 
on ur box.One is install a gaim plugin ,the other is 
install a Linux based software developed by a Chinese
student in Java.
I recommend the first way. what you need to do is
go to download a plugin called 

[COLOR=Navy][openQ](http://prdownloads.sourceforge.net/openq/openq_0.3.1-2_i386.deb?download)[/COLOR] 

then , ```
dpkg -i openq_0.3.1-2_i386.deb
``` 
restart you gaim you will find a new protocol option in your list.
you need not set up any login server and port.

But the pity is it seems do not support proxy. So people
who use proxy to indirect connect to internet may 
 not use it. Anyway , hope everyone enjoy it .

Now I can use Msn messenger , Yahoo messenger and QQ 
all in one Gaim. it is bloody awkward to use three clients
to do it in windows.

Ubuntu rocks!!

---

### Post by Nano on 2005-05-21
[QUOTE=wxm505]OICQ which is called QQ is a internet chat client.
It is a windows based software.
There are more than 10 millions of people use it
everyday. It is a good news that you can use it in 
Ubuntu.
It is quite simple , there are two ways to get installation 
on ur box.One is install a gaim plugin ,the other is 
install a Linux based software developed by a Chinese
student in Java.
I recommend the first way. what you need to do is
go to download a plugin called 

[COLOR=Navy][openQ](http://prdownloads.sourceforge.net/openq/openq_0.3.1-2_i386.deb?download)[/COLOR] 

then , ```
dpkg -i openq_0.3.1-2_i386.deb
``` 
restart you gaim you will find a new protocol option in your list.
you need not set up any login server and port.

But the pity is it seems do not support proxy. So people
who use proxy to indirect connect to internet may 
 not use it. Anyway , hope everyone enjoy it .

Now I can use Msn messenger , Yahoo messenger and QQ 
all in one Gaim. it is bloody awkward to use three clients
to do it in windows.

Ubuntu rocks!![/QUOTE]
 You can use Gaim also in Windows, if what you want is to avoid running one app for protocol.
Actually, for Windows, I've found better solutions than Gaim, as Miranda-IM

---

### Post by wxm505 on 2005-05-22
Yes, you can use gaim under windows too. :)

---

### Post by pro on 2005-05-28
I've tried the 0.3.1 deb package from openq's sf site. But I've been experiencing alot of crashes from GAIM. And also 0.3.2 is the latest version but there isn't a deb package for it.

So ... I end up compiling the 0.3.2 version for it and made a deb package for it .. hehe ...

anyway I found the self compiled version is much more stable. GAIM doesn't crash anymore.

---

### Post by lyly on 2005-09-21
[QUOTE=pro]
So ... I end up compiling the 0.3.2 version for it and made a deb package for it .. hehe ...
anyway I found the self compiled version is much more stable. GAIM doesn't crash anymore.[/QUOTE]
Cool!
is there a place we can download your compiled package?

And howto create a new account?

---

### Post by wxm505 on 2006-02-08
see the follows

---

### Post by wxm505 on 2006-02-08
Please go to the website [openq-0.3.2]("http://sourceforge.net/project/showfiles.php?group_id=119670&package_id=130383&release_id=272545")

 download the source code.

Then unpack it with the code
```
tar -zxvf openq-0.3.2.tar.gz
```

install the plugin by steps

```
sudo ./configure

make

make install


```

Restart GAIM. Good luck.

---

### Post by EPHEMERA on 2006-08-19
checking for gaim... Package gaim was not found in the pkg-config search path. P erhaps you should add the directory containing `gaim.pc' to the PKG_CONFIG_PATH environment variable No package 'gaim' found
configure: error: Library requirements (gaim) not met; consider adjusting the PK G_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix  so pkg-config can find them.


What can I do? Who can tell me?

---

### Post by quantboy on 2006-08-20
I'm getting the same error as EPHEMERA in ubuntu 6.06. 

I've used the find command to look all over my drive for gaim.pc- and have not found it. 

Has anyone else seen this problem before?  And what can be done to get around this problem?

---

### Post by gremlingreen on 2006-08-25
FYI:

install the dev packages for gaim

sudo apt-get install gaim-dev

and for gtk2

sudo apt-get install libgtk2.0-dev

Worked okay for me.

---

### Post by EPHEMERA on 2006-08-27
I did as your follows but when I typed the 'sudo ./configure', it can run correctly, but when I type 'make', it said 'command not found', what can I do?

---

### Post by quantboy on 2006-08-27
gremlingreen's instructions worked!

---

### Post by Yumi on 2006-08-28
I installed everything as mentioned. However Gaim does not show the new protocol, And by the way, where to find the java programm of the "Chinese Student"?

Have an AMD64 and Dapper.

Michael

---

### Post by fk4n on 2006-09-10
so where is the new option?? i did everything and restarted Gaim. But i cant find the new option anywhere.:confused:

---

### Post by Yumi on 2006-09-11
I decided to wait on this one. Got a message from the GAIM developer that the protocoll will be included in the next version of GAIM.

Michael

---

### Post by wxm505 on 2007-04-15
It is new generation of Gaim, actually [Pidgin]("http://www.pidgin.im/")
In the google summer of code project, QQ protocol has been bundled in the new 
release of Pidgin.
You do not have to config server and port. It has been all done for you.
It is end of the story. Enjoy

---

