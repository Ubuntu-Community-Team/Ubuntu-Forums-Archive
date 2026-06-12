---
title: "qmake, meshlab"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by ashvin on 2008-10-19
I'm trying to install meshlab on ubuntu. i've followed all the steps given in the link ([http://meshlab.sourceforge.net/wiki/index.php/Compiling](http://meshlab.sourceforge.net/wiki/index.php/Compiling)). but finally when qmake needs to be executed (qmake -recursive meshlabv11.pro) i came to know that the -recursive option is not there in the qmake. 

can anyone tell me what can be done? is there any meshlab deb or rmp available for automated install>

Ashvin

---

### Post by Paulo KIefe on 2008-11-08
Meshlab is a great tool!

Try installing this package. Worked perfectly for me.

[http://sid.ethz.ch/debian/meshlab/meshlab_1.1.1-1_i386.deb](http://sid.ethz.ch/debian/meshlab/meshlab_1.1.1-1_i386.deb)

Cheers :)

---

### Post by ashvin on 2008-11-11
i  am getting " Error: dependency is not satisfiable libqt4-gui" the libis installed on my machine.

any suggestions?

---

### Post by Paulo KIefe on 2008-11-11
Sorry to hear that. I installed it on an Ubuntu 8.10 installation and it worked.

---

### Post by putt1ck on 2009-09-16
Use [http://packages.debian.org/sid/i386/meshlab/download](http://packages.debian.org/sid/i386/meshlab/download) - works in Jaunty Kubuntu if you install libmuparser0 libqhull5 and do sudo dpkg -i --ignore-depends=libglew1.5 meshlab_1.2.1-1_i386.deb (the package libglew1.5 needs to be installed, but the Debian dependencies are not recognising it as the right version). Presumably it will be in Karmic?

---

### Post by tallia1 on 2010-03-30
I am trying Karmic right now. 

When I tried to follow the instruction above there was still something not working. After installing the lib3ds, qhull and mup****r, I still had a problem with Karmic which has  weird Qt versions:[INDENT][COLOR=Red] meshlab depends on libqt4-network (>= 4:4.5.3); however:
  Version of libqt4-network on system is 4.5.3really4.5.2-0ubuntu1.

[/COLOR][/INDENT]This extended ignore statement worked though, at least to install:[INDENT][COLOR=Red]sudo dpkg -i --ignore-depends="libglew1.5,libqtgui4,libqt4-network,libqt4-opengl,libqt4-xml,libqtcore4" meshlab_1.2.2-2_i386.deb
[/COLOR][/INDENT]But then the plugins were not installed correctly :( which means that you cannot import any file in the viewer:[INDENT][COLOR=Red]"The plugin '/usr/lib/meshlab/plugins/libsamplefilterdyn.so' uses incompatible Qt library. (4.5.3) [release]" 
aboutPlugins(): Current Plugins Dir: /usr/lib/meshlab/plugins 
[/COLOR]
[/INDENT] 


**[COLOR="Red"]SOLUTION[/COLOR]**
I ended up for just compiling the sources.. I was already successful in compiling them but the viewer was not working... At the load of a mesh the whole UI was getting messed up and un-responsive. The reason was that the [COLOR="red"]GLX libraries were not installed[/COLOR]. I am going to try to post a link to a karmic compatible deb package with the 4.3.3 libraries, as soon as I remember that command needed to generate them easily

---

### Post by tallia1 on 2010-03-30
> **ashvin said:**
> I'm trying to install meshlab on ubuntu. i've followed all the steps given in the link ([http://meshlab.sourceforge.net/wiki/index.php/Compiling](http://meshlab.sourceforge.net/wiki/index.php/Compiling)). but finally when qmake needs to be executed (qmake -recursive meshlabv11.pro) i came to know that the -recursive option is not there in the qmake. 

can anyone tell me what can be done? is there any meshlab deb or rmp available for automated install>

Ashvin
You might want to download and then use QtCreator rather than the makefile based system.
I managed to compile it correctly but then the GUI has some issues...

---

### Post by KenSeehart on 2010-03-31
> **tallia1 said:**
> I am trying Karmic right now. 

When I tried to follow the instruction above there was still something not working. After installing the lib3ds, qhull and muparser, I still had a problem with Karmic which has  weird Qt versions:[INDENT][COLOR=Red] meshlab depends on libqt4-network (>= 4:4.5.3); however:
  Version of libqt4-network on system is 4.5.3really4.5.2-0ubuntu1.

[/COLOR][/INDENT]This extended ignore statement worked though, at least to install:[INDENT][COLOR=Red]sudo dpkg -i --ignore-depends="libglew1.5,libqtgui4,libqt4-network,libqt4-opengl,libqt4-xml,libqtcore4" meshlab_1.2.2-2_i386.deb
[/COLOR][/INDENT]But then the plugins were not installed correctly :( which means that you cannot import any file in the viewer:[INDENT][COLOR=Red]"The plugin '/usr/lib/meshlab/plugins/libsamplefilterdyn.so' uses incompatible Qt library. (4.5.3) [release]" 
aboutPlugins(): Current Plugins Dir: /usr/lib/meshlab/plugins 
[/COLOR]
[/INDENT]Now I am trying to download the Qt environment for linux from [here]("http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp"). It comes as a bin release so I hope that they will over-ride the system wide Qt setup.

Yup, me too.  Please let me know if you find a solution.  I will do the same...

---

### Post by KenSeehart on 2010-03-31
... I installed Qt as you mentioned you would try.  It had no effect on the "4.5.3really4.5.2-0ubuntu1" version number for me.

---

### Post by KenSeehart on 2010-03-31
:guitar: It works!

I found this somewhat older version:

[http://openartisthq.org/debian/karmic/meshlab_1.2.1-1_i386.deb](http://openartisthq.org/debian/karmic/meshlab_1.2.1-1_i386.deb)

This version does not have the ** libqt4-network (>= 4:4.5.3)** dependency, so it works great.


[COLOR=Red]
[/COLOR]

---

### Post by tallia1 on 2010-03-31
It was not just the network dependency, there were a bunch of them.
I found the solution though. I will post it above :)

---

### Post by KenSeehart on 2010-04-02
> **tallia1 said:**
> It was not just the network dependency, there were a bunch of them.
I found the solution though. I will post it above :)

You are correct, it was certainly not just the network dependency.  But obviously, since the version I mentioned worked, it did not have any of the other dependencies either.

After all, nothing about my solution targets the network dependency specifically; it's just an older version that doesn't have the weird dependency problem in the first place.

The real weakness of my solution is that I don't get to use the latest version of MeshLab.

I'm looking forward to the new working deb package.  Thank you.

---

### Post by hasnat on 2010-07-27
Hi,
I have compiled Meshlab according to the instructions and it was successful. Now, I can't find the way to run it. I think its a silly question but can anybody tell me how to run Meshlab in ubuntu? (ubuntu version 10.04)

---

### Post by Mecasickle on 2010-09-12
Same Problem over here. Just installed it with Ubuntu 9.10. Can't seem to find an executable file like :
./Meshlab ?? Am I missing something?

---

### Post by Mecasickle on 2010-09-12
Found it!

Once in the MEshlab folder go to src / distrib /

then open the terminal on that location
and type ./Meshlab

Thread Solved!

One more thing:

I really reccomend your guys run this on the terminal if your have an error saying that
-recursive isn't part of the qmake library:

open terminal and type:
sudo apt-get install libqt4-dev qt4-dev-tools qt4-doc

if taht doesnt work, try uninstalling your previous versions of qmake (version 4.3) using the synaptic manager. Then type the command above again, and you should have no problems !

Go Meshlab!

---

