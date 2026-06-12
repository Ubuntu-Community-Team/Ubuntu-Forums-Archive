---
title: "[SOLVED] iPod linking"
date: 2008-09-28
forum: Programming Talk
---

### Post by Stoodle on 2008-09-28
I'm writing a program that cuts up text files into smaller pieces for the iPod. I'm almost done except for one problem: The iPod keeps giving me a "Bad link, file not found" error.

Does this look syntactically incorrect?
```
<A HREF=file://part_1>Next</A>
```To let you know, the file is there. I can select it in the iPod menu. I would like to link to it however, and that's where I'm having a problem. My only guess is that in my program, it adds a "" to the file name. However, the files are still valid when I select them and I'm doing the same thing when creating the links.

Even when I hardcoded a valid link, I got an error.

---

### Post by Stoodle on 2008-09-29
Bump???

---

### Post by pp. on 2008-09-29
I am too lazy to look it up, but I would say that the part of the URL which starts with a double slash was the host name. The File path part either starts with a slash if it starts from root, or it does not start with a slash but with the first character of the directory or file name.

Also, I would enclose attribute values in quotes.

Also, be aware that in a URL not all characters are valid. The underscore ought to be ok, though.

---

### Post by Mindzai on 2008-09-29
Try:

```
<a href="file:///part_1">Next</a>
```

Assuming part_1 is sitting in /

if for example part one is in /my/path/part_1, you would use:

```
<a href="file:///my/path/part_1">Next</a>
```

---

### Post by Stoodle on 2008-09-29
I tried

<a href="file:///part_1">Next</a> (without a third slash because I wanted to use relative locations) but it didn't work. Instead of "", I'm going to try " ".

The "" character (what is that anyway? Does it take up memory?) was suggested to me for a program I'm writing in C++ using the stringstream function to label files "part_[num]" and increment the number.

---

### Post by Mindzai on 2008-09-29
its just the correct (xhtml-wise) syntax for the anchor (a) tag, you could no quotes and it would work the same, just wouldn't be xhtml compliant and as a web developer i have these habits ingrained :D

As to why its not working, I cant think of anything else to suggest, the link is syntactically correct.

---

### Post by Stoodle on 2008-09-29
XD!
Someone passed me the idiot ball. I forgot the .txt ending for the link. So! Correct syntax for future reference is 

```
<A HREF="part_1.txt">back</A>
```
Now, in C++ code, that's 
```

//Going backwards
         if(i>0 && (fileResults.st_size/3699)>1)
         {
             fNum.str("");
             fNum<<--i;
             outFile << "\n<A HREF=\"part_"+fNum.str()+".txt\">back</A>";
             i++;
         }
//Going forward
         if(i<(fileResults.st_size/3699)-1 && (fileResults.st_size/3699)>1)
         {
             fNum.str("");
             fNum<<++i;
             outFile << "\t<A HREF=\"part_"+fNum.str()+".txt\">Next</A>";
             i--;
         }

```

---

### Post by Mindzai on 2008-09-29
ah i assumed you were referencing an extentionless file as we are in unix world. it's easy to miss these things when you are staring at the same code for too long!

---

