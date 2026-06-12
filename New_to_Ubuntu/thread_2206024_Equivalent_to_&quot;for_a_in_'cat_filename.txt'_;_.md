---
title: "Equivalent to &quot;for a in 'cat filename.txt' ; do [command]; done&quot;"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by Francisco_Trucco on 2014-02-17
Hello Ubuntu fellows! I was trying to change my bash.bashrc file so bash would prompt a list of commands and their explanations (i.e., "for a in 
[list of commands that should be readed from a text file]; do whatis $a; done" ). I want to have that information in a separate file because I will be changing the list every day and I don't want to be editing the batch file every day. I know that, for security reasons, I have to create this new file with the same access permissions than bash.bashrc and don't worry, I will. 

Now, my problem is that I don't know how to handle the output of the cat command and use it in a for in. 

Well, that's all. Thank you very much, people.

---

### Post by steeldriver on 2014-02-17
Hello and welcome to the forums

I think a better way to read lines from a file is the 'read' command

```

while read -r command; do
   whatis "$command"
done < filename.txt

```

---

### Post by sudodus on 2014-02-17
Try something like this (to read from the file **temp.txt**)

```
while test 1;do read a;if [ $? -eq 0 ];then echo $a;else break;fi;done<temp.txt
```

---

### Post by Francisco_Trucco on 2014-02-17
Oh! that would do it! thank you!

---

