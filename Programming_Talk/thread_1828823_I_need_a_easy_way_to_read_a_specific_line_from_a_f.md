---
title: "I need a easy way to read a specific line from a file c++"
date: 2011-08-19
forum: Programming Talk
---

### Post by 7cardcha on 2011-08-19
Lets say I have a file like this:

'Line 1'
"Line 2"
"Line 3"

How would I cout out a specific line from the file?

---

### Post by Bachstelze on 2011-08-19
If you want an easy way, don't reinvent the wheel and just use sed or grep to get the desired line, and feed it to the program on standard input. ;)

```
sed -n 'N'p input.txt | program
```

will pass the Nth line of input.txt to the program.

---

### Post by fdrake on 2011-08-19
> **7cardcha said:**
> Lets say I have a file like this:

'Line 1'
"Line 2"
"Line 3"

How would I cout out a specific line from the file?

you can try this

```
less file.c++ | nl -s "~"| grep " num~" | cut -d "~" -f 2
```

where in num you put the line number you wish to see.  just make sure there are not "~" since cut uses it as a delimiter

---

### Post by fdrake on 2011-08-19
> **Bachstelze said:**
> If you want an easy way, don't reinvent the wheel and just use sed or grep to get the desired line, and feed it to the program on standard input. ;)

```
sed -n 'N'p input.txt | program
```

will pass the Nth line of input.txt to the program.

damm i have to start using sed more often... lol

---

### Post by 7cardcha on 2011-08-19
No No and No. I meant USING c++ how would you do it. 
Thanks anyways to those who have already answered.

---

### Post by Bachstelze on 2011-08-19
Why do you absolutely have to use c++? Sounds like homework...

---

### Post by cgroza on 2011-08-19
You can do it using an std::ifstream and std::getline.
You can loop through the file like this and identify the line you need.

```

string my_line;
ifstream my_file("my_path_here_as_C_string");
while(!my_file.eof()) my_line = getline(my_file);

```Do you want to get a specific line number or it can be anywhere and respect some criteria?

---

### Post by 7cardcha on 2011-08-19
No i don't have to use c++ and its not homework. I am making a program for fun and wondered how to do this. I need to be able to print out a certain line. In python you would do this with linecache.

---

### Post by 7cardcha on 2011-08-20
Common guys I googled this for a half an hour.

---

### Post by 7cardcha on 2011-08-20
Bumpity bump bump.

---

### Post by simeon87 on 2011-08-20
What exactly did you attempt before we post the answer? All you need to do is

- Read the file, line by line.
- Count the lines as go you.
- Store the line you want in a variable.
- Use the content of the variable somewhere else.

---

### Post by cgroza on 2011-08-20
> **7cardcha said:**
> Common guys I googled this for a half an hour.
My above post gives you a way to do it. 
It opens the file, loops through it and stores the current line in a variable. From there, you should be able to handle it yourself.

---

### Post by 7cardcha on 2011-08-20
Ok that will work

---

### Post by cgroza on 2011-08-20
> **7cardcha said:**
> Ok that will work
You are welcome.

---

