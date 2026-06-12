---
title: "How to make a windows executable from my python code???"
date: 2008-09-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-05
So I have installed activestate python and pygame on my windows.
But when I try to run pygame2exe/py2exe, it says "--force not found" or something.

How can I make a windows executable from my python game?? My friends want
to play my game but because they don't know nearly anything about computers, 
they can't install python + pygame.

All they use windows, so I must make a windows exe.

---

### Post by LaRoza on 2008-09-05
> **crazyfuturamanoob said:**
> So I have installed activestate python and pygame on my windows.
But when I try to run pygame2exe/py2exe, it says "--force not found" or something.

How can I make a windows executable from my python game?? My friends want
to play my game but because they don't know nearly anything about computers, 
they can't install python + pygame.

All they use windows, so I must make a windows exe.

Why can't they install Python and PyGame?

---

### Post by cmay on 2008-09-05
[http://www.jrsoftware.org/isinfo.php](http://www.jrsoftware.org/isinfo.php) 
when i used windows i used this inno set compiler for all kinds of things.
it creates a setup program from the folders and files you specify and its easy to use. as for this specific problem you have i cant say that its the perfect solution since i dont know how to set up python with this pygame.
if you can somehow create a setup install program that includes a working version of your game it may work. i remember once i installed devcpp and downloaded all the updates and extras for it and then packed it with the inno setup creator. and i burned it on a cd as my own version of devcpp .
i imagine it can be done with your game as well. its free so you can maybe use it for other things as well. i also used it to create setup program for my back up folders with pictures and other stuff so it was a handy tool for me back then.anyway hope you find a solution if this dont work for you.

---

### Post by pmasiar on 2008-09-05
> **crazyfuturamanoob said:**
> My friends want
to play my game but because they don't know nearly anything about computers, 
they can't install python + pygame.

I bet that ActiveState python installer is nicer and more user-friendly than your custom-made installer will ever be. It takes about 5 clicks to install it, so I do not see your point - especially taking into account your lack of compiling skills.

Sun-Tzu teaches that (programmer-warrior) should be like water: "Water shapes its course according to the nature of the ground over which it flows; the soldier works out his victory in relation to the foe whom he is facing. ... He who can modify his tactics in relation to his opponent and thereby succeed in winning, may be called a heaven-born captain."

You are banging your head against the wall, while open door is 3 steps to your left. Have fun!

---

### Post by LaRoza on 2008-09-05
> **pmasiar said:**
> 
You are banging your head against the wall, while open door is 3 steps to your left. Have fun!

The only reason for this that I can see is that the users of the Windows boxes don't have admin rights to install.

Is that so?

---

### Post by pmasiar on 2008-09-05
> **LaRoza said:**
> The only reason for this that I can see is that the users of the Windows boxes don't have admin rights to install.

Is that so?

Just the opposite: default mode on Windows until Vista was: every user is superuser. How else spread all those viruses? :-)

---

### Post by LaRoza on 2008-09-05
> **pmasiar said:**
> Just the opposite: default mode on Windows until Vista was: every user is superuser. How else spread all those viruses? :-)

If it is a school computer or not theirs, they may be restricted like this.

@OP I suggest you tell them they need admin rights on the Windows box to use it, like most apps. Perhaps you can make a portable version later.

---

### Post by mssever on 2008-09-05
If you want to use py2exe, I suggest that you read the (boring to you) manual to find out how to use it. If after doing that you're still having problems, you'll have a better shot at getting help if you show the exact error and the relevant code. And convince us that you at least made a good faith effort to read and understand the documentation.

---

### Post by nvteighen on 2008-09-05
Just a very strange idea, but could this work?

1. Create a C application that opens the Python code and executes it, using dlopen() and friends to have access to libpython.so.
2. Compile it for Win32 static-linking all libraries.

---

### Post by cmay on 2008-09-05
> Just the opposite: default mode on Windows until Vista was: every user is superuser. How else spread all those viruses? 
rename the project to virus.bat then ?

---

### Post by pmasiar on 2008-09-05
> **LaRoza said:**
> If it is a school computer or not theirs, they may be restricted like this.

But if they are restricted, should we help OP to find a way around such restriction? To help some lazy people to remain lazy? You first, I am off for weekend 8-)

---

### Post by LaRoza on 2008-09-05
> **pmasiar said:**
> But if they are restricted, should we help OP to find a way around such restriction? To help some lazy people to remain lazy? You first, I am off for weekend 8-)

No, that is why I recommended they find a box in which they have admin permission.

---

### Post by crazyfuturamanoob on 2008-09-06
Huh? How did this discussion lead to admin permissions? :confused:
Well, on the school computers we can't even open dos console! :(
Although it is possible to install python + pygame, console is still needed.

If making an .exe is too much, how to run python script on windows without needing console?

---

### Post by LaRoza on 2008-09-06
> **crazyfuturamanoob said:**
> Huh? How did this discussion lead to admin permissions? :confused:
Well, on the school computers we can't even open dos console! :(
Although it is possible to install python + pygame, console is still needed.

You can't open a terminal or you can't figure out how to? There is a difference.

How is it possible to install python and pygame? That requires admin priveleges.

To get a console, if you really need one. Open notepad (or any editor) and save a file named "c.bat" with the contents:

```

start cmd.exe

```

Double click it.

---

### Post by crazyfuturamanoob on 2008-09-06
Gotta try it next friday then.

But on the school computers there are no admin privileges!

