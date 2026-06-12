---
title: "File/Directory permission question??"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by KingTermite on 2008-06-09
Ok....I thought I understood file/directory permissions. There is nobody using this computer but me, so permissions aren't really a big deal. I could make full permission on every file/directory if I wanted. Anyway.....it's just "the point".

I am writing a script, and in this script it writes another small script "on the fly". It uses echo commands and redirects (script taken from "Linux Desktop Hacks" book).

Anyway, ignore the script, because I've got this down to a command line and can see the problem.

I have a directory created in my home directory called ".reminders". It defaulted to 755 (rwxr-xr-x) permissions.

From the command line I can issue 

```
echo 'some text" > ~/.reminders/somefile
```

I get a permission denied error.

I modified directory permissions to 777 (rwxrwxrwx) and I can perform the same command with no problems.

Why is this? This is MY home directory, I'm the ONLY user and I'm also an admin. Why is it denying me permission to write files to this directory?


I also tried to do the exact same thing naming the "reminders" instead of ".reminders". It worked just fine. No permission issues.

Why are hidden (starts with ".") directories different? Any way around this easily besides just naming it "reminders" instead of ".reminders"?

---

### Post by wdaniels on 2008-06-09
> **KingTermite said:**
> Why are hidden (starts with ".") directories different? Any way around this easily besides just naming it "reminders" instead of ".reminders"?

They're not. There's something wrong here, but I can't think what it could be :confused: Are you absolutely sure about the permissions on this directory? Try recreating it again clean:

```
rm -rdf ~/.reminders
mkdir ~/.reminders
echo 'some text' > ~/.reminders/somefile
```

I double-checked this myself and it works fine here.

---

### Post by spiderbatdad on 2008-06-09
The default permissions are correct, and hidden folder are not treated differently...in other words, I can perform the operation you described, and I get no such error.

Check your id```
id
```see if it matches the id of the user at the end of /etc/passwd  which should also be the owner of the /home directory. Presumably 1000 for a single user installation.

---

### Post by KingTermite on 2008-06-09
> **spiderbatdad said:**
> The default permissions are correct, and hidden folder are not treated differently...in other words, I can perform the operation you described, and I get no such error.

Check your id```
id
```see if it matches the id of the user at the end of /etc/passwd  which should also be the owner of the /home directory. Presumably 1000 for a single user installation.

Well I am the only user and "id" shows me as user 1000. When I show contents of the /etc/passwd file it shows me in next to last position. Does position matter? It shows something for pyscrabble (some game I was goofing with last week) in the last slot.

---

### Post by KingTermite on 2008-06-09
> **wdaniels said:**
> They're not. There's something wrong here, but I can't think what it could be :confused: Are you absolutely sure about the permissions on this directory? Try recreating it again clean:

```
rm -rdf ~/.reminders
mkdir ~/.reminders
echo 'some text' > ~/.reminders/somefile
```

I double-checked this myself and it works fine here.

You are right...I made directory clean and it seemed to work. I wonder if there was an issue with the directory initially being created by the script, not by me at the command line.

---

### Post by spiderbatdad on 2008-06-09
so who owns /.reminders?```
ls -al
```

---

### Post by wdaniels on 2008-06-09
> **KingTermite said:**
> You are right...I made directory clean and it seemed to work. I wonder if there was an issue with the directory initially being created by the script, not by me at the command line.

Maybe you ran the script as sudo or something like that?

---

### Post by KingTermite on 2008-06-09
> **wdaniels said:**
> Maybe you ran the script as sudo or something like that?
Would that make a difference? I may have run the script as sudo if it had an issue the first time (not being sure if it was required).


> **spiderbatdad said:**
> so who owns /.reminders?```
ls -al
```
I had done that (that's my alias for ls anyway). It had the permissions mentioned in 1st post.

---

### Post by wdaniels on 2008-06-09
> **KingTermite said:**
> Would that make a difference? I may have run the script as sudo if it had an issue the first time (not being sure if it was required).

Yes, because if the script is run with sudo, it is executed by the root user, meaning that if it creates a directory, root will own that directory, which is why you couldn't create a file in it afterwards as your normal user.

> **KingTermite said:**
> I had done that (that's my alias for ls anyway). It had the permissions mentioned in 1st post.

Yes, but those permissions relate to an owner and a group (or at least the first two parts do), which are also shown by ls -l. You presumably would have seen "root" listed there as the owner.

---

### Post by KingTermite on 2008-06-09
> **wdaniels said:**
> Yes, but those permissions relate to an owner and a group (or at least the first two parts do), which are also shown by ls -l. You presumably would have seen "root" listed there as the owner.I don't recall seeing "root" there, but its quite possible it was and I overlooked it.

Thanks for the help. I'll trying to finish that script tonight.....on *standby* for a another question or two perhaps. ;)

---

