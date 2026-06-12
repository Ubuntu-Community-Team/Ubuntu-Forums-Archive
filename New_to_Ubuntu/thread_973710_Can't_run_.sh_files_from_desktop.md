---
title: "Can't run .sh files from desktop"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Gennn89 on 2008-11-06
Hey trying to run a shell or executable file (in this case install-crossover-pro-7.1.0.sh) and when i double click to make it run it gives me 
"Could not open the file /home/noah/Desktop/install-crossover-pro-7.1.0.sh."
and 
"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."
then it gives me a character coding option for current locale utf something rather.
what do i need to do to fix these errors because ive been getting a few
is there a certain command i need to run in the terminal? i think i got my friend to type some sort of gibberish that i cant remember that gave access to execute the files but i dont remember 
please if you know how fix this let me know!

---

### Post by randy78 on 2008-11-06
Right click on the file>Properties>Permissions>Check Allow executing file as program

---

### Post by deanjm1963 on 2008-11-06
Open a terminal window and type

sh /home/noah/Desktop/install-crossover-pro-7.1.0.sh

that should get it started for you ...

hope this helps

---

### Post by kdcoetzee on 2008-11-07
Yes, 

open up those files in a terminal.

```

cd Desktop

```

```

./install-crossover-pro-7.1.0.sh

```

this will only work if the file is a executable.
if it is not. 

```

chmod +x Desktop/install-crossover-pro-7.1.0.sh

```

---

### Post by Gennn89 on 2008-11-07
thanks guys those both were very helpful i appreciate it :D it sucks being a noob on linux lol

---

### Post by kdcoetzee on 2008-11-07
its just a matter of time and effort. then Linux is easer that Windows. because of community, logs "tail -f /var/log/messages" , and tools.

---

### Post by randy78 on 2008-11-07
Cool... Check out these sites: [http://ubuntuguide.org/wiki/Ubuntu:Intrepid]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid")
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

---

### Post by kdcoetzee on 2008-11-07
[http://www.psychocats.net/]("http://www.psychocats.net/")

And if you want to go a level up.

[http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html]("http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html")

[http://en.wikibooks.org/wiki/Bourne_Shell_Scripting]("http://en.wikibooks.org/wiki/Bourne_Shell_Scripting")

---

