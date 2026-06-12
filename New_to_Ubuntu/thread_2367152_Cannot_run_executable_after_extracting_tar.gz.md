---
title: "Cannot run executable after extracting tar.gz"
date: 2017-07-26
forum: New to Ubuntu
---

### Post by aks2161989 on 2017-07-26
Hi,

I have downloaded an IDE for C/C++ programming called "MinGW Developer Studio" from [this link]("http://vaultec.mbnet.fi/files/miscellaneous/mingwstudio/mingw-devstudio_linux-2.06.tar.gz") . After extracting the files to a folder, I cannot run the executable inside **either by double-clicking** or by navigating to the folder in the terminal and typing ./MinGWStudio (the name of the executable). 

When I type the command "**file MinGWStudio**" I get the following output:

```
MinGWStudio: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.2.5,
```

When I navigate to the folder in terminal and type "**MinGWStudio**" I get the following output:

```
MinGWStudio: command not found
```

When I navigate to the folder and type the command **./MinGWStudio **I get the following output:

```
bash: ./MinGWStudio: No such file or directory
```

What can I do to run this executable? Any help will be appreciated.

Ubuntu version : 17.04 Zesty Zapus

---

### Post by wildmanne39 on 2017-07-26
*Thread moved to **New to Ubuntu**.*

---

### Post by thejeremy-net on 2017-07-26
Hi aks2161989,

Have you tried checking if the executable flag is set?

You can run
```
ls -lah
```
to see what the file's permissions are set to.

And run
```
sudo chmod +x MinGWStudio
```
to give it the execution permission.


Also, make sure you have the correct dependencies installed (from Readme.txt):
```
* GTK+ 2.0 or higher.
* GNU gdb 5.21 or higher.(Optional if you don't use its debugging features)
```

---

### Post by aks2161989 on 2017-07-26
Hi thejeremy-net,

Thank you for replying. 

When I run the code **"ls -lah" **I get the following output:

```
drwxr-xr-x  4 hp   hp   4.0K May 17  2005 MinGWStudio
```

When I navigate to the folder in terminal and run the command **sudo chmod +x MinGWStudio**, it asks me for the password. Later when I navigate to the folder and use the command **./MinGWStudio**, I get the following output:

```
bash: ./MinGWStudio: No such file or directory
```

On Running the command **MinGWStudio **I get the output:

```
MinGWStudio: command not found
```

When I run the command 

```
**dpkg -s libgtk2.0-0|grep '^Version'**
``` 

The output is

```
Version: 2.24.31-1ubuntu1
```

When I run the command

```
dpkg -s libgtk-3-0|grep '^Version'
```

The output is

```
Version: 3.22.11-0ubuntu3
```

To check the version of GNU gdb i used the command "**gdb --version**" I got the following output:

```
GNU gdb (Ubuntu 7.12.50.20170314-0ubuntu1) 7.12.50.20170314-git
```

BTW, I have extracted the contents of the tar.gz file to the path **/home/MinGWStudio**

---

### Post by vocx on 2017-07-26
> **aks2161989 said:**
> Hi,

I have downloaded an IDE for C/C++ programming called "MinGW Developer Studio" from [this link]("http://vaultec.mbnet.fi/files/miscellaneous/mingwstudio/mingw-devstudio_linux-2.06.tar.gz") . After extracting the files to a folder, I cannot run the executable inside **either by double-clicking** or by navigating to the folder in the terminal and typing ./MinGWStudio (the name of the executable). 

When I type the command "**file MinGWStudio**" I get the following output:

```
MinGWStudio: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.2.5,
```
...
When I navigate to the folder and type the command **./MinGWStudio **I get the following output:

```
bash: ./MinGWStudio: No such file or directory
```

...
The problem you are experiencing seems to be related to running a 32-bit application in a 64-bit environment.

See this link
[https://askubuntu.com/questions/231479/no-such-file-when-running-a-32-bit-program-on-a-64-bit-system](https://askubuntu.com/questions/231479/no-such-file-when-running-a-32-bit-program-on-a-64-bit-system)

The message "No such file or directory" looks puzzling because you obviously see the file there. The link above explains that it may be referring to the 32-bit library loader, which means there is no loader in your 64-bit system to run the 32-bit executable. Maybe if you install the appropriate loader you will be able to run the program, or at least get a more meaningful error message. It may also work if you install your Ubuntu system as 32-bit, instead of 64-bit.

Now, with that said, who told you to use this program? From reading the "readme.txt" it seems like an old integrated development environment (IDE) for C and C++ programming, I guess for the MinGW or GCC compilers. You do not require it to do C and C++ programming in Linux. You can use any text editor, such as "gedit", "kate", "geany", "vim", etc., to write your code, and then use "gcc" or "g++" to compile the program from the terminal. If you are using a programming guide, or taking a programming class, and they suggest you use this, you may want to look for alternatives, as this "MinGWStudio" seems to be an old program which hasn't been updated since 2005.

---

### Post by Impavidus on 2017-07-26
> **thejeremy-net said:**
> 
And run
```
sudo chmod +x MinGWStudio
```
to give it the execution permission.
No need to use sudo there.

> **aks2161989 said:**
> Hi thejeremy-net,

Thank you for replying. 

When I run the code **"ls -lah" **I get the following output:

```
drwxr-xr-x  4 hp   hp   4.0K May 17  2005 MinGWStudio
```That's the directory where the executable should be. The first letter of the output is a d, indicating directory. Get into that directory. I assume that's where you ran the **file MinGWStudio** command. There the next command should work.
> Later when I navigate to the folder and use the command **./MinGWStudio**, I get the following output:

```
bash: ./MinGWStudio: No such file or directory
```That means exacly what it says: the filename was wrong or you're not in the right directory.
> 
On Running the command **MinGWStudio **I get the output:

```
MinGWStudio: command not found
```That's to be expected. You can only run commands in your $PATH without the ./ prefix. The current directory is not in your $PATH.
> 
BTW, I have extracted the contents of the tar.gz file to the path **/home/MinGWStudio**
Not in /home/your_username/MinGWStudio?

---

### Post by Dennis N on 2017-07-26
You need to install various 32-bit libraries to run 32-bit software. As a start, I would install lib32z1 and then try running your executable again from the terminal.

---

