---
title: "Bad .dmrc file?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-11-02
In installing 8.10 and overwriting the home folder with a 8.04 version I screwed up and now I am getting a message on boot-up concerning the .dmrc file.  I apparently don't own it and it needs 644 permissions.  How can I fix it without reinstalling?

Thanks,

---

### Post by Pro-reason on 2008-11-02
Hit Ctrl-Alt-F1 to get to a console session.  Log in.  Type the following:

```

sudo chown -v $USER:$USER .dmrc
chmod -v u=rw .dmrc
chmod -v go=r .dmrc

```

---

### Post by Scunizi on 2008-11-02
Perhaps "sudo chmod 644 /home/<uname>/.dmrc".. Also check out [http://penguinpetes.com/b2evo/index.php?title=chmod_squad_howto_use_linux_file_permiss&more=1&c=1&tb=1&pb=1](http://penguinpetes.com/b2evo/index.php?title=chmod_squad_howto_use_linux_file_permiss&more=1&c=1&tb=1&pb=1).

---

### Post by Pro-reason on 2008-11-02
The chmod command can be used with the numbers explained on that webpage, or with the more intuitive system with letters.  If you put **u=rw**, that means that the file is **r**ead-**w**rite for the **u**ser who owns the file.  If you put **go=r**, that means that the file is **r**ead-only for the user-**g**roup that owns the file, and all **o**thers.

By the way, &#8220;/home/<uname>/&#8221; is wrong.  The &#8220;uname&#8221; command prints system information, in particular the kernel version.  It is not a shorthand for the person's username.  For that, we use &#8220;$USER&#8221;, which will be automatically replaced with the correct username when the person hits Enter.

An even better abbreviation for &#8220;/home/$USER&#8221; is &#8220;$HOME&#8221;.  We can even just use &#8220;~&#8221;.

---

