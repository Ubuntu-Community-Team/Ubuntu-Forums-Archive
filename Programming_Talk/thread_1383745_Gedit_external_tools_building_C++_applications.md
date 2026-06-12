---
title: "Gedit external tools building C++ applications"
date: 2010-01-17
forum: Programming Talk
---

### Post by jc4gavejc on 2010-01-17
How do I implement in gedit's external tools manager a tool that will compile all the cpp files in the current working directory, link them, and then execute the application?

I am a very new programmer, and an even newer Linux programmer, so keep that in mind when answering. Thanks very much!

Josh

---

### Post by Senesence on 2010-01-17
> **jc4gavejc said:**
> How do I implement in gedit's external tools manager a tool that will compile all the cpp files in the current working directory, link them, and then execute the application?

I am a very new programmer, and an even newer Linux programmer, so keep that in mind when answering. Thanks very much!

Josh

Hmm, I'm not sure about the "external tools" for gedit specifically, but you can open all .cpp files in gedit from your terminal; just cd into your project directory (with all the .cpp files) and run this command:

```
gedit *.cpp
```

Gedit should pop-up, and all your .cpp files will be open in tabs.

For actually building your project, you can use make files, or (even easier) use cmake to generate make files.

---

### Post by not_a_phd on 2010-01-17
I think the key thing is to have a makefile in the working directory. You can enable integration with external build tools in gedit through the main menu: Edit | Preferences | Plugins | External Tools. With External Tools checked and selected, Configure Plugin allows you to edit scripts associated with the build command. But, it should come already configured to build when you push F8. It will run the makefile in the directory you are in.

It is ok for rudimentary developing without an IDE. But, I would recommend you investigate Geany or Eclipse if you feel you need an IDE for your development.

---

### Post by jc4gavejc on 2010-01-17
Thank you so much!

I was able to use your advise to set up a script attached to the shortcut key [CTRL + F5] (same as in Visual Studio), and it compiles all the cpp files, links them to an output file which carries the name of the tab I had open at the time. Works just like Visual Studio on Windows! You need to install a package called gedit-plugins, so
```
sudo apt-get install gedit-plugins
```

Then open gedit => Edit => Preferences => Plugins => External Tools

See to it that the option to enable external tools is checked, then go into its configuration.

Add a "tool" and in the "Edit" box enter:

```

g++ *.cpp -o ${GEDIT_CURRENT_DOCUMENT_NAME%.*}
./${GEDIT_CURRENT_DOCUMENT_NAME%.*}

```

Then assign whatever shortcut key you want.

Thanks again for the help with that!

Josh

---

### Post by Aleksandar_B on 2011-03-02
Thanks for this great tip. Since I'm starting to work in C++ and also wanted a simple editor this comes as a great solution.

However, I would need the command to compile only the document I'm currently working on, not all documents in the current folder, is there a way to achieve this?

EDIT:
Found an answer on another thread: [http://ubuntuforums.org/showthread.php?t=784979](http://ubuntuforums.org/showthread.php?t=784979)

---

