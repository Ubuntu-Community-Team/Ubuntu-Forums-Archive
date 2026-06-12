---
title: "How Do I Create .bat like Scripts?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Bosconian on 2008-07-14
How do you create script files in Ubuntu like .bat files in Windows? I want to place a list of commands in a script file and be able to run it as and when required.

---

### Post by DGortze380 on 2008-07-14
google shell scripting. 

In linux you basically have a choice of ksh, bash, or csh (there are other shells but those are the major ones).

---

### Post by appi2012 on 2008-07-14
they are .sh files

run them with a:
```
./foo.sh
```

---

### Post by quantumstitch on 2008-07-14
for bash:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by hyper_ch on 2008-07-14
[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by Cypher on 2008-07-14
Create a new file with the following contents
```

#!/bin/sh

`command`
`command`
`command`

```
This is the most basic script with 3 commands..

Save the file to script.sh and then do
```

chmod 755 script.sh

```
You can  now execute it with
```

./script.sh

```

Bash and other shell language have a fairly rich programming environment, so you can do quite a lot more than MS BATCH files..

---

### Post by Squid Tamer on 2008-07-14
To get started create a file with a name of x.sh (you can replace the x with whatever you want.).    Open it in gedit, and for the first line type 
```
#!/bin/bash
```

Then you can type in whatever script code you want (pretty much the same thing you type into the terminal. You'll have to read some tutorials if you want to do more complex scripting.

Save the file, close gedit and right click on the x.sh icon. Go to "Properties" and then to the Permissions tab.
Check the Execute: box.

Now you can double click on it and it'll give you a chooice of opening in the terminal.

All of this process has terminal equivalents, but you can figure those out later.

---

### Post by Bosconian on 2008-07-14
Thanks everyone.

---

