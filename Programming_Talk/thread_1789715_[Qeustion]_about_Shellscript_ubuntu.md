---
title: "[Qeustion] about Shellscript ubuntu"
date: 2011-06-24
forum: Programming Talk
---

### Post by Thibault89 on 2011-06-24
Well i have an qeustion, i need to know how you need add stuffs on script. what i need list

-give int passwd user, Shadow user, Group user
-All file's (tar.gz) /home/user

Can you please for me to help? i need it just for Shell Scripts ubuntu.

Thanks you..

---

### Post by Tony Flury on 2011-06-24
Is this homework ?

Do you know how to do any of this stuff from the command line ?

---

### Post by Thibault89 on 2011-06-24
No really, i am helping my uncle. so he was qeustion to me. and he doenst know very as well english. Alright i hope you guys/girls help to us =)

---

### Post by FormatSeize on 2011-06-24
> **Thibault89 said:**
> 
-give int passwd user, Shadow user, Group user
These should be done at the command line, even if you are adding tons of people, since you have to come up with names and passwords for them all anyway. 
> **Thibault89 said:**
> -All file's (tar.gz) /home/user
I actually did this last night:
```

#!bin/bash
# -- your comments or whatever
FILES=/home/user/*tar.gz
for f in $FILES
do
    tar -xvvzf $f
done

```

---

### Post by geirha on 2011-06-25
For adding many users in batch, look into newusers(8).
```
man 8 newusers
```

---

### Post by Thibault89 on 2011-06-25
:D Awesome, That is really nice helper. but i dont understand kind about 
[I]-give int passwd user, Shadow user, Group user? Because my uncle told me he must need it from his friend. Maybe Any people explain me what does this mean?
but any people dont know how Bash Shellscript of Give Int passwd user,Shadow,Group User?


Sorry about late reply.

Thanks you if you want to help us.
[/I]

---

### Post by geirha on 2011-06-25
Your question is not understandable, not to me at least. You'll have to write it in valid english. Perhaps see if there's a Loco team for your language and ask your question there.

[https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

---

### Post by Thibault89 on 2011-06-25
well i am sorry, but i want just last one Shellscript about give int passwd user, Shadow user, Group user =/ then i have all what i need.. and thanks you.. if you help me..

Thanks you

Thibault

---

### Post by geirha on 2011-06-25
Well, problem is, "give int passwd user" doesn't make any sense, what do you mean? And what do you mean by "Shadow user" and "Group user"? 

If you have some sample input and wanted output you could provide, that would probably help.

---

### Post by Thibault89 on 2011-06-27
sorry my uncle speak a wrong word. he mean 

 Data int passwd user        (/etc/passwd)
Shadow user(/etc/shadow)
              Group user(/etc/group)
  but i am not sure. =/ Well It is okay if you dont understand then i am trying check on site.

Thanks you if you are trying help me:)


Thibault.

---

### Post by nothingspecial on 2011-06-27
What does the script do with the data in the three files?

---

