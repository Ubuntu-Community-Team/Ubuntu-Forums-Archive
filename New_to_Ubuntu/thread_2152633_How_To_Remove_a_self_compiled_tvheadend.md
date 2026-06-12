---
title: "How To Remove a self compiled tvheadend"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-06-08
From github, I d/l'd the zip of tvheadend. Extracted it into /home/username and did:


./configure
make
sudo make install

then calling: tvheadend in a terminal and surfing to: [http://localhost:9981/simple.html](http://localhost:9981/simple.html)

shows the browser blank or empty.

How do I remove the files (objects, what-have-you) that I installed using the above 3 commands?

The entire set of files and terminal output can be seen at: [http://pastebin.com/Eh0GLz4v](http://pastebin.com/Eh0GLz4v)

---

### Post by monkeybrain2012 on 2013-06-08
Self compiled programs don't show up in the package manager. Unless it comes with an uninstall script, you have to locate the pieces and remove them manually. That can be easy or painful, depending on your program. Some programs install their components inside one or a few folders, in that case you can just remove those folders. Some may have pieces scattered over the file system, there is no packaging standard.

For future references you should install checkinstall from the repo. This will create a .deb when you compile from source with it (change "sudo make install" to "sudo checkinstall" in your last step of compiling) and it will show up in the packaging manager (e.g synaptic) and you can remove it easily.

---

### Post by sandyd on 2013-06-08
try going to the directory you ran make install in, and run
```

sudo make uninstall
```
some developers build that in, some dont.

---

### Post by Mark_in_Hollywood on 2013-06-08
What command will recursively find the stings "tvh" or "tvheadend"?

---

