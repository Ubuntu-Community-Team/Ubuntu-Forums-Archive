---
title: "Python Regex and Splitting of Strings"
date: 2010-02-14
forum: Programming Talk
---

### Post by covertcj on 2010-02-14
Hi,

I'm creating an VERY basic assembler for my computer architecture class, in python and I have a few questions. I haven't programmed much in python, but was attracted due to the incredibly nice string/file parsing features, although I never can seem to figure out regular expressions. Our assembler language takes a line such as:

```
add $t1, $s1, $zero # comment
```I would like to be able to take this line and convert it to a binary representation. This I will do through the use of dictionaries that take, for instance:

```
opcode["add"]
```and return:

```
"0000"
```This is all well and good; however, I am unsure of how I will go about splitting the string. I know I could use a regex of "," in order to split by the commas, but I have no idea how to split by whitespace (do I need one for both tabs and spaces?). Most of all, I don't really know how to ignore the rest of the line after the comment character '#'. Is there a good way to do this?

Thanks,
Chris

---

### Post by oedipuss on 2010-02-14
Check out the string split() and partition() methods that are pretty useful for things like that, and also the strip() method. Oh and replace() might come in handy too. 
Look here for details [http://docs.python.org/library/stdtypes.html](http://docs.python.org/library/stdtypes.html)
Basically with line = "add $t1, $s1, $zero # comment" , something like :
```

command, sep, comment = line.partition('#')
opcode, sep, argstring = command.partition(' ')  #or replace /t with space first in case there's a tab after the opcode instead of a space
arglist = argstring.split(',')

```
possibly with some strips() to clean off whitespace.

---

### Post by Dies on 2010-02-14
Sounds like you can just use 'split' and 'startswith' but that's just from what you said and it also may not be the most efficient way.

For example to get rid of the comment you can do something like

```

line = 'add $t1, $s1, $zero # comment'
if line.find('#'):
    line = line.split('#')[0].strip()

```

which would drop anything after the # and strip any whitespace.


But I suggest you do a quick

```
sudo apt-get install devhelp python2.6-doc -y
```

That will give you local access to the python docs including the tutorial. ;)

---

### Post by covertcj on 2010-02-14
This was extremely helpful!

Thanks,
Chris

---

