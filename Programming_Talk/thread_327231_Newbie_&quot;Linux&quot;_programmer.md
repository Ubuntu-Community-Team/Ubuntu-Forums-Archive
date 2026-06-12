---
title: "Newbie &quot;Linux&quot; programmer"
date: 2006-12-28
forum: Programming Talk
---

### Post by sdmike on 2006-12-28
Ok on windows I use Microsoft compilers but I use linux so much that I want to just program on it now. I got automatix and it installed Anjuta IDE and I thought it was a C++ compiler but either I'm wrong or I do not know how to compile on it.

My next question is what is a solid C++ compiler on linux?

---

### Post by Tomosaur on 2006-12-28
If you open up a terminal and type 'sudo aptitude install build-essential', then you will download and install the most common linux dev related stuff, including gcc (the best C compiler around, bar none).

---

### Post by Wybiral on 2006-12-28
GNU GCC, G++... I *think* it's preinstalled. Go to the terminal and type "man g++" and it will bring up a help page if it is installed (exit the help page with q, btw). Otherwise go to your synaptic package manager and look for g++.

---

### Post by SuperMike on 2006-12-28
Welcome aboard, SDMike! I think you'll like programming on Linux. Some cool things I like about it compared to Windows:

[LIST]
[*]If you have a program that takes a shortcut and shells out to the console (like "DOS" on Windows), a black command prompt window doesn't flash open and closed on the screen.

[*]There's a great abundance of editors. I prefer Bluefish and have tried practically every one known to humanity that I could find.

[*]In Windows, you often get boxed in with a 'you can't get here from there' problem. I stopped having that when I switched to Linux. I even had a very tough problem where I needed to get Linux to talk to a flatbed scanner so that I could programmatically control it. I found a company on the Internet that was eager to write the scanner driver so that they could brag about having more drivers supported in their Linux product, and they worked with me as a tester and within 2 days we had a driver that worked just fine!

[*]There's a ton of languages for it and there are fewer that are supported on Windows.

[*]Many of the newer languages are started on Linux these days.

[*]In my belief, the development world has switched to Linux. Companies are cutting costs so much, and hating the viruses with Windows, and they hate vendor lockin -- that's why they love Linux these days in the server room.
[/LIST]

---

### Post by maddog39 on 2006-12-28
The C++ compiler isnt installed by default. You can install it simply by going:
```
sudo apt-get install g++
```
From terminal, then going:
```
g++ myprogram.cpp -o mycompiled_program.o
```
Then to run your program, go:
```
./mycompiled_program.o
```

---

### Post by amo-ej1 on 2006-12-29
maddog39: I wouldn't use the .o suffix there since it can be confusing to beginning users. The .o  mainly signifies compiled (but not linked) code. While you actually compiled and linked your code.

---

