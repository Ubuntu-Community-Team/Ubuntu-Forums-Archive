---
title: "HOWTO: Installing Hamachi 0.9.9.9"
date: 2005-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by MicroChris on 2005-12-20
To install Hamachi:

-Download hamachi-0.9.9.9-7.tar.gz (link)

-Extract the folder to your Desktop

```
cd home/$USER$/Desktop/hamachi-0.9.9.9-7
```

Then:

```
install -m 755 hamachi /usr/bin
```

```
ln -sf /usr/bin/hamachi /usr/bin/hamachi-init
```

```
install -s -m 700 tuncfg/tuncfg /sbin
```

After that, try running(root):

```
tuncfg
```
```
hamachi-init
```


Try some commands which are supplied in the README. I still have not figured out a way to actually access users, but I can install it.

-Chris

---

### Post by nikopol on 2006-02-10
These commands
```
install -m 755 hamachi /usr/bin
ln -sf /usr/bin/hamachi /usr/bin/hamachi-init
install -s -m 700 tuncfg/tuncfg /sbin
```
have to run with sudo.

---

### Post by zachtib on 2006-02-10
and a gui for hamachi for linux is available here: [http://forums.hamachi.cc/viewtopic.php?t=2488](http://forums.hamachi.cc/viewtopic.php?t=2488)

simply untar and copy to your /usr/bin directory

---

### Post by Havoc on 2006-02-10
GUI doesn't display well with composite on.Gives me a lot of problems.Disable composite.

Otherwise, a nice app.Version 0.9.9.9-7 is old though.

```
havoc@Nosgoth:~$ hamachi
Hamachi, a zero-config virtual private networking utility, ver 0.9.9.9-12

  version  : hamachi-lnx-0.9.9.9-12
  pid      : 28109
  status   : logged in
  nickname : Havoc


```

Newer version out.

Stop.

---

### Post by anabelle on 2007-04-27
Im getting 

hamachi: error while loading shared libraries: libcrypto.so.0.9.7: cannot open shared object file: No such file or directory

when i do hamachi-init

i downloaded libcrypto.so.0.9.7-1.rpm and made it a .deb using alien, i installed it and still the same error, what else can i do?

---

### Post by anabelle on 2007-04-27
i solved it installing libssl0.9.7 using adept

---

### Post by sin on 2007-04-30
you can make it see the network by setting localhost to the hamachi ip in /etc/hosts, but that generates further issues. i'm still looking for a viable solution.

---

### Post by somethings90 on 2008-07-26
When I try that I get the error "cd home/$USER$/Desktop/hamachi-0.9.9.9-20"

hamachi-0.9.9.9-20 is the latest version.

---

### Post by mattzink on 2008-11-29
Not trying to start a flame war - am just totally frustrated and want to vent.  I LOVE Ubuntu and will never go back to Windows.  But if a program is not in a repository, it is a serious, serious pain in the @$$ to install in Ubuntu.  I usually try to avoid it altogether.  Nothing in this thread (and actually, one other and a blog as well!) has worked.  As much as it pains me to admit it, this is one area where Micro$uck has a slight advantage over Ubuntu - it's nice to just download/double click to install a program.  I give up on Hamachi for Ubuntu - end of rant - Ubuntu is still #1 and I'm really not as big of a jerk as I seem.  Moderator, please feel free to delete this response, though I hope you'll leave it up for other folks who feel as I do.

---

### Post by jag2000 on 2009-07-11
Mattzink i couldn't agree more. i am beyond frustrated at the moment.

---

