---
title: "How To: Compile and Install the Scizzor Plugin for the XMMS Multimedia Player"
date: 2009-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by DustStuff on 2009-10-04
The contents of this tutorial are based on my experience with the **xmms** package downloaded and installed from _**[Knut Grythe's handy repository]("http://www.pvv.ntnu.no/%7Eknuta/xmms/")**_ and the **scizzor** plugin package (scizzor-1.3.3.tar.gz) from _**[SourceForge]("http://scizzor.sourceforge.net/")**_, which adds pitch and speed control sliders to **xmms**. While this tutorial is written specifically for an Ubuntu-based system, I'm assuming it would be useful for users running other Linux distros as well, although some of the specifics would probably need to be adjusted.

The system I was working on is a minimal install of Xubuntu 9.04 (on i386 architecture). Xubuntu is similar to Ubuntu, but uses the **xfce** desktop along with some other variations to give it a smaller memory footprint, which is nice when working with older hardware. What I mean by 'minimal install' is that I used an alternative CD to install a command-line-only system, and then added the 4-5 basic packages needed to be able to log in to the default **xfce** desktop. Since then, I have simply installed packages as needed.

In my own experience and in my searches on the web, it seems that the main reason for problems users face in trying to compile the **scizzor** plugin is that they do not have the necessary packages installed on their system. Here is the list of packages that were necessary for me to install before I could compile this plugin for **xmms**:
  
[LIST=1]
[*]**make** 	– The GNU version of the 'make' utility. It is likely that a 	default install of Ubuntu 9.04 will already have this installed.
[*]**gcc** 	– GNU C Compiler. This installs an additional 4 packages it is 	dependent on.
[*]**libgtk1.2-dev** 	– Development files for the GIMP toolkit. This installs an 	additional 13 packages it is dependent on.
[*]**libglib1.2-dev** 	– The GLib library of C routines (development). This installs one 	additional package it is dependent on.
[/LIST]
      To check whether you have these packages and/or install them you can use Synaptic Package Manager ('System > Administration > Synaptic Package Manager' in the desktop menu of Ubuntu 9.04) and it's search capabilities. For some reason, packages #3 and #4 above didn't show up for me when using the 'Quick Search' function, but did show up once I used the regular search function. Or if you prefer to use the terminal, you can use **apt-get**. For example, if you want to install package #3 above, open a terminal window ('Applications > Accessories > Terminal') and type the following at the prompt:
```
sudo apt-get install libgtk1.2-dev
```
     **Note:** If you think you may want to uninstall some or all of these packages, you may want to make a note of the names of the additional packages installed with the four listed above. Then you can use Synaptic or **apt-get** to uninstall them if you need to.

Once the above packages have all been installed, you should be able to successfully compile and install the **scizzor** plugin for **xmms**. Following is a step-by-step example of how to do that, assuming that the downloaded plugin file (scizzor-1.3.3.tar.gz) is placed in a directory named **xmms-scizzor** in the home directory (in Ubuntu 9.04's default file browser, this may be called 'Home Folder' or may be named with your user name, depending on what view you're using). Please note that if you use a different directory or directory location, you will need to adjust the terminal code examples accordingly in order to get it to work.

**Step 1:** Unzip/decompress the **scizzor-1.3.3.tar.gz** file:
```
tar -xzf xmms-scizzor/scizzor-1.3.3.tar.gz
```
 **Note: If you do not understand what the terminal commands included in this tutorial mean and what they do, it will be worth your time and effort to educate yourself, preferably before executing them.**
                                      The result of this first step is that a directory named **scizzor** is created in the home directory, with a number of files in it that will be used in the compiling process.

**Step 2:** Go to the newly-created **scizzor** directory:
```
cd scizzor
```

**Step 3:** Compile the **scizzor** plugin for **xmms**:
```
make xmms
```
This will create three new files in the **scizzor** directory. The one you're interested in is called **scizzor-xmms.so**, which is the actual plugin.

**Step 4:** Copy the plugin to the directory where **xmms** expects to find it:
```
cp scizzor-xmms.so ~/.xmms/Plugins/
```

**Step 5:** Check that the plugin was successfully installed by opening **xmms** and going to 'Options > Preferences > Effects Plugins' to see if it is listed there. Once it's enabled there, then it should open each time you open **xmms**.

**Step 6 (optional):** Do some basic cleanup:
```
make clean
```
This simply deletes the three files that were created in Step 3. You may also want to do some further cleanup of your home directory to avoid clutter, either by deleting files related to this installation that you no longer want, or by moving them to another location. The main advantage of having them in the home directory during the compilation/installation process is that the terminal commands are simpler/shorter, leaving less chance for errors.

**To Uninstall:** If you ever wish to uninstall this plugin, I think all you need to do is delete the plugin file from **xmms's** plugin directory. This can be done in the terminal in the following way:

**Step 1:** Go to the **.xmms/Plugins** directory, where the plugin is stored:
```
cd ~/.xmms/Plugins
```

**Step 2:** Check the contents of the directory to make sure you're in the right one and that the plugin you want to delete is there:
```
dir
```
This will give you a list of the files in the directory, one of which should be the **scizzor-xmms.so** plugin file.

**Step 3:** Delete the plugin file:
```
rm scizzor-xmms.so
```
If no error is given, then the file was probably deleted, but if you want to make sure you can do Step 2 again.

[B]Some notes for more advanced users or those interested in the inner workings of the above compilation process:

[/B]The **Makefile** file included in this package also has a **make install** command option that runs a Perl script. When I ran this, it tried to install the compiled plugin to the /usr/lib/xmms/Effect/ directory, but a 'permission denied' error was returned. So presumably, those with the scripting/programming ability would be able to make the necessary adjustments to the Perl script or other parts of this overall package to make this command work for them. But to me, the copy process in Step 4 works fine; the main thing that needs to be figured out first is where the **xmms** plugins are stored on whatever Linux distro is being used. I'm assuming that a binary install file could also be made from this package if anyone was interested in that kind of project.

It may also be interesting to some that on my system the following warning was returned after running the first 'gcc' command string (of **make xmms**) in the **Makefile** file:

scizzor.c: In function 'scizzor_write_audio':
           scizzor.c:508: warning: ignoring return value of 'write', declared with attribute warn_unused_result

I really have no idea what this warning means, but as far as I was able to tell it didn't impact the successful installation and functioning of the plugin.

[B]Acknowledgements:
[/B]--The final post by **vicarious** in _**[this thread]("http://ubuntuforums.org/showthread.php?t=159335")**_ gave me some good initial ideas for coming up with the information in this tutorial. This may also be a good resource for anyone trying to compile and install this plugin for **beep-media-player**, although I have not tested it myself.
--A comment by **word-virus** in _**[the post here]("http://ubuntuforums.org/showthread.php?t=38119&highlight=xmms+scizzor")**_ got me on the trail of packages #3 and #4 listed above, which are development libraries required by **xmms**.

**Caveat:** I began using Linux/Ubuntu/Xubuntu in April 2009, so I am a relative newcomer to this part of the computing world. Also, I have no experience with computer programming and very little experience with scripting. So if you are a beginning user yourself, please take whatever precautions you feel are necessary to verify that following this tutorial will do what you want it to and will not mess up your system. And to all users, beginning or more advanced, I welcome any comments or suggestions you might have about how this tutorial could be made more user-friendly and/or more accurate.

**Support:** I plan to monitor this thread in order to keep track of any replies received. I'll do my best to answer any questions or help solve problems that people have with this tutorial, as well as make necessary changes to the tutorial itself. If anything is clearly beyond my own ability to solve, I will do my best to point users to possible sources for a solution.

---

