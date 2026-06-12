---
title: "[SOLVED] newbie question about javac"
date: 2008-02-15
forum: Programming Talk
---

### Post by plastichero on 2008-02-15
hello all in ubuntu world of programming. I'm a newcomer and hence facing childish problems. Need your urgent help to get pass it.

what I want to do
------------------------
install jdk manually (non-packaged way or without apt-get) and run a simple "hello world" program (just to get started)

I'm using Ubuntu 6.10 and running from LIVE cd.

What I did
--------------
1. downloaded [COLOR="DarkRed"]j2sdk-1_4_2_16-linux-i586.bin[/COLOR] on [COLOR="DarkRed"]/mnt/F/ubuntu/[/COLOR]

2. from a terminal, navigated to [COLOR="DarkRed"]/mnt/F/ubuntu[/COLOR]

3. ran "[COLOR="DarkRed"]sudo ./j2sdk-1_4_2_16-linux-i586.bin[/COLOR]" - then a new folder appeared named j2sdk1.4.2_16

4. ran these two commands- 
[COLOR="DarkRed"]"export JAVA_HOME=/mnt/F/ubuntu/j2sdk1.4.2_16"
"export PATH=$JAVA_HOME/bin:$PATH"[/COLOR]

5.then inside [COLOR="DarkRed"]/mnt/F/ubuntu/j2sdk1.4.2_16/bin [/COLOR] I created a file named "[COLOR="DarkRed"]HelloWorldApp.java[/COLOR]" containing these lines of coding:

[COLOR="Blue"]import java.io.*;
import java.util.*;

class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
}[/COLOR]

6. from the terminal tried to compile using:
[COLOR="DarkRed"]"sudo javac HelloWorldApp.java" (or, "javac HelloWorldApp.java")[/COLOR]

7. and got this error message:

[COLOR="Red"]Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object[/COLOR]

8. Now I'm quite at a loss ...**what to do? did I miss something during installation of JAVA or setting the PATH variable?**

*I'm using ubuntu 6.10 live on 256 MB ram, thats why cannot copy the installed java directory to /opt ... if I do so ... system becomes too slow.*

Can anyone please spend some of his minutes to help me out what to do step-by-step?

thnx in advance.

---

### Post by hod139 on 2008-02-15
I'm not sure why you want to install the jdk manually.  Using the package manager, it is very easy to install and set up Sun's java.
     ```
 sudo apt-get install sun-java6-jdk
```This will install the required packages, however, we now need to make Sun's java the default.
     ```
 sudo update-java-alternatives -s java-6-sun
```That will install and configure Sun's java on your system, and you will be able to use the javac command like you expect.


When compiling your application, do not use sudo.

---

### Post by plastichero on 2008-02-15
thanks for replying me ...
My internet speed here is very low (4-5 KBPs) and hence I cannot install it from net every time I run ubuntu live ..

any idea perhaps?

---

### Post by LaRoza on 2008-02-15
> **plastichero said:**
> thanks for replying me ...
My internet speed here is very low (4-5 KBPs) and hence I cannot install it from net every time I run ubuntu live ..

any idea perhaps?

Install Ubuntu?

---

### Post by mysticrider92 on 2008-02-15
I am not certain, but I think that error message is because the Java compiler does not look in the */bin folder, it looks in the folder it was run inside (probably /home/<user>/). Javac has a very odd way of telling you what the problem is...

And LaRoza is right, you could make a Ubuntu Live cd with the JDK on it (probably have to be a DVD), but installing Ubuntu properly would be a whole lot easier.

---

### Post by LaRoza on 2008-02-15
Also, it seems you have enough RAM to run Ubuntu live, and install Java on it. You probably have enough RAM to use a VirtualMachine.

It may take a while, but if you don't have to pay more, you can download VirtualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

If you are using Windows, install the Windows version, and install Ubuntu in VirtualBox.

---

### Post by plastichero on 2008-02-15
> **LaRoza said:**
> Install Ubuntu?
no no ... i meant installing java from internet

well ... I think there is no problem with finding the javac ...otherwise it would have said javac as unrecognized command. But why the VM error is shown??

---

### Post by mysticrider92 on 2008-02-15
> **plastichero said:**
> no no ... i meant installing java from internet

well ... I think there is no problem with finding the javac ...otherwise it would have said javac as unrecognized command. But why the VM error is shown??

I think it is telling you it can't find the source file that you specified. The compiler does not look in the */bin folder, it uses the folder it was run from. Try putting your .java file in your /home/<user> folder, then run the same command (it should work)..

Sorry I didn't say that right in my first post, I haven't been thinking quite right lately (been sick for a few days, too much cold/flu medicine...)

---

### Post by plastichero on 2008-02-15
> The compiler does not look in the */bin folder, it uses the folder it was run from

right now, i put the .java file inside the $my_javahome_directory/bin/ , navigated to the same folder i.e. $my_javahome_directory/bin/  and ran the command "javac HelloWorldApp.java" - but that didn't work out, same problem.

