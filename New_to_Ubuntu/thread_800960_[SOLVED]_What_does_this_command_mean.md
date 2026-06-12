---
title: "[SOLVED] What does this command mean?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sharks on 2008-05-20
I want to know what this mean when compiling a kernel:

cp /boot/config-`uname -r` .config && make oldconfig

---

### Post by Joeb454 on 2008-05-20
Copy /boot/config-`uname -r` to .config (in your current directory I assume) then make oldconfig.

And `uname -r` just executes that command and uses the output of it, which for me is ```
:~$ uname -r
2.6.24-16-generic
```

---

### Post by bartcramer on 2008-05-20
Indeed. the backquotes ` (not ' !!) means: replace the output of the command in the current command. In my case to:   

cp /boot/config-2.6.23.15-80.fc7PAE .config && make oldconfig

&& means: execute the second command only if the first command did not give an error (i.e. when the exit code is 0). 

HTH.

---

### Post by graham-cracker on 2008-05-20
The '&&' means, execute the first part, then when finished (if the first part worked correctly), execute the second. So  you can think of the command as actually two command.
I can take a stab at the first part:
```
cp /boot/config-`uname -r` .config
```
The backwards single quotes tell the terminal to first execute this portion of the command and fill in the output. uname -r will output your current kernel release. On my system, uname -r outputs this:
2.6.22-14-rt
so it will take the previous command and what it will finally execute will look something like this:
```
cp /boot/config-2.6.22-14-rt .config
```
This will take your current kernel configuration file and copy it to .config within the current working directory.
The second part, I'm not quite sure, but I think this will configure your kernel based on whatever your previous setting were (as detailed in the .config you just copied into the working directory). Someone correct me on this if I'm wrong.

---

### Post by jingo811 on 2008-05-20
```
bill@gates$ uname -r
2.6.20-16-generic
```

Like the guys before me said, so instead of you typing in your specific kernel version manually.  You use backticks ( `command` ) to transport the values from your command into your "outer" command syntax explained with bad english :)
```
cp /boot/config-`uname -r` .config && make oldconfig
cp /boot/config-`2.6.20-16-generic` .config && make oldconfig
```

The ( && ) stands for the logical AND operator.  Which means if the first  part of the command line is OK. 
```
cp /boot/config-`uname -r` .config
```
And the second part of the command line is OK.
```
make oldconfig
```

Then your entire command line syntax (bad english again) will execute.
But if either of the first or second part doesn't give you an OK then none of the 2 command parts will execute.

If I have understood shell scripting correctly, still a newbie scripter.
The "make oldconfig" probably means compile the script "oldconfig" into a working program on your PC.

---

### Post by bartcramer on 2008-05-20
> **jingo811 said:**
> 
The ( && ) stands for the logical AND operator.  Which means if the first  part of the command line is OK. 
```
cp /boot/config-`uname -r` .config
```
And the second part of the command line is OK.
```
make oldconfig
```

Then your entire command line syntax (bad english again) will execute.
But if either of the first or second part doesn't give you an OK then none of the 2 command parts will execute.



A slight error here: if the first command has an error, the second will not even be tried (*because* there is an error). The AND operator can only succeed if both its conjuncts succeed, and if the first one doesn't, the second shouldn't even be tried...

---

### Post by BDNiner on 2008-05-20
How do i type back ticks?

---

### Post by Joeb454 on 2008-05-20
On my keyboard they're on the key next to the number 1 :)

---

### Post by jingo811 on 2008-05-20
> **BDNiner said:**
> How do i type back ticks?
Shift + (back tick key) + (back tick key) = SHORYUKEN!!!!
Shift + ( ` key ) + ( ` key ) = SHORYUKEN!!!! :)
[IMG]http://i26.tinypic.com/dow6xf.jpg[/IMG]

> **bartcramer said:**
> A slight error here: if the first command has an error, the second will not even be tried (*because* there is an error). The AND operator can only succeed if both its conjuncts succeed, and if the first one doesn't, the second shouldn't even be tried...

Mentally that sounds right but technically I think I'm still correct when looking at logical AND, OR and NOT operators from a circuit, light bulb point of view :) The second part will be tried me thinks.

[IMG]http://i28.tinypic.com/2jbo8jt.png[/IMG]
....................................................
[IMG]http://i28.tinypic.com/2j2x1ms.png[/IMG]
....................................................
[IMG]http://i32.tinypic.com/2w4z4nr.png[/IMG]

---

### Post by bartcramer on 2008-05-20
We're getting slightly off-topic here... but: 

[http://www.livefirelabs.com/unix_tip_trick_shell_script/june_2003/06232003.htm](http://www.livefirelabs.com/unix_tip_trick_shell_script/june_2003/06232003.htm)

To not look at the second conjunct if the first conjunct is false, is a technique called 'minimal evaluation': [http://en.wikipedia.org/wiki/Minimal_evaluation](http://en.wikipedia.org/wiki/Minimal_evaluation)

It is used here to prevent the (costly) command 'make oldconfig' in case the copying went wrong (for example, disk full).

---

### Post by jingo811 on 2008-05-20
ic :) learnt something new today.

---

