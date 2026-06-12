---
title: "problem with shell commands in C file"
date: 2007-07-19
forum: Programming Talk
---

### Post by rlagksquf on 2007-07-19
Hi

I was writing some shell commands in my C file, but only this command won't work (I'm running Ubuntu)

>  system("cp `ls ~/Desktop/assa/backup | tail -1` ~/Desktop/assa");
the c file and the file I want to move is in different folder, as you can see from the code

so i tried

>  system("cd ~/Desktop/assa/backup");
                 system("cp `ls | tail -1` ~/Desktop/assa");

and

>  system("convert `ls ~Desktop/assa/backup | tail -1` ~/Desktop/assa/image.jpg");

but both of them didn't work as well

can anyone help with this?

thanks

---

### Post by yabbadabbadont on 2007-07-19
"~" will not be defined in the subshell that is created when the system command is run.  Use the full path or, better yet, implement the same actions using pure C code.  :D

---

### Post by rlagksquf on 2007-07-19
> **yabbadabbadont said:**
> "~" will not be defined in the subshell that is created when the system command is run.  Use the full path or, better yet, implement the same actions using pure C code.  :D

thanks yabbadabbadont

but it still doesn't work with the full path

> system("cp `ls /home/rlagksquf/Desktop/assa/backup | tail -1` /home/rlagk
squf/Desktop/assa");


I still get an error saying 

> cp: cannot stat `filename.jpg': No such file or directory

I must implement this with the shell command..it's like an assignment hehe

---

### Post by yabbadabbadont on 2007-07-19
I wondered if it was homework.  You're on your own.  ;)

---

### Post by rlagksquf on 2007-07-19
lol thanks anyway :)

---

### Post by Mr. C. on 2007-07-20
Now what do you think this means?

```
... stat `filename.jpg': **No such file or directory**
```

MrC

---

### Post by Ramses de Norre on 2007-07-20
This works here: ```

int main(void) {
    system("cp \"$(ls /home/ramses/|tail -1)\" /home/ramses/Desktop/");
    return 0;
}

```

---

