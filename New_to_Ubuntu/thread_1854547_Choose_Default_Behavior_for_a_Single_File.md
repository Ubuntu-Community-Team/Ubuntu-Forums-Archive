---
title: "Choose Default Behavior for a Single File"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by mkhaytman on 2011-10-04
Hello again ubuntu gurus!

I am running ubuntu 10.04.

I have installed Mozilla Sunbird calendar program, and have made a symbolic link to the executable file on my desktop. Every time I double click it, it gives me the option of "run in terminal", "display", "Cancel" or "Run".

How can I set it up so that Ubuntu automatically Runs this one file? Not all files of this type, but just this one file.

I should also mention that I would like to configure this from the command line rather than through the GUI. 

Hope that was clear, I await your gracious responses. Thank you in advance!

---

### Post by audiomick on 2011-10-04
I don't think you can specify a behaviour for one specific file. I think the characteristics mechanism can only be applied  to all files of the type.

Why don't you make a starter for it? Right click on the panel, add starter, and point it at your executable file. I think you can add a starter to the desktop too, but I am not sure of that.

---

### Post by mkhaytman on 2011-10-05
If the starter will just run the program without prompting, that is an acceptable solution. 
I would have to be able to create the starter from command line, is that possible?

---

### Post by audiomick on 2011-10-05
> **mkhaytman said:**
> I would have to be able to create the starter from command line, is that possible?
I'm afraid I don't know. I imagine that if one know where the appropriate config files were that it would be possible, but I have no idea where they might be.

Why can you not do this using the GUI tools?

---

### Post by mcduck on 2011-10-06
> **mkhaytman said:**
> If the starter will just run the program without prompting, that is an acceptable solution. 
I would have to be able to create the starter from command line, is that possible?

Yes, you can create one from CLI, if you really want to. The launchers used by Linux desktops are simple text-based configuration files.

The easiest way to create one from CLI is to copy one of the .desktop files from /usr/share/applications, and then modify it using whichever CLI text editor you prefer.

---

### Post by philinux on 2011-10-06
> **mkhaytman said:**
> Hello again ubuntu gurus!

I am running ubuntu 10.04.

I have installed Mozilla Sunbird calendar program, and have made a symbolic link to the executable file on my desktop. Every time I double click it, it gives me the option of "run in terminal", "display", "Cancel" or "Run".

How can I set it up so that Ubuntu automatically Runs this one file? Not all files of this type, but just this one file.

I should also mention that I would like to configure this from the command line rather than through the GUI. 

Hope that was clear, I await your gracious responses. Thank you in advance!

Have you considered adding sunbird to the top panel as a one click launcher.
From the menus right click and choose Add to Panel.

---

