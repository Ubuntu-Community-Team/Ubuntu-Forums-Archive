---
title: "Cannot open .jar files"
date: 2018-09-07
forum: New to Ubuntu
---

### Post by milos.sarenac on 2018-09-07
Hello,
I cannot open .jer file. It says that file is not trusted and its not executable. I installed java oracle and i tried with openJDK. I even tried to go to properties and put file as executable but when i do that its just like i didnt click it at all cause nothing happen (not even that "not executable" pop up).
Programs is made by my friend on Apple lap top for some work. Can that be an issue or am i just doing something wrong? Please help :(

---

### Post by Frogs Hair on 2018-09-07
Hello and Welcome

Try setting the file manager to run executable files in preferences>behavior.

---

### Post by milos.sarenac on 2018-09-07
Thank you for answer and help but nothing changed. It is still the same..

---

### Post by Frogs Hair on 2018-09-07
Right click and check the open with options. Beyond that search for similar problems on the web and wait for a user with .jar experience.

---

### Post by milos.sarenac on 2018-09-07
Already tried with that option. Thank you for helping. I ll search and wait :)

---

### Post by Frogs Hair on 2018-09-07
Being that .jar files have different uses you could add what context they are being used in.

---

### Post by milos.sarenac on 2018-09-07
Program is made to pull JSON file from one website. In the JSON file are lists of some people (contestants) that program needs to shuffle in specific categories and groups (that job i do manually in program cause judges need to see it). So its nothing complicated. There is few buttons and few pics with that buttons. At the end program create similar JSON file that i need to use for other stuff. Thats all that what is it doing

---

### Post by Impavidus on 2018-09-07
I don't know about .jar files. I guess they may have to be executable. Have you stored them on a partition that allows to set execute permissions? If the .jar files are stored on some ntfs or fat partition, you cannot set execute permissions because those file systems don't support Unix-style permissions. If the partition is mounted with the noexec option, you can't execute programs either.

---

### Post by milos.sarenac on 2018-09-07
It is in downloads cause i downloaded it from mozzila if you mean on that. I did go to Properties>Permission and put it "Allow executing files as programs" but with that nothing happend, not even that warning message i get..

---

### Post by Holger_Gehrke on 2018-09-07
Run the jar from the command line with 'java -jar full-path-and-filename-goes-here'. Even if it doesn't work, the output should give you an idea about what's wrong.

Holger

---

### Post by milos.sarenac on 2018-09-07
Thanks for help, unfortunately i already tried that, even with "sudo java -jar full_name.jar" there was space in name so i putted "_" i even deleted space and tried without and every time it says "Error: Unable to access jarfile File_Name.jar"

Disclaimer: i did put actual name instead of File_name just to be clear :)

---

### Post by ajgreeny on 2018-09-07
You have not said if this is a new problem for you that has recently started occurring or has been present always.

There is a bug [https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250](https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250) which gives a workaround at post #4 that works for me using Xubuntu 18.04, though others have said it did not work in Ubuntu 18.04.  This bug was apparently overcome by using Oracle java in place of openjdk-11-jre but you say you have already tried that
Try out the post #4 workaround from the bug report; it may be successful for you.

---

### Post by Holger_Gehrke on 2018-09-07
'Unable to access" is the Java error message for - among other, worse things - "file not found". Is the directory with the jar-file your current working directory ? If the prompt is "user@machine:~$" (replacing user and machine with your username and the name of your computer), then you are in your home directory and you can either change the working directory with 'cd directory-name' (you'll see that the part of the prompt after the colon changes) or give the directory name with the name of the jar (example: java -jar Downloads/"File Name.jar" {and that's one way of handling file names with spaces: put them in quotes}).

Holger

---

### Post by milos.sarenac on 2018-09-07
I am tottaly new. I first time trying Ubuntu (18.04). I tried openjdk 8-11 and none worked.. I didnt quite understand you. What is post #4 workaround from the but report. I am really new to all of this so sorry for stupid questions..


This is the massage that appear when i disable "Allow executing file as program"

[IMG]http://i68.tinypic.com/v5eru0.png[/IMG]

I did try now with " " instead of  _ and changing directory but still same thing. PS: Ty for tip with quotes very useful for future :)

---

### Post by Geoffrey_Arndt on 2018-09-07
Can you post a screen shot of the actual folder the file is in, then another screen shot of the right-click menu for each tab for that specific file?

---

### Post by Holger_Gehrke on 2018-09-08
Let's try the command line again, now that I can see the path to your jar-file in your screenshot of the error message. Open a terminal and try:
```
java -jar "/home/milos/Downloads/v1.0 ZREBANJE/v1.0 ZREBANJE/JSS Zrebanje.jar"
```To reduce typing and the risk of typing errors use command completion with the tabulator key. Command completion fills in the rest of file and directory names if the part you typed is enough to identify a file. What you would actually type of that long path is something like /ho<tab>mi<tab>Dow<tab>v1<tab>v1<tab>JSS<tab>. This should at least give us a new error instead of 'unable to access" ...

Another idea: jar files are actually zip files full of java classes and the resources the program needs with a manifest file in META-INF/MANIFEST.MF telling the Java run time which class to start. Use the Archive Manager to check the integrity of the jar file. A broken jar doesn't run ...

Holger

---

### Post by milos.sarenac on 2018-09-09
I just think program isnt made for ubuntu or have something other problem with it.. None of solutions worked and thats very strange..

---

