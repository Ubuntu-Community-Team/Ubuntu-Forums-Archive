---
title: "Where can I find list of all characters meaning at terminal?"
date: 2016-02-07
forum: New to Ubuntu
---

### Post by helm10101 on 2016-02-07
Hi,

Is there a link where I can see all the letters and chars meaning, such as when I do sudo apt-get install** -y **<something> **&& **<something>

Btw, what is the meaning of "&&" when you install something? Is it "and"? if so, it makes no sense as I followed instructions that told me to install the same thing then, it was: ```
sudo apt-get install -y boot-info && boot-info
```

Thank you

---

### Post by QIII on 2016-02-07
"&&" does mean "and" in general. The reason you command failed is that apt-get install takes a non-delimited list:

```
sudo apt-get install -y boot-info foo bar thisapp thatapp
```

For your purposes, you need only have entered

```
sudo apt-get install -y boot-info
```

As for the meanings of the options (the "letters"), those will be different for each utility/app/process you initiate in the terminal.  You can find their meanings and use in the "man pages" by issuing the following command:

```
man <foo>
```

For instance 

```
man apt-get
```

You use && in circumstances where, for instance, you want two commands to follow each other without having to wait and type the next, i.e.:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by helm10101 on 2016-02-07
Thank you QIII!
I now realize that every "man" shows its own letters. 
Last thing:
> [COLOR=#000000]The reason you command failed is that apt-get install takes a non-delimited list:[/COLOR]


My command did not fail, it did install. But does it have any meaning to do "sudo apt-get install -y boot-info && boot-info"? or I could've only done "sudo apt-get install -y boot-info"

---

### Post by QIII on 2016-02-07
```
sudo apt-get install -y boot-info
``` would have been sufficient.

---

### Post by helm10101 on 2016-02-07
Thank you again, and the really last thing: If it is sufficient, why would the official installation guide (on official Ubuntu's help website) show to double write the same package?

---

### Post by howefield on 2016-02-07
> **helm10101 said:**
> .. why would the official installation guide (on official Ubuntu's help website) ...?

Can you Link to the page ?

Think I found it.. is it [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Generally the second command after the "&&" would be dependant on the first one completing, so what your command is suggesting is firstly install the package boot-info and if successful then run the command boot-info.

---

### Post by QIII on 2016-02-07
Thanks, howefield.  I'm asleep on my feet and should have noticed that from the beginning.

Good night!  :)

---

### Post by buzzingrobot on 2016-02-07
> **helm10101 said:**
> Hi,

Is there a link where I can see all the letters and chars meaning, such as when I do sudo apt-get install** -y **<something> **&& **<something>

Btw, what is the meaning of "&&" when you install something? Is it "and"? if so, it makes no sense as I followed instructions that told me to install the same thing then, it was: ```
sudo apt-get install -y boot-info && boot-info
```



The commands we execute in a terminal are read, interpreted and acted on by a program called a 'shell'.  Ubuntu uses a shell called 'bash'.  Others exist, but bash is the most popular in Linux. 

Bash has a large range of capabilities. It's use in the terminal might be its simplest. 

So... if you *really* want to get into the why's and how's of what's going on with terminal commands, look at bash.  

(A "terminal" is a window in a GUI set up to emulate the full screen we see in a non-GUI environment. Using the shell is the only way you interact with the system in those.)

---

### Post by vasa1 on 2016-02-07
> **helm10101 said:**
> Hi,

Is there a link where I can see all the letters and chars meaning, such as when I do sudo apt-get install** -y **<something> **&& **<something>

Btw, what is the meaning of "&&" when you install something? Is it "and"? if so, it makes no sense as I followed instructions that told me to install the same thing then, it was: ```
sudo apt-get install -y boot-info && boot-info
```

Thank you

In simple English, you would use```
sudo apt-get install -y boot-info && boot-info
```to first install the package "boot-info" with all its dependencies without being prompted (because of the "-y") and then, if the installation is successful, to run the program "boot-info".

Generally, *command1 && command2* means you want to execute *command1* first and only if *command1* executes and completes successfully, *command2* should be executed.

If you don't care whether *command1* executes and completes successfully as a precondition to running *command2*, you could use *command1 ; command2*.

The Bible on Bash is this: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Edit: I don't like using or recommending "-y".

---

### Post by grahammechanical on 2016-02-07
> followed instructions that told me to install the same thing

Just to be clear. The instruction in that command was not to install the same thing twice but to first _install_ boot-info and then _run_ boot-info. The result should have been the loading of this utility

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

The creator of this excellent utility is recommending that boot-info be installed and run from a live session. Which will not permanently store the new utility. So, the command to install the PPA and the command to install and run boot-info will need to be done each time we want to run boot-info from a new live session.

Regards.

---

### Post by vasa1 on 2016-02-07
> **grahammechanical said:**
> ...
The creator of this excellent utility ...
And for some sad reason, people have to resort to a ppa. IIRC, the dev couldn't find a "sponsor" to get it into Debian?

---

### Post by pauljw on 2016-02-07
Here's a good book to read on the subject of the command line.

[http://www.it-ebooks.info/book/2012/](http://www.it-ebooks.info/book/2012/)

---

### Post by helm10101 on 2016-02-07
Thanks everyone it's more than clear now :)
starting to getting used to Linux :D

---

