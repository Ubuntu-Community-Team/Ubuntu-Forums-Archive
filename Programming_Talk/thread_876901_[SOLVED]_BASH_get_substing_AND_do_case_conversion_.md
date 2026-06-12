---
title: "[SOLVED] BASH: get substing AND do case conversion in one line?"
date: 2008-08-01
forum: Programming Talk
---

### Post by justleen on 2008-08-01
I have a   CSV text file, which contains userid,first and lastname

 a line looks like
DRN90002; Doe, John

What I need from the user name is the first three letters as uppercase, and i need the whole userid as lowercase.

What i have so far is this:
```
while read line; do
        USERNAME=${line%;*}
        USERNAME=$(echo $USERNAME | tr A-Z a-z)
        REGIO=${line:0:3}
        echo $REGIO $USERNAME
done < ${NEWFILE}

```

Now.. this does exactly what I want. But, I am wondering, can I somehow combine the 2 lines that create the $USERNAME that I need?

As in, can I grab the first part of the line and to a tr on it, without splitting over 2 lines (and adding another proccess since I launch tr)?

---

### Post by c2olen on 2008-08-01
> **justleen said:**
> I have a   CSV text file, which contains userid,first and lastname

 a line looks like
DRN90002; Doe, John

What I need from the user name is the first three letters as uppercase, and i need the whole userid as lowercase.

What i have so far is this:
```
while read line; do
        USERNAME=${line%;*}
        USERNAME=$(echo $USERNAME | tr A-Z a-z)
        REGIO=${line:0:3}
        echo $REGIO $USERNAME
done < ${NEWFILE}

```Now.. this does exactly what I want. But, I am wondering, can I somehow combine the 2 lines that create the $USERNAME that I need?

As in, can I grab the first part of the line and to a tr on it, without splitting over 2 lines (and adding another proccess since I launch tr)?

Would this work for you?
```

USERNAME=$(echo ${line%;*} | tr A-Z a-z)
```

---

### Post by ghostdog74 on 2008-08-01
```

awk -F";" '{print substr($0,1,3),tolower($2)}' file

```

---

### Post by justleen on 2008-08-01
Yep, that would work.. cheers! 

but, thats still requires a second proccess, awk or tr..

Is their any way you can do this with "plain substition" eg, with only bash and not starting an extra binary?

I know this is quite trivial, and it doenst really matter for my script, but Im just curious how far I can stretch the string manipulation possiblities of ${}

---

### Post by ghostdog74 on 2008-08-01
if you happen to know ksh, there's a typeset -u you can use, however bash (AFAIK) doesn't support -u. The portable way to convert cases, is tr (or awk)

---

### Post by justleen on 2008-08-01
> **ghostdog74 said:**
> if you happen to know ksh, there's a typeset -u you can use, however bash (AFAIK) doesn't support -u. The portable way to convert cases, is tr (or awk)

Hm, Ill look into that.. 


thnx peeple!

---

