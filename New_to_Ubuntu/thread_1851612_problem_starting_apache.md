---
title: "problem starting apache"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2011-09-28
Hello everyone,

i previously had apache flawlessly running on my ubuntu 10.10, but few days back i mistakenly deleted my httpd.conf file.
i removed apache by

sudo apt-get remove apache2.2
sudo apt-get autoremove

and then i compiled it from the binary

after that if i am typing

apachectl start

then i am getting the following message:

"/usr/sbin/apachectl: 148: /usr/sbin/apache2: not found
Action 'start' failed.
The Apache error log may have more information."

the error log is empty. what could be the problem and how do i fix it??

---

### Post by viditgoyal3009 on 2011-09-28
over 60 people viewed this and still no one has the answer???

---

### Post by Dangertux on 2011-09-29
I'm a little confused, did you compile from source or install the binary?

In any case, does 

```

sudo /etc/init.d/apache2 start

```

Because the command you are looking for back there is

```

apache2ctl start

```

If that doesn't work and you installed from the repos you can try.


```

sudo apt-get remove --purge apache2.2
sudo apt-get install apache2.2

```

---

### Post by viditgoyal3009 on 2011-09-29
i compiled from the source.

i tried both of your commands but nothing worked and i haven't installed it from the repos...

what else can i do??

and also why is this happening??

---

### Post by azmyth on 2011-09-29
```
sudo /etc/init.d/apache2 start

or

sudo service apache2 start
```

What does the terminal say when you run this command?

---

### Post by aura7 on 2011-09-29
check apache2 process is running or not by typing

ps -e | grep apache2

---

### Post by viditgoyal3009 on 2011-09-29
apache2 process is not running

---

### Post by viditgoyal3009 on 2011-09-29
> **azmyth said:**
> ```
sudo /etc/init.d/apache2 start

or

sudo service apache2 start
```

What does the terminal say when you run this command?

root@ubuntu:/home/vidit# service apache2 start
No apache MPM package installed

---

### Post by Dangertux on 2011-09-29
I'm thinking you didn't compile it properly.

---

### Post by azmyth on 2011-09-29
> **Dangertux said:**
> I'm thinking you didn't compile it properly.
I agree. Something went wrong on your compile,

---

### Post by viditgoyal3009 on 2011-10-01
No error message displayed while compiling it.
i used the following code to compile it:

./configure
make
make install

what else could have happened???

---

### Post by viditgoyal3009 on 2011-10-02
someone please reply...

---

### Post by azmyth on 2011-10-03
Did you do?

```
sudo make install
```

---

### Post by viditgoyal3009 on 2011-10-07
> **azmyth said:**
> Did you do?

```
sudo make install
```

yeah i did..

---

### Post by azmyth on 2011-10-09
I suspect your apache2 is installed in the /usr/local/apache2/ since you didn't set a path on configure. Do you see this directroy and do you see files in the dir?

---

### Post by viditgoyal3009 on 2011-10-09
somehow i got my apache running and its running fine. But it turns out my httpd.conf file is empty and even if i edit it and write
Listen 891
on it, even then i am unable to open 891 port. i tries editing port.conf file too but still of no use..
Why is it happening??

---

