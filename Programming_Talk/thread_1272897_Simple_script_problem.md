---
title: "Simple script problem"
date: 2009-09-22
forum: Programming Talk
---

### Post by RobotAlligator on 2009-09-22
I'm running a console-based program with a script, and I'm having trouble inputting more than one prompt..

in other words, ill do something like echo 0.31223 | ./add and then I get prompted for the next number.  I've tried just echoing another number but it runs it outside the program, i've tried sending it to ./add again but it just runs the program again. google has been no help whatsoever due to the awkward wording my situation

---

### Post by RobotAlligator on 2009-09-22
I'm running a console-based program with a script, and I'm having trouble inputting more than one prompt..

in other words, ill do something like echo 0.31223 | ./add and then I get prompted for the next number. I've tried just echoing another number but it runs it outside the program, i've tried sending it to ./add again but it just runs the program again. google has been no help whatsoever due to the awkward wording my situation

---

### Post by hailtothethief on 2009-09-22
I've found this to be very helpful: [http://www.linuxconfig.org/Bash_scripting_Tutorial]("http://www.linuxconfig.org/Bash_scripting_Tutorial")

You need to use the **read** command.

Something like

```
read NUM
echo $NUM
```

is probably what you're looking for.

---

### Post by RobotAlligator on 2009-09-22
i don't understand, that just saves my number to a variable but doesn't help me input it to the 2nd prompt in my program any easier.  ill check out the link

---

### Post by hailtothethief on 2009-09-22
Well, this will do what you're looking for right now. I trust that you'll teach yourself now that you have a resource to start with.

```
read NUM <&1
read NUMTWO
echo $NUM + $NUMTWO = $(($NUM + $NUMTWO))
```

---

### Post by yabbadabbadont on 2009-09-22
```
while read newValue
do
./add $newValue
done < fileWithValuesToAddOneValuePerLine

```
Try something like that and see if it (or a variation) does what you need.

Edit: Actually, that only works if your "add" program only takes one parameter on the command line.  If it needs more than that, then you can either echo multiple values (like your example), or have the proper number of values on each line of the data file in my example.

```
echo value1 value2 value3 ... valueN | ./add
```

Edit2: If the "add" program expects multiple values, but each one must be entered separately, then either use my first example, or you can try modifying your "echo" statement to include either newline escape codes '\n' or perhaps carriage return escape codes '\r'.  

```
echo value1\nvalue2\n | ./add
```
or maybe
```
echo value1\rvalue2\r | ./add
```

It really just depends upon how the "add" program was written to expect its arguments.

---

