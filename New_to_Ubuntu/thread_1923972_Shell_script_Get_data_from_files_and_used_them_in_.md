---
title: "Shell script: Get data from files and used them in while conditions"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by zinonas on 2012-02-11
Hello guys,

i have to make as soon as possible the following program using shell scripting, but unfortunately i don't have the knowledge.


read first line of break_out.txt (each line contains a number)
counter=0
read file send. txt line by line (each line contains a number)
read file received.txt line by line (each line contains a number)
while number.send > number.break_out and number.received > number.break_out and counter <3421
   diff send.txt received. txt and save output to a new file (but start from specific line where the conditions are satisfied, not from the beginning of the files)
   counter++


Please, it's urgent!

Thank you in advance!

Zinon

---

### Post by sisco311 on 2012-02-11
Hi and welcome to the forums!

Check out BashFAQ 001 (link in my signature).

Is this your homework?

---

### Post by zinonas on 2012-02-11
> **sisco311 said:**
> Hi and welcome to the forums!

Check out BashFAQ 001 (link in my signature).

Is this your homework?

Thank you very much! It's so kind of you!

No, this is not my homework. 

I have to make this in order to get some results for my phd. I'm newbie in ubuntu. I tried to make my program in windows but a friend of mine told me that is easier using linux based os.

I must get results until tomorrow and know i'm very confused...

---

### Post by sisco311 on 2012-02-11
Where did you get stuck?

---

### Post by zinonas on 2012-02-11
> **sisco311 said:**
> Where did you get stuck?

At the point where I have to go to a specific line of send.txt file where number.send > number.break_out. I have no clue how i can manage this. And afterwards, i want to save to a new file the result of diff send.txt received.txt for e.g. only for numbers 60 - 3201. The numbers are written in one column in files respectively.

---

