---
title: "Post install script question"
date: 2011-02-01
forum: Packaging and Compiling Programs
---

### Post by skepticalgeek on 2011-02-01
I have developed an application, and successfully create a deb package for it. This application needs to have a directory in the user's home directory to store it's configuration and resource files. I added a post install script, that goes to the user's home directory, creates the sub-directory, and copies the needed files and sym links into it. The problem is, when installing the package, the system is acting as root, so the subdirectory gets created under /root instead of under /home/*username*. I use a cd command with no arguments as the first line of the script file, to get to the home directory. Any ideas as to how I can get the behavior I want?

Also, on an unrelated note, I am getting ready to release this soon, under my own website. What steps do I have to go through, so that my app shows up in the Ubuntu Software Center, when the user types music or jukebox (it is a jukebox app)?

---

### Post by gmargo on 2011-02-01
Package installation scripts have no business messing with user directories.  Stay away completely.

If your program needs some user-owned directories, then it should set them up when the user runs the program for the first time.

Question: In your scenario, if your program is installed as is, and then a new user is created, how does that user use your program?

---

### Post by skepticalgeek on 2011-02-01
Good question. I never though about this in terms of multiple users. When the app starts, it checks for the existence of its Config file. If it doesn't find it, a screen pops up asking the user to put in some data, such as where their music is located, normal or netbook screen, etc, and creates one. I'll put in some code there to create the directory if it does not exist. Thanks.

---

