---
title: "Snusp"
date: 2006-08-22
forum: Programming Talk
---

### Post by Tomosaur on 2006-08-22
[SNUSP](http://scienceblogs.com/goodmath/2006/08/beautiful_insanity_pathologica.php) Is an esoteric programming language based on brainfuck, befunge, and path. Essentially, the program runs in a 'pattern' defined by the various symbols (each of which has a function). I only discovered it today and I've been getting to grips with it so I thought I'd share it with you guys. Although programs written in SNUSP look generally...weird, they have a certain quality to them which makes them seem so much more interesting than generic programming language source. Theoretically, you can write a program that looks like a picture, although figuring out how to do that is probably most of the challenge. Many programs end up looking like circuit boards - my simple examples look like....well, nothing I guess :D

Here's the generic 'Hello World' program written in SNUSP. I couldn't find one on the internet so I made my own.
```

  /==\	hello     
  | //\/\/\/\ world
  | \+++++++/ /\/\/\/\/\
  | /+++++++\ \++/\--/++
  \+\\/\/\/\/ /++.=--\.+
    \\+++++++.\/\<\\\//.
$,===/\\/\.---/.\ | \/-\=\
     \+\+\/+++/>/./  \\-\|
      -\+//   \=/=.---/\-/
      \../ /\/\//\/\
          /---!-.#
          \----/  

```
This takes '0' as its input (you have to do this manually, there's no way to do it within SNUSP), then cycles through ASCII characters to select the components to make 'HELLO WORLD'. Doesn't look like anything, but it certainly looks more interesting than most other Hello Worlds :P The words 'hello' and 'world' are just comments, 'hello' is nearest to all the stuff that prints 'HELLO' and 'world' is nearest to all the stuff that prints 'WORLD'. They're ignored by the interpretor.

And here's one which takes 3 single-digit numbers and adds 1 to each of them. Fairly pointless, but this one was my first SNUSP program:
```

  $,>,>,\ /+<=\
   /==/@///+=#|
   |#.\==/\<+=/
   .  >
   \>./

```
Since snusp can only print one byte at a time, the highest digit you can pass it is '8' in this case (since 8 + 1 = 9, and that's the highest single digit number :P)

The perl interpretor I've been using to run these programs can be found [here](http://c2.com/cgi/wiki?SnuspLanguage). You'll need to c+p the script into a perl file.

Have fun :D

---

