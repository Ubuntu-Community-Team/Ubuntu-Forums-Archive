---
title: "Bash script to search other bash files for nasty code"
date: 2009-11-10
forum: Programming Talk
---

### Post by prupert on 2009-11-10
I tried this on DonationCoder, but I thought it would be useful if I posted here as well.
	
I have been thinking about this for a while, and sadly I am not very good with Bash, so I was hoping someone could help me.

I am well aware of the warning on the Ubuntu forums:

[http://ubuntuforums.org/announcement.php?f=39](http://ubuntuforums.org/announcement.php?f=39)

about nasty people telling less knowledgeable people like me to carry out commands that would toast their install.

Now, I love to mess around with Bash, and basically learn as I go, reading forum posts and using other Bash scripts that people have posted. However, I am always worrying that someone could have posted a malicious bit of code in their Bash script for a laugh (I am meaning a script I find anywhere on the internets, not just from the Ubuntu forums). Obviously I only use scripts from what look like reputable sites where people have commented on the script afterwards, but still the risk exists.

I was wondering if it was possible to make a Bash script that reads another Bash script that you pass it (basically a text file) and looks for any nasty pieces of code in it (the nasty pieces of code taken from the examples given in the post above and then updated from time to time with other sources).

In a sense, it would be like a mini-anti-virus program. It would have a definitions file that contained the nasty pieces of code, and then you would get it to scan a text file for those pieces of code and it would tell you if it found anything nasty or not.

I know this should use either the sed, awk or gawk commands, but I don't know how to create a script that could search for multiple strings of commands from a given list (the definitions file).

Obviously, this isn't a fool proof solution and it is entirely possible that it will miss nasty code or a certain piece of nasty code isn't in the definitions file, but, hey, it's a start and it should help new users to Linux and provide a little bit more internet security. Once it is created, I'll host it on Google Code and publicise it on my Blog (so all 10 of my readers can learn about it!!).

So, does anyone have any suggestions how I might go about this, i.e. what would be the best commands to base the script on (I don't want to choose one command, only to find after reading about it and trying for hours to use it that there is a better command out there that I should have used to begin with). Cheers for any views on this ;)

(Note, Bash is preferred, since it is a relatively easy language to understand and users would be able to see how it works and learn a bit about Bash along the way).

---

### Post by CptPicard on 2009-11-10
At least in general case this is very hard to achieve. It is actually theoretically impossible to prove programmatically that any other given program is correct. There are many ways to hide things into a program... the only way to be sure is to actually execute the program, which results in the aforementioned problems, among others.

You could, perhaps, just check for the existence of some potentially harmful commands, such as "rm", or run the script in some sort of "chroot jail" and see what you get. Otherwise it really is down to just normal UNIX safety and security...

---

### Post by Bodsda on 2009-11-10
> **prupert said:**
> I tried this on DonationCoder, but I thought it would be useful if I posted here as well.
	
I have been thinking about this for a while, and sadly I am not very good with Bash, so I was hoping someone could help me.

I am well aware of the warning on the Ubuntu forums:

[http://ubuntuforums.org/announcement.php?f=39](http://ubuntuforums.org/announcement.php?f=39)

about nasty people telling less knowledgeable people like me to carry out commands that would toast their install.

Now, I love to mess around with Bash, and basically learn as I go, reading forum posts and using other Bash scripts that people have posted. However, I am always worrying that someone could have posted a malicious bit of code in their Bash script for a laugh (I am meaning a script I find anywhere on the internets, not just from the Ubuntu forums). Obviously I only use scripts from what look like reputable sites where people have commented on the script afterwards, but still the risk exists.

I was wondering if it was possible to make a Bash script that reads another Bash script that you pass it (basically a text file) and looks for any nasty pieces of code in it (the nasty pieces of code taken from the examples given in the post above and then updated from time to time with other sources).

In a sense, it would be like a mini-anti-virus program. It would have a definitions file that contained the nasty pieces of code, and then you would get it to scan a text file for those pieces of code and it would tell you if it found anything nasty or not.

I know this should use either the sed, awk or gawk commands, but I don't know how to create a script that could search for multiple strings of commands from a given list (the definitions file).

Obviously, this isn't a fool proof solution and it is entirely possible that it will miss nasty code or a certain piece of nasty code isn't in the definitions file, but, hey, it's a start and it should help new users to Linux and provide a little bit more internet security. Once it is created, I'll host it on Google Code and publicise it on my Blog (so all 10 of my readers can learn about it!!).

So, does anyone have any suggestions how I might go about this, i.e. what would be the best commands to base the script on (I don't want to choose one command, only to find after reading about it and trying for hours to use it that there is a better command out there that I should have used to begin with). Cheers for any views on this ;)

(Note, Bash is preferred, since it is a relatively easy language to understand and users would be able to see how it works and learn a bit about Bash along the way).

You describe a very simplified anti virus program. You have a set definitions of what you think/know is malicious and then search the file in question for that string. However as CptPicard pointed out, there are many ways to hide malicious code and in order to find it in the first place, you (pretty much) have to know exactly what your looking for.

Complex anti virus programs work on the same principal, they have definition files that define what code appears malicious, it can then flag/jail them appropriately. 

You could always just open the file and take a gander. If there is something you don't like the look of, ask someone to check it first, or run it in a chroot jail.

---

### Post by prupert on 2009-11-10
Thx for the reply.

I don't whish to check to see if the bash script works, I simply wish to scan the bash script for nasty commands, taken from a "library file" of nasty commands, or there abouts.

So, I would run my script checking program (lets call it check.sh) on say test.sh. check.sh would then search test.sh for all the phrases listed in a dictionary file (lets call it list.txt). List.txt would contain the commands listed here 
[http://ubuntuforums.org/announcement.php?f=39](http://ubuntuforums.org/announcement.php?f=39) and check.sh would scan test.sh to see if any of the commands listed in list.txt were there.

The problem is, I don't know what command to use that would read though a list of search strings, and run that search against a file, checking to see if any of the strings are in the file.

---

### Post by prupert on 2009-11-10
So you think the idea would be pointless, since people who wanted to include nasty code in a script would use various ways to obsfuscate the commands, making them hard to find?

chrootjail sounds like the best option then I suppose.

Oh well. 

It'd be interesting to know what bash command I could have used though ;)

---

### Post by Can+~ on 2009-11-10
There's also good-intended uses, for instance, my usual makefile has:

```
clean:
	rm -rf $(OBJECTS) $(TARGET)
```
(Both target and objects autogenerated)

Which is intended to clean a code before sending, after a compilation.

---

### Post by prupert on 2009-11-11
So I guess it is a case of me learning more about Bash, so I can spot anything dodgy and check it out.

Fair enough I guess.

---

### Post by CptPicard on 2009-11-11
> **prupert said:**
> 
I don't whish to check to see if the bash script works

The problem of seeing whether a script "works" (that is, works correctly for your definition of correct) is often (in the generic case) actually the same problem as making sure that it behaves in "any" (predetermined, given) way. The underlying theoretical problem is the so-called halting problem (whether the program stops at all). They're all the same. This is why programmatic program analysis is hard.


> The problem is, I don't know what command to use that would read though a list of search strings, and run that search against a file, checking to see if any of the strings are in the file.

Well, see "grep".

---

