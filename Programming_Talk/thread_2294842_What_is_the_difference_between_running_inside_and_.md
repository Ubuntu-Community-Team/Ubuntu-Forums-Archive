---
title: "What is the difference between running inside and outside of bash?"
date: 2015-09-13
forum: Programming Talk
---

### Post by Kohn_Ywith on 2015-09-13
**(EDIT: Maybe this post is in the wrong section, it should be in [Ubuntu, Linux and OS Chat]("http://ubuntuforums.org/forumdisplay.php?f=434"))**


For a one-file source code hello-world.c for a program ```
hello-world
``` whats the difference between ```
$./hello-world
``` (after this of course)```
$gcc hello-world.c -o hello-world
``` and ```
$sudo apt-get install hello-world
$hello-world
``` (assuming it is available in this way)? I mean what happens inside the system in both cases (except the thing that **gcc** does in the first case)? Like for the first case, new process starts, it has a PID, maybe it has a default memory limit set by Ubuntu & what until I ctrl+c it?

For the second case, something gets downloaded. Can it have formats other than .deb? Will only the final output file from gcc in the first case **hello-world** be inside it & where the other system changes occur? When it is run, now what happens & how it is different from the execution in first case?  :roll:

---

### Post by lisati on 2015-09-13
*Thread moved to **Programming Talk**.*

---

### Post by brian-mccumber on 2015-09-13
Using ./hello-world executes the compiled file. Using apt-get to install a program that has been packaged for distribution just means that the installer is putting the compiled file and it's resource files in the places they need to be so that the program can then be ran on another computer. This usually includes a .desktop file in user/share/applications so that the program can be found in the dash and then executed by clicking an icon instead of having to open the terminal to run the program. You could take your compiled program and put a copy in /user/bin/ and then you can run it from the terminal by just typing it's name without ./ first like you do with all the commands you can run from the terminal, they are in essence compiled programs residing in /user/bin/. You can also do that and then create a .desktop file for your compiled program and then you can run it by clicking it's desktop icon. So basically ./ is running the compiled program sudo-apt get is putting a compiled file and resource files onto your computer so it can be ran. You can download pure c source and supporting files and libs and you can put the files where you want them, compile it yourself and create a desktop launcher for it yourself and that would pretty much be the same thing that apt-get install does. 

Everything is still being run in the shell whether you install it using apt-get install or compile it and run it from the terminal or your desktop launcher. The terminal is just an interface to the shell it is not the actual shell.

---

### Post by spjackson on 2015-09-14
I think it would help you to read this. [http://www.linfo.org/path_env_var.html](http://www.linfo.org/path_env_var.html)

---

### Post by Kohn_Ywith on 2015-09-14
I was actually trying to know what happens inside the system (I am really trying to avoid to read Ubuntu's source code ;) ), not how to run a program or invoke easily. In other OSes the internal events should be different.

---

### Post by brian-mccumber on 2015-09-14
I am not really sure I know what you mean when you say inside the system. When you invoke ./app-name the system is running your compiled program, when you use apt-get install app-name the system is installing the files it needs to run the compiled program after the compiled program has been made into a package that apt-get install can install. This is pretty much a recap of what I had posted earlier.

---

### Post by ian-weisser on 2015-09-14
> **Kohn_Ywith said:**
> I was actually trying to know what happens inside the system (I am really trying to avoid to read Ubuntu's source code ;) ), not how to run a program or invoke easily. In other OSes the internal events should be different.

'What happens inside the system' is a pretty loose description. It can cover a lot of territory.
How detailed and technical do you want the answer to be?

---

### Post by brian-mccumber on 2015-09-14
Also I guess it would help to understand what your definition of the system is too. I consider the system the OS and the hardware working together as a whole to accomplish the things I want or need to do.

---

