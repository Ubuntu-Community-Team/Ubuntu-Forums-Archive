---
title: "I can´t open a .jar file by double clicking it, only using the terminal."
date: 2021-07-18
forum: New to Ubuntu
---

### Post by andyfc3 on 2021-07-18
I am running a POS software on Ubuntu 20.04 called ORO POS for my restaurant that runs on Java. I have successfully installed the recommended Oracle Java 8 in order to run the software. Everything works fine except I can only open the software using the java -jar filename.jar command in the terminal. I would really like to be able to create a menu item with the file so the staff can open the software by clicking on an icon instead of using the terminal. I have already checked the box for execute file as program but still doesn't work. Also, there is no Java option in the Open With options. I have tested the java version and it is correctly installed. I have no clue what I am doing wrong, I have successfully created menu items for .jar files before with no issues (using OpenJDK).

---

### Post by Holger_Gehrke on 2021-07-18
I don't know about Oracle Java, but OpenJDK comes with .desktop files that produce context-menu entries on .jar-files like "open with 'Open-JDK Java 8 Runtime'". I haven't used the 'official' branded versions of Java since years before Sun was bought by Oracle.

Getting your program into the Activities menu is not really difficult. Just write a .desktop file for it and put it either into '~/.local/share/applications/' for a specific user ('~' is a short-hand for the home directory of a user; the directory '.local' is hidden in the shell and in file managers to avoid cluttering up the file listings with configuration files you usually don't want to see; to show hidden files in the file manager hit 'ctrl-h') or into /usr/local/share/applications/ for all users. A .desktop-file is a short text file which tells your system what name and icon to show for the program and what executable to run to start it. It looks like this:

```

[Desktop Entry]
Name=ORO POS
GenericName=Point of Sales
Exec=java -jar **/path/to/the/jar/file.jar**
Icon=**/path/to/an/image/to/use/as/the/icon.png**
Terminal=false
Type=Application
Categories=Office;Java
Path=**/working/directory/for/your/program/**
StartupNotify=true

```

Cut and paste this into an editor, replace the bold parts as needed, save as oropos.desktop, and move it into either of the directories I mentioned above. Further details on desktop files can be found [here]("https://specifications.freedesktop.org/desktop-entry-spec/latest/").

Holger

---

### Post by andyfc3 on 2021-07-19
Holger:

Thank you so much for the quick reply, I got it to work and man, that was way too easy. At first, when I started the application I got a database error but after restarting the computer everything went back to normal. It´s cool to have such a helpful community around this OS, I haven´t been using Ubuntu for the last few years but got back on it recently and this makes me realize I really miss it. Anyways, I appreciate all the help.

Thanks again,
Andy

---

### Post by ActionParsnip on 2021-07-21
Please mark as solved if the issue is resolved

---

