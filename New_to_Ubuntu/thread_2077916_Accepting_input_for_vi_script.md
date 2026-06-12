---
title: "Accepting input for vi script"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by subiza on 2012-10-29
I've been trying to write the simplest script, but I can only find a few sources that may or may not be right for what I'm looking for... I have an old textbook as well, but even my teacher had said it was useless.
Basically I'm trying to write a script that clears the screen, 
says "Hello!", 
has 5 blank lines before that sentence, 
asks a question, 
accepts an input,
touches a file in the home directory,
clears the screen again,
and long lists the home directory contents of the user.
 
This is what I have:
 
```
 clear
echo "Hello!"
echo
echo
echo
echo
echo
echo -n "What do you want to call the file?"
read -e INPUT
touch INPUT.txt
clear
ls
```
 
...please help me. So which parts have I got wrong? :confused:

---

### Post by mahdiolfat on 2012-10-29
Hi,

It is unclear what your problem is. Please elaborate.
The only thing I can see that does not make sense to me in your script is that you do not do anything with the input from the "read" command.
[Edit: or maybe you are trying to do something with it that I can't understand, why does your input variable (INPUT) and the .txt file have the same name?]

Regards,
Mahdi

---

### Post by subiza on 2012-10-29
Well firstly I want to know if I even have the coding right, haha
 
And yes, I would like to make the input taken from the user to that INPUT.txt file. 
(I think I meant to have that initial INPUT as $INPUT or $ANSWER variable...) So maybe 
```
read -e INPUT as $ANSWER
``` ....?
And then some more code for actually creating the INPUT.txt file that I have no idea what it could be. :-k

---

### Post by Vaphell on 2012-10-29
```
**$** ls
**$** read -p "name of file: " **file**
name of file: new_file
**$** > "**$file**.txt"
**$** ls
new_file.txt
```

if you want to use the contents of the input variable, use it with $ in front of it.
**> "$file.txt"** redirects nothing to $file.txt - in other words creates it with 0 size
but **touch "$file.txt"** is ok too.
if you want to have some initial content there:
```
echo "content" > "$file.txt"  # to overwrite
echo "content" >> "$file.txt"  # to append
```


Besides generally avoid all-caps names, there are plenty all-caps environment variables that you can overwrite by accident if you accidentally pick the 'right' name.

---

