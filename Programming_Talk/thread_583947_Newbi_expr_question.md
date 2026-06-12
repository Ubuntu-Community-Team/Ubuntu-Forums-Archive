---
title: "Newbi expr question"
date: 2007-10-20
forum: Programming Talk
---

### Post by philip.yhelzon on 2007-10-20
I've been trying a command from Linux guide I've been reading.
And it keeps giving me a syntax error massage  :confused:

expr 0 `ls -l | grep '^-' | \
    sed 's/^\([^ ]*[ ]*\){4,4}\([0-9]*\).*$/ + \2/'`

What I missing here?

---

### Post by slavik on 2007-10-20
nvm ...

---

### Post by bigboy_pdb on 2007-10-20
I'm not too certain about what you are trying to accomplish with that command.

You should try to develop your code in separate parts and then test those parts together.

In your case since you are trying to use the output of a command within another command, it would be a good idea to test the command in the back quotes first. When I tried to test your command in the back quotes, I didn't get any output on the screen. Can you please explain what you want it to output to the screen?

Also, since you are reformatting text, if you expect a certain output from the command in the back quotes then you can test the "expr" command with the expected output separately using the expected output. For example, if you were going to execute two commands and compared their output to find out which output is greater then you could use 'expr *output1* ">" *output2*' where *output1* and *output2* are strings that you are expecting to see from your two commands (such as first *output1* is 1 and *output2* is 2, second *output1* is 2 and *output2* is 1, and so forth if you are expecting positive numbers to be returned).

It might be a good idea to post what you are trying to do so that we can better help you.

---

### Post by philip.yhelzon on 2007-10-20
Hmm....I'll do my best, this command is kind of a "du" command, it should give as an output the space usage of all the files in a folder.
ls -l | grep '^-'  ------- picks all files (not dir)

sed 's/^\([^ ]*[ ]*\){4,4}\([0-9]*\).*$/ ---  devids the string to parts and assigns "\2" to the size parameter.

 + \2/ ---  adds the second parameter to the size all previous lines.

then the expr should sum them all up...

I've been learning from this ebook:
LINUX:
Rute User's Tutorial and Exposition....and its good, the thing is that he has ALLOT of syntax errors in it, and its very time consuming to go online and check every time I try to run something.....
Do you guys have any recommendations about this book or any other?

---

### Post by bigboy_pdb on 2007-10-20
Your sed command was essentially right and the other code was fine as well, but you need to put back slashes before the squiggly brackets. Otherwise, they are interpreted as squiggly brackets instead of being references to the number of back to back matches that you want to make. So change "{" and "}" to "\{" and "\}". You will then get output for the command in the back ticks.

You can avoid using grep by changing your command to:
ls -l | sed -n 's/^-\([^ ]*[ ]*\)\{4\}\([0-9]*\).*$/ + \2/p'

I tested your command with the changes and it will do what you wanted it to do.

**[EDIT]**
Sorry, I didn't explain the additional changes. The "-n" option in sed tells the program that you only want to print lines that you tell it to print. I added a dash to the beginning of the regular expression to indicate that substitutions would only occur when a dash is found at the beginning of the line. The "p" that was added at the end of the code of the form "s/*regex*/*replacement*/" indicates that you want to print all of the lines where substitutions are made. I also removed one of the fours and the comma in the squiggly brackets because it wasn't necessary.
**[/EDIT]**

---

### Post by bigboy_pdb on 2007-10-20
Regarding your question about learning resources, the Linux Documentation Project website has some good guides and other useful things.

The site can be found here:
[http://tldp.org/](http://tldp.org/)

I would recommend looking at:
*Introduction to Linux - A Hands on Guide*,
*GNU/Linux Command-Line Tools Summary*,
*Bash Guide for Beginners*, and
*Advanced Bash-Scripting Guide* (but more as a reference than something that should be read completely),

Regarding sed and awk, I've read a good amount of the O'Reilly "sed & awk" book and so far it has been helpful, but I already knew a good deal about regular expressions before I read it (from the O'Reilly Perl books) and that might have made it easier to read for me.

The following site has some useful information on regular expressions:
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

You should be aware that this site does not consider sed and awk when it mentions regular expressions and that some characters that are special characters, such as "{", "}", "(", and ")", in programs that have a special meaning, but in sed they represent those characters. When those characters are preceded by back slashes (for example, "\{", "\}", "\(", and "\)"), this indicates that you want the character to have it's literal meaning, but in sed they have their special meaning. In other words, the meanings of the characters and their escaped forms are reversed. You can either look up the syntax for regular expressions for that program or you can create an expression to figure out which representation is being used. For example, when the commands "echo -e 'a{5}' | sed -n '/.\{5\}/p'" and "echo -e 'a{5}' | sed -n '/.\{5\}/p'" are used, 'a{5}' will be printed for whichever command is using the literal interpretation of squiggly brackets.

---

### Post by ghostdog74 on 2007-10-20
> **philip.yhelzon said:**
> I've been trying a command from Linux guide I've been reading.
And it keeps giving me a syntax error massage  :confused:

expr 0 `ls -l | grep '^-' | \
    sed 's/^\([^ ]*[ ]*\){4,4}\([0-9]*\).*$/ + \2/'`

What I missing here?

my advise, you can use sed for simple tasks, but as your problem gets complex, using too much regular expressions makes your code unreadable, difficult to troubleshoot and prone to errors. however , since you are still in learning phase, i guess its still alright.
Use awk for your task. Its simpler, more flexible and combines the capabilities of grep/sed/cut etc into one powerful tool.
Judging by what you want to do, it could be as simple as this
```

 # ls -l | awk '{total+=$5}END{print total}'
14628091

```

---

