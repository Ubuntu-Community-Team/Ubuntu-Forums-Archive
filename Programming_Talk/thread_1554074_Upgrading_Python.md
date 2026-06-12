---
title: "Upgrading Python"
date: 2010-08-16
forum: Programming Talk
---

### Post by 7raTEYdCql on 2010-08-16
Right now my distribution has Python2.4.3 installed in it.

I downloaded the 2.7 tar.gz. Placed it alongside my script.

I extracted the tar, and installed it in the created directory itself.

How do I make sure, that when I run my '.py' file, I run it from the "python" which is created in the directory alongside it??

Any suggestions??

Thanking you,
Mehrzad.

---

### Post by 7raTEYdCql on 2010-08-16
I basically want to change the version of Python in the middle of my script.

Something like, in the shabang statement I want to make it like this.

#!/some/path/Python-2.7/python

Where /some/path/=os.getcwd()

Can this be done?? Any suggestions??

---

### Post by -grubby on 2010-08-16
> **i.mehrzad said:**
> I basically want to change the version of Python in the middle of my script.

That doesn't even make sense. If you need Python 2.7 features, you have to depend on Python 2.7 for the whole script.

As for the shebang, yes, it can be relative, but including one that's relative to something on your system is a bad idea (unless you plan on including Python with your app, which is also a terrible idea.)

I would forget the shebang entirely and just manually run it from the directory Python 2.7's executable is; or you can even alias python2.7 to that executable in your shell of choice.

Actually, you could probably even "sudo make install" in the directory and have a global Python 2.7 exeuctable (/usr/bin/python2.7) - be careful though, it'll probably overwrite /usr/bin/python which could cause problems for scripts on your system depending on Python 2.4.

---

### Post by 7raTEYdCql on 2010-08-16
Thanks for that.

I had the idea of linking /usr/bin/python with /path/to/file/python-new.

---

