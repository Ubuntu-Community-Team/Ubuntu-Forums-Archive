---
title: "IPython debugger"
date: 2009-12-15
forum: Programming Talk
---

### Post by C++buntu on 2009-12-15
Hi everyone, 

I want to use the ipython debugger for a little program just to see how it goes, when i try the following line:

```

In [1]: run -d ball_table.py
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)

/home/steeve/Python/Source/basic/<ipython console> in <module>()

/var/lib/python-support/python2.6/IPython/iplib.pyc in ipmagic(self, arg_s)
    951         else:
    952             magic_args = self.var_expand(magic_args,1)
--> 953             return fn(magic_args)
    954 
    955     def ipalias(self,arg_s):

/var/lib/python-support/python2.6/IPython/Magic.pyc in magic_run(self, parameter_s, runner)
   1613                     maxtries = 10
   1614                     bp = int(opts.get('b',[1])[0])
-> 1615                     checkline = deb.checkline(filename,bp)
   1616                     if not checkline:
   1617                         for bp in range(bp+1,bp+maxtries+1):

/usr/lib/python2.6/pdb.pyc in checkline(self, filename, lineno)
    450         line or EOF). Warning: testing is not comprehensive.
    451         """
--> 452         line = linecache.getline(filename, lineno, self.curframe.f_globals)
    453         if not line:
    454             print >>self.stdout, 'End of file'

AttributeError: Pdb instance has no attribute 'curframe'

```

What is wrong? Any ideas?

Thanks

---

### Post by jpkotta on 2009-12-15
I don't know what exactly is wrong, but clearly ipython doesn't work with the default pdb.  This works for me:
```
sudo apt-get install pydb
ipython -pydb
```
```
run -d *script*
```

BTW, I didn't even know about this debugger, I was using python -mpdb *script*.  This looks better, thanks.

---

### Post by C++buntu on 2009-12-16
Thank you!

---