Do you suggest me to navigate back to /usr/bin/ and try to compile from there? I'll try that out and be back in few minutes ...

---

### Post by plastichero on 2008-02-15
nope  ... nothing seems to work for me :(

---

### Post by mysticrider92 on 2008-02-15
When you put the file in a special folder, you will need to use the cd command to get to it. This is not hard, but it is a lot quicker to leave it in your /home folder so you can easily compile it without switching folders.

Try putting the .java file in the /home/ubuntu (if you are on the live cd) folder. Now open a terminal and type 'ls'. The .java file should show up in the list. If it shows up, you can use javac to compile it. If not, the file is in the wrong place.

I see no reason to compile from /usr/bin, especially if you are testing a program.

Also, to test something, could you post the output of: > echo $my_javahome_directory
It sounds like you are possibly trying to run a file in a folder that does not exist (just a guess, but possible).

---

### Post by Shin_Gouki2501 on 2008-02-15
just for interest why u want to install the old 1.4 version?!

---

### Post by plastichero on 2008-02-15
Thanks for being with me :)

> **mysticrider92 said:**
> Try putting the .java file in the /home/ubuntu (if you are on the live cd) folder. Now open a terminal and type 'ls'. The .java file should show up in the list. If it shows up, you can use javac to compile it. If not, the file is in the wrong place.

yeah .. I tried it, didnt work. :(
I'm losing interest in ubuntu :(

> **mysticrider92 said:**
> Also, to test something, could you post the output of 
It sounds like you are possibly trying to run a file in a folder that does not exist (just a guess, but possible).

well ... I've written $my_javahome_directory to indicate /mnt/F/ubuntu/j2sdk1.4.2_16 - that means where I installed java.

---

### Post by LaRoza on 2008-02-15
> **plastichero said:**
> 
I'm losing interest in ubuntu :(
.

You haven't installed it yet, have you?

Install Java on Ubuntu is very easy, it is one command.

---

### Post by plastichero on 2008-02-15
no ..haven't done it yet :(
trying to resolve the problem ...
I guess I should try the jdk 1.6

---

### Post by Shin_Gouki2501 on 2008-02-16
i think there is a basic communication problem as i can think you can ran of java from the live cd but its not that easy.

---

### Post by LaRoza on 2008-02-16
> **Shin_Gouki2501 said:**
> i think there is a basic communication problem as i can think you can ran of java from the live cd but its not that easy.

Due to bandwidth issues, the OP cannot use the repository often.

You can install it, it would take a while at that speed.

It would make things easier to install Ubuntu then install Java.

---

### Post by plastichero on 2008-02-16
> **LaRoza said:**
> 
It would make things easier to install Ubuntu then install Java.

yeah .. I also plan to install ubuntu ... but I'm using windows in the same machine .... so I'm afraid that a misguided ubuntu installation may erase everything. I need to know more before going for the installation.

and ...still hanging out with same javac problem :confused:

---

### Post by LaRoza on 2008-02-16
> **plastichero said:**
> yeah .. I also plan to install ubuntu ... but I'm using windows in the same machine .... so I'm afraid that a misguided ubuntu installation may erase everything. I need to know more before going for the installation.

and ...still hanging out with same javac problem :confused:

For Dual Booting: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

If you have 1 GB of RAM or more: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by xlinuks on 2008-02-16
Well, first off you only have to set your $PATH variable for the system to find your "javac" compiler.
Nothing else.
Here comes the most interesting thing. As a rule of thumb - if you can install an application (in our case the "jdk") in a non-root dir, then do so.
Then, you have to find a nice place where you "work". That "nice place" would be ${HOME}/dev, in my case it's "/home/fox/dev/java", "/home/fox/dev/c++" and so on.

That's it. From now on you only use "batch files" to compile your files.
Here's what my ones look like (a batch file I called "jc" inside your {HOME}/bin folder):

```

#!/bin/sh
cd ${HOME}/dev/java/src
tput reset
javac -d ${HOME}/dev/java/bin xlinuks/*.java

```

To run your app (a batch file I called "ja" inside your {HOME}/bin folder):
```

#!/bin/sh
cd ${HOME}/dev/java/bin
tput reset
java -cp ${HOME}/dev/java/bin xlinuks.Main

```

"xlinuks.Main" means the main class called "Main.java" which is in a subpackage called "xlinuks" thus resides in ${HOME}/dev/java/src/xlinuks/Main.java
It's a good practice to keep the source files separated from your compiled classes.

You also MUST use a package otherwise it won't compile!! This is a new Java rule introduced since JDK 1.4.
In the example you use at the start of the thread you are not using a package. Keep it in mind..
If something remains unclear or doesn't come out feel free to PM me

---

### Post by plastichero on 2008-02-16
finally ... it worked! but in the same process that i described in my first post in this thread. strange! I got the "Hello World!" finally.

thnx everybody .. the link by LaRoza will be helpful surely.

(btw.. I downloaded jdk 1.6 (67MB) today and tried to install ...but it denied saying a corrupted file, though it was downloaded fine. I'll try it again later)

---

