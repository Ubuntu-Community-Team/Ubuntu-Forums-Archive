---
title: "Using rpath?"
date: 2005-12-04
forum: Programming Talk
---

### Post by thedevilsjester on 2005-12-04
In an attempt to keep my application self contained, I am putting all of its required libs in the applications install directory ( which is, usually, /opt/<appname>/system )

To force ld to look there I have to pass g++ the rpath flag like:
-Wl,--rpath,./system

And this is fine if they are in the programs directory when they run it, because ld will look in ./system for the files, however if they are in another directory and just typed in the full path, or if they clicked a link to the app, etc..., then ld will not find the libs (because the . 'current directory', is not the same as the apps directory.)  

Basically my quesion is, is there another way to have ld dynamically look for the libs?  Or another flag I can pass to have it use the apps directory, not the current directory? I would hate to force my app to be installed in a specific directory, simply because ld cant find the libs otherwise....

On a side note, although I appreciate any help and suggestions, please dont give me a lecture on dynamic libs and their purpose ;)   I know that they should be installed into a public directory and not sit with the app itself, but this is a situation where that is not a good option.

---

### Post by LordHunter317 on 2005-12-04
Use a script and LD_LIBRARY_PATH.  Be wary of security issues.  It's far more flexible than -rpath will ever be.

---

### Post by thedevilsjester on 2005-12-04
I dont know if I like the idea of having to run a script that runs my program...although I guess it would make it a bit more dynamic...although I would really prefer a built in method...

Security issues?  Care to elaborate?

---

### Post by LordHunter317 on 2005-12-04
Well, it's how everything does it, so I don't see a better option.   Your other option is to use dlopen()/dlsym() and do the pathing yourself.

Security issues?  Well, if the path is set correctly, you could call some function you didn't expect to.

For example, if your script does this:```
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/myapp/lib
``` and LD_LIBRARY_PATH contained '/home/user/hackm/' or something else malicious, you could call an authentication function that would record the password you passed in, if you were asking for a password.  Google around, plently of details available I think.

---

### Post by thedevilsjester on 2005-12-05
I will google around and look into it a bit more, however my inital attempts using a script to change the path variable were unsuccessfull (it says that the lib cannot be found).  However pointing -fpath to the same directory, works.

My script is simple:
```

#!/bin/bash
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/mylogin/Desktop/myapp/system/
/home/mylogin/Desktop/myapp/myapp
```

Using dlopen really isnt a solution in this case, mainly because of the object orientated gui framework the app is using, would be a pain to setup with dlopen.  (or else I would probably do it).

---

### Post by LordHunter317 on 2005-12-05
You need to export LD_LIBRARY_PATH

---

### Post by thedevilsjester on 2005-12-05
ah I missed that, I dont really script very often, thanks.

---

### Post by k33n3r on 2012-03-15
or use $ORIGIN haha

7 years late

---

### Post by howefield on 2012-03-15
Old thread closed.

---

