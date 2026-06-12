---
title: "awk print the body of an email"
date: 2012-06-16
forum: Programming Talk
---

### Post by maddog21 on 2012-06-16
I have fetched a couple of emails and stored then in /fetch/mail/oracle.txt, the displayed content is

Date:
From:
Subject:
To:
Content-Type:
---body -----
---------
Date:
From:
Subject:
To:
Content-Type:
----body -----
------
Date:
From:

I want to retrieve the body only from the emails i fetched,the problem i am having is the body doesn't have a tag,

the output should be like
email-1
----body---
email-2
----body---

---

### Post by jobix on 2012-06-17
If you know for sure that the only lines that you do not need are these:
Date:
From:
Subject:
To:
Content-type:

you could simply use "grep -v" 

e.g., grep -v "^Date:" oracle.txt | grep -v "^From:" ......[etc., etc.] > final-output.txt

The ^ means the beginning of a line.

---

### Post by lisati on 2012-06-17
Most emails have a header section followed by a blank line, followed by the body.

---

### Post by maddog21 on 2012-06-17
> **jobix said:**
> If you know for sure that the only lines that you do not need are these:
Date:
From:
Subject:
To:
Content-type:

you could simply use "grep -v" 

e.g., grep -v "^Date:" oracle.txt | grep -v "^From:" ......[etc., etc.] > final-output.txt

The ^ means the beginning of a line.
grep -v "^Date" /var/mail/oracle | grep -v "^From:" /var/mail/oracle | grep -v "^To:" /var/mail/oracle |grep -v "^Subject:" /var/mail/oracle > final-output.csv

i tried the above command but it displays everything instead of displaying the body only.

Sorry for the inconvenience, Thank you.

---

### Post by codemaniac on 2012-06-17
You can tell awk what is the start and end pattern .Something like below .

```
awk '/---body -----/,/------/{print}' email.txt
```

---

### Post by jobix on 2012-06-23
> **maddog21 said:**
> grep -v "^Date" /var/mail/oracle | grep -v "^From:" /var/mail/oracle | grep -v "^To:" /var/mail/oracle |grep -v "^Subject:" /var/mail/oracle > final-output.csv

i tried the above command but it displays everything instead of displaying the body only.

Sorry for the inconvenience, Thank you.


I guess I should have been more explicit. You should not specify the file name after the first pipe.

grep -v some-pattern filename | grep -v another-pattern | grep -v yet-another-pattern > final-output

"-v" is to exclude. | is used to direct the output from the previous operation to the next command. So, you only need the filename in the first command, i.e., before the first |

---

### Post by codemaniac on 2012-06-24
> **jobix said:**
> I guess I should have been more explicit. You should not specify the file name after the first pipe.

grep -v some-pattern filename | grep -v another-pattern | grep -v yet-another-pattern > final-output

"-v" is to exclude. | is used to direct the output from the previous operation to the next command. So, you only need the filename in the first command, i.e., before the first |

If you are using grep , you can avoid using multiple pipes and save some keystrokes .Use extended features , see below

```
egrep -v "(some-pattern filename|another-pattern|yet-another-pattern)" filename > final-output
```

---

