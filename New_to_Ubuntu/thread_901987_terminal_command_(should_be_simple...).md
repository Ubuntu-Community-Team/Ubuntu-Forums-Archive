---
title: "terminal command (should be simple...)"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-26
Hypothetically,I am using terminal which is curently at home/documents how would I ls the contents of home without cd-ing to it, or how would I ls the main home folder(not just for this user) or even more the root directory
all without changing directories or cding?

---

### Post by kdorf on 2008-08-26
Just append the path you want after the ls command.
```
ls ~
```
Will list home directory, for example.

---

### Post by starcannon on 2008-08-26
To list the contents of your home
```
ls ~
```

want it to spit out one screen at a time?
```
ls ~ | less
```
press any key to see another screen of listed files, press q to exit less.

To list the contents of /home
```
ls /home
```

To list contents of some other local accounts home
```
ls /home/acount_name
```

Also note that ls can do some cool stuff
```
man ls
```

---

### Post by iaculallad on 2008-08-26
> **hyperhopper said:**
> Hypothetically,I am using terminal which is curently at home/documents how would I ls the contents of home without cd-ing to it, or how would I ls the main home folder(not just for this user) or even more the root directory
all without changing directories or cding?

For your home:

```
ls ~
```

For your / (root)

```
ls /
```

For HOME folder:

```
ls /home
```

-:They're fast:-

---

### Post by hyperhopper on 2008-08-26
now hypothetically, if there was a terminal prompt-aka a place to type in ls, whatever its called-on a website, how can you ls the contents of the directory that that web page is stored in?

---

### Post by starcannon on 2008-08-26
ssh into the site, after login simply type "ls"

A good way to practice might be to set up your own LAMP server on any old beater you got laying around or pick up at goodwill or dumpster diving.

Practice remote logins and commands on the Apache server, you'll get the hang of it in no time that way.
Anyway, i'd recommend learning on something like that as opposed to possibly hosing your website by using a command your not comfortable with.

---

### Post by hyperhopper on 2008-08-27
Ok thank you, I do have a few spare desktops lying around that I could turn into a server, however I have no clue how to do so. nor do I know how to do remote logins or commands... and help?

---

### Post by starcannon on 2008-08-30
Heres a nice guide with links to needed install media and pictures. A very nice walk through:

[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

Enjoy and Have Fun!

---

### Post by bodhi.zazen on 2008-08-30
> **starcannon said:**
> To list the contents of your home
```
ls ~
```want it to spit out one screen at a time?
```
ls ~ | less
```press any key to see another screen of listed files, press q to exit less.

To list the contents of /home
```
ls /home
```To list contents of some other local accounts home
```
ls /home/acount_name
```Also note that ls can do some cool stuff
```
man ls
```

To list the contents of "some other local accounts home" just use the tide :

```
~account_name
```

Also use tab completion. To list the contents of /home :

```
ls /ho<tab>
```

---

