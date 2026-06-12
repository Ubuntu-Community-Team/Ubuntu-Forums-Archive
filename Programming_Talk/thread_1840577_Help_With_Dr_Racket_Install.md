---
title: "Help With Dr Racket Install"
date: 2011-09-07
forum: Programming Talk
---

### Post by briigga on 2011-09-07
Hello Everyone

I need to install Dr Racket environment for my class and although i managed to install it, the actual Dr Racket program is an executable text file which I need to click and run for it to open. Did I do something wrong? How do I make it an executable application? Also, how do i move the folder containing all its install files, libs etc to my usr directory? It wouldnt let me install it in there originally.

Im using ubuntu

Thank you.

---

### Post by Toz on 2011-09-15
> **briigga said:**
> Hello Everyone

I need to install Dr Racket environment for my class and although i managed to install it,
How did you install it? Did you compile from source?

> the actual Dr Racket program is an executable text file which I need to click and run for it to open. Did I do something wrong?
What do you think should be happening? Are you expecting a menu item to select to run the application?

> How do I make it an executable application? Also, how do i move the folder containing all its install files, libs etc to my usr directory? It wouldnt let me install it in there originally.

Im using ubuntu

Thank you.

I just download the unix source and compiled it via the instructions in the src/README file:
> Quick instructions:

 From this directory (where the `configure' file is), run the following
 commands:

   mkdir build
   cd build
   ../configure
   make
   make install


However, I made some changes to those instructions so that it installs into /usr/local. Here are the instructions I used:
```

cd racket-5.1.3/src
mkdir build
cd build
../configure --prefix=/usr/local
make
sudo make install
```

Now running either **racket** or **drracket** from the command line start up the applications.

---

### Post by briigga on 2011-09-23
Thanks for the reply. I did exactly as you said (even installed it in usr/local ) however it seems i have a problem. First, typing drracket in the terminal does nothing. The only things I can run are gracket and racket. gracket opens up a simple interactions window which i actually think is pretty cool. However when I code racket into the terminal it says " Welcome to Racket v 5.1.3" and does nothing else. How do I get the dr racket or dr scheme programming environment to open up?

---

### Post by Toz on 2011-09-23
Did you get any errors during compilation?

Have a look in **/usr/local/bin** to see if the **drracket** file is there. Perhaps try running it as such:
```
/usr/local/bin/drracket
```

---

### Post by briigga on 2011-09-23
during compilation my screen went black, it had some writing on it and then my computer shut off. i figured it was restarting by itself?  in the directory you mentioned there is no drracket..only gracket and racket. Ive deleted all the files and am compiling it again to see what happens

---

### Post by briigga on 2011-09-23
another thing i dont know if it matters but in the src directory in racket-5.1.3/src there is no drracket there is only gracket and racket. should drracket be there?

---

### Post by Toz on 2011-09-23
> **briigga said:**
> during compilation my screen went black, it had some writing on it and then my computer shut off. i figured it was restarting by itself?  in the directory you mentioned there is no drracket..only gracket and racket. Ive deleted all the files and am compiling it again to see what happens

Good idea. I'm guessing that the system crashed before compilation completed.

---

### Post by Toz on 2011-09-23
> **briigga said:**
> another thing i dont know if it matters but in the src directory in racket-5.1.3/src there is no drracket there is only gracket and racket. should drracket be there?

I may be wrong, but I believe drracket gets created from the source files.

---

### Post by briigga on 2011-09-23
Ok so i compiled it again which took much longer this time but when I coded sudo make install and it was compiling it crashed again after about 10 mins. However this time It managed to install drracket. I guess ill leave it as it unless i encounter a problem.

thanks

---

### Post by Palmstroem on 2011-10-31
Which version of Ubuntu are you using? I compiled and installed racket 5.1.3 under Ubuntu 10.04 as well as under 11.10 with no problems. The final DrRacket program launcher is a script file named drracket which is usually placed in /usr/local/bin and should be accessible by every user from any directory. Although the build went OK in both cases, I noticed a graphics problem (missing buttons) with drracket in Ubuntu 11.10, probably due to some incompatibility between racket and the new Unity desktop.

Did the build really crash your operating system (hard to believe)? Or could it have been just the screensaver getting in your way ;-)

---

