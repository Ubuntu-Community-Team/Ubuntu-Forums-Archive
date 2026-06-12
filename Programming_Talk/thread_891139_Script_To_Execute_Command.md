---
title: "Script To Execute Command?"
date: 2008-08-15
forum: Programming Talk
---

### Post by cchung85 on 2008-08-15
Hey guys, I recently downloaded this program that runs from it's extracted folder, I don't know how to make it install on the computer but I'd like to make a script for it so that I can access it easily on my AWN dock.

Here is what I have to do to get it to run:

1. "cd Desktop/brainworkshop"
2. in Desktop/brainworkshop I type "python brainworkshop.pyw"

Then the file opens and I get to run my program. I want to add it to my menu in either Gnome or Openbox, how would I do that?

Also, while I am at it... I tried to run the file in one line in terminal so I typed:

"cd Desktop/brainworkshop/"python brainworkshop.pyw"

I am pretty sure that doesn't work because it's trying to access a directory... How would I go about writing that line in terminal.
(how do I open a file with a program from a specific folder in one line?)

I think I am just going to confuse you guys so I'll stop here. Anyways, please help me out, I am trying to learn some commands for the terminal...

---

### Post by eriqjaffe on 2008-08-15
You should be able to just run:

```
python ~/Desktop/brainworkshop/brainworkshop.pyw
```

---

### Post by Bachstelze on 2008-08-15
And if you want to be able to run your script with just one command, add a line like this as the first line on your script:

```
#!/usr/bin/env python
```

and make it executable:

```
chmod +x ~/Desktop/brainworkshop/brainworkshop.pyw
```

Then you can for example copy it somewhere in your PATH:

```
sudo cp ~/Desktop/brainworkshop/brainworkshop.pyw /usr/local/bin/brainworkshop
```

And voilà:

```
brainworkshop
```

---

### Post by cchung85 on 2008-08-16
> **HymnToLife said:**
> And if you want to be able to run your script with just one command, add a line like this as the first line on your script:

```
#!/usr/bin/env python
```

and make it executable:

```
chmod +x ~/Desktop/brainworkshop/brainworkshop.pyw
```

Then you can for example copy it somewhere in your PATH:

```
sudo cp ~/Desktop/brainworkshop/brainworkshop.pyw /usr/local/bin/brainworkshop
```

And voilà:

```
brainworkshop
```

I haven't tried it yet, I'm trying to figure out what each of those commands mean, I haven't toyed around with chmod yet... Will post in a bit about the results.

---

### Post by gareththomasnz on 2010-08-09
I am trying to create a launcher for this very same application.

Can somebody please walk me through it - i don't want the folder on my desktop either.

cheers

---

### Post by Bachstelze on 2010-08-09
Have you tried what I wrote above?

---

### Post by anjexe on 2011-03-31
i want script to do so commands

1-cd acpi_call

2-sudo insmod acpi_call.ko

3-./test_off.sh

help me on how to do

---

### Post by d3v1150m471c on 2011-03-31
append the following to ~/.bashrc :
```

alias nameofcommand="/path/to/command"

```then,
```

. ~/.profile

```now you can launch the program from any terminal with the chosen command. btw, was it a tar file? it probably has to be compiled and installed with `make' and `install'.

---

### Post by anjexe on 2011-03-31
Using acpi_call module to switch on/off discrete graphics card in Linux

One of the hybrid-graphics-linux Launchpad team members has 
created a Linux kernel module to call ACPI methods through 
/proc/acpi/call. The code is here:

[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)

You can try it by installing the module and calling it like this:

git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh


orginaly it is about the above 

some more clear help please
i dont know how to do it at all
tnx

---

### Post by supergirlkara on 2011-04-06
There is also the perl alternative...

```


#!/usr/bin/perl;

system('1st command');

system('2nd command');

system('3rd command');


```save file as auto.pl

from terminal type: perl auto.pl

---

### Post by anjexe on 2011-04-06
> **supergirlkara said:**
> There is also the perl alternative...

```


#!/usr/bin/perl;

system('1st command');

system('2nd command');

system('3rd command');


```save file as auto.pl

from terminal type: perl auto.pl

how to gave the toot privilage (sudo)??

---

