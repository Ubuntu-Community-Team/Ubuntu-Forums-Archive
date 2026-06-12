---
title: "[SOLVED] Installed Skype... but how to"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-06-06
I downloaded the .deb file for skype. 
The Ubuntu site instructions for .deb files say that I could just double click the file, and that is what I did, but now I wonder... how can I uninstall it if I wish not to use it anymore, or wish to upgrade it. It is not on the ADD-REMOVE programs list of my OS.

Please  help.

---

### Post by Golem XIV on 2008-06-06
I think you *should* be able to uninstall it through Synaptic or **sudo apt-get remove skype**

BTW, Skype is in the Medibuntu repos, you could add them to your sources list and then install Skype the "usual" way

---

### Post by brian_p on 2008-06-06
> **bilbo.san said:**
> I downloaded the .deb file for skype. 
The Ubuntu site instructions for .deb files say that I could just double click the file, and that is what I did, but now I wonder... how can I uninstall it if I wish not to use it anymore, or wish to upgrade it. It is not on the ADD-REMOVE programs list of my OS.

Please  help.

Try

```
dpkg -r <package_name>

```

I don't know what your <package_name> is but it could be skype-debian.

---

### Post by Maestro23 on 2008-06-06
> sudo dpkg --purge packagename

*Gets rid of config files as well.

---

### Post by Joeb454 on 2008-06-06
True - it should be in System > Administration > Synaptic Package Manager :)

It *should* also be possible to remove it by running the following from a terminal ```
sudo dpkg -r skype
```

---

### Post by bilbo.san on 2008-06-06
Thanks.

I ran a test and that did it!
Perhaps I should install that Medibuntu source too.

b.

---

