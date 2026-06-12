---
title: "experimental esoteric scripting language"
date: 2007-01-02
forum: Programming Talk
---

### Post by Wybiral on 2007-01-02
ScripTur is a new language I'm working on that allows you to script your own turing machines!
You can download and read some about it here: [ScripTur]("http://p13.wikispaces.com/ScripTur") and if you have any questions or need help getting the hang of it, contact me via reply or PM. Here are some example scripts...

Hello World!
```

(0,72,1,2)
(0,101,1,3)
(0,108,1,4)
(0,108,1,5)
(0,111,1,6)
(0,32,1,7)
(0,119,1,8)
(0,111,1,9)
(0,114,1,10)
(0,108,1,11)
(0,100,1,12)
(0,33,1,0)

```

Binary Incrementor
```

(48,48, 1,1) (49,49,1,1) (0, 0,-1,2)
(49,48,-1,2) (48,49,0,0) (0,49, 0,0)

```

Y/N completion
```

(89, 89, 1, 2) (121, 89, 1, 2) (78, 78, 1, 4) (110, 78, 1, 4)
(0, 101, 1, 3)
(0, 115, 0, 0)
(0, 111, 0, 0)

```

As I said, this is really more of an esoteric language, not something you would want to start a serious project in. Right now it only supports console in/out but I am working on some more complicated models for handling other things (as well as a user interface for designing the machines instead of scripting them)

---

### Post by bernied on 2007-01-02
yeah, seems really intuitive

---

### Post by Wybiral on 2007-01-02
The only downside is that you have to use the ASCII character codes instead of the real characters in the script. I had to do it this way so it wouldn't read spaces or "(,)" characters as in/out values. But, there is a list here: [http://p13.wikispaces.com/ascii](http://p13.wikispaces.com/ascii)

Anyway, I've been thinking about adding multi-tape support, and possibly more complex in/out types, like "*" for any, or "!48" means any, except 48, stuff like that...

There's also the possibility of file/device in/out which would be pretty interesting. However, I don't want to add anything too complex until I make some kind of graphical interface.

---

### Post by lloyd mcclendon on 2007-01-02
looks like a complete waste of time to me

but hey if you think it's fun then whatever

---

### Post by Wybiral on 2007-01-02
> 
looks like a complete waste of time to me

but hey if you think it's fun then whatever


LOL, it's funny that you wasted your time to post that.

Anyway... Yeah, it isn't meant to be a PROGRAMMING LANGUAGE, but a scriptable turing machine maker.

Here's some links on turing machines...

