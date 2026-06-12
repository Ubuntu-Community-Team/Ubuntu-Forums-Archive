---
title: "PATH question"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by cheeky_lankan on 2008-09-10
hey could someone explain to me the path evviroment variable; to my knowledge it means that it stores the path to commands so when i do "echo $PATH" it spat out "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"  so wat did this just show me... the pathways to "$"(if so what is that )or "PATH"... please i am a lil confused thank you;and example if i did something like this "echo dfPATH " would that show me the path to the binary of the comman "df" ?

thank you for your time

---

### Post by Titan8990 on 2008-09-10
In BASH "$" is prefixed for variables. So "echo $PATH" prints the contents for the variable "PATH". 

What is the PATH?

The PATH by default is where commands are located and can be specified without issuing their absolute names (directory + file).

For example, the echo command you used is located in the directory /bin/. If you notice by default /bin is in your PATH variable. If this was not in your PATH variable you would have had to execute the command like this:

/bin/echo $PATH


Hope that helps.

---

### Post by Vivaldi Gloria on 2008-09-10
Look [[COLOR="DarkOliveGreen"]here[/COLOR]]("https://help.ubuntu.com/community/EnvironmentVariables") for env variables. To find the binary of a command use

```
which <command>
whereis <command>
```

---

### Post by cheeky_lankan on 2008-09-10
> **Titan8990 said:**
> In BASH "$" is prefixed for variables. So "echo $PATH" prints the contents for the variable "PATH". 

What is the PATH?

The PATH by default is where commands are located and can be specified without issuing their absolute names (directory + file).

For example, the echo command you used is located in the directory /bin/. If you notice by default /bin is in your PATH variable. If this was not in your PATH variable you would have had to execute the command like this:

/bin/echo $PATH


Hope that helps.

ok.. i understand but then; when i type "echo $ls" nothing is spat out; so shoudnt it print out the contents for the variable "ls"?

---

### Post by john test on 2008-09-10
two commands show the path to a file or program
"locate myfile"
or 
"Whereis thatfile"

You can do "echo $PATH"
or 
"export"

---

### Post by Vivaldi Gloria on 2008-09-10
> **cheeky_lankan said:**
> ok.. i understand but then; when i type "echo $ls" nothing is spat out; so shoudnt it print out the contents for the variable "ls"?

No. ls is a command, not variable. There are some predefined variables like 

```
GDM_LANG
USERNAME
HOME
SHELL
PATH
```

etc. The command

```
env
```

shows some of them.

---

### Post by cheeky_lankan on 2008-09-11
> **Vivaldi Gloria said:**
> No. ls is a command, not variable. There are some predefined variables like 

```
GDM_LANG
USERNAME
HOME
SHELL
PATH
```

etc. The command

```
env
```

shows some of them.


Thank you m8 it cleared me up ..i was heading the wrong direction 

cheers 

cheeky

---

