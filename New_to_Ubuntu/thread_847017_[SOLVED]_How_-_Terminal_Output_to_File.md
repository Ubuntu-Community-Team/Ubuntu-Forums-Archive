---
title: "[SOLVED] How - Terminal Output to File?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by adamslade on 2008-07-02
Hi, 

A really basic question, but I've searched and can't find the answer!

How do I direct the text output displayed in the Terminal Window to a file.  I am getting some errors that I want to be email to email/post and I can't scroll up enough just to copy and paste them.

Thanks

Adam

---

### Post by iaculallad on 2008-07-02
> **adamslade said:**
> Hi, 

A really basic question, but I've searched and can't find the answer!

How do I direct the text output displayed in the Terminal Window to a file.  I am getting some errors that I want to be email to email/post and I can't scroll up enough just to copy and paste them.

Thanks

Adam

On your terminal: Use **>** 

Example: ```
lspci > mytxt.txt
```

This will print all PCI devices to <mytxt.txt> file

---

### Post by mevets on 2008-07-02
Its real simple
```

cmd > output.txt

```

---

### Post by geirha on 2008-07-02
If you need to catch stderr as well, use either 
```
cmd 2>&1 >output.txt
```
or
```
cmd &>output.txt
```

---

### Post by kerry_s on 2008-07-02
just to add:
using " > " will overwrite anything in the file
using " >> " will append/add to the file

---

### Post by adamslade on 2008-07-02
Wow - Thanks all, what a wonderful response.  Keep up the good work.  

:KS

---

### Post by cmcanulty on 2010-06-07
One question. Is there a way to include the original command at the top of the .txt file?

---

### Post by geirha on 2010-06-07
> **cmcanulty said:**
> One question. Is there a way to include the original command at the top of the .txt file?

```
{ echo cmd; cmd; } > output.txt
```

---

### Post by cmcanulty on 2010-06-07
That gives me an error 
```
cmcanulty@Gateway:~$ dpkg --get-selections > installed-software { echo cmd; cmd; } > output.txt
bash: syntax error near unexpected token `}'
cmcanulty@Gateway:~$ ^C

```

---

### Post by cgb on 2010-06-07
you need to replace cmd with the command..  for your example try this code...

```
{ echo dpkg --get-selections; dpkg --get-selections; } > installed-software
```

---

### Post by cmcanulty on 2010-06-07
Thanks, but again nothing
```
cmcanulty@Gateway:~$ { echo dpkg --get-selections; dpkg --get-selections; } > installed-software
cmcanulty@Gateway:~$ 
```

---

### Post by cgb on 2010-06-07
??  There should now be a file called installed-software located in your home directory that you ran that command under.  in the same directory you could run the below code.

```
gedit installed-software
```

---

### Post by cmcanulty on 2010-06-07
Oh yes it is there. I thought the output would be in the terminal too. So when that was empty I though the command wasn't working. Thanks so much.

---

