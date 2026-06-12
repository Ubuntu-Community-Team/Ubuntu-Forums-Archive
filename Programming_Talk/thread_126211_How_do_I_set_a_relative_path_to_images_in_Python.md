---
title: "How do I set a relative path to images in Python?"
date: 2006-02-06
forum: Programming Talk
---

### Post by moephan on 2006-02-06
Hello,

I am using some images in a dialog box to show different states. I have the images in a sub-directory and can refer to them in my python scripts like:

```

myimag.set_from_file("images/imagename.png")

```

This works fine when I run the script from within the directory, but when I create a link to the script and try to run it from somewhere else, like the panel, it can't find the images. I have fixed the problem by putting the images in /usr/share/pixmaps/. Is that the right fix, or is there someway to specify the path as relative to the script no matter where the script is being called from? Thanks.

Cheers, Rick

---

### Post by markmark on 2006-02-12
The reason it breaks is because python works relative paths like that from the current working directory rather than the location of the script. You could try using the info [here]("http://diveintopython.org/functional_programming/finding_the_path.html") to find the path to the script and then os.chdir to change the current working directory.

Something like:
```
import os, sys
pathname = os.path.dirname(sys.argv[0])
fullpath = os.path.abspath(pathname) 
os.chdir(fullpath)
```Although I haven't tried it, and I don't know how it will work with links and the like. The simpler option is to just hardcode the location of the script and do:
```
import os
os.chdir('/path/to/your/script/directory')
```

---

### Post by moephan on 2006-02-13
Thanks for the info. What I ended up doing was putting all the images in a new directory in /usr/share/pixmaps and hardcoding the image path to that. Hope that makes sense. It seems like the way other apps are taking care of it.

Cheers, Rick

---

