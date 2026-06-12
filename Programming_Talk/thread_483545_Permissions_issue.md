---
title: "Permissions issue"
date: 2007-06-24
forum: Programming Talk
---

### Post by NuNn DaDdY on 2007-06-24
I'm writing a simple program to produce HTML code through scripting; the name for the file is "make_page" and once I save it I try to redirect it to page.html just to view it but when I put in the command "make_page > page.html" I recieve a permission denied message.  but I'm unable to change the permissions on the page.html when I use "sudo chmod 755 page.html".  This is probably just a simple fix but thanks for the help.

---

### Post by jack@tortuga on 2007-06-24
Are you using bash? Try typing 'set +C' on a line by itself, then try clobbering the file ( 'makepage > page.html' ).

Also, if this doesn't work, can you post the output of your command, as well as 'ls -l page.html'?

---

### Post by NuNn DaDdY on 2007-06-24
I put in the 'set +C' but that didn't work.  for the make_page file the code is as follows:

#!bin/bash

#make_page - A script to produce an HTML file.

cat <<- _EOF_
   <HTML>
   <HEAD>
 	<TITLE>
		My System Information.
	</TITLE>
   </HEAD>
 
   <BODY>
 	<H1> My System Information. </H1>
   </BODY>
   </HTML>
_EOF_


and for the output on the terminal:


corey@NuNn-DaDdY:/home$ sudo gedit make_page
Password:
corey@NuNn-DaDdY:/home$ make_page > page.html
bash: page.html: Permission denied

---

### Post by jack@tortuga on 2007-06-24
More than anything else, what will help me/anyoneelse determine the cause of your issue is the output from the command below.

[QUOTE=jack@tortuga]Also, if this doesn't work, can you post the output of your command, as well as **'ls -l page.html'**?
[/QUOTE]


This looks like a basic file permissions issue. I've always had trouble with sudo / file redirection , but never really looked into it much.

Maybe you have to use 'sudo' to edit your file (the makepage script) but I would just change the permissions so that you would not.

You could just create a 'wrapper script' around your command, 'makepage > page.html' and use 'sudo' to execute the wrapper script. But the better practice would probably be to get the file permissions worked out so that you can overwrite the file yourself (without relying on 'sudo').

There are some great tutorials on the net about **UNIX file permissions**. It might be beneficial to google it.

---

### Post by NuNn DaDdY on 2007-06-24
Opps sorry about not including that, when I put the command in i recieve

corey@NuNn-DaDdY:/home$ ls -l page.html
ls: page.html: No such file or directory

---

### Post by Mr. C. on 2007-06-24
The owner of the file is root.  You are trying to redirect into the file as you, a normal user.  This will always fail, as you do not have permission to write a root-owned file.

The command:

```
sudo echo Hello > root-owned-file
```

fails because the redirection occurs *in the current shell*; sudo never sees the redirection.  The current shell sets up the redirection *first* and then executes the sudo command, which in turns runs the echo command as UID root.

MrC

---

### Post by jack@tortuga on 2007-06-24
So now we want to check the directory permissions.  *In the same directory*, type '**ls -ld .**'.  ( That's a SPACE + DOT following the -ld. )

Also, type '**id**' and post that, since I don't know who you are on your system.

What is your _actual_ home directory?  You probably want to be running everything from there, instead of /home , correct? I suspect this is the cause. Also type these 2 commands and post the result:

1) **echo $HOME**
2) **ls -ld $HOME**

---

### Post by NuNn DaDdY on 2007-06-24
Here are the details, I believe you are right on not being in the correct home directory.  I thought about that earlier but didn't switch because I was unsure.

corey@NuNn-DaDdY:/home$ ls -ld .
drwxr-xr-x 3 root root 104 2007-06-24 22:25 .

corey@NuNn-DaDdY:/home$ id
uid=1000(corey) gid=1000(corey) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(corey)

corey@NuNn-DaDdY:/home$ echo $HOME
/home/corey

corey@NuNn-DaDdY:/home$ ls -ld $HOME
drwxr-xr-x 19 corey corey 1064 2007-06-24 22:23 /home/corey



I'll switch the make_file page over to the actual home directory and see if that works also.

---

### Post by NuNn DaDdY on 2007-06-24
I moved the file over to my actual home directory but still recieve:

corey@NuNn-DaDdY:~$ make_page > page.html
bash: make_page: command not found

Is there something I have to do with the page.html because that's where the problem may be.  At the current moment the file doesn't exist and I'm trying to create it with the script I believe :)

---

### Post by jack@tortuga on 2007-06-24
[QUOTE=NuNn DaDdY]I moved the file over to my actual home directory but still recieve:

corey@NuNn-DaDdY:~$ make_page > page.html
**bash: make_page: command not found**[/QUOTE]

Bash just told you what your error was. Now it can't find the make_page command. You have to have the command in your $PATH, OR if '.' (DOT) is in your current path, then you must be in the current directory as the command. OR you could just use an absolute path to the make_page command:

Do this:

cd $HOME
mv /home/make_page $HOME
$HOME/make_page > $HOME/page.html

ls -rlt /home
ls -rlt $HOME/

Please cut & paste these commands & post the results.

---

### Post by Mr. C. on 2007-06-24
This error is the shell telling you it doesn't know where your make_page program is.  Either use the full pathname, or place the make page program in your own personal bin directory that you create, and add that bin directory to your path:

```
mv make_page ~/bin
PATH=$PATH:~/bin/
```

MrC

---

### Post by NuNn DaDdY on 2007-06-24
Problem Solved!  Yet another simple user error on my part which caused alot of hastle, haha.  My problem was in my first line of code; instead of using '#!/bin/bash'  I had #!bin/bash which caused nothing to happen as a result.  Thank you very much for your help and time I appreciate it.  Have a good night.

---

### Post by NuNn DaDdY on 2007-06-24
Also, Mr C. if I were to create my own bin directory, would I just do that in my home directory?

---

### Post by Mr. C. on 2007-06-24
You can create the directory anywhere you want; so long as you have permission, and set your PATH to look there.  The name "bin" is typically used, just like the system's "bin" directory.

MrC

---

