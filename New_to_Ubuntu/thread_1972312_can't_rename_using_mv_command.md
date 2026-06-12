---
title: "can't rename using mv command"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by jola on 2012-05-03
i'm trying to rename an abiword doc from "test" to "test1", I get this message.

 mv test test1
mv: cannot stat `test': No such file or directory

What am I missing? Thanks, jola

lubuntu 12.04
Thinkpad R51
1.5ghz
1.2 RAM
30gHD

---

### Post by sportfreak2020 on 2012-05-03
are you sure the filename dose not have any extensions that you could be missing ? or was this file made by another user for which you do not have permissions to rename or mv in this case ?!

---

### Post by marinara on 2012-05-03
make sure you are in the correct directory so that mv can find test

---

### Post by imran042 on 2012-05-03
you are forgetting the file extensions.
your command will be like,   

mv test.txt test1.txt

-mark solved, if satisfied

---

### Post by Tibuda on 2012-05-03
Linux file system is case sensitive, so make sure it is not name File or FILE instead of file

---

### Post by Hadaka on 2012-05-03
ls -l test      * if it shows up..then you are in YOUR home directory*

*if not...you arent*

---

### Post by Hadaka on 2012-05-03
or...maybe test never was written..or saved.

to verify your mv function is working.
try this.

echo "this is a test" > newtest
cat newtest  #it should say this is a test
touch newtest1
cat newtest1   #it will be blank#
mv newtest newtest1
cat newtest1    #it should say  this is a test#


fun with command lines...Enjoy

---

