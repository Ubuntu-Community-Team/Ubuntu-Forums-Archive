---
title: "Pkg-Config Error"
date: 2009-06-24
forum: Packaging and Compiling Programs
---

### Post by kaspar_silas on 2009-06-24
Hi All,

Hopefully someone can do some translating for me. I am trying to install the Imlib3D library (for some c++ volumetric image processing).

So I downloaded the source from:
[http://imlib3d.sourceforge.net/]("http://imlib3d.sourceforge.net/") 
and tried:

./configure

This failed finishing with:
```
configure: error: Package requirements (libxml++-2.6 >= 2.6.1) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the XML2_CFLAGS and XML2_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

When I look in synaptic I do in fact have libxml++-2.6.2 . So I guess as the error suggests it is some error with pkg-config's reply.

However I have no idea how to implement either suggested fix. Can someone tell me how to do set these flags or adjust the variable.

Thanks for any help

---

### Post by wojox on 2009-06-24
Go to **Applications** > **Accessories** > **Terminal**

Enter **sudo apt-get install libxml++-2.6-dev**

Then try install again.

---

### Post by kaspar_silas on 2009-06-24
Thanks alot that was it. I was totally thrown of the scent by the error message referring to libxml++-2.6 not libxml++2.6-dev.

Just in case someone else encounters the same problem the above line has a slight typo (extra "-") it should be 

sudo apt-get install libxml++2.6-dev

Thanks again

---

### Post by kaspar_silas on 2009-06-24
Spoke far too soon. Moving onto "make" gave the error:

```

TaskProgressManager.cpp: In member function 'void TaskProgressManager::EndTask(const TaskInProgress*)':
TaskProgressManager.cpp:107: error: cast from 'const TaskInProgress*' to 'uint' loses precision
make[3]: *** [TaskProgressManager.lo] Error 1
make[3]: Leaving directory `imlib3d-0.9.2/ImLib3D'
make[2]: *** [all] Error 2
make[2]: Leaving directory `imlib3d-0.9.2/ImLib3D'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `imlib3d-0.9.2'
make: *** [all] Error 2

```

Why is this an error? Surely a losing precision note should be a warning. I commented out the line in the .cpp as it was only a printf line. This worked but I just ran into the same problem in the next file. A quick search showed that there were loads of these casts. 

Is there a flag for g++ to ignore these precision losses. Or does anyone know a better way around this. Come to think of it has anyone actually compiled imlib3d on an ubuntu (64b) machine before.

---

