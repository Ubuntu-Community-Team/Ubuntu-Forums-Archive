---
title: "Compare lines between two txt files"
date: 2017-08-29
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-29
Hello folks,

I am searching to a command where I can compare each line between two .txt files.
On first txt file I have this:
```

785 banana
458 fruta
444 pera
444 ananas
214 castanha
864 cenoura

```
And on second txt files I have this:
```

785 bananasdf
458 fruta
474 pera
444 ananassdf
214 castanhasdfsd
864 cenourasdf

```


I need find a way to compare this two list and put on log.txt file a report with only lines it is diffent. But, I only want compare each line from 4 character. For exemple, the first line, on each files, only compare between "banana" with "bananasdf".
I am trying a program "diff". Firstly I was trying with program "uniq", but I can't find a good way to this works. Therefore I am trying with software "diff". What do you think about this?


I am thinking use diff and grep program to handle the report of the program "diff". What do you think about this?
Thanks
[B]
[UPDATE1][/B]
I don't know which sort has list in two txt files. Therefore, when I compare first line with lines inside the second txt files I need compare this line with all lines present inside second txt files, thanks

---

### Post by aromo2 on 2017-08-29
Can you please rephrase UPDATE 1? Perhaps provide examples? I couldn't get what you were trying to say.

---

### Post by HermanAB on 2017-08-29
There is a program called 'cut' that can be used to select text on a line column basis.

I would try to rewrite the two files first to remove the junk on the left, then run diff on the new files.

---

### Post by sed_faster on 2017-08-29
Hello folks,

Sorry, but my english it is not the best!
I will try explain my goal through an example:

I have two files .txt:
[B]First:
[/B]```

785 banana/carrot
458 fruit/5625
444 pear
444 ananas
214 chestnut
864 carrot

```

**Second:**
```

245 banana/carrot
dsf fruit
343 carrot
243 pear
356 ananas
663 chestnut

```



I need create a report where I can see only differ lines between this two files.
For example, the report about this two examples files will can be:
```

Exist only first.txt -> 458 fruit/5625
-----------------
Exist only second.txt -> dsf fruit

```

The program don't consider the first three characters.
Di I explain it well?
Thanks

---

### Post by papibe on 2017-08-29
Hi Edgar_Oliveira.

Try this:
```
diff <(cut -c4- first.txt) <(cut -c4 second.txt)
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by SunnyDaze on 2017-08-30
You can open the text files up in **Meld**, and it will break down the differences for you, side-by-side, line-by-line, in a nice graphical manner.

If you want a command line that shows added and deleted lines, then **diff** is what you are looking for.

There is a great GitHub class at UDacity.com that includes how to use **diff** in conjunction with **git** and **Sublime Text Editor**.

---

### Post by HermanAB on 2017-08-30
Meld is a very good suggestion: 
$ sudo apt install meld

You can go to the Edit, Preferences tab and create a filter to ignore the leading numbers, something like ^[0..9]* may work.

---

