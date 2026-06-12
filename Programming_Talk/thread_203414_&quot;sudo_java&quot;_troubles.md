---
title: "&quot;sudo java&quot; troubles"
date: 2006-06-25
forum: Programming Talk
---

### Post by ubuntuuser on 2006-06-25
Hello everybody,

I am forced to test certain jar-files as root. To do that, I type ```
 sudo java -jar Simcap.jar
``` Strangely, I get the following error message: ```
sudo: java: command not found
``` This is pretty weird, because when I become root using "su" and type the same command w/o sudo, it works flawlessly. But still, even as root, when I run the command with sudo I get that message.

Where do I have to set the path for sudo?

---

### Post by Stromham on 2006-06-25
you need to navigate to the bin/binary folder in the java sdk, java cannot find the command because your not in  the commands root dir. ex. jar.exe is located in java sdk's bin folder, you must be in the bin folder to use the command.

---

### Post by Stromham on 2006-06-25
or you may not be able to use the command with sudo.

---

### Post by ubuntuuser on 2006-06-25
I'm sorry, but I don't understand your answer. I can do ```
sudo apt-get
``` for example without being in the /usr/bin directory, because I have /usr/bin in my PATH variable. I also have /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin in PATH (in the first place), so why can't I do ```
sudo java
``` Even if I do not use the -jar parameter I am still told that the command was not found. The java dir is in my PATH as well as in root's PATH.

---

### Post by Stromham on 2006-06-25
maybe you just cannot use sudo with java commands??

---

### Post by kunnk on 2006-06-26
[QUOTE=Stromham]maybe you just cannot use sudo with java commands??[/QUOTE]

"just cannot" is not a good answer, there must be reason why it does not work.

In my computer sudo java works fine. Maybe ubuntuuser should check, is java in root user PATH or not.

---

### Post by ubuntuuser on 2006-06-26
The internet is full of examples where users are supposed to use "sudo java something". I also thougth about a path issue, but my regular user and root have exactly the same PATH variable set. The java dir is always the first dir in PATH.

---

### Post by bieber on 2006-06-26
You could try making a link to the executable and putting it in the root of the /usr/bin directory as just "java."  Or, if you wanted, try sudo su and then just type your command.

---

### Post by ubuntuuser on 2006-06-26
Ok, I found the solution. There was a soft link called java in /usr/bin, but I didn't bother at first to look where it linked to. Well, the link was wrong, so I created a new one to the correct "java" binary, now it works.

---

### Post by santiagozky on 2006-06-26
isnt it better to add the java bin directory to root's PATH ?

---

### Post by ubuntuuser on 2006-06-26
[quote=santiagozky]isnt it better to add the java bin directory to root's PATH ?[/quote]
I have the java dir in root's PATH, but it didn't work because of some reason I don't understand. After fixing the link in /usr/bin it works.

---

