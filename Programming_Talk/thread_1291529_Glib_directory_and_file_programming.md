---
title: "Glib directory and file programming"
date: 2009-10-14
forum: Programming Talk
---

### Post by addmoreice on 2009-10-14
Context:

C, Glib, Directory functions.

I'm programming a project framework that will be loading different modules depending on a configuration file. I'm trying to use the GKeyFile routines in Glib, I've got a line that roughly goes like this:

g_key_file_load_from_file(settingsfile, "/settings/plugins.cfg", flags, &error)

my problem is that my file 'plugins.cfg' is not being found. the error message in error->message is 'not a directory' which indicates to me that for whatever reason the directory I am reading is *not* the directory I started the program from + /settings/plugins.cfg. this makes sense as when i tried to load 'plugins.cfg' without the subfolder it did not work either (saying this was an unknown folder or directory). ok, so I understand my problem.

here is the issue. I need to make it so that the plugins.cfg file is in a directory 'settings' that will be in the default install directory which is different on each of the major platforms:

program files/'project name'/settings on windows
/home/'user name'/.'project name'/settings/plugins.cfg for linux (i think?)

and something else on mac osx i'm sure.

Here is my problem. I can't for the life of me determine 
1) where my default start directory is for my project on linux when i start it 
2) how to make sure i'm accessing the correct directory based on which version of the program i'm compiling for (oh please not ifdef's please oh please be utility functions in glib!). 

Finally basic directory/file handling tutorials for glib (i have a real issue with the documentation, tutorials would REALLY help).

I'm looking for any suggestions on 
1) smarter ways to solve this problem 
2) Tutorials on how to play with directories using glib (or some other cross platform library).

I'm not looking for a solution here just a hint of the right direction to travel.

---

