---
title: "split string"
date: 2012-06-19
forum: Programming Talk
---

### Post by maddog21 on 2012-06-19
I am trying to get some data from a file and print it on the same line. 
I have a script that gets the body of emails and display it, but i want it to display each emails body in one line no matter how big it is. eg

insted of this 

email1: bla bla bla
bla bla bla
bal
email2: bla bla bla bal
bla bla bal

 i want it to print

email1: bla bla bal bal bal bal
email2: bla bal bla blalba bla bla

the code i used to print the body is awk '/Content-Type/{p=1;c++;print "Email-",c;}/Date/{p=0}p' file

Thank You!

---

### Post by sudodus on 2012-06-19
You can use ***tr*** to substitute [FONT="Courier New"]new-line[/FONT] with [FONT="Courier New"]space[/FONT]. You can easily pipe via ***tr***.

```
tr '\n' ' '  < file-with-several-lines.txt
```

---

### Post by codemaniac on 2012-06-19
You can try up something like below .

```
awk '/email/{c++}{print > "file" c}' *emaildata_file*
```

The above would strip out email bodies and place them into files file1 , file2 ..etc .

---

### Post by maddog21 on 2012-06-19
> **codemaniac said:**
> You can try up something like below .

```
awk '/email/{c++}{print > "file" c}' *emaildata_file*
```

The above would strip out email bodies and place them into files file1 , file2 ..etc .


how can i make this in to a script where it reads from one file and outputs to different file?

thanks

---

### Post by codemaniac on 2012-06-19
> **maddog21 said:**
> how can i make this in to a script where it reads from one file and outputs to different file?

thanks

You can put the above awklet in a bash script and execute.

```
#!/bin/bash

awk '/email/{c++}{print > "file" c}' emaildata_file
```

---

