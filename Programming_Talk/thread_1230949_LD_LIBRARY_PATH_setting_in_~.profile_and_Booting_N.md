---
title: "LD_LIBRARY_PATH setting in ~/.profile and Booting Nautilus error"
date: 2009-08-04
forum: Programming Talk
---

### Post by flylehe on 2009-08-04
Hi,
I just met a booting error:
> 
Nautilus cannot be used now, due to an unexpected error. Nautilus cannot be used now, due to an expected error from Bonobo when attempting to register the file manager view server.
The Panel has encountered a fatal error: The panel could not register with the bonobo-activation server (error code: 3) and will exit. It may be automatically restarted.


Fortunately I happened to find the reason is that I messed up my ~/.profile file:
in order to use Matlab engine in C C++ code ([http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f29148.html&http://www.mathworks.com/support/compilers/interface.html](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f29148.html&http://www.mathworks.com/support/compilers/interface.html)), I add the shared library path in .profile:
```

LD_LIBRARY_PATH=/home/MatlabLinux/bin/glnx86:/home/MatlabLinux/bin/glnx86:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH

```

After removing these lines, I am able to boot into my gnome now.

I still wonder though: is there anything wrong with my setting of LD_LIBRARY_PATH in ~/.profile? Why these lines can make Nautilus and Bonobo not work?

Thanks and regards!

---

### Post by dwhitney67 on 2009-08-04
Have you tried placing the statements in your ~/.bash_profile (or ~/.bashrc) instead?

Btw, if you want, you can combine the two statements into one; for example:
```

export LD_LIBRARY_PATH=<MatLab paths>:$LD_LIBRARY_PATH

```

---

