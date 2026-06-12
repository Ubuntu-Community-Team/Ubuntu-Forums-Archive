---
title: "Can anyone explain why the &quot;less&quot; command doesn't seem to be working?"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by t-julian101 on 2014-02-03
I'm working my way through Ubuntu unleashed (a book).

I've come across the dmesg and less commands, used in tandam. I have been getting some error messages so I thought I would look at the file and try learn something new. This happened:

```
tom@tom-HP-Pavilion-g6-Notebook-PC:~$ less /var/log/messages
/var/log/messages: No such file or directory


```

Thanks for helping me learn something new!

---

### Post by deadflowr on 2014-02-03
What errors were reported?
That can help tell which file to look at.

I don't think there is such a file in the /var/log folder called messages.

---

### Post by sudodus on 2014-02-03
***less*** does not find any file with the name **/var/log/messages**

less is a viewer that reads text files. For example run a command and create a file

```
echo 'Hello World' > hello.txt
```

and view it with less

```
less hello.txt
```

Another example: View the bash running conditions file (a hidden file, the name starts with . (dot), sitting in your home directory ~ (tilde))

```
less ~/.bashrc
```

Use the arrow keys, PgUp, PgDn, to navigate and q to quit. See ```
man less
``` for more details.

---

### Post by t-julian101 on 2014-02-03
I follow you now. Weird as to why the book thinks this is correct. 

I do have another question if you don't mind sudodus. When you create as file as with:

```
echo 'hello world' > hello.txt
```

Where does the file go? Is it left in the current directory?

---

### Post by sudodus on 2014-02-03
> **t-julian101 said:**
> I follow you now. Weird as to why the book thinks this is correct. 

I do have another question if you don't mind sudodus. When you create as file as with:

```
echo 'hello world' > hello.txt
```

Where does the file go? Is it left in the current directory?

Yes, the current directory, if no directory path is preceding the file name.

-o-

The > sign means 'redirect to a file with the name as the following text'
The < sign means 'redirect from a file with the name as the following text'
and these redirections are used with programs and scripts that otherwise read from and write to the terminal window.

---

### Post by deadflowr on 2014-02-03
> **t-julian101 said:**
> I follow you now. Weird as to why the book thinks this is correct. 

I do have another question if you don't mind sudodus. When you create as file as with:

```
echo 'hello world' > hello.txt
```

Where does the file go? Is it left in the current directory?

Yep.
The file will be in whatever the current directory you're in. Unless you point to another in the command.
like change the out put

```
[COLOR=#000000][FONT=Ubuntu Mono]echo 'hello world' > ~/Downloads/hello.txt[/FONT][/COLOR]
```
The command
```
pwd
```
will tell you where you currently are.

---

### Post by t-julian101 on 2014-02-03
Thanks guys, apprechiate it!

---

### Post by nothingspecial on 2014-02-03
There used to be a file /var/log/messages but it was disabled. You can find what used to be in there in /var/log/syslog. See here
[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505) .

---

