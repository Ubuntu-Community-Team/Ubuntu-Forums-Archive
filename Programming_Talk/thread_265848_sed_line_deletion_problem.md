---
title: "sed line deletion problem"
date: 2006-09-26
forum: Programming Talk
---

### Post by mslonik on 2006-09-26
Hello,

Task: delete the lines that have just one key in it: 0x0A (new line).

Problem is as simple as follows. The line below should remove all empty lines with use of sed:

sed -e 's/\x0A$//' proba03.txt

or

sed -e '/^$/ d' proba03.txt

or

sed -e '/^^M/d' proba03.txt 

or

sed -e '/^M^/d' proba02.txt 

or

sed -e 's/\n//' proba02.txt 

Unfortunately none of above works. I'm using sed ver. 4.1.4 and 'Konsole' application under KDE.

Is this problem specific to Kubuntu? Help!

Kind regards,
Maciej

---

### Post by colo on 2006-09-26
```
sed "/^$/d"
```

should do the trick.

---

### Post by mslonik on 2006-09-26
Yes, I agree, it should do the trick. But it does not. That is a problem.

---

### Post by colo on 2006-09-26
```
colo@spareparts:~$ echo -e "line1\n\n\nline2\n\n\nline3" | sed "/^$/d"
line1
line2
line3
colo@spareparts:~$ sed --version
GNU sed version 4.1.5
```

(Edgy from today)

---

### Post by mslonik on 2006-09-27
Thanks a lot Colo. That shed some light on a problem. The core of a problem was that a file that I tried to remove empty lines has had \r\n sequence at the end of each line. To remove such a combination:

sed -e 's/.$//;/^$/d' proba04.txt

Thanks again!
Maciej (mslonik)

---

### Post by mslonik on 2006-10-02
Dear Colo,

By the way, can you help me with the following sed tasK:

There is a file (1temp1.txt) with the following line:
[http://abra.ka.dabra/20060927-one-two/1000/002.jpg](http://abra.ka.dabra/20060927-one-two/1000/002.jpg)

I need sed command that will replace anything before and after
20060927-one-two

I tried something like this:
sed -e 's/.\+\/\///;s/.*\///' 1temp1.txt

but it replaces the longest pattern that fits to specified search pattern, so as a result I get just:
002.jpg

Any ideas?

Kind regards,
mslonik (Maciej)

---

### Post by colo on 2007-03-02
Hey mslonik,

sorry, haven't checked the forums for a few months - are you still in need of a solution for the problem?

Regards,
- colo

---

### Post by mslonik on 2007-03-02
Hey colo,

Thanks a lot for your reply. In the meantime I've mastered "sed" editor by myself, with help of guides that I've found in Internet. Anyway I appreciate your help :-]

Kind regards,
Maciej (mslonik)

---

