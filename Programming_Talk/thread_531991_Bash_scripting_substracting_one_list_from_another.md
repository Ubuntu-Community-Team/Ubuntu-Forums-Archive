---
title: "Bash scripting: substracting one list from another"
date: 2007-08-22
forum: Programming Talk
---

### Post by Jonne on 2007-08-22
Hi,

I have a list of e-mail addresses, and i need to remove the addresses that are in that list if they are listed in another list (i think i used the word 'list' too much in this sentence).

I'll give an example:
list1.txt (the original list with addresses):
item1
item3
item4
item5

list2.txt (addresses that don't need to be in list1)
item1
item2
item5
item6

So the result I need is a new list with the foillowing:
item3
item4

How would you do this?

---

### Post by ghostdog74 on 2007-08-22
```

awk 'FNR==NR{ array[$0];next}
 { if ( $1 in array ) next
   print $1}
' "list2" "list1"


```
output:
```

# ./test.sh
item3
item4


```

---

### Post by cwaldbieser on 2007-08-22
Assuming that the items are not repeated in a single list:
```

$ sort list1.txt list2.txt | uniq -u

```

---

### Post by sacherjj on 2007-08-22
> **cwaldbieser said:**
> Assuming that the items are not repeated in a single list:
```

$ sort list1.txt list2.txt | uniq -u

```

This returns item#s that are only in one of the two lists, but not exactly what the original poster needs.

Not sure exactly how I would do it though.  One thing is that you probably need a Ucase or Lcase operation on the email addresses to make sure you are properly filtering duplicates.

---

### Post by Arndt on 2007-08-22
> **Jonne said:**
> Hi,

I have a list of e-mail addresses, and i need to remove the addresses that are in that list if they are listed in another list (i think i used the word 'list' too much in this sentence).

I'll give an example:
list1.txt (the original list with addresses):
item1
item3
item4
item5

list2.txt (addresses that don't need to be in list1)
item1
item2
item5
item6

So the result I need is a new list with the foillowing:
item3
item4

How would you do this?

The command 'comm' may be useful.

---

### Post by sacherjj on 2007-08-22
That is pretty slick.

```
comm -23 list1.txt list2.txt
```

Learn something new every day.

Is there a way to send in a ```
tr list1.txt A-Z a-z
``` instead of just the file, for lower casing?  Not sure how to do a double pipe.

---

### Post by Jonne on 2007-08-22
Argh, i can't believe it. I actually looked at comm, but in my stupidity I did
```
comm -23 list1.txt list2.txt
```
because some apps allow you to add more than one option after the - .

I think it also had problems with Windows line endings in the original files.

Anyway, I'd already done it in a server-side script (which was about 30 lines, with database calls and stuff), but I guess this is a common problem, and hopefully someone learnt something today (I know I did).

---

### Post by sacherjj on 2007-08-22
comm worked for me when I used -23.  I actually changed my post to that above after trying it in a script.

---

### Post by Jonne on 2007-08-22
I guess it was a newline thing then. At work I'm still kinda forced to use Windows, and I have ubuntu living in vmware just to have a decent CLI.

At home it's ubuntu all the way, though.

---

### Post by pmasiar on 2007-08-22
you can use Python instaed of bash, and run Python on windows. With os and os.path modules, you can do even crossplatform scripts. :-)

```


ignore = open('emails_ignore.txt').readlines()

for line in open('emails_check.txt'):
    email_found = 0
    for email in ignore:
        if email in line:
              email_found = 1
    if not email_found:
        print line

```

---

