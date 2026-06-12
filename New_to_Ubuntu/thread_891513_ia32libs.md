---
title: "ia32libs"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Drezard on 2008-08-16
hey...

how do i install ia32libs on an ubuntu server 8.04?

thanks, Daniel

or even just install libX11.so.6?

---

### Post by Paqman on 2008-08-16
Same way as any other package:
```

sudo apt-get install ia32libs

```

---

### Post by jeromer43 on 2008-09-01
I need this file also.  But when I try to "apt-get" the file I get the message line

"E: Couldn't find package ia32libs" 

Have tried "apt-get update" but still can't fine it.  Any ideas?

---

### Post by Kevbert on 2008-09-01
Am I right in thinking you're trying to get 32 library files for a 64 bit machine ?  If so you have two options.  You could try getting them with Quickstart (in my signature) or try getlibs.deb (attached).

---

### Post by knattlhuber on 2008-09-06
The package you are looking for is actually called 'ia32-libs' I think.

```
sudo apt-get install ia32-libs
```

---

### Post by redactech on 2008-09-06
```
aptitude search ia32
```

will give you all the related package. I have a 64bits server sitting next to me and the result is 

```
p   ia32-libs                                                - ia32 shared libraries for use on amd64 and ia64 systems 
```

---

### Post by Astrals on 2010-01-17
> **knattlhuber said:**
> The package you are looking for is actually called 'ia32-libs' I think.

```
sudo apt-get install ia32-libs
```


Correct!!

This for me fixed an issue from updates stopping avast4workstation working via command line, fixed the issue plus as a side bonus got the not needed gui working.

Hope this helps.

---

### Post by moravveji on 2011-03-06
Thanks Kevin, you recipe really works. I found no other way to get around this problem on the net.
Cheers man.

---

