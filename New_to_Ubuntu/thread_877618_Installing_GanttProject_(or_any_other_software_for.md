---
title: "Installing GanttProject (or any other software for that matter)"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Eikokubyo on 2008-08-02
Hey everybody. I just installed Xubuntu in a nice little laptop with no CD drive (worth the extra trouble for the decrease in weight and cost) and now I'm loading it up with all the software I'm going to need (this machine will be my planner/database/notekeeper/something to type my thoughts into on in the train). 

I have figured out how to add new software using the built-in function, but I'm afraid I'm a bit lost when it comes to installing things from the web. I don't know which file to double-click on to start the installation process, for example, so the files just sit there on my desktop and do nothing.

In addition, I'm trying to install GanttProject, and that happens to run on an extra Java layer, meaning that the installation process for that particular software will probably be completely different than usual for linux machines.

The GanttProject website has no instructions for installing the Linux versions, just the files themselves. Oddly, it has instructions for the Windows and Mac versions, which I would think would be more or less self-evident. 

Would anyone who has successfully installed GanttProject like to point a total newb in the right direction on this one?

Thanks,
Ei.

---

### Post by collinp on 2008-08-02
are the files mainly .c files?

---

### Post by mevets on 2008-08-02
I downloaded the app and it seems theres no installer in the archive they provide to Linux users. Its relativly easy to run the program though. Extract the ZIP archive > Navigate to the folder extracted > Right click ganttproject.sh > Properties > Allow executing file as program > Close > Double click ganttproject.sh > Hit Run

---

### Post by thedevnull on 2008-08-02
> **Eikokubyo said:**
> Hey everybody. I just installed Xubuntu in a nice little laptop with no CD drive (worth the extra trouble for the decrease in weight and cost) and now I'm loading it up with all the software I'm going to need (this machine will be my planner/database/notekeeper/something to type my thoughts into on in the train). 

I have figured out how to add new software using the built-in function, but I'm afraid I'm a bit lost when it comes to installing things from the web. I don't know which file to double-click on to start the installation process, for example, so the files just sit there on my desktop and do nothing.

In addition, I'm trying to install GanttProject, and that happens to run on an extra Java layer, meaning that the installation process for that particular software will probably be completely different than usual for linux machines.

The GanttProject website has no instructions for installing the Linux versions, just the files themselves. Oddly, it has instructions for the Windows and Mac versions, which I would think would be more or less self-evident. 

Would anyone who has successfully installed GanttProject like to point a total newb in the right direction on this one?

Thanks,
Ei.

Hey,

I assume you have the Java VM right?  If not, then install the xubuntu-restricted-extras.  If you have trouble with the command line google on how to use apt-get to get those packages installed.  Basically its sudo apt-get install package name.  =) 

To install GanttProject you need to [download the zip file here]("http://downloads.sourceforge.net/ganttproject/ganttproject-2.0.7.exe?modtime=1214191241&big_mirror=0") and then unzip it.  After you unzip it go into the command line and cd into that directory you put it in (usually a subdirectory of your home directory) and then run ganttproject.sh  If you want it to add these elements to the GUI you should check out [http://ubuntu-tutorials.com/2008/07/10/edit-the-applications-menu-with-two-clicks-ubuntu-804/](http://ubuntu-tutorials.com/2008/07/10/edit-the-applications-menu-with-two-clicks-ubuntu-804/)

Oh, and happy project management! :guitar:

---

### Post by Eikokubyo on 2008-08-04
Awesome. Thanks a million guys. I have it totally up and running now.

---

