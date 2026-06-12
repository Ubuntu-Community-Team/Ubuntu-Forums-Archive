---
title: "Need help with shell script"
date: 2012-03-25
forum: Programming Talk
---

### Post by gooch1025 on 2012-03-25
Hey guys,

I'm trying to write a shell script that searches and replaces a string in all text files in the current working directory and sub-directories. When used in the terminal, this command works perfectly:

```
find ./ -type f | xargs sed -i 's/abc/123/' *.txt

```However, when running in a shell script, the command above doesn't do anything. Hopefully one of you guys can help me. Here is my script:

```
#!/bin/bash

#Function For TXT String Replace
function replace {
clear
echo
echo -n "Enter the string that you want to replace: "
read oldstring
echo
echo -n "Enter your new string: "
read newstring
echo
echo "Editing all .txt files..."
find ./ -type f | xargs sed -i 's/"$oldstring"/"$newstring"/' *.txt
sleep 1
clear
exit
}

#Start Script
$"replace" 
```

---

### Post by matt_symes on 2012-03-25
Hi

I prefer to use -exec with find.

```
matthew@matthew-Aspire-7540:~/test$ cat t.sh 
#!/bin/bash

#Function For TXT String Replace
function replace {
clear
echo
echo -n "Enter the string that you want to replace: "
read oldstring
echo
echo -n "Enter your new string: "
read newstring
echo
echo "Editing all .txt files..."
find * -type f -name "*.txt" -exec sed -i "s/$oldstring/$newstring/" {} \;
sleep 1
#clear
exit
}

#Start Script
replace
matthew@matthew-Aspire-7540:~/test$
```

This is a test.

```
matthew@matthew-Aspire-7540:~/test$ ls
text2.txt  text.txt  t.sh
matthew@matthew-Aspire-7540:~/test$ cat text.txt text2.txt 
a a

c

matthew@matthew-Aspire-7540:~/test$ 
```

```
+ echo

+ echo -n 'Enter the string that you want to replace: '
Enter the string that you want to replace: + read oldstring
a
+ echo

+ echo -n 'Enter your new string: '
Enter your new string: + read newstring
b
+ echo

+ echo 'Editing all .txt files...'
Editing all .txt files...
+ find text2.txt text.txt t.sh -type f -name '*.txt' -exec sed -i s/a/b/ '{}' ';'
+ sleep 1
+ exit
matthew@matthew-Aspire-7540:~/test$
```

```
matthew@matthew-Aspire-7540:~/test$ cat text.txt text2.txt 
b a

c

matthew@matthew-Aspire-7540:~/test$
```

If you need global replace the use the g option on sed

Kind regards

---

### Post by WasMeHere on 2012-03-25
> **gooch1025 said:**
> Hey guys,

I'm trying to write a shell script that searches and replaces a string in all text files in the current working directory and sub-directories. When used in the terminal, this command works perfectly:

```
find ./ -type f | xargs sed -i 's/abc/123/' *.txt

```However, when running in a shell script, the command above doesn't do anything. Hopefully one of you guys can help me. Here is my script:

```
#!/bin/bash

#Function For TXT String Replace
function replace {
clear
echo
echo -n "Enter the string that you want to replace: "
read oldstring
echo
echo -n "Enter your new string: "
read newstring
echo
echo "Editing all .txt files..."
find ./ -type f | xargs sed -i [COLOR="Red"]'[/COLOR]s/"$oldstring"/"$newstring"/[COLOR="Red"]'[/COLOR] *.txt
sleep 1
clear
exit
}

#Start Script
$"replace" 
```
Try to remove the single quotes [COLOR="Red"]'[/COLOR], because I think they stop the substitution of the shell variables.

---

### Post by gooch1025 on 2012-03-25
matt_symes,

Your command worked perfectly! Thank you so much, this little script is going to save me a lot of time. That find command was tricky lol.

---

