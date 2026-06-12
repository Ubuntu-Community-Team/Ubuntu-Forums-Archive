---
title: "Python : How to locate the current user's Desktop folder"
date: 2010-11-21
forum: Programming Talk
---

### Post by yanes on 2010-11-21
Hi all , 

I coded a python application in Python that manage some files 
when we need to locate the User Home folder , We do some thing like :
```

>>> import os
>>> print os.getenv("HOME")
/home/yanes


```
Or simply you can get all possible environment variables via :
```

>>> import os
>>> print os.environ


```

But in all system variables , I can't locate The desktop folder path 
:p , in an english version of the distribution it's a :
"/home/yanes/Desktop" ;) (Example)
but in other distirbution languages it's name 'll be translated 
it's called "Bureau" in french copies for example 
So is there a python issue or system variable that return the exact name or full path for the Desktop folder ? 

thanks in advance ;)

---

### Post by OgreProgrammer on 2010-11-21
Usually when I run across a problem like this, I like to look outside the box. In this case, the question that pops into my head is "How do I tell ubuntu to use a different folder for the Desktop?"

I hunted around for this and found it in ~/.config/user-dirs.dirs which just so happens to be a text file. 

Mine is stored on the first line after the comments, so a tiny bit of reg-ex to skip the lines starting with # should be enough.

---

### Post by StephenF on 2010-11-22
os.path.expanduser("~")

There is another thread about this started barely a week ago. The above code will locate the home folder in a platform independent way.

os.path.join(os.path.expanduser("~"), "Desktop")

This will connect path elements in an os independent way.

Your desktop folder depends on which desktop environment is in use so naturally the first place to go digging is gconf-editor where I found absolutely nothing. My guess is it's hard coded to a key of a translation file. In KDE the whole conception of a Desktop folder was dropped entirely and you may specify various folders to appear in a desktop background window instead.

I think writing software that assumes such a folder exists and will act like you assume is a mistake.

---

### Post by unknownPoster on 2010-11-22
In this circumstance, it may be best to explicitly prompt the user for the path to your requested directory and then check the path for validity.

---

