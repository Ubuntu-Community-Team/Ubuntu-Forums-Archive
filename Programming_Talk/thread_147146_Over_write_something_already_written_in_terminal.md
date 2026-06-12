---
title: "Over write something already written in terminal"
date: 2006-03-19
forum: Programming Talk
---

### Post by zootreeves on 2006-03-19
I'm sure i've seen this done in various programs, but I couldn't find any info on how to do it.

How could I count from 1 - 10 without printing 12345678910 in the terminal, but printing 1, then overwrting 1 and printing 2 etc..

---

### Post by hod139 on 2006-03-19
```

[COLOR=#808080][I]#!/bin/bash
[/I][/COLOR][COLOR=#880088]**echo**[/COLOR] -n [COLOR=#dd0000]"1"[/COLOR] [COLOR=#808080]*# -n --> no newline*[/COLOR] [COLOR=#cc00cc][B]
sleep[/B][/COLOR] 1s [COLOR=#008000]
i=[/COLOR]2 
**while**[COLOR=#880088]** [**[/COLOR] [COLOR=#008000]$i[/COLOR] -le 10[COLOR=#880088]** ]**[/COLOR] [B]
do[/B]     [COLOR=#880088][B]
    echo[/B][/COLOR] -n -e [COLOR=#dd0000]"\b[/COLOR][COLOR=#008000]${i}[/COLOR][COLOR=#dd0000]"[/COLOR]    [COLOR=#808080][I]# -e enables backslashed-escaped chars
                        [/I][/COLOR]            [COLOR=#808080]*# \b is backspace*[/COLOR]
    [COLOR=#008000]i=$(([/COLOR]i+1[COLOR=#008000]))[/COLOR]
    [COLOR=#cc00cc]**sleep**[/COLOR] 1s [B]
done[/B]
[COLOR=#880088]**echo**[/COLOR] [COLOR=#dd0000]"" [/COLOR][COLOR=#808080]*# Add a newline*[/COLOR] 

```

---

### Post by paulipe on 2006-03-20
```
#!/bin/bash
echo -n "1" # -n --> no newline 
sleep 1s 
i=2 
while [ $i -le 10 ]; do     
    echo -n -e "\b${i}"    # -e enables backslashed-escaped chars
                                    # \b is backspace
    i=$((i+1))
    sleep 1s;
done
echo "" # Add a newline 
```

I tried hod139's code but i got a syntax error. It looks like the semi-colons are important for bash while-loop. Atleast for my breezy setup it is.

---

### Post by hod139 on 2006-03-20
Sorry about that. The word "do" must be on a new line after the while if I don't put a ";".  I fixed it in my original post.

---

