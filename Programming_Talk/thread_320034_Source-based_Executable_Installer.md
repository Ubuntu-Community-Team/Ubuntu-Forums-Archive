---
title: "Source-based Executable Installer?"
date: 2006-12-16
forum: Programming Talk
---

### Post by TheForkOfJustice on 2006-12-16
Is there such a technology or project underway which will install software much like debs, rpms, msi and exe files do EXCEPT they compile the program from source instead of pre-compiled binaries? 

Basically, is there an linux installer that uses for source code?  We are all familiar with tar.gz files and the make commands, but I wish I could start installation by double-clicking on a single file and not the command line.  Any special configurations or settings that can be changed (like the install path) should be alterable just like they are during Windows installer dialogs.

I've been wondering if this could be possible. It would take longer to install a program but it would create better software installations and make it easier for developers since they would not have to supply a multitude of files for different setups. They could just provide one installer and it would work for everyone regardless of the setup of their systems.

---

### Post by Wybiral on 2006-12-16
You could use a shell script... In fact, you could combine a shell script with a makefile and pretty much accomplish what you just mentioned.

---

### Post by TheForkOfJustice on 2006-12-16
Well what I'm looking for is the ability to have the whole thing run with a nice GUI. It would be nice to install something simply from source without a command line and I don't have the skills to develop a system like that.

---

### Post by Wybiral on 2006-12-16
In ubuntu, if a shell script has executable status, it can be ran from clicking it. You can also use something like zenity to give your shell script a little GUI to it.

Regardless, I don't think the command line is that bad... All you have to do is type "make", sometimes "./configure".

What kind of stuff would you want the GUI to do? Aside from actually BEING an IDE for the compiler I can't see what other stuff you would need.

---

### Post by maddog39 on 2006-12-16
Well the one huge problem with source packages is dependencies. If someone could make a program with a GUI that would take its own sort of config file and then build the dependencies along with it, also requiring the packager to pack the dependencies with the rest of the source. Would be really nice. If Linux and or Ubuntu want to get anywhere with novice computer users, as in people who aren't technalogically aware, then it needs to do something about handling all sorts of software packages, including raw source.

---

### Post by Wybiral on 2006-12-16
Well, problems with raw source aren't ubuntu's fault... Most people don't know how to compile it on other os's either. You would have to blame the distributor of the software for that... Either they should release a binary, or they should list the dependencies. Makefiles are particularly nice but the average user may have a hard time interpreting the error messages. So, just make sure you have all of the required files to compile it, and run the make file. It *should* work. If not, it's probably the distributors fault. You can't do much about that...

---

### Post by SuperMike on 2006-12-16
There's a way on Linux to take a bash script and a set of directories and convert it into an ELF-style executable that you can install by typing the command. However, it doesn't come with a GUI for that and you would have to build one with something like zenity or Python.

It's called **makeself**.
There's also a command that just compiles single shell scripts called **shc**.

Both of these can be installed with the 'apt' command if you flip over the universe option temporarily to retrieve them and then flip back to standard mode.

If you use Python and Glade-2, you can draw a wizard-like app and call it from this script that's compiled into makeself. Or, you can go the cheap way and call zenity to throw up short little dialogs and progress windows as you go.

There was also a discussion that seemed to indicate that it should be the job of the configure and make commands to be smarter and not only very nicely alert you of dependencies, but perhaps give you some remediation method to hunt them down in signed format from reliable sources and install them. My vote is behind that argument -- I agree. However, the community is open, and if this user happens to know C, he can consider contributing to that team.

---

### Post by maddog39 on 2006-12-17
Yeah, I personally prefer GTK+ for my GUI toolkit, but if you wanted to expand this idea, to say windows or mac. You might want to use something like wxPython, a cross-platform framework with easy installation on all OSes. Although, on mac they make you compile from source code in apple's IDE, XCode, and it takes like 2 hours, almost. It took something like ~1:40 to compile from source (i did it manually, with ./configure && make && sudo make install), on my PowerBook G4 w/ 1GHz PowerPC. Although nevermind that, compiling PyGTK2 from the Darwin/BSD ports repository, took almost 3-4 hours on the same computer. That included its dependencies.

---

### Post by TheForkOfJustice on 2006-12-17
The compile time would prevent a source code installer from becoming a common install method, but it is a good idea if you do wish to do a compile-install.

