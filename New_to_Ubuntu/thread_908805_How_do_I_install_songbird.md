---
title: "How do I install songbird"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by MinderBinderNW on 2008-09-02
I read that it wasn't in the repository, so I downloaded it from their website.  But I can't find an executable to start the install from.  Do I need to simulate a disc?  If so, then what program do I need to use and is it preloaded? 

Thanks

---

### Post by OutOfReach on 2008-09-02
I'm pretty sure that the package that you download has an executable, it should be by the name 'songbird' or something along the lines of that.

---

### Post by coolbrook on 2008-09-02
Try the .deb package

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by MinderBinderNW on 2008-09-02
The website won't load at the moment.  In the meantime though I am also incompetent when it comes to installing a program in wine.  I downloaded itunes, but when i went into winefile and tried to open it I got an error message stating that I wasn't using a compatible os.  So how do I install programs in wine?

---

### Post by OutOfReach on 2008-09-02
Just execute the .exe file, WINE isn't perfect so expect frequent crashes for some programs.

---

### Post by MinderBinderNW on 2008-09-02
Cannot open /home/ryan/Downloads/iTunesSetup.exe: No application suitable for automatic installation is available for handling this kind of file.

This is what it says when i click the .exe  I checked to see if I had the latest version of wine and it says I do.

---

### Post by crispy_420 on 2008-09-02
It is looking for iTunes in your wine install try just not using that option on install and wait till getdeb is up again (there uptime is pretty random).

Or you could wait for a random stranger to post it for you:

[http://www.filefactory.com/file/85de64/n/songbird_0_6_1-0_getdeb1_i386_deb](http://www.filefactory.com/file/85de64/n/songbird_0_6_1-0_getdeb1_i386_deb)

---

### Post by aysiu on 2008-09-02
This should help:
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by petronell on 2008-09-04
There is a package available for the latest version (0.7.0) over at getdeb.

Take a look here...

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

daveR

---

### Post by kpkeerthi on 2008-09-04
> **MinderBinderNW said:**
> Cannot open /home/ryan/Downloads/iTunesSetup.exe: No application suitable for automatic installation is available for handling this kind of file.

This is what it says when i click the .exe  I checked to see if I had the latest version of wine and it says I do.

If you have wine installed already, run this command:
```
wine /home/ryan/Downloads/iTunesSetup.exe
```

---

