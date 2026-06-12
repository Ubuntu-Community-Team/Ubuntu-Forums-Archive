---
title: "Pidgin desn't start"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by jack_harper2007 on 2008-09-24
I have just reinstalled UBbuntu and i'm havin problems with pidgin.
Every time i try to start pidgin, the window appear then it shuts down, there is no icon on the tray or anything.
When i go to system monitor i see about 10 pidgin icons all of them zombie, and i can't terminate any of them.
I've also tried to run pidgin from the terminal and the same thing happens. :(
Can someone help me with this one?
Thanks in advance

---

### Post by perlluver on 2008-09-24
> **jack_harper2007 said:**
> I have just reinstalled UBbuntu and i'm havin problems with pidgin.
Every time i try to start pidgin, the window appear then it shuts down, there is no icon on the tray or anything.
When i go to system monitor i see about 10 pidgin icons all of them zombie, and i can't terminate any of them.
I've also tried to run pidgin from the terminal and the same thing happens. :(
Can someone help me with this one?
Thanks in advance

Open up your home folder, Places>Home, press ctrl-h, look for .purple and delete that folder, then try to reopen pidgin.

---

### Post by Sef on 2008-09-24
Appllications > Accessories > Terminal

then type pidgin.   Copy and paste any error messages you get.

---

### Post by LashSilence83 on 2008-09-29
I get this:
pidgin: symbol lookup error: pidgin: undefined symbol: purple_smileys_get_all

---

### Post by ewcrider on 2008-09-30
i had the same problem.  To fix, you need to remove libpurple.  You can use synaptic package manager to remove libpurple. After removing, type "pidgin" into the terminal and it should load.

---

### Post by LashSilence83 on 2008-09-30
Thank you! Now it's working fine. So for the sake of learning more about ubuntu and linux in general, how do I (in the future) figure things like that out on my own?

---

### Post by perlluver on 2008-09-30
> **LashSilence83 said:**
> Thank you! Now it's working fine. So for the sake of learning more about ubuntu and linux in general, how do I (in the future) figure things like that out on my own?

Just search here for Pidgin, or google pidgin won't open.  Most likely someone else had that problem already.

---

### Post by sharky6000 on 2008-11-14
Ok, so I'm using Intrepid.. got all the latest packages.

I'm getting the same problem, but only under Fluxbox (works perfectly fine in Gnome):

```

pidgin: symbol lookup error: pidgin: undefined symbol: purple_smileys_get_all

```

I can't remove libpurple without also removing pidgin because it's a dependency: 

```

root@somehostname:~# dpkg -r libpurple0
dpkg: dependency problems prevent removal of libpurple0:
 pidgin depends on libpurple0 (>= 1:2.5.2-0ubuntu1).
dpkg: error processing libpurple0 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libpurple0
root@somehostname:~# apt-get remove libpurple0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libpurple0 pidgin
0 upgraded, 0 newly installed, 2 to remove and 32 not upgraded.
After this operation, 6861kB disk space will be freed.
Do you want to continue [Y/n]? 

```

Has it only been made a dependency in Intrepid? I thought pidgin has always depended on libpurple.. I'm surprised you can remove it and still use pidgin.

---

### Post by orawax on 2008-11-15
I'm not sure but, but for me it seems Music tracker is the problem. Pidgin hangs few seconds after enabling the plugin, but seems to work when it's disabled.

---

### Post by sabry_lk on 2009-04-14
Thanks!! This worked

---

### Post by Tipped OuT on 2009-05-05
Thanks too! :)

---

### Post by Insanity01 on 2009-05-05
Could always use alternatives then pidgin, there are lots of em

---

### Post by Paul_K on 2009-07-28
I tried removing libpurple but it always gets reinstalled when I install pidgin.  I also tried uninstalling pidgin and reinstalling to no avail.  I also tried `sudo ldconfig` (from here [http://www.nabble.com/-8620:-symbol-lookup-error:-pidgin:-undefined-symbol:-purple_smileys_get_all-td22438010.html](http://www.nabble.com/-8620:-symbol-lookup-error:-pidgin:-undefined-symbol:-purple_smileys_get_all-td22438010.html))

I am still getting:

 /usr/bin/pidgin
/usr/bin/pidgin: symbol lookup error: /usr/bin/pidgin: undefined symbol: purple_smileys_get_all

before all this I was running pidgin 2.40 I have tried 2.55 from the repos and 2.58

I am running 32bit Ubuntu 9.04

I think it is cruft from the 2.40 install that is messing things up, including looking for pidgin in /usr/local/bin:

pdkwj3:~$ pidgin
bash: /usr/local/bin/pidgin: No such file or directory
pdkwj3:~$ which pidgin
/usr/bin/pidgin
pdkwj3:~$ /usr/bin/pidgin -v
Pidgin 2.5.8 (libpurple 2.4.0)

 

Any ideas?

Thanks

-PaulK

---

### Post by twizler on 2010-01-28
try this  

from terminal type$

** pidgin -n**


((((((this makes it so it does not auto load an account name worked for me ))))

---