I was only wondering if there was a standard being developed that would provide a GUI to the whole compiling process. It would be nice if the Ubuntu Team or some experienced coder would tinker with the idea.

I am aware that the make commands aren't complex but there can be a multitude of additional configuration commands that the average user fails to consider when installing a package.  Ignoring them can leave you with an unusable (or at least 'ill-configured') installation after an hour or so of compiling.  I was hoping that a source installer with a GUI would help make the process of configuration more palatable and obvious to everyone, novice and expert.

Unlike Windows and Mac, Linux lacks standardization that would would make installs easy.  Creating a wizard that distro developers could use to list their distro's default options (ex - install paths, use of dpkg/apt/yum, autodetecting the sound/video servers, etc) and then exporting them to an editable conf file the installer could read, would be nice.

Checking and installing dependancies is a must. The conf file should already have which package-nabber to use and the installer may have the option to compile dependancies from source or from a repository deb/rpm.

My coding skills are non-existant and I can't make something like this (besides I'm already on another project) but from what I'm reading in the above posts it wouldn't be extraordinarily difficult for an experienced programmer. The hardest part would probably be having the installer generate an interface for a custom configuration based on the conf files in the source package. 

If this installer operated only on archive files with a certain extension different than tar.gz then it would be easy to tell which packages have been properly configured for compiling/installing in this manner. The installer should give someone the choice of installing the package, checking dependancies or simply extracting the code to a folder.

Dang, how long have I been brainstorming this :P

---

### Post by TheForkOfJustice on 2006-12-17
> **maddog39 said:**
> Yeah, I personally prefer GTK+ for my GUI toolkit, but if you wanted to expand this idea, to say windows or mac. You might want to use something like wxPython, a cross-platform framework with easy installation on all OSes.

I'm a novice at using glade but doing rather well at it. Zenity was mentioned earlier and I hope I remember to check that our when I get my main system back. Personally, I'd just get it working on one distro first, then all of linux. I wouldn't bother with Windows and Mac. They have good installers and don't have to worry about configurations like Linux users do.

---

### Post by maddog39 on 2006-12-17
Hmm.. true I suppose, about not needing to port it to other platforms, didn't think about that at first. So okay, I will submit a request for a new SF.net project and i'll come up for a name for this and I plan to use Compiled Python (bytecode) since it's easier and doesn't require pesky binaries and other stuff for the final product but written in python none the less. Also, every single linux distrobution out there comes with Python 2.4 now I think and GNOME installations defaultly have PyGTK2 installed. So, that there pretty much eliminates C++ in my mind.

So I've thought of many ideas for this project. I'll list them here.
[LIST]
[*]The GUI would have a wide array of options.[LIST]
[*]The developer/packager would be able to offer either a binary or a source package or just one of the two.
[*]So when the user goes to install the package, they'll have a few choices there.
[*]If the user selects the source package option (if availible), they will have the option to choose from ./configure options with check buttons probably and so on.
[*]if the user selects the binary package option (if availible), they will have the option to choose where they might want to install the software or any other options the developer/packager wants to include.[/LIST]
[*]There will be a very easy to use Python API for scripting custom installlers, to gain extra options during the installation process. Some things/examples were mentioned above.[LIST]
[*]Maybe, later on in the project, another GUI will be include or be optionally downloaded that would automatically generate customizable installers without the need of knowing how to using the Python API and or scripting.[/LIST]
[*]Eventually, as more compatibility will be needed for cross-platform unix support, the installer will attempt to detect (if using platform specific binary package (e.g. rpm, deb, etc) command to use to unpack/install the package.
[*]If the developer/packager doesn't want to use a platform specific package (which of course, platform specific packages [e.g. rpm, deb, etc] won't be supported initially) they can simply instruct the installer to install raw compiled binary files into certain areas of the system and so on.[/LIST]Well, those are most of my thoughts and ideas that I have for this. If successful, something like this could mean a revolution in linux usability.

---

### Post by pmasiar on 2006-12-17
> **TheForkOfJustice said:**
> Is there such a technology or project underway which will install software much like debs, rpms, msi and exe files do EXCEPT they compile the program from source instead of pre-compiled binaries? 

Basically, is there an linux installer that uses for source code?  We are all familiar with tar.gz files and the make commands, but I wish I could start installation by double-clicking on a single file and not the command line.  Any special configurations or settings that can be changed (like the install path) should be alterable just like they are during Windows installer dialogs.

