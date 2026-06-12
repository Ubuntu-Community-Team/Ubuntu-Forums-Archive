---
title: "bash script: cd"
date: 2009-08-17
forum: Programming Talk
---

### Post by mcintire319 on 2009-08-17
Ok, so I'm trying to install a program via binary file. The instructions are as follows:

1. Download a BIN application file to the computer's hard drive. Once the file is downloaded, copy and paste it to the desktop.
2. Open the Terminal. The Terminal can be accessed in the Applications menu at the top of the screen by choosing "Accessories" and "Terminal."
3. Type "CD DESKTOP" in the Terminal (without the quotes) and press the "Enter" key on the keyboard. The Terminal should now read "computer@name:~$ Desktop"
etc...

However... when I look in folder/s that contain my bash commands, I see 100+ different bash scripts, but cd is not among them.

Any idea where I can get this script?

Thank you :)

---

### Post by lisati on 2009-08-17
The "cd" command isn't a bash script, it's a command that comes as standard "built in' on Linux, MS-DOS and Windows. Type it in and go for it.

---

### Post by DaithiF on 2009-08-17
also, bear in mind that the terminal is case-sensitive, so
```
CD DESKTOP
```
will not actually work
```
cd Desktop

```however will

---

### Post by dribeas on 2009-08-17
To be a little more precise, they are built in commands of the shell. All shells I have used (from MSDOS command or 4dos shell to Windows cmd or powershell, sh, bash, tcsh) share that same built in command to change directory. Some other built in commands are shared among shells, some are not. Even the ones that are shared have different implementations and possible arguments (i.e. 'cd -' will go back to the last visited directory in bash, but does not have that effect in command).

---

### Post by mcintire319 on 2009-08-17
Me noob.

Thanks for your help :)

---

