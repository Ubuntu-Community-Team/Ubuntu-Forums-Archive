---
title: "HOW TO:  MySpace IM with PIDGIN"
date: 2007-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by kelly.seay on 2007-09-07
Original guide from [http://developer.pidgin.im/wiki/MsimInstall](http://developer.pidgin.im/wiki/MsimInstall).  I updated with latest directions.  I am using Gutsy, but I also got this working for Feisty.  Here it goes:
I am using Pidgin 2.1.1 from Gutsy

Download this [http://msimprpl.darkthoughts.net/msimprpl-0.16.tar.gz](http://msimprpl.darkthoughts.net/msimprpl-0.16.tar.gz) (0.17 is available, but i couldn't get it to work)

Download these
[http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_16.png?format=raw](http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_16.png?format=raw)
[http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_22.png?format=raw](http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_22.png?format=raw)
[http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_48.png?format=raw](http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_48.png?format=raw)
copy the PNG's to  /usr/share/pixmaps/pidgin/protocols/

apt-get install pidgin-dev
apt-get source pidgin
tar zxvf pidgin_2.1.1.orig.tar.gz
mkdir msimprpl-0.16

cd msimprpl-0.16
tar zxvf ../msimprpl-0.16.tar.gz
cd libpurple/protocols/myspace

gcc `pkg-config  --cflags pidgin ` -D PURPLE_PLUGINS -c message.c myspace.c -I../../../../pidgin-2.1.1/libpurple/  -I.
gcc -shared -`pkg-config --libs pidgin` message.o myspace.o -o libmyspace.so

sudo cp libmyspace.so /usr/lib/purple-2/


This is my first How To, and I hope I put enough for everyone to get it working.  Have fun.

---

### Post by fakie_flip on 2007-09-15
> **kelly.seay said:**
> Original guide from [http://developer.pidgin.im/wiki/MsimInstall](http://developer.pidgin.im/wiki/MsimInstall).  I updated with latest directions.  I am using Gutsy, but I also got this working for Feisty.  Here it goes:
I am using Pidgin 2.1.1 from Gutsy

Download this [http://msimprpl.darkthoughts.net/msimprpl-0.16.tar.gz](http://msimprpl.darkthoughts.net/msimprpl-0.16.tar.gz) (0.17 is available, but i couldn't get it to work)

Download these
[http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_16.png?format=raw](http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_16.png?format=raw)
[http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_22.png?format=raw](http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_22.png?format=raw)
[http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_48.png?format=raw](http://developer.pidgin.im/attachment/wiki/MySpaceIM/myspace_48.png?format=raw)
copy the PNG's to  /usr/share/pixmaps/pidgin/protocols/

apt-get install pidgin-dev
apt-get source pidgin
tar zxvf pidgin_2.1.1.orig.tar.gz
mkdir msimprpl-0.16

cd msimprpl-0.16
tar zxvf ../msimprpl-0.16.tar.gz
cd libpurple/protocols/myspace

gcc `pkg-config  --cflags pidgin ` -D PURPLE_PLUGINS -c message.c myspace.c -I../../../../pidgin-2.1.1/libpurple/  -I.
gcc -shared -`pkg-config --libs pidgin` message.o myspace.o -o libmyspace.so

sudo cp libmyspace.so /usr/lib/purple-2/


This is my first How To, and I hope I put enough for everyone to get it working.  Have fun.

pidgin 2.2.0 has built-in support for Myspace IM, but my password is not working. I am using the same password that I use to login to the webpage. Should I be using a different one?

---

### Post by Nomisdk on 2007-09-16
I cant login to.

Any know how to fix it?

---

### Post by kelly.seay on 2007-09-17
make sure for screen name, you use the email address you sign in with.

---

### Post by Nomisdk on 2007-09-17
> **kelly.seay said:**
> make sure for screen name, you use the email address you sign in with.

Thanks :)

---

### Post by kelly.seay on 2007-09-17
> **Nomisdk said:**
> Thanks :)

Sorry, I didn't mean to sound like a jerk, if that is the way it seemed.  I was busy at work and tried throwing a quick suggestion out.  I know some of my friends thought they just had to use their name and not their email, or their page name instead of their e-mail.  I really hope it did work for you.

---

### Post by Dudemeister on 2007-09-19
Did you know you can easily chat with MyspaceIM via [www.ebuddy.com](www.ebuddy.com) ?

It's webbased and you can use all your IM-accounts together... MSN/AOL/Myspace!

I tried it and it's really great! much easier then all this pidgin crap.

---

### Post by gigaferz on 2007-11-09
thnaks for the link, 

I know is very frustating to get things working in linux, but pidgin, as any other software outhere free, deserve some appreciation,

i spent a lot of time compiling the new pidgin 2.2.2 and after all that ,guess what, it didnt work.... lol

  just relax!

---

### Post by MicroChris on 2007-11-09
Thanks for the HOWTO. 

MyspaceIM works fine for me by default though. :P

---

### Post by KEE on 2008-06-29
> **kelly.seay said:**
> Sorry, I didn't mean to sound like a jerk, if that is the way it seemed.  I was busy at work and tried throwing a quick suggestion out.  I know some of my friends thought they just had to use their name and not their email, or their page name instead of their e-mail.  I really hope it did work for you.

I still cant get pidgin to work =/ its the newest one and i tired my number for screen name and email that i use to sign in with,:confused: But nothing works =/ this needs to be fixed cause its broken =(

anyone know anything about THis????

---