They are just the activestate python and pygame installers
I have ran on the computers, and they don't need any privileges.

When I try to launch dos console trough Start->idontrememberthenameofthisfolder->console,
it says something like this "this is not allowed blablabla ask the system administrator", :(

---

### Post by LaRoza on 2008-09-06
> **crazyfuturamanoob said:**
> Gotta try it next friday then.

But on the school computers there are no admin privileges!

They are just the activestate python and pygame installers
I have ran on the computers, and they don't need any privileges.

When I try to launch dos console trough Start->idontrememberthenameofthisfolder->console,
it says something like this "this is not allowed blablabla ask the system administrator", :(

It is unlikely to restrict the batch file, unless the admin was very vigilent (and even then...). 

Windows's security is backwards. It by default has admin priveleges, executes files based on file extensions, hides file extensions and has its path set to the current working directory. That is very dangerous and securing and managing Windows properly takes a lot of training, knowledge and time.

---

### Post by crazyfuturamanoob on 2008-09-06
Ok, the batch file seems to be a good solution.
But how can I have a batch file that doesn't show console,
but executes "python myfile.py" in console?

---

### Post by pmasiar on 2008-09-06
> **crazyfuturamanoob said:**
> But on the school computers there are no admin privileges!

You should not run your programs on school computers without permission to do so. It is wrong, and also might get you into problems, so no help from me.

> I have ran on the computers, and they don't need any privileges.

When I try to launch dos console trough Start->idontrememberthenameofthisfolder->console,
it says something like this "this is not allowed blablabla ask the system administrator", :(

Good, so you don't have rights to do stuff you have no clue about and no right to do. Otherwise, your school network would be even worse zombie farm :-)

Tell your friends experiment on home computers - and help them double-boot  ubuntu 8-)

---

### Post by crazyfuturamanoob on 2008-09-06
> **pmasiar said:**
> You should not run your programs on school computers without permission to do so. It is wrong, and also might get you into problems, so no help from me.



Good, so you don't have rights to do stuff you have no clue about and no right to do. Otherwise, your school network would be even worse zombie farm :-)

Tell your friends experiment on home computers - and help them double-boot  ubuntu 8-)
My friends aren't interested in about Ubuntu because counter-strike doesn't run on it. :(

---

### Post by nvteighen on 2008-09-06
> **crazyfuturamanoob said:**
> My friends aren't interested in about Ubuntu because counter-strike doesn't run on it. :(
Tell them to drop that silly games and play the great masterpiece SuperTux is. :)

---

### Post by cmay on 2008-09-06
> Tell them to drop that silly games and play the great masterpiece SuperTux is. 
yes another devoted fan:)
how many times have you completed all rounds ?
i did it twice. i cant wait for the next version to come out.

---

### Post by nvteighen on 2008-09-06
> **cmay said:**
> yes another devoted fan:)
how many times have you completed all rounds ?
i did it twice. i cant wait for the next version to come out.

Never... :p, but I like it.

---

### Post by cmay on 2008-09-06
> never... , but I like it. 
supertux is easy to like. i always play a couple of rounds before i start reading my programming books. it is a great game.

---

### Post by Kadrus on 2008-09-06
> My friends aren't interested in about Ubuntu because counter-strike doesn't run on it. 
It does actually.([https://help.ubuntu.com/community/CounterStrike](https://help.ubuntu.com/community/CounterStrike))..[Transgaming]("http://transgaming.com/")

> supertux is easy to like. i always play a couple of rounds
Heh,It's a neat game,although Super Mario still better ;p

---

### Post by cmay on 2008-09-06
> Heh,It's a neat game,although Super Mario still better ;p
but there is no penguins in super mario :)

i used to play super mario and the legend of zelda a lot on my brothers tv game thingy. super mario is cool too.

---

### Post by forger on 2008-09-06
Wouldn't it just be easier to boot using the Ubuntu Live CD?
Provided that there is network support:
```
sudo apt-get update
sudo apt-get install python-pygame
```

And you can run your game, right?

---

### Post by pmasiar on 2008-09-06
> **crazyfuturamanoob said:**
> My friends aren't interested in about Ubuntu because counter-strike doesn't run on it. :(

You play counterstrike at school? Some school :-)

Drop those lamers and get friends who compile kernel instead :-) I know one High-school student who (as sophomore) set his  home server to proxy websites banned by High School IT, and his computer privileges were revoked. IT were scared by him, he knows so much more about networking. He runs slackware on home server farm, has 3 screens (one on top), compiles his kernel, and his file server has 2 terabytes of MP3s and video.

---

### Post by LaRoza on 2008-09-06
> **nvteighen said:**
> Tell them to drop that silly games and play the great masterpiece SuperTux is. :)

Or World War vi. I was playing that last night.

---

### Post by crazyfuturamanoob on 2008-09-07
Uh... Counter-Strike doesn't work well on wine, steam chat doesn't work, graphics must be low.

And yeah, actually we sometimes play counterstrike on school computers :P

---

### Post by Bush_Roo on 2008-09-07
> **crazyfuturamanoob said:**
> steam chat doesn't workGotta have a closer look at the CounterStrike Ubuntu community howto to get steam to work ;)

> **crazyfuturamanoob said:**
> graphics must be lowSimple beef problem ;)

---

### Post by crazyfuturamanoob on 2008-09-07
> **Bush_Roo said:**
> 
Simple beef problem ;)
No it isn't. This computer can run counter-strike source with maximum detail on windows vista.
The shaders don't work on wine.

---

