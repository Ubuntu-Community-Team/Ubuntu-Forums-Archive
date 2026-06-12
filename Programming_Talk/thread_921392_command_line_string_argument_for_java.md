---
title: "command line string argument for java"
date: 2008-09-16
forum: Programming Talk
---

### Post by MeLight on 2008-09-16
Hi all,
my first post here, so be gentle with me :D
I'm working on a string tokenizer in Java, until now I got the texts from file inputs and all was good. Now we'll be needing to input the strings through command line (run it from PHP scripts and such), ie as an args[] argument. The problem is that the strings contain quotes (') which make the execution impossible. 
The question is can I escape those somehow or pass the text in some other way? thanx (whew that was long)

---

### Post by drubin on 2008-09-16
Try this
```
java classname "first's another first's" second third
```

**EDIT:** I forgot welcome. Nice to have you here.

---

### Post by drubin on 2008-09-16
wait also if you are passing the vars from a php script. Maybe try 

system/shell_exec('java...etc'.add_slashes($params));

this will do
```
java ... how\'s it going is my param\'s
```

array in java
0=>how's
1=>it
2=>going
3=>is 
4=>my
5=>param's

Not 100% sure if this is what you would like but might point you in the right direction.

---

### Post by MeLight on 2008-09-17
Thanx a bunch :D Worked like magic

---

