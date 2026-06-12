---
title: "Still lost on downloads Libre Office Add ons."
date: 2012-06-27
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-06-27
Clicking the extension and downloading they go to firefox download. Then if I open and extract everything ends up in the home folder. BUT how do I get the files to add into Libre Office? I guess I need to know where and how I find the windows equivalent of .exe. I have looked in vain for .deb.

In a nutshell (and some of these only in Open Office repository,) 


[LIST]
[*]Writer2epub (have files)
[*]Readability
[*]Writer's Tools
[/LIST]
The add ons in the download have no appeared. However I don't actually need them.


This is frustrating as I am trying to write and to edit.


If all else fails can I safely download Open Office or will that give me the same problem?


Also need the thing to make the pages larger or smaller that WAS in my windows version (as were all of the above.)


Thanks for any help. I do know now how to open the terminal. I am still not sure what to do with it.

Using Acer 6930g with Ubuntu 12.4 and the original desktop (at the moment.)



J

---

### Post by jmfal on 2012-06-27
Do the files have a period in front of the file name===   .conkyrc, or  .bashrc
if it does it is executable.

does the web site say to make them executable.
You should be able to left click on the file to highlight it then right cllick and a menu with some options will popup "make executable" should be there >>click on it,, or

You should be able to install Open Office from synaptic.

---

### Post by drmrgd on 2012-06-27
I think you just need to use the extensions manager to import the .oxt files.  For example, the Writer2ePub instructions say:

> Installation
Just double click on the dowloaded file, it will install or replace the old W2E version.
Otherwise, please open the Extension Manager from the Tools menu and add the extension from there.
Once installed, on opening a new writer document you will find a small toolbar with three green icons.

I haven't tried to do this, but it seems you simply have to navigate to those files from the Open Office Extensions Manager and follow from there.

---

### Post by Jackalyn on 2012-06-27
> **drmrgd said:**
> I think you just need to use the extensions manager to import the .oxt files.  For example, the Writer2ePub instructions say:

[COLOR=Purple]Yes that is what I TRIED to do! That is my problem. It does not work to do that. I know the process as I did it a lot in Windows. It just does not work in Libre in Ubuntu.[/COLOR]



I haven't tried to do this, but it seems you simply have to navigate to those files from the Open Office Extensions Manager and follow from there.


I would if I could....

---

### Post by Jackalyn on 2012-06-27
> **jmfal said:**
> Do the files have a period in front of the file name===   .conkyrc, or  .bashrc
if it does it is executable.

does the web site say to make them executable.
You should be able to left click on the file to highlight it then right cllick and a menu with some options will popup "make executable" should be there >>click on it,, or

[COLOR=Purple]No they don't have that ending.....I have been right clicking but found nothing that says "make executable."[/COLOR] [COLOR=Magenta]However at least I now know what an executable file is labelled as to be able to recognise it.[/COLOR]

You should be able to install Open Office from synaptic.

[COLOR=Purple]Please can you explain what synaptic is.
 I could happily use both....
[/COLOR]

---

### Post by jmfal on 2012-06-27
The synaptic package manager is like the software center  but it offers more info on the apps and version numbers , repositories .............

Open a terminal and enter
```
 sudo apt-get synaptic     
```

enter your password (you will not see it)>> press enter

to open synaptic enter
 ```
 synaptic    
```
in a terminal and press enter

---