I've been wondering if this could be possible. It would take longer to install a program but it would create better software installations and make it easier for developers since they would not have to supply a multitude of files for different setups. They could just provide one installer and it would work for everyone regardless of the setup of their systems.

Seems to me you are looking for [gentoo]("http://en.wikipedia.org/wiki/Gentoo_Linux") linux distribution. Compiles all from source, with own package format. But you cannot be afraid of command line - there is no GUI until you will compile it. Go ahead try Gentoo - I am sure you will learn a lot. :-P You will either love it and stay with Gentoo, or will come back appreciating more what a great job debian and ubuntu maintainers do so you don't have to.

For great non-GUI admin tool, try mc - midnight commander. It is the first tool I install on any server where I can. :-)

Good luck!

---

### Post by Game_Ender on 2006-12-17
You guys have heard of Portage and Ports right?  Both are two large source based package systems.   In portage and ports (just like with debian packages) you have a custom file that list dependencies and the commands necessary to install the package.  

They both have GUI's for the user to install packages with, but to the best of my knowledge they don't (maybe the Gentoo ones due)  allow you to customize the package.   Protage has a python API for its system, but I am not sure of Ports.

It might be better to and adapt Portage or Ports than two right yet another packaging system.  You might also consider adding source package capability to [Autopackage]("http://autopackage.org/") which is already distro independent.

EDIT: pmasiar beat me to it.

---

### Post by maddog39 on 2006-12-17
Yes however this is NOT a package manager, something completely different. It's a graphical package installer, which has the goal of creating an easy to use standard for linux users. Completely different from portage and what not. Also gentoo takes nearly 2-4 days to compile, who wants that.

---

### Post by TheForkOfJustice on 2006-12-18
> **maddog39 said:**
> Yes however this is NOT a package manager, something completely different. It's a graphical package installer, which has the goal of creating an easy to use standard for linux users. Completely different from portage and what not. Also gentoo takes nearly 2-4 days to compile, who wants that.

Quite. What we are thinking about now is a lot like the installers that pop up with you install something in Windows and Mac but instead of binaries it will compile source code. This could really be a help towards standardizing linux.

[http://www.techspot.com/news/19128-free-standards-group-launches-linux-standardization-project.html](http://www.techspot.com/news/19128-free-standards-group-launches-linux-standardization-project.html)

I know gdebi works for installing debs. This is sort of like that but for source code and probably with a lot more configuration possibilities. It would end the need for software makers to offer many different debs and rpms when they make a release, and it would probably make adding software to repositories quicker. It may even help game developers out by providing a way for their software to know how to configure itself and where to put its binaries/media.

Once you figure out how to get it working on Ubuntu then you can see if other distros can operate it. It could really be a boon to linux. Hopefully, you won't need to create another package type, but if you did it need not be any more than the tar.gz file with a different extension, so the installer will know what files to act upon. Else, the archive manager would probably activate instead of the installer when the file is double-clicked.

Just another 2 cents added to the pot ;) 

Don't forget to add a CANCEL button at every step in the GUI. Lets us know how things are going!

God's speed!

---

### Post by Wybiral on 2006-12-18
You know... This doesn't sound like a bad idea. The only problem would be that it would have to parse the source and determine the libraries and include files to be able to compile it... Or, the source distributors can setup a file that feeds this to the source installer. It would kindof be like a user friendly makefile system.

---

### Post by TheForkOfJustice on 2006-12-18
> **Wybiral said:**
> You know... This doesn't sound like a bad idea. The only problem would be that it would have to parse the source and determine the libraries and include files to be able to compile it... Or, the source distributors can setup a file that feeds this to the source installer. It would kindof be like a user friendly makefile system.

When you think about it, it is only a GUI for the makefile system.  Everything, from gathering depends to compiling is already handled in virtually every linux distro. The installer would just have to know when to activate each activity on the backend and hopefully give it graphical output when essential.

The hardest part would probably be getting the people who write code to include a conf file that would list each possible configuring command. You may have to create a format guide for these files so developers would know what format to follow. Something like this:

```
[check][command=""][field=3][description="blah blah blah"]
```

