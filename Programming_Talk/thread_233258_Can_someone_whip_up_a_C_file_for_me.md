---
title: "Can someone whip up a C file for me"
date: 2006-08-09
forum: Programming Talk
---

### Post by %hMa@?b&lt;C on 2006-08-09
I have been working on modifying a GPL'd program (camerahacking.com's ceres if anyone wishes to know) to spit out a text file. What I need is a C program that takes "output.txt" and adds a "C" then a space on the beginning of each line.
For example, turning this
```

04e1ff207d9961a23fb810b00dad53be943f6379e217d866787f62c6a169b9be

02b3d7b471a964fc0bcc72b480d26aecb2ed460b7f50016ddaf04c51218783f3

aadfdff5a04ded030d7b3fb7376b61ba30b90e2da921a4470740d63fb99fa16c

c8ed81abaf8ce4016e50df81da832070372c24a80890aa3a26fa675710b8fb71
```
into  this
```
C 04e1ff207d9961a23fb810b00dad53be943f6379e217d866787f62c6a169b9be

C 02b3d7b471a964fc0bcc72b480d26aecb2ed460b7f50016ddaf04c51218783f3

C aadfdff5a04ded030d7b3fb7376b61ba30b90e2da921a4470740d63fb99fa16c

C c8ed81abaf8ce4016e50df81da832070372c24a80890aa3a26fa675710b8fb71

```

thanks
-Jeff

---

### Post by LordHunter317 on 2006-08-09
Why would you use C for that?  Is a shell script OK?

If so:```
awk '{print "C " $0}' <filename>
```ought to work more than suitably.

---

### Post by LordHunter317 on 2006-08-09
Additionally, that puts 'C ' on all lines, even blank ones.  You could use grep to filter out the blank lines, or get rid of them:```
awk '/[^[:space:]]/ {print "C  " $0}' <filename>
```If you really must keep them unaltered you get the uglier:```
awk 'if ($0 ~ /[^[:space:]]/ print "C " $0 ; else print $0 }' <filename>
```

---

### Post by LordHunter317 on 2006-08-09
And if you really want a C version, I can give it to you.  But you really don't want one.

---

### Post by %hMa@?b&lt;C on 2006-08-10
Well, the shell version doesnt seem to work, is there anything that I am doing wrong? I keep getting this as an error
bash: syntax error near unexpected token `newline'

---

### Post by Ragazzo on 2006-08-10
> **jeffc313 said:**
> Well, the shell version doesnt seem to work, is there anything that I am doing wrong? I keep getting this as an error
bash: syntax error near unexpected token `newline'

Remove < and > around the filename.

---

### Post by LordHunter317 on 2006-08-10
Also, the last one is missing a { after the first '.

---

### Post by %hMa@?b&lt;C on 2006-08-10
> **LordHunter317 said:**
> Also, the last one is missing a { after the first '.

thanks a bunch! now how do i get that saved into the file? it just prints it on the terminal as is?

---

### Post by Revert on 2006-08-10
You can redirect output in Bash with ">".

Example-
ls > file.txt
...would save the output of ls into file.txt.

---

### Post by LordHunter317 on 2006-08-10
Note that if you redirect it to the file you're reading, you'll end up just destroying the file.

This is because sh must process the redirections first.  And existing files opened via a '<' redirect are automatically emptied. 

In short, make sure you use another filename.

---

### Post by bieber on 2006-08-10
Wow.  I really need to learn how to use sed and awk.  That's just awesome...

---

### Post by LordHunter317 on 2006-08-10
One can also do it in Perl via -pi -e, but perl is rather overkill for this. Awk or sed will generally be faster for tasks like this.  Also, when working with fields, awk is vastly superior.

---

