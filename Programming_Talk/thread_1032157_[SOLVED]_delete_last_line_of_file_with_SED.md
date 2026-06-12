---
title: "[SOLVED] delete last line of file with SED"
date: 2009-01-06
forum: Programming Talk
---

### Post by b-boy on 2009-01-06
Hi guys 


I have a file and I would like to remove the last line so this is what i have done
```
sed -e '$d' file>newfile
```

this does the job but the problem I am having is SED changes the format of my file 

File before SED

hello world 
how are you

File after SED

hello world how are you


i would like the format to remain the same how can i do that?

---

### Post by ndefontenay on 2009-01-06
It could be that sed deletes your carriage return no?
It's not really sed changing the format. 

It just does what you tell him to do.

A good way to test is, try to ask sed to find and delete one of the word existing in your file and see if it still changes the format. That way you'll be certain that it deletes your carriage return or just plainly (and stupidly) changes your file format.

---

### Post by ghostdog74 on 2009-01-06
it should work fine. another way perhaps
```

numlines=`wc -l file`
numlines=`expr $numlines - 1`
head -$numlines > newfile

```

---

### Post by b-boy on 2009-01-06
> **ndefontenay said:**
> It could be that sed deletes your carriage return no?
It's not really sed changing the format. 

It just does what you tell him to do.

A good way to test is, try to ask sed to find and delete one of the word existing in your file and see if it still changes the format. That way you'll be certain that it deletes your carriage return or just plainly (and stupidly) changes your file format.

ok you were right i change just a word in the file and the format was the same ....so how do i apply this to what I am trying

---

### Post by b-boy on 2009-01-06
sorry guys but I was wrong it was echo that deleted the carrage not sed any idea how i can get echo to keep the carrage

---

### Post by b-boy on 2009-01-06
Solved

I just used the sed -i option and it solved my problem as i did not have to write to a new file .It just edited the current file ...thanks

---

