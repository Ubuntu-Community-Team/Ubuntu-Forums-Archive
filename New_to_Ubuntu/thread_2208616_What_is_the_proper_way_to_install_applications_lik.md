---
title: "What is the proper way to install applications like a text editor?"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by robertzito on 2014-03-01
When you download an application like sublime text editor or any application that can run by just pressing on the file type "executable (application/x-executable)". What is the proper why to install it? I already created a desktop icon so I can run it from there, but should a global variable be set so you can run it from the command line in any directory? And if so what is the proper terminology so I can search on how to set the variable?

---

### Post by Lars Noodén on 2014-03-01
The best way is to look for the application in the repository using the Software Center or Synaptic.  The next best way is to look for it in a PPA and add that, then use the Software Center or Synaptic.  After that, the next best way is to look for a package (.deb) built for your version of Ubuntu on your type of hardware (AMD64 or i386 or PPC) and then install that.  

What type of file did you download and what does the site you got it from say about system requirments?

---

### Post by ibjsb4 on 2014-03-01
Im guessing you got sublime from here

[https://launchpad.net/~webupd8team/+archive/sublime-text-2?field.series_filter=precise](https://launchpad.net/~webupd8team/+archive/sublime-text-2?field.series_filter=precise)

So I installed it using the commands:

```
sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo apt-get update
sudo apt-get install sublime-text
```

On my desktop it created its own launcher in my menu.  What desktop are you running?

---

### Post by buzzingrobot on 2014-03-01
The key thing is that the application has been compiled and packaged for Ubuntu, and, usually, your specific release of Ubuntu.

The packages, which all have a '.deb' file extension, contain scripts and other material to ensure correct installation, including creation of icons.

If you find these packages in the official Ubuntu repositories -- where Software Center and Synaptic point -- you should be fine.

Other repositories can be added to the list that Software Center and Synaptic use.  The most common are the PPA's mentioned earlier. Care needs to be taken using them. They are not official. 

If, as is common in Windows, downloaded software is installed manually -- from something that is not a .deb package prepared for Ubuntu -- you have the responsibility for putting all the pieces in the right places, finding and installing any required dependencies, then their dependencies, etc.  The system that tracks software on your machine and handles updates will be unaware of those files, so you would need to update them manually.

Learn to use the Ubuntu repositories and all other software packaged for Ubuntu. Together with the update and dependency resolution capabilities, they provide a convenience that Windows cannot.

---

### Post by lykwydchykyn on 2014-03-01
If you have something that's a "ready to run" binary file in a tar or zip archive, it's kind of up to you where to put it.  I'd recommend this though:

- Copy the directory to /usr/local/share/myapplication (you'll need to do this as root or with sudo).
- Make a symlink to the executable file in /usr/local/bin/.  Try to launch the file by the executable name from a command prompt.  If you get a bunch of errors, it might be expecting to be in the actual directory, so I make a little script to cd to that directory and then launch the file.  
- Finally you can make a .desktop file that runs the executable.  If you want this to show up in regular menus and such, put the .desktop file in /usr/share/applications/

Of course, as others mentioned, it's better to get a .deb file when you can because all that stuff is typically done for you.

---

