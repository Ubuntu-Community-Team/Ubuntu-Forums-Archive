---
title: "Compiling and running straight from Gedit"
date: 2007-01-02
forum: Programming Talk
---

### Post by ephesius on 2007-01-02
I do most of my c++ coding in Gedit. I know there are certain plugins for it that allow you to do different things....is there a way to compile and run the program straight from gedit? I.e. without having to open terminal and g++ filename.cpp and then run it.

---

### Post by Wybiral on 2007-01-02
Thats a great idea... If there isn't a plugin someone should make one.

---

### Post by ephesius on 2007-01-02
There is a plugin called external tools which lets you add commands to run but I don't know how to go about using it for compiling. There is an entry for make already in it but I dont know how to set it to compile and run as well. I'll try to figure it out maybe by doing g++ $filename or something like that.

I tried it but I cant figure out what the variable for filename is in gedit. Otherwise it seems like the external tools plugin will work wonderfully.

---

### Post by phossal on 2007-01-02
Once you've downloaded the plugins package, and enabled the External Tools plugin, configure it.

For example, you could edit the "Build" tool, or create a new one. The "command" line should read  (edit as necessary):

```

gcc $GEDIT_CURRENT_DOCUMENT_NAME

```

There are other variables. Google them. 

$GEDIT_CURRENT_DOCUMENT_URI
$GEDIT_CURRENT_DOCUMENT_NAME
$GEDIT_CURRENT_DOCUMENT_SCHEME
$GEDIT_CURRENT_DOCUMENT_PATH
$GEDIT_CURRENT_DOCUMENT_DIR
$GEDIT_DOCUMENTS_URI
$GEDIT_DOCUMENTS_PATH

If you're programming in C++, you can (con)figure out the rest. ;)


As an example, with plugin downloaded and enabled, I went to Tools -> External Tools
I selected "Build" in the Tools column, I left the accelerator F8. I changed the command to:

```
gcc -ofileName $GEDIT_CURRENT_DOCUMENT_NAME
```

Input: nothing
Output: Insert into output panel
Applicability: All Documents.

I also enabled the output and terminal plugins so that I can execute commands too.

---

### Post by ephesius on 2007-01-02
I figured it out that far...how would you get the run command to launch in some kind of pop up window so commands can be input and do you know the variable for the filename minus the extension.

---

### Post by ephesius on 2007-01-02
One other question how did you enable those other plugins...I dont seem to have them.

---

### Post by Engnome on 2007-01-02
> **ephesius said:**
> One other question how did you enable those other plugins...I dont seem to have them.

```
sudo apt-get install gedit-plugins
```

Then Edit -> preferences -> plugins.

---