The [check] would be a simple checkbox that would tell the installer to activate the customized configuration command listed in [command=""]. The [field=3] is simply an empty field 3 spaces long (can be any required size of course) that the user needs to enter a value needed by [command=""]. [description=""] would simply be the command's description. 

Basically, every widget that can be on a GUI should be able to be used when needed. I'm ignorant when it comes to coding, but whatever happens it should be simply formatted like I demonstrated above.

Commands and descriptions are usually listed in readmes, which are useless for this purpose. This project will establish a standardized format for such files.

Once developers realize this method is open you will certainly get packages with the proper conf file.

---

### Post by hod139 on 2006-12-18
Check out [iCompile]("http://ice.sourceforge.net/").  I don't know of a GUI for it, but it sounds along the lines of what you want for a backend.

---

### Post by winch on 2006-12-18
> **maddog39 said:**
> Yes however this is NOT a package manager, something completely different. It's a graphical package installer, which has the goal of creating an easy to use standard for linux users. Completely different from portage and what not. Also gentoo takes nearly 2-4 days to compile, who wants that.

The big difference between this a gentoo is the naive idea you can just download source tarballs from the net and ./configure && make && make install and have good quality working software.
It doesn't work like that in a lot of cases. That's why every other system maintains their own source repository where they import software and massage it until it compiles, runs and is integrated into the system.

> **hod139 said:**
> Check out [iCompile]("http://ice.sourceforge.net/").  I don't know of a GUI for it, but it sounds along the lines of what you want for a backend.

Looks quite interesting, I often write makefiles that do essentially the same thing. Once you spend the time learning how to do it with make it's very easy but if you don't want to it's probably a nice alternative.
The assumption that you want to compile all C++ files in the current directory into a single executable whose name matches the directory name is very inflexible compared to makefiles and other methods. What about software where this assumption is incorrect?

---

### Post by -Rick- on 2006-12-18
Maybe my little project interests you? [Link]("http://nixstaller.berlios.de").

---

### Post by TheForkOfJustice on 2006-12-20
[http://sourceforge.net/search/?type_of_search=soft&words=source+code+installer](http://sourceforge.net/search/?type_of_search=soft&words=source+code+installer)


I went into SourceForge to check out what they had on the subject. Apparently, we weren't the first to think about this as some of the projects on the first page alone describe what we are talking about here.

I can't test out any of the projects but if someone else wanted to have a good look their work could turn out to be useful.

---

### Post by blueCommand on 2006-12-20
What about emerge?

Wouldn't you be able to modify it?

---

### Post by maddog39 on 2006-12-20
> **TheForkOfJustice said:**
> [http://sourceforge.net/search/?type_of_search=soft&words=source+code+installer](http://sourceforge.net/search/?type_of_search=soft&words=source+code+installer)


I went into SourceForge to check out what they had on the subject. Apparently, we weren't the first to think about this as some of the projects on the first page alone describe what we are talking about here.

I can't test out any of the projects but if someone else wanted to have a good look their work could turn out to be useful.
Okay, I took a look and past page 2 is like a bunch of misc projects unrelated. All of the projects that were related were either alpha or beta and most werent far enough in development to be useful. Most of them were pretty inactive aswell, although one of them did appeal a bit.

gConfiugre: [http://gconfigure.sourceforge.net/](http://gconfigure.sourceforge.net/)

It's in beta but looks the most promising of them all. I have not tried it yet but  will compile it tonight and try it.

---

### Post by maddog39 on 2006-12-20
Okay, well apparently it's just a shell script that automates this so no compiling needed as I expected. Although after running the installer for gconfigure it's completely disfunctional. It apparently is supposed to make a scripts menu with a thing in it to automatically configure/compile/install a tar.gz but that didn't appear for me and no command was installed either.

---

### Post by TheForkOfJustice on 2006-12-20
Bah. Well that just means you may be the one who brings this function to the world of linux. Too bad the others gave up so easily.

---

### Post by TheForkOfJustice on 2006-12-23
Hye, maddog39. this may interest you a tad.

[http://puppylinux.org/wikka/DotPup](http://puppylinux.org/wikka/DotPup)

I use Puppy Linux and have to say they have a nice installation method. Their dotpup files are zip archives that use binary files (not source code) butit is related in principle to what we are discussing. The abilityto check the md5 hash before installing is a great feature and I'm not sure if curent repositories do this.

Just a heads up. Hopefully this can be useful.

---

