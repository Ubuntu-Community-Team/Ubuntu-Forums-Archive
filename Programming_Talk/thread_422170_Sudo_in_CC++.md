---
title: "Sudo in C/C++"
date: 2007-04-24
forum: Programming Talk
---

### Post by twentytortures on 2007-04-24
I'm pretty new to C++ and Linux so I hope this isn't a stupid question.

I want to write a program that will run several sudo commands. I want the program to ask the user for input for the password and store that into a variable. I need to be able to pass that variable to the password prompt.

If I run something like:
system("sudo gedit");

How do I pass the password to it?

Thanks

---

### Post by Mr. Picklesworth on 2007-04-24
I believe if your program is run as root, all child processes will also get that access, so what you need is for your own program to be run with sudo or gksudo.
(Although there is probably a better way... I'm pretty new to Linux development, too).

---

### Post by JT673 on 2007-04-25
Hmms, it's better to use a shell script like this:

```
gksudo ./myapp
```

That will ask for a password, and all commands afterwards will be done as root, instead of irritating your end-user with lots of password inquiries.

---

### Post by dio3 on 2009-01-02
You can execute sudo command including the sudo password like this
```
**echo XXXXXX | sudo -S and the command**
``` 

where XXXX is your password.
The -S (stdin) option causes sudo to read the password from the standard input instead of the terminal device.(just a copy from man sudo)

a safer way is to save your pass to a well protected file
> **cat ~/.password_file | sudo -S and the command**

so try this way to the system function.
> **system("echo XXXX | sudo -S gedit");**

if you want the user to give the password then save it somehow to a string and use system() like this..

```
/*const*/ char *new_text,*pass;

/* save the password */
scanf ("%s",pass);  


/* save the command to new_text */
sprintf (new_text, "echo %s | sudo -S -b shutdown -r +%d",pass, value);


/* or sth like new_text = g_strdup_printf ("echo %s | sudo -S -b shutdown -r +%d",pass, value); if u r on a gtk program */
	
system(new_text);
```

;)

---

