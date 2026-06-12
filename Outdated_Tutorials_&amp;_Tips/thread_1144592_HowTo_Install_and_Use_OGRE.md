---
title: "HowTo: Install and Use OGRE"
date: 2009-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by CalderCoalson on 2009-04-30
Here's a quick guide I wrote up for installing OGRE on Ubuntu.  I hope it's useful.



[SIZE="3"]**1 Installing OGRE**[/SIZE]

**1.0 Install Dependencies**
Execute the following in a terminal window:
```
sudo apt-get install build-essential autoconf libtool libdevil-dev libfreeimage-dev libfreetype6-dev libglew1.5-dev libxaw7-dev libxrandr-dev libxt-dev libxxf86vm-dev libzzip-dev
```
In case you're curious, the dependencies are as follows:
Bootstrap: autoconf libtool
Make: build-essential
Ogre: libdevil-dev libfreeimage-dev libfreetype6-dev libglew1.5-dev libxaw7-dev libxrandr-dev libxt-dev libxxf86vm-dev libzzip-dev

**1.1 Install OIS**
Go to OIS's download's page: [http://sourceforge.net/project/showfiles.php?group_id=149835](http://sourceforge.net/project/showfiles.php?group_id=149835) and download the latest release.  Decompress the file, open a terminal window, and cd to the decompressed folder.  Then, in a rather particular order, type:
```
./bootstrap
./configure
make
sudo make install

```

**1.2 Obtain the OGRE Source**
Download the "Ogre x.x.x Source for Linux / OSX" from [http://www.ogre3d.org/download/source](http://www.ogre3d.org/download/source) where x.x.x is the current distribution number.

**1.3 Create a Permanent Location**
Unlike most source distributions, you can't simply build, install and dispose.  The OGRE directory will need to be situated in a place you won't mind having it forever.  Personally, I have everything in ~/.ogre, but you can choose your own.  If you pick something else, just remember to substitute the location of your permanent folder whenever I say ~/.ogre.

**1.4 Unpack and Relocate**
Unpack the OGRE source using whatever means you choose, and move it to your undislosed permanent location, (~/.ogre).

**1.5 Configure**
Open a terminal window and cd to the OGRE source directory, (~/.ogre/ogre).  Now execute the following in the terminal:
```
./bootstrap
```
Now enter and execute the following:
```
./configure
```
If configuration fails after telling you to get nVidia's Cg library, then see the next step.

**1.6 Install nVidia Cg libraries**
**Note:** Do not perform this step if configuration runs successfully.
Download the "Linux x86" (32-bit) or Linux x86-64" (64-bit) tar files from [http://developer.nvidia.com/object/cg_toolkit.html#downloads](http://developer.nvidia.com/object/cg_toolkit.html#downloads) .  Decompress the file to wherever you want, and copy all the files to their appropriate folders on your system.
After placing the files, you need to reconfigure:
```
./configure
```

**1.7 Make**
Once configuration has finished, run the following:
```
make
```
Note that this can take a REALLY long time.  On my dual core 2Ghz it took nearly an hour.  If you want to speed this up, you can run make in multithreaded mode using the following command:
```
make -j x
```
where x is twice the number of cores your computer has.
**WARNING:** Do not execute 'make -j', this will run make with an unlimited number of concurrent threads and will overload and freeze your OS within a couple seconds.  This is called a makebomb.

**1.8 Install**
Now that everything has (hopefully) been built correctly, you're finally ready to install OGRE.  Cross your fingers and type:
```
sudo make install
```

**1.9 Update Dynamic Linker**
Now that you've installed everything in its proper place, you need to tell the linker to update it's chaches.  Run:
```
sudo ldconfig
```



[SIZE="3"]**2 Installing CEGUI [OPTIONAL]**[/SIZE]

**2.0 Install Dependencies**
Open a terminal window and type:
```
sudo apt-get install libpcre++-dev libpng12-dev libjpeg62-dev libmng-dev libwxgtk2.8-dev
```
Again, if you're curious, here're the dependencies:
CEGUI: libpcre++-dev
SILLY: libpng12-dev libjpeg62-dev libmng-dev
Layout Editor: libwxgtk2.8-dev

**2.1 Download and Relocate**
Download the current source release of CEGUI, SILLY Image Loading Library, CEGUI Layout Editor, and CEGUI Imageset Editor from [http://www.cegui.org.uk/wiki/index.php/Downloads](http://www.cegui.org.uk/wiki/index.php/Downloads) .  Unzip all the packages and move CEGUI-x.x.x, CEImagesetEditor-x.x.x and CELayoutEditor-x.x.x to your permanent location, (~/.ogre).

**2.2 Install SILLY**
Open a terminal window and cd to the SILLY directory.  No execute the following commands, one after another.
```

./configure
make
sudo make install

```
You are now free to dispose of the SILLY source directory.

**2.3 Install CEGUI**
Now cd to the CEGUI directory, (~/.ogre/CEGUI-x.x.x) and run the following commands:
```

./bootstrap
./configure
make
sudo make install
sudo ldconfig

```
This build also takes a while, so if you want to use multithreading you can replace 'make' with 'make -j x' like last time.

**2.4 Install CEGUI Layout Editor**
Open a terminal window, cd to the CEGUI Layout Editor directory, (~/.ogre/CELayoutEditor-x.x.x), and enter:
```

./configure
make
sudo make install

```
To run CEGUI Layout Editor, use 'CELayoutEditor'.  You can make a launcher for it or add it to your main menu at your leisure.
CELE requires you to give it the location of the default datafiles, (~/.ogre/CELayoutEditor-x.x.x/datafiles), when you start it for the first time, so it knows where all the default resources are.

**2.6 Install CEGUI Imageset Editor**
In a terminal window, cd to the the Imageset Editor directory, (~/.ogre/CEImagesetEditor-x.x.x), and enter:
```

./configure
make
sudo make install

```

**2.7 Build and Install CEGUIOgreRenderer**
After installing CEGUI, it is necessary to rebuild Ogre.  Change to the ogre root directory, (~/.ogre/ogre), and execute the following:
```

./bootstrap
./configure
make
sudo make install

```
**Note:** On Windows and in the tutorials, this library is called OgreCEGUIRenderer and leads to much unnecessary confusion.



[SIZE="3"]**3 Installing QuickGUI [OPTIONAL]**[/SIZE]

**3.1 Download and Relocate**
Obtain QuickGUI from the latest release thread here: [http://www.ogre3d.org/addonforums/viewforum.php?f=13](http://www.ogre3d.org/addonforums/viewforum.php?f=13) .  Extract the source and move it to your Ogre folder, (~/.ogre).

**3.2 Configure**
You may either use Code::Blocks or CMake to build the QuickGUI library.  If you are using Code::Blocks, the process is rather self-explanatory.
**Note:** Code::Blocks only builds the library, but does not install it.  You will have to manually move the dynamic library file (~/.ogre/QuickGUI/bin/libQuickGUI.so) to /usr/local/lib or wherever else you want to put it.
If, however, you decided to use CMake, cd to the QuickGUI source directory, (~/.ogre/QuickGUI) and type:
```

cmake .

```
**Note:** if you want to alter the default build options, you can type 'ccmake .' rather than 'cmake .'

**3.3 Build and Install**
Now that CMake has generated the Makefiles for you, you can simply run:
```

make
sudo make install
sudo ldconfig

```



[SIZE="3"]**4 Installing ODE [OPTIONAL]**[/SIZE]

**4.0 Install Dependencies**
*PLACEHOLDER*

**4.1 Download and Relocate**
Download the latest release from [http://sourceforge.net/project/showfiles.php?group_id=24884](http://sourceforge.net/project/showfiles.php?group_id=24884) , and unarchive it in OGRE home directory, (~/.ogre).

**4.2 Build and Install**
Open a terminal window, cd to the ODE directory, (~/.ogre/ode-x.x.x), and type the following:
```

./autogen.sh
./configure
make
sudo make install
sudo ldconfig

```



[SIZE="3"]**5 Creating an OGRE Project**[/SIZE]
**Note:** I will be using Code::Blocks for these instructions, although they will probably be easily adaptable to other IDEs as well.

**5.1 Create an Empty project**
Open Code::Blocks and select File->New->Project.  Choose an Empty Project, (the Ogre Project is broken on Linux), click Go, and choose a location.  Leave all the options on the next page default and click Finish.

**5.2 Add Linked Libraries**
In Project->Build Options select the "Linker Settings" tab and add "OgreMain" and "GL" to the "Link Libraries" box.
**Note:** Also add "OIS" for OIS, "CEGUI" for CEGUI, "QuickGUI" for QuickGUI and/or "ODE" for ODE, depending on which of these additional libraries you will be using.

**5.3 Setting up your plugins.cfg File**
Create a file named "plugins.cfg" in the directory your project's executable will reside in.  At the very minimum, this should include the following:
```

PluginFolder=/usr/local/lib/OGRE
Plugin=RenderSystem_GL.so
Plugin=Plugin_OctreeSceneManager.so

```

**5.4 Using the Example Application [OPTIONAL]**
If you are doing the tutorials or otherwise basing your project on the Example Application framework included with the OGRE source, you must copy the Samples/Media, and the Samples/Common/include/* from your OGRE source directory, (~/.ogre/ogre), to your project directory and your project include directory respectively.  Also remember to add the following to your main OGRE file:
```
#include "ExampleApplication.h"
```

**5.5 Setting up the Media files**
This is rather self explanatory if you're setting up your own application, and the wiki does a fairly good job explaining how the resource loader works.  If you are going to start with the tutorials, however, things can be a bit more enigmatic.  You should first copy the OGRE Samples' Media folder, (~/.ogre/ogre/Samples/Media), into your project, or create an alias to it if you want to save space.  Next, copy resources.cfg from your OGRE Samples' bin folder, (~/.ogre/ogre/Samples/bin/resources.cfg), to the directory containing your project's executable.  Finally, replace all the ../../Media with ./Media, (or the location/name of your Media folder, if you've changed that).



Once you have all this done, you should finally be able to follow the generic instructions on the Wiki.  I hope somebody finds these instructions helpful.  The whole installation process was hellishly time consuming and frustrating for me, and I hope this makes that slightly better.

-Calder

---

### Post by alfakini on 2009-05-05
[SIZE=3][SIZE=2]Hello Calder,

What is the CEGUI dependencies? It was not clear for me.

Thanks,

alfakini
[/SIZE][/SIZE]

---

### Post by CalderCoalson on 2009-05-05
Woah, sorry!  Thanks for pointing that out.  Fixing it now.

Also, CEGUI depends only on libpcre++-dev, but to function properly, you should install SILLY, (their in-house image library), which depends on libpng12-dev, libjpeg62-dev, and libmng-dev.

---

### Post by KunTheCronos on 2009-07-22
Hi Calder,

For some reason (with OGRE 1.6.2 Source for Linux / OSX) I couldn't do step 1.7 (make) without doing step 2.0 first
```
 sudo apt-get install libpcre++-dev libpng12-dev libjpeg62-dev libmng-dev libwxgtk2.8-dev
```I don' t know witch library solve the problem.

My system:
 - Ubuntu 9.04
 - Kernel Linux 2.6.28-13-generic
 - Gnome 2.26.1

Best regards,
K.

---

### Post by Banduin on 2009-07-25
If you want to use OgreCEGUIRenderer which is used in some of the Ogre tutorials, you have to make sure to install CEGUI before installing OGRE to get the OgreCEGUIRenderer module to build.

---

### Post by CalderCoalson on 2009-07-25
@KunTheCronos: That seems odd for two reasons.  First, the configure script should detect all missing dependencies, not the actual build.  Second, I wrote these instructions by following them to the letter on a freshly installed virtual machine.  If you wanted, you could remove all the packages, and re-add them one by one to see which one does the trick, and I could add that to the dependencies.

@Banduin: Thank you for pointing that out.  I've modified the CEGUI instructions to reflect that.

---

### Post by VIV0411 on 2010-05-16
Hello, i am unable to execute step 1.5 for version 1.7.1.

---

### Post by CalderCoalson on 2010-05-17
Sorry, Ogre has moved to CMake for its build process.  The instructions are now simply
```

cmake .
make
sudo make install

```

I'll change the HowTo once Ogre's tutorials are updated and 1.7 really goes official.

---

### Post by sihem on 2010-10-20
please help me.I'd like to compile and running an ogre application by  code blocks and not using cmake.i have code blocks 8.02 with and ogre1.7  installed in my ubuntu 10.04 system.so please i ask the necessary  configuration to do to code blocks for that.thank you in advance.

---

### Post by CalderCoalson on 2010-11-07
Umm...  CMake is only used for building Ogre itself.  Follow the instructions in Step 5 of the HowTo for setting up a project with CodeBlocks.

---

### Post by Medivh90 on 2011-03-01
1.5 Configure
Open a terminal window and cd to the OGRE source directory, (~/.ogre/ogre). Now execute the following in the terminal:

I have successfully came to this point and cd into dir with src(it has Cmake, Components, Docs, OgreMain, etc) 
when i try 
./bootstrap or ./configure
bash: ./bootstrap: No such file or directory 
I am on Ubuntu 10.05 - ogre src v1.7.2.

Can someone help me with this?

---

### Post by CalderCoalson on 2011-03-01
Sorry, use the CMake instructions above.

---