[http://en.wikipedia.org/wiki/Turing_machine](http://en.wikipedia.org/wiki/Turing_machine)
[http://plato.stanford.edu/entries/turing-machine/](http://plato.stanford.edu/entries/turing-machine/)
[http://mathworld.wolfram.com/TuringMachine.html](http://mathworld.wolfram.com/TuringMachine.html)

There are plenty of simulators out there, but I haven't seen many scriptable ones.

Anyway, thanks for your time, lloyd mcclendon!

---

### Post by lloyd mcclendon on 2007-01-02
no problem son

well can you at least tell us about the code for the interpreter and what the hell all those numbers do.

---

### Post by Wybiral on 2007-01-02
I tried explaining it some on the download page... Unfortunately I'm terrible at explaining things like this.

You should do some research on turing machines.

Basically, you have states or functions. Each line in the script is a state of the turing machine. Different states have different conditions or nodes. A node is arranged like this...
(in, out, mov, jumpToLine)

If the current character that the turing machine is reading equals the in value of that node (when the turing machine is in that state (on that line)) then it changes that character to out, and moves the virtual tape in the direction of move. If mov is 1 then the next character read is to the right of the current character, -1 will move it to the left. Then it jumps to the line defined by "jumpToLine". It will only execute all of this if the current character equals the "in" character of that node character of that node. Each line/function may contain multiple conditions/nodes.

To understand the machine a little more, the nodes are checked from left to right. If it runs into a node where the current character equals the node, then it jumps to wherever that node tells it to, so to repeat a line, just make it jump to itself.

It is possible to create very complex functions using turing machines, I've managed to parse simple mathematical equations, perform simple logical conditions, etc...

BTW, the in/out values of the node's are the ascii character they represent. The input (initial state of the turing tape) is the argument passed to the interpreter.

The command to execute a script is...

```

./scriptur script_file argument

```

So, if you take that binary incrementor and save it to a file such as "binInc.sct" and you wanted to see what the binary value "10111" would be plus 1... Use this command line command...

```

./scriptur binInc.sct 10111

```

And the turing machine interpreter will read the script "binInc.sct" and create a virtual turing machine from it, then submit 10111 to it as turing tape.

---

### Post by Ben Sprinkle on 2007-01-02
This is a bit like bran f*ck.
Except non compiling. ;)

---

### Post by Wybiral on 2007-01-02
Here's a little binary adding machine I wrote...

```

(48, 48,  1, 1) (49, 49,  1, 1) (43, 43,  1, 1) (0, 0, -1, 2)
(48, 49, -1, 2) (49, 48, -1, 3) (43,  0,  1, 6)
(48, 48, -1, 3) (49, 49, -1, 3) (43, 43, -1, 3) (0, 0,  1, 4)
(48, 48,  1, 4) (49, 49,  1, 4) (43, 43, -1, 5)
(49, 48, -1, 5) (48, 49,  0, 1) ( 0, 49,  0, 1)
(48,  0,  1, 6) (49,  0,  1, 6)

```

Just save it as something like "binAdd.sct" and run it with "./scriptur binAdd.sct 111+111"

Obviously you don't need 111+111, you can use any two binary numbers and it will add them and display the results. There's probably a faster way to do it with a turing machine, but this script works fine. You can also do decimal addition too, but it's a much more lengthy script.

Here is a decimal adding machine...

```

(48,48,1,1)(49,49,1,1)(50,50,1,1)(51,51,1,1)(52,52,1,1)(53,53,1,1)(54,54,1,1)(55,55,1,1)(56,56,1,1)(57,57,1,1)(43,43,1,1)(0,0,-1,2)
(48,57,-1,2)(57,56,-1,3)(56,55,-1,3)(55,54,-1,3)(54,53,-1,3)(53,52,-1,3)(52,51,-1,3)(51,50,-1,3)(50,49,-1,3)(49,48,-1,3)(43,0,1,5)
(43,43,-1,4)(48,48,-1,3)(49,49,-1,3)(50,50,-1,3)(51,51,-1,3)(52,52,-1,3)(53,53,-1,3)(54,54,-1,3)(55,55,-1,3)(56,56,-1,3)(57,57,-1,3)
(57,48,-1,4)(48,49,0,1)(49,50,0,1)(50,51,0,1)(51,52,0,1)(52,53,0,1)(53,54,0,1)(54,55,0,1)(55,56,0,1)(56,57,0,1)
(57,0,1,5)

```

Just save that as "decAdd.sct" and execute it with something like "./scriptur decAdd.sct 123+456"

Once again, filename and input argument are up to you.

---

### Post by Grey on 2007-01-03
It looks like a REALLY unreadable version of assembly to me.  I have no idea what the numbers mean, but I would imagine that they follow a format similar to "(opcode, operand, xposition, yposition)".  Which, honestly isn't a far cry from native machine language.  But I'll just say that it could use some cleaning up.

---

### Post by Wybiral on 2007-01-03
Well, it's not exactly assembly, although it is a low-level language like it. Turing machines are sortof in their own category... I guess you can liken it to stack manipulation similar to assembly, except turing machines use an infinite stack, and any element can be accessed without having to pop it. There aren't any registers like assembly either. BrainF*ck is pretty close to a turing machine, but turing machines allow you to anylize the data that you are changing and the "stack" is infinite in both directions (left/right). Nothing has a static position, it's just relative to the current position. I'm working to add some better stuff to it, mostly interested in device in/out (sound, graphics... etc).

---

### Post by amo-ej1 on 2007-01-03
Hehe, just read the code, but in fact it's rather straightforward. It's simply state machine pushing things onto a stack. 
Only the examples are really scary looking ;)

---

### Post by Wybiral on 2007-01-03
> Hehe, just read the code, but in fact it's rather straightforward. It's simply state machine pushing things onto a stack.
Only the examples are really scary looking 
Thats a very accurate description of a turing machine.

Yeah, I wrote the scripting language and I've been playing with turing machines for a while so it probably is a little chaotic for anyone new to them. The hello world one should help though.

---

### Post by Ben Sprinkle on 2007-01-03
> **Grey said:**
> It looks like a REALLY unreadable version of assembly to me.  I have no idea what the numbers mean, but I would imagine that they follow a format similar to "(opcode, operand, xposition, yposition)".  Which, honestly isn't a far cry from native machine language.  But I'll just say that it could use some cleaning up.

No, I think they are the numeric equality to an ASCII character. ;)

---

### Post by Tomosaur on 2007-01-03
I like esoteric languages, if nothing more than a brain exercise. I analysed your Yes/No completion, let me know if I got this right:
```

(89, 89, 1, 2) (121, 89, 1, 2) (78, 78, 1, 4) (110, 78, 1, 4)
(0, 101, 1, 3)
(0, 115, 0, 0)
(0, 111, 0, 0)

```

Line 1:
If input is Y, output Y, shift to next, move to line 2.
If input is y, output Y, shift to next, move to line 2.
If input is N, output N, shift to next, move to line 4.
If input is n, output N, shift to next, move to line 4.

Line 2:
Output e, shift to next, move to line 3.

Line 3:
Output s, shift to first, terminate.

Line 4:
Output o, shift to first, terminate.

I can't use your interpretor yet because I am on Windows atm.

---

### Post by Wybiral on 2007-01-03
> Line 1:
If input is Y, output Y, shift to next, move to line 2.
If input is y, output Y, shift to next, move to line 2.
If input is N, output N, shift to next, move to line 4.
If input is n, output N, shift to next, move to line 4.

Line 2:
Output e, shift to next, move to line 3.

Line 3:
Output s, shift to first, terminate.

Line 4:
Output o, shift to first, terminate.

Yeah, exactly how it works, even down to the terminate (0 line jump). BTW, the source should all be portable, it's all standard C++. It would probably only take a few seconds to compile it on windows (if you do, I'd like that exe so I can put it on the download page, I don't have windows)

The binary incrementer is a pretty simple one (and a very command turing machine example)...

```

(48,48, 1,1) (49,49,1,1) (0, 0,-1,2)
(49,48,-1,2) (48,49,0,0) (0,49, 0,0)

```

Translates to pseudocode that looks like...

```

def func1(a):
    if a == '0': a = '0'; movePointerRight(); func1(nextChar());
    if a == '1': a = '1'; movePointerRight(); func1(nextChar());
    if a == '': a = ''; movePointerLeft(); func2(nextChar());

def func2(a):
    if a == '1': a = '0'; movePointerLeft(); funct2(nextChar());
    if a == '0' or a == '': a = '1'; end;

```

Interestingly enough, the binary adding machine is just an incrementer on one side, and a decrementer on the other, it goes until the decrementer side is gone, then it erases the "+" and the decrementer side.

---

