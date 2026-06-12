---
title: "Displaying only a specific part of command output"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2012-02-26
Hi Guys,

Could someone please tell me how to get just a part of a command's output to show up?

If I run 
```

free -t -m

```I get
```

             total       used       free     shared    buffers     cached
Mem:          2012       1867        145          0         85       1357
-/+ buffers/cache:        423       1588
Swap:         2043          2       2041
Total:        4056       1869       2187

```I'd like just  the used 423 and free 1588 to show.

I'm sure this is pretty simple and I appreciate the help!

---

### Post by The Cog on 2012-02-26
grep is the tool for this kind of thing. It only prints lines matching the search text. This works nicely:
```
free -t -m | grep s/c
```
Looking for the +/= seems obvious, but grep interprets the leading - as a command option rather than the search string so if you wanted to search for that, you need to escape the - like this:
```
free -t -m | grep \\-/+
```
or use the start-of-line symbol to hide the minus like this:
```
free -t -m | grep ^-/+
```

EDIT:
What you are doing here is piping the output of one command (free) to the input of a second command (grep), replacing the keyboard input. The | symbol is used to indicate that you want to do this and it is very common in *nix. It works on windows too, but is less well known amongst windows users. It is a very powerful technique, and many *nix tools are written to be able to be used this way.

Another example of this: the program lp is the printing program. So the command ```
ls -l | lp
``` will print your directory listing.

---

### Post by GrouchyGaijin on 2012-02-26
Hey thank you!

I have one follow up question though.
I'm trying to get just the numbers - that is none of the text.
The idea is to save that as a script and then call it though the generic monitor applet in the XFCE panel.

---

### Post by Lars Noodén on 2012-02-26
Something like this then:
```

free -t -m | awk '/-\/+/ { print $3 "\t" $4 }'

```

---

### Post by GrouchyGaijin on 2012-02-26
Thanks!

---

### Post by Bobhuber on 2012-02-26
you can also use the -c  command which picks a specific section of the string.

free -m | grep 'Mem:' | cut -c35-40

In your case this would display 145 using ' Mem:'  as the first line search parameter

---

### Post by GrouchyGaijin on 2012-02-26
> **Bobhuber said:**
> you can also use the -c  command which picks a specific section of the string.

free -m | grep 'Mem:' | cut -c35-40

In your case this would display 145 using ' Mem:'  as the first line search parameter
Thank you - that is very useful.

Could you tell me how I can add text to the output of the command?
What I mean is if I have a script that has:

```

#!/bin/bash
free -mt | grep '^-/+ buffers/cache:' | cut -c20-30

free -mt | grep 'Mem:' | cut -c10-20

``` That give me  the amount of ram in use and the total in the machine.
Is there a way I can put the words **out of** between those two numbers?

---

### Post by Lars Noodén on 2012-02-26
> **GrouchyGaijin said:**
> Thank you - that is very useful.

Could you tell me how I can add text to the output of the command?
What I mean is if I have a script that has:

```

#!/bin/bash
free -mt | grep '^-/+ buffers/cache:' | cut -c20-30

free -mt | grep 'Mem:' | cut -c10-20

``` That give me  the amount of ram in use and the total in the machine.
Is there a way I can put the words **out of** between those two numbers?

[awk](http://manpages.ubuntu.com/manpages/oneiric/en/man1/awk.1posix.html) does that easily:

```

free -t -m | awk '/^Mem/ { print $3 " out of " $2 }'

```

You can choose any columns you want by adjusting the print statement. As it stands it prints the third column then the second column from the line starting with "Mem".

---

### Post by GrouchyGaijin on 2012-02-26
That is pretty cool!
Is there a way to print from  two different lines?
```

Mem:          2012       1393        618          0         90        783
-/+ buffers/cache:        519       1492

```
I'd like the 519 out of 2012.  So would that be third or second column of buffers/cache? 
and column two of Mem

---

### Post by Lars Noodén on 2012-02-26
Scary.  I think I'm starting to understand a little how awk works.  This will give you the 2nd column from the line matching "Mem" and the 3rd column from the line matching -/+ as combined output.

```

free -t -m | awk '/^Mem/ { N= $2 } /^-\/+/ { print $3 " out of " N}'

```

---

### Post by GrouchyGaijin on 2012-02-26
> **Lars Noodén said:**
> Scary.  I think I'm starting to understand a little how awk works.  This will give you the 2nd column from the line matching "Mem" and the 3rd column from the line matching -/+ as combined output.

```

free -t -m | awk '/^Mem/ { N= $2 } /^-\/+/ { print $3 " out of " N}'

```

WOW - you Sir, are a god!

---

### Post by Lars Noodén on 2012-02-26
It's the people with the foresight and ability to design and build these tools have been truly amazing.  I'm in awe every time something like this works.  It's also fun to be able to string things together and get a useful result.

---

