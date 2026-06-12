---
title: "How can I make a Bash script use input? Is it possible?"
date: 2011-09-17
forum: Programming Talk
---

### Post by Thorin Oakenshield on 2011-09-17
I have a little script that converts videos and thus changes slightly each use because it uses different videos for input and different names for input. 

Anyhow I was wonder if there was a way to have the video name parts just be input. Is this possible?

---

### Post by erind on 2011-09-17
Take a look at ***read ***command:

     *8.2.1. Using the read built-in command* in

[http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf](http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf)

... Also if you need to define the input/output in the command line check **positional parameters **( $1, $2, $3, ... ) in the same link above.

---

