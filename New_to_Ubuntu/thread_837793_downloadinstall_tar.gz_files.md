---
title: "download/install tar.gz files"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by archinephew on 2008-06-22
Greetings. I have been using a pro version of qcad for some time. On a newly installed 8.04 on a new machine, I can't do anything with the downloaded tar.gz. Firstly, I have been advised that the preferred place for programs is in usr, so I've created a usr partition, but I don't see any way to direct anything to it. Secondly, when I download to the desktop, I get the little carton with the label "qcad.etc., tar.gz". I right-click on this, and choose "extract here" and get an image of a file labelled "qcad, etc", when I double-click on that, I get a bunch of files, none of which installs or starts the program, and a little blue-gray cube, which I can't get to do anything. On previous installs, I remember periods of desperation, but usually, after much trial and error, something has worked. But there must be a better way! Does anyone know of a simple tutorial for installing a downloaded program that comes in tar.gz format? Do it in the GUI, and you will have the gratitude of many desperate souls. Thanks in advance.

---

### Post by oldos2er on 2008-06-22
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by macaholic on 2008-06-22
If it is a normal linux program, you would install it by opening a terminal and typing:```
cd </path/to/folder containing program>
./configure
make
sudo make install
```
if all goes well it should compile and install the program.

---

### Post by RomeReactor on 2008-06-22
Hi. As you may have noticed, a TAR.GZ, much like a ZIP or RAR file, is a compressed archive. **/USR** is not a partition, but a directory in Ubuntu. After extracting the files, you should look for a README or INSTALL file which should contain instructions on how to install/run. Not all TAR.GZ files contain source code, so the instructions could be on just how to run the precompiled program.

If the instructions are to compile it, then you need to install some tools to do so:
```
sudo aptitude install build-essential
```

However, if you don't absolutely need to install QCAD from source--to get the absolute newest version, for example--you may find it's easier to search for **cad** in 'Applications->Add/Remove', or in 'System->Administration->Synaptic'.

QCAD is available this way. You can install QCAD by searching for it in 
these package managers, or to install it from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install qcad
```
You should try to find programs through these package managers before trying to compile them from source.

---

### Post by archinephew on 2008-06-24
Thanks to all. To clarify: I meant that I have been advised that a usr partition is a good idea, and that usr is the natural place to put programs. Having downloaded and stored the program in desktop, I cannot move it to usr because I get a "no go"message. The download was in the form of an image of a carton and a label with the program name, tar.gz. When I clicked on "extract here" I got the image of a folder labelled with the program name. When I double clicked on that, I got several files,(none of them implying "install" or "readme"),and a blue grey cube, labelled "qcad". This is where the problem lies. On a previous version (7.10) I double clicked on the cube and the program opened. Now, when I right-click the cube, I'm told it is an executable file, but no left-clicking on the cube achieves anything. I am happy to try to solve the problem in the terminal, but I need keystroke by keystroke help because I have no expertise in this.BTW, all this arises because I need the functionality of the full version of qcad which I get from Ribbonsoft, and not just the slimmed down version that comes through "add/remove, adept, etc.". If I haven't bored everyone to tears, I hope someone can help. Thanks

---

### Post by RomeReactor on 2008-06-24
Try right-clicking on the executable, select 'Properties', go to the 'Permissions' tab make sure the 'Execute' box is checked.

Also try opening a terminal and drag the executable there, then press enter. If you get errors, please post them.

---

### Post by archinephew on 2008-06-24
Thanks. The "execute" box was already checked,(I don't remember if I previously checked it or if it was that way). Dragging the executable into the terminal, I clicked on the little open rectangle following the file name, then hit "enter". I got "bash:path program name : no such file or directory" Whether it makes sense or not, I also typed in sudo, then dragged in the cube, etc., with the same result.Does it get any clearer? Thanks for help so far!

---

### Post by RomeReactor on 2008-06-24
Try it like this:
```
~/Desktop/NAME_OF_FOLDER/NAME_OF_EXECUTABLE
```

If the folder is still in your desktop, and assuming the name of the folder is **qcad-2.2.1.0-1.linux.x86** and the name of the executable is **qcad**:
```
~/Desktop/qcad-2.2.1.0-1.linux.x86/qcad
```

Just downloaded the demo and it runs without need to download/install anything else. Did you move the executable out of its folder?

---

