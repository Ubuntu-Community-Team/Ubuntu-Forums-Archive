---
title: "Command Line Concerns and Questions"
date: 2022-05-13
forum: New to Ubuntu
---

### Post by Complete on 2022-05-13
I confess, I have been using GUI interfaces for a few decades.  I have gotten used to Microsoft Windows Operating Systems and I have not spend enough time navagating all of the command line commands.... and this is especially true for Linux distributions like Ubuntu.

I DO know what 'cd ..' does when I type it on a Ubuntu command line as well as 'ls'.  And I know where '../Directory' will take me.  It goes up one level in the folder structure and then back down to where ever the 'Director' folder is.  So, if the folder I am currently is is called 'RightHere', then the command line entry of '../RightHere' will seemingly take me no where.

But I never learned what a single dot means.  For example, where is the folder 'interest' in the command 'gzip -d ./interest/dino-mod.tar.gz'.

Also, I do not know how '&&' is used.  What would the following line do:

'cd ../engine && mkdir thirdparty'

It looks like two commands.  So why are they on one line?  Is it to make them execute at the same time?  Is one command dependent on the other?  Where would the directory 'thirdparty" be made?

All of these are examples of what (sort of) appears in a .sh file I need to execute.  I need to know these details to ensure that the directory paths align and are accurate to where I will execute the .sh file.

---

### Post by Impavidus on 2022-05-13
A single . is the current directory.

&& is a logical AND. A logical AND will test its left operant. If that is true, it will also test the right operant and if that's true too, it returns true. Testing an operant when that's a command means running the command and looking at the exit status, which is used here to run two commands. If the first command ran successfully, the second is executed too, but if the first returns error, the second isn't executed.

---

### Post by grahammechanical on 2022-05-13
> 'cd ../engine && mkdir thirdparty'

As I understand things you would be running a command to change directory to the engine directory and then running a command to make a directory called thirdparty in the engine directory.

Here is a Ubuntu tutorial

[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)

[https://www.freecodecamp.org/news/the-linux-commands-handbook/](https://www.freecodecamp.org/news/the-linux-commands-handbook/)

Regards

---

### Post by keylowmike on 2022-05-14
> I DO know what 'cd ..' does when I type it on a Ubuntu command line as well as 'ls'. 

To give credit where credit is due, you AT LEAST know what most would consider to be basic commands in the terminal.  To be honest, when I had to install drivers for the Ol' Reliable's wireless card, I had to check this place and a couple of Google searches to find the correct commands and procedures to get what I need so don't feel too alone in that regard ;).

---

### Post by mIk3_08 on 2022-05-14
[QUOTE=Complete][COLOR=#000000]Also, I do not know how '&&' is used. What would the following line do:[/COLOR][/QUOTE]
As what I have learned, this is to execute two commands. Its either the two will run or not, if the first one run and the second won't and vice versa and if both command are valid then it will have a successful execution of both. I think the purpose of this is for fast and continues process of the command execution. I think the disadvantages of this multiple executions of command is the prerequisite of commands. Because their are times that we have the sequence of command execution and so forth. First command should be the first to be execute and so forth or your application won't work the proper way you wanted. correct me guys if Im wrong. Glad to be corrected here. Good Luck and Cheers.

---

### Post by Holger_Gehrke on 2022-05-14
As Impavidus already said, '&&' is a logical AND with shortcut evaluation. That means that the second command will not be executed if the first produces an error. You could also write this as 'if first_command ; then second_command ; fi'. There's also '||' a logical OR which will execute the second command only if the first fails. In the specific example you give, the directory 'thirdparty' will only be created if the change of working directory to '../engine/' succeeded meaning if that directory exists and is accessible to the user.

Holger

---

