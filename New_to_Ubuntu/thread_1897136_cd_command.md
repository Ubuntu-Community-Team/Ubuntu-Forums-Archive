---
title: "cd command"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by arunes007 on 2011-12-18
how to use cd command in ubuntu 11.04?
which command we should use instead of cd command?
i always get an error "permission denied"?
wtf....plz help......
i have also used sudo command bt nt any ....help....plzzzzz....

---

### Post by Lars Noodén on 2011-12-18
You use [cd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/cd.1posix.html) to switch working directories.  

In what context are you getting the error?  Can you show us exactly what you are typing and the exact error message?

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-18
cd works normally...what are you trying to do?
I use it frequently

---

### Post by arunes007 on 2011-12-18
i have just installed john the rippertar -zxvf john-1.7.8.tar.gz
and extracted it using....
"tar -zxvf john-1.7.8.tar.gz"
nw i was going to...run this....
"cd john-1.7.8"
then each time i get "permission denied".

---

### Post by arunes007 on 2011-12-18
after cd john-1.7.8 
that i have seen that in the tutorial.....



The patch lets “john” call crypt(3) to encode passwords when it sees unsupported encryption. There are 3 files we need to change/create: Makefile, crypt_fmt.c and john.c.

 

Append “-lcrypt” to line “LDFLAGS = -s”, making the line reads as:
 i didnt get last line......properly......

---

### Post by sudodus on 2011-12-18
It's probably a permission issue. Try (as superuser) to change the directory access.

Check what it is ```
ls -l john-1.7.8
```
and change owner and or permissions to read and execute
```
sudo chown "$USER":"$USER" john-1.7.8
sudo chmod ugo+rx john-1.7.8
```

---

### Post by MG&amp;TL on 2011-12-18
Unless you *need* the latest and greatest (and I doubt you do), use:

```
sudo apt-get install john
```

---

### Post by arunes007 on 2011-12-18
> **sudodus said:**
> It's probably a permission issue. Try (as superuser) to change the directory access.

Check what it is ```
ls -l john-1.7.8
```
and change owner and or permissions to read and execute
```
sudo chown "$USER":"$USER" john-1.7.8
sudo chmod ugo+rx john-1.7.8
```


as i said i have already used sudo command bt of no use..."command not found"(i am the superuser)

---

### Post by arunes007 on 2011-12-18
> **MG&TL said:**
> Unless you *need* the latest and greatest (and I doubt you do), use:

```
sudo apt-get install john
```
 
i mst inform u that using the command "sudo apt-get install john"
obviously install john on ur system bt it will be of no use for ubuntu 11.04..as it does nt support "SHA15" encryption and will give error "no password hashes loaded"...

---

### Post by arunes007 on 2011-12-18
> **Lars Noodén said:**
> You use [cd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/cd.1posix.html) to switch working directories.  

In what context are you getting the error?  Can you show us exactly what you are typing and the exact error message?
.......
i will ask u....."which command we should use to patch john-1.7.8"..plzz help...

---

### Post by sudodus on 2011-12-18
> **arunes007 said:**
> as i said i have already used sudo command bt of no use..."command not found"(i am the superuser)
Well, **cd** is not accepted as a command by sudo, so you ***cannot*** run [FONT=Courier New]**sudo cd something** [/FONT]but you can use sudo to change owner and permissions. Another option is to run as root, but it is not recommended because you may forget to exit from it and make some big mistake.

---

### Post by arunes007 on 2011-12-18
> **sudodus said:**
> Well, **cd** is not accepted as a command by sudo, so you ***cannot*** run [FONT=Courier New]**sudo cd something** [/FONT]but you can use sudo to change owner and permissions. Another option is to run as root, but it is not recommended because you may forget to exit from it and make some big mistake.
so any other idea...?????

---

### Post by sudodus on 2011-12-18
Did you try [FONT=Courier New]sudo chown[/FONT] and [FONT=Courier New]sudo chmod[/FONT] according to my previous thread?

---

### Post by arunes007 on 2011-12-18
> **sudodus said:**
> Did you try [FONT=Courier New]sudo chown[/FONT] and [FONT=Courier New]sudo chmod[/FONT] according to my previous thread?

i have used that commands....
output ....
```

abc@ubuntu:~$ sudo chmod ugo+rx john-1.7.8
abc@ubuntu:~$ cd john-1.7.8
abc@ubuntu:~/john-1.7.8$

```

---

### Post by arunes007 on 2011-12-18
what to do next...???????

---

### Post by sudodus on 2011-12-18
> **arunes007 said:**
> what to do next...???????
The problem of the thread is solved, so please mark this thread SOLVED ;-)

I'm kidding, I see what you mean. I guess there is a README file with further instructions what to do. If you can't find instructions in the directory, search where you found the package. If that does not help, use the tip by MG&TL
> **MG&TL said:**
> Unless you *need* the latest and greatest (and I doubt you do), use:

```
sudo apt-get install john
```

---

### Post by sudodus on 2011-12-18
> 
**Using John the Ripper in Ubuntu 11.04**

 John the Ripper is a free password cracking software tool. Initially developed for the UNIX operating system,
  
 Firstly, install the package
  
 # apt-get install john
 Even the web-site suggest that you download from the  repositories (remove the # sign to make the command active), so I  suggest that too.

Good luck :smile:

---

### Post by sudodus on 2011-12-18
```
root@ubuntu:~/john-1.7.8$
``` simply means that you have now changed directory to john-1.7.8 which is what cd is supposed to do. Now you can list the files in the directory using the ls command
```
ls -l 
``` and you might find a README file. But if these things are too difficult, please use the straight-forward installation of john. Maybe you prefer the synaptic or the software-center graphical user interface.

---

### Post by MG&amp;TL on 2011-12-18
Perhaps you need to: (although it's really a bad package if it does)

```
sudo apt-get install john john-data
```

---

### Post by nothingspecial on 2011-12-19
Brute forcing remote ssh servers is not supported here.

Closed.

---

