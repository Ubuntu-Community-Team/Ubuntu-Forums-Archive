---
title: "REG???? how should I do it in shell programming"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-03
ok
Here: :popcorn:I have a huge collections of text files (html) and I want to write a program that go through all of the files and find all the words( or better to say the string ) of the URL address that has "YAYA" in it and put it in a now file named"adress_[the name of the file]"

So if I have a file named "toop.html" and somewhere in the file I have 
"here is the link we want you to .......www.YAYA.co.go/sdf/fg.html" I want to get that ONLY "www.YAYA.co.go/sdf/fg.html"in a new text file called "address_toop.txt". :confused:

I know that might be a big project abd trust me it is part of a bigger protect so PLEASE help me at any part you can so I could it we all of your help :)

Thanks A LOT :KS

PC plz be clear and write clear examples Do not just say "USE SED" b/c I do not know how to use it ;):lolflag:
:guitar:

---

### Post by angry_johnnie on 2008-08-03
I wouldn't know how to make a new file for each url... but you could use grep to get all urls (and the name of the file they came from) into a text file.

Supposing you have all your text files inside a directory called ~/whatever
you could (if you're just looking for YAYA):

```
grep -rs YAYA ~/whatever/* > yaya.txt
```

Then it will look, recursively, at all the files within ~/whatever, and search for the text "YAYA."  If it finds anything, it will send the output into a text file called yaya.txt.

Said output would look something like this:

> /home/yourname/whatever/some-file:[www.someurl-something-YAYA-something](www.someurl-something-YAYA-something).
/home/yourname/whatever/some-other-file:[www.someurl-something-YAYA](www.someurl-something-YAYA)

and so on...

---

### Post by ghostdog74 on 2008-08-05
that would depend on how your html files look like.
give a sample of the html files and describe how you want them to be.

---

