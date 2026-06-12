---
title: "An easy way to learn the commands?"
date: 2013-03-09
forum: Programming Talk
---

### Post by sevensevenone on 2013-03-09
So I'v been looking around for a program that could help me/others learn the commands and how to use them with little to no results. Tho I did find "something" like it for windows.

I'v been thinking of the complexity of the cli and have been wondering if it would be posable to create a simple program that could take all the raw data and put it into an easy to read/use format on the screen.

So far my toughs on it are, a drop down box that has all the commands in it, and once a command is selected all the arguments are displaded under. 
Most of the data for it is already available with the man files, with a hopefully simple search of them for the -a, --arguments would result in a relativelly easy way to see what each command can do. 
You would want to have some type of text file that holds all the commands/file paths for the program to call on to save from having the have the program search each time, as well as a easy to use way of adding/removing commands to and from the program. 
A posable "plus" button to add additional commands, to be exacuted after the first command is done.
Finally there would be some type of export button that would spit out all of the chosen commands, options, file/paths to the terminal so you can do a "final" review and exacute the commands.

I kinda figure it would be best if the program ether called on the last used terminal, ether launching a new one or sticking it all in an already open terminal window.

Any one got any idea if something like that is already out there or how difficult it would be to make one like it?

---

### Post by ibjsb4 on 2013-03-10
Here's a couple of links that may help.

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

[http://playterm.org/](http://playterm.org/)

---

### Post by ofnuts on 2013-03-10
On konqueror, you can use URLs with the "man:" or "info:" protocol  to do just that. And after the "man:" or "info:" protocol, you have a dropdown with the possible command name completions.

You can also have the konqueror window split in two, one with the man/info display and one with a terminal.

---

### Post by slickymaster on 2013-03-11
You might want also to see these:
[Using the Terminal]("https://help.ubuntu.com/community/UsingTheTerminal")
[Learning the Shell]("http://linuxcommand.org/learning_the_shell.php")
[Bash Reference Manual]("http://www.gnu.org/software/bash/manual/bash.html")
[BASH Programming - Introduction HOW-TO]("http://www.linuxdoc.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
[The Bash-Hackers Wiki]("http://wiki.bash-hackers.org/doku.php")
[Advanced Bash-Scripting Guide]("http://www.tldp.org/LDP/abs/html/index.html")
[The Art of Unix Programming]("http://catb.org/~esr/writings/taoup/html/")

---

