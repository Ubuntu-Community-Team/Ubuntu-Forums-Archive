---
title: "How to get kylix to run"
date: 2006-05-17
forum: Programming Talk
---

### Post by JNowka on 2006-05-17
Ok for the past week i have been trying to get kylix to run there have been several things I have found to work that may or may not be found elsewhere on this forum.  I felt that this would make a good topic to have for others to maybe help them get kylix to work for them on ubuntu.

In the following I am assuming you had successful kylix install to the default options, have root access, how to use gui, and know basic commands such as how to copy and change directorys using the terminal.

Assume everything I say to do is done in the terminal and I will specify when its done else where. 

When you downloaded Kylix from borland.com you recieved an email from them, it has and attachment that you will have to save in both your "/home/<username>" directory and the "/root" directory. 

You can copy it to your "/home/<username>" directory without problem using a GUI file browser but will need to copy it to have root access to copy it to "/root" I don't know why but delphi looks in your home directory while I have experienced c++ looking in my root directory while just using sudo.

Next you will need to goto /usr/local/kylix3/bin

I am assuming Gnome, if you have KDE use your default text editor for the following.

Just in case we make a mistake type "sudo cp startdelphi startdelphi_backup"

type "sudo gedit startdelphi" and this will bring up a gui screen with text in it.
you will need to change some text. 

You will need to replace the first part of the file with the following.

#!/bin/bash

# BEGIN STRING TABLE
export LD_ASSUME_KERNEL=2.4
LANG=en_US.ISO8859-1
KYDEF_LOCALE="en_US"
LC_ALL_IS_C1="The LC_ALL environment variable is set to C. Kylix cannot start with this setting."
LC_ALL_IS_C2="Defaulting LC_ALL to"

# END STRING TABLE

Go no farther than the "# END STRING TABLE" or you may make kylix inoperable for delphi.

Save the file and exit.

Just in case we make a mistake type "sudo cp startbcb startbcb_backup"

Next type "sudo gedit startbcb"

Another Gui with similar text appers.

Follow the directions for changing startdelphi again with startbcb.

Save it and exit.

Now change the directory you are in to "/root/.borland"

Type "sudo cp bcb69rc bcb69rc_backup"

Type "sudo gedit bcb69rc"

Scroll down to [Known Packages] and look for references to SOAP and dbExpress.

They should be called dclsoap.so.6.9 and dcldbdbx.so.6.9 and remove them from the file.

Save and Exit

If at any time you need SOAP or dbExpress in C++ you will need to use Component -> Install Packages from the menubar and install it.  Remember to remove them before exiting or you will be unable to use C++.  If you do accidentally do that just follow the instructions for editing the bcb69rc file and you should be able to use c++ again.

In order to run delphi you will need to use either "sudo startdelphi" or "sudo startbcb" recpectively

They may still hang when used, but you will be able to get them started and running.

If something doesn't work, or if you know something I don't about Kylix let us know.

---

