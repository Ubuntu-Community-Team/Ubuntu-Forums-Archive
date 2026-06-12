---
title: "WOW Easy Python Script Not Working?"
date: 2013-01-08
forum: Programming Talk
---

### Post by CaseyC on 2013-01-08
What is wrong here? 

```

while True: 
       print("Hello, enter STOP to stop")
       varQ = str(input("Input: ")
       if var == "STOP":
               break

```

---

### Post by sanderj on 2013-01-08
tip: line 3 is your problem ...

---

### Post by CaseyC on 2013-01-08
Sorry this is my line 3

varQ = str(input("Input: "))


I had to type it by hand it does contain 2 )'s at the end.

---

### Post by CaseyC on 2013-01-08
See attachments.

---

### Post by sanderj on 2013-01-08
> **CaseyC said:**
> Sorry this is my line 3

varQ = str(input("Input: "))


I had to type it by hand it does contain 2 )'s at the end.

OK. Variable name is also correct?

So do you realise that that line is the problem? Did you Google how to get input in Python? If Google gives you a hit on stackoverflow, use that ...

BTW: I'm not going to write the script for you. That won't help you very much. I think it's better you find out how debug it yourself ...

---

### Post by CaseyC on 2013-01-08
Got it :) 

I used something similar to input int's into varibles but strings were handled correctly. 

```
varQ = raw_input("Input: ") 
```


Was what I found worked however I am unsure if that is best practice. Research and learning will continue & thanks!

---

