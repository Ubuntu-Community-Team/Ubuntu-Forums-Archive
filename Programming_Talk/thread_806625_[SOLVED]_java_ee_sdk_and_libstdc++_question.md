---
title: "[SOLVED] java_ee_sdk and libstdc++ question"
date: 2008-05-25
forum: Programming Talk
---

### Post by animefan82 on 2008-05-25
ran chmod +x java_ee....
---
$ ./java_ee_sdk-5_05-linux.bin
./java_ee_sdk-5_05-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
---
gcc has been installed, but still no go.

And on a side note, I ran chmod both with and without sudo. Doesn't work.
Oh, and the jre was installed from add/remove applications (GNOME)

I think that's about it. Now.
What do I do to access libstdc++? Step by step, please.

---

### Post by Zugzwang on 2008-05-25
Use "packages.ubuntu.com" for searching for packages containing some file. You will see that the package "libstdc++5" contains the library version you need. Install it and it might work:
```

sudo apt-get install libstdc++5

```

---

### Post by animefan82 on 2008-05-25
Dammit, why didn't I think of searching synaptic for the actual missing library??
Thanks man. Worked like hand in a glove. Now I just got the infamous "swing vs. compiz-fusion"-problem, but that one I know I can handle ;)

---

### Post by animefan82 on 2008-05-25
When I think about it, I can just add it here for future reference. If anyone who reads this have the problem with a gray window without anything in it while opening java-based programs, and are running compiz/compiz-fusion, do this:

- open up a terminal window, and type/copypaste
- export AWT_TOOLKIT=MToolkit
- minimize & unminimize the java program

This is only a temporary solution, as in for the session you are running only.
To make the change permanent, that is, to run that export command every time linux starts do almost the same thing:

- open up a terminal window and type/copypaste
- sudo gedit ~/.bashrc (not sure about the sudo command, but I use it just in case)
- when the text editor opens, add a new line at the very bottom of the document and copypaste
- export AWT_TOOLKIT=MToolkit
- save and exit

This should bring the swing/compiz problems to a minimum.

NOTE: I'm not sure about ATI cards, but I'm 96.32% certain it'll work with most nVidia cards.

---

