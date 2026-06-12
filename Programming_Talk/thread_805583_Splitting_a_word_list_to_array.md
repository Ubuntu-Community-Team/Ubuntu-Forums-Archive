---
title: "Splitting a word list to array"
date: 2008-05-24
forum: Programming Talk
---

### Post by true_friend on 2008-05-24
Hi folks
I am C# learner want to make array of a word list. Words are written like this
abc
def
ghi
jkl
I mean every word in new line. How can I convert it into an array. I tried to use Array.Split(\n) but it doesn't work. Split method only accepts space as a criteria (as far as I tried).
Any ideas?
Regards

---

### Post by Lau_of_DK on 2008-05-24
> **true_friend said:**
> Hi folks
I am C# learner want to make array of a word list. Words are written like this
abc
def
ghi
jkl
I mean every word in new line. How can I convert it into an array. I tried to use Array.Split(\n) but it doesn't work. Split method only accepts space as a criteria (as far as I tried).
Any ideas?
Regards

Are you reading the lines of a file and want to pick them up in an array as you go along?

[PHP]
ArrayList ar_Words = new ArrayList()
foreach line in file {
    ar_Words.add(file.ReadLine()
}

[/PHP]

Its been a while since I used C#, but my memory tells me thats how I would do it :)


/Lau

ps. In Windows, ArrayList is in System.Collections

---

### Post by smartbei on 2008-05-24
If you are working on Windows, then perhaps the problem is that the line seperator is not \n, it is \r\n.

---

### Post by Lau_of_DK on 2008-05-24
> **smartbei said:**
> If you are working on Windows, then perhaps the problem is that the line seperator is not \n, it is \r\n.

I imagine it would still work, you'd just get an extra \r and the end of every string.

/Lau

---

### Post by smartbei on 2008-05-24
I was not sure what the OP meant by "doesn't work". Perhaps what he meant was that he gets the words but with an extra character appended - that fits in with what he said regarding it working only with spaces.

---

### Post by ajackson on 2008-05-24
> **true_friend said:**
> Hi folks
I am C# learner want to make array of a word list. Words are written like this
abc
def
ghi
jkl
I mean every word in new line. How can I convert it into an array. I tried to use Array.Split(\n) but it doesn't work. Split method only accepts space as a criteria (as far as I tried).
Any ideas?
Regards
If we assume temp holds the string you wish to parse and arr is the arraylist
```
arr = temp.Split('\n');
```
Should do what you want.

---

