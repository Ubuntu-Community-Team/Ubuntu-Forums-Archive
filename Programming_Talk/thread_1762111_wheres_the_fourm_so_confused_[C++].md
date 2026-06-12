---
title: "wheres the fourm?? so confused [C++]"
date: 2011-05-18
forum: Programming Talk
---

### Post by WiKiDCLown456 on 2011-05-18
hey i'm new to ubuntu and im loveing it now i want to start programing  again since i need to do some school work(falling behind) and at school we use MS visual studios well i dont want to run a VM to do this work so ive found Eclipse and installed the c/c++ development tool(so far so good) made a new black project got an idea in my head of what im gonna do and now i want to make my layout so how do i add a Fourm like in VS or something graphical like it? or is it even possible:confused:

---

### Post by slooksterpsv on 2011-05-18
> **WiKiDCLown456 said:**
> hey i'm new to ubuntu and im loveing it now i want to start programing  again since i need to do some school work(falling behind) and at school we use MS visual studios well i dont want to run a VM to do this work so ive found Eclipse and installed the c/c++ development tool(so far so good) made a new black project got an idea in my head of what im gonna do and now i want to make my layout so how do i add a Fourm like in VS or something graphical like it? or is it even possible:confused:

I'm not sure if Eclipse does forms or not. But to do forms in C/C++ that depends on what API you want to use there's quite a few out there. For Windows Forms you may want to look into MonoDevelop as you can do .NET type GUI interface (forms) in C, C++, C#, Vala, etc.

If you want to use Eclipse you could look into FLTK, wx, Qt, GTK+, etc. It just all depends.

---

### Post by cgroza on 2011-05-18
There is this GUI designer called Glade. Also, what GUI toolkit do you wish to program in?

---

### Post by WiKiDCLown456 on 2011-05-19
> **cgroza said:**
> There is this GUI designer called Glade. Also, what GUI toolkit do you wish to program in?

i'm really new to the programing world and basicly only know whats been tought at school (visual studios) so im guessin i want a .NET GUI for C++ so i can start and make programes at home then midway through take it to school and continue working on it there and vise versa

---

### Post by cgroza on 2011-05-19
You are probably using Winforms API.
If you are interested into GUI coding in Linux, there is Qt, GTK and wxWidgets. All of them are very powerful  and cross-platform.

---

### Post by nvteighen on 2011-05-19
Be aware that programming is far deeper (and far more interesting) than designing a GUI in a designer and just "making the GUI work". I also had my fair share of Visual Basic some years ago and I know what kind of mindset it usually imposes to beginners.

Really, GUIs are secondary: they're just one possible mean of letting the user interact with a program. But there are lots of them and all of them are better or worse depending on conditions that are external to the program itself. 

For example, I could write code that defines the basic features of a calculator, let say:

```

Add x, y
Substract x, y
Multiply x, y
Divide x, y

```

As soon as you write code for adding two arbitrary numbers x and y, or multiplying them, all your real work is done. Now you can choose how to make the user define what values do x and y take or what operation is going to be performed on those two values. That's the user interface...

... But the user could be a machine... You could connect two computers in your network and make one machine feed numbers and operations, while the other executes the calculations. Or it could be a human user... using a non-GUI environment... (feeding a text file as input, a prompt-based interface, a command line interface)... or a GUI... but what GUI? Windows's? Apple's? AmigaOS's? KDE, GNOME, GNUStep, Xfce, twm...? (all of these last ones are just some of the GNU/Linux Desktop Environments available). As you see the user interface is an accessory to allow access to the features of your code.

I strongly suggest you to take a look at the Sticky threads of these forums. The usual suggestion here is to point people towards the Python language and drive people's attention off C++ for a couple of serious reasons I won't get into this time. Of course you could learn programming by using C++ as your first language, but if you do, you better not expect to know how to write GUIs just from the start.

---

### Post by cgroza on 2011-05-19
[nvteighen]("http://ubuntuforums.org/member.php?u=273037") is maybe right. You should see if you master the important  C++ concepts before going further.

---

### Post by slooksterpsv on 2011-05-19
While I somewhat agree with nvteighen, you will need to know the structure for how to set properties, variables, etc. to the GUI elements.

You should take a look at all the commands you can run with just apt-get the program parses what the user put in:

check
install
remove
purge
etc.

Then depending on the option decides where to go, check database for this and see if it's installed, if not then see if it's on the repositories, if not let the user know this. And I could be wrong which what he's going after, but think of it like this:

You code a program a game, you make the following functions for the game (pong):
move_paddle - to move the paddle
move_ball - to move the ball
check_block_collision - check collisions of the ball the blocks
check_ball_collision - check collisions with the side of the screen and paddle
set_score - set the score
set_level - set the level
game_lost - player loses the game
etc.

All the user knows to do is use the Arrow keys (user presses left, move_paddle(left)) or press space to start (set ball speed to x=1, y=1), enter to start the game (start_new_game()).

So its easy to map simple things like up to jump, left to move left etc. but the actual code to do it is a lot better to learn. I'm just now learning that. And believe me, pong in python alone is approx 200 lines of code. The user doesn't see how I move the ball, calculate collisions, etc. they just know press left for left, right for right, space to start.

That help any? Either way its up to you, one thing I find useful is to draw with pen and paper, a diagram of what you want to do and break it down, e.g.:

```

Draw Objects (break that down)
-draw ball
-draw paddle
-draw blocks (break that down)
--load a file for a level
--read each line/character
--create a block in an array (break that down)
---do a for loop
----decide what color based on number or letter
----draw based on width*row_number and height*col_numer
-check collisions (break down)
--loop through blocks and see if bottom touches top of ball
...

```

Sorry for a long post, but I hope it helps.

---

### Post by WiKiDCLown456 on 2011-05-19
ok i under stand what yous are saying and yes i would love to learn more langues but i have to use c++ for my school work but if i understand yous completly are yous saying that theres a way for me to code it so when the user runs the program it will bring up a window with things i code like a drop down menu or a pic for the background?,buttons and whatever else id like them to interact with for example i have to make a program useing arrays that the user picks how they want to sort a bunch of processors wither it by cach or clock speed etc then in another one pick the speed(3 GHz) then it checks the boxes beside the processors that have a speed of 3Ghz is this possible to make this kind of visual things useing only code in C++? if so your recommendations to a totoural on such things would be awesome thanks for all the help so far

---

### Post by cgroza on 2011-05-19
> **WiKiDCLown456 said:**
> ok i under stand what yous are saying and yes i would love to learn more langues but i have to use c++ for my school work but if i understand yous completly are yous saying that theres a way for me to code it so when the user runs the program it will bring up a window with things i code like a drop down menu or a pic for the background?,buttons and whatever else id like them to interact with for example i have to make a program useing arrays that the user picks how they want to sort a bunch of processors wither it by cach or clock speed etc then in another one pick the speed(3 GHz) then it checks the boxes beside the processors that have a speed of 3Ghz is this possible to make this kind of visual things useing only code in C++? if so your recommendations to a totoural on such things would be awesome thanks for all the help so far
You don't need a GUI for that, but if you really want a GUI, use wxWidgets or Qt because they are more cross platform.
A tutorial for wxWidgets:
[http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)

---

### Post by WiKiDCLown456 on 2011-05-19
> **cgroza said:**
> You don't need a GUI for that, but if you really want a GUI, use wxWidgets or Qt because they are more cross platform.
A tutorial for wxWidgets:
[http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)

ok so now im not so worryed about the GUI part if you can code the same things :KS that works awesome for me cause then i can just use code and will have no problems with going btwn something like eclipse(home) and MS visual studios(school) but ive only ever used GUI's to make things like a button and drop down boxes  so now i need a TuT on how to make them with just code and what do i search to find more on it maybe something like C++ code or C++ consul???:confused:

---

### Post by cgroza on 2011-05-19
> **WiKiDCLown456 said:**
> ok so now im not so worryed about the GUI part if you can code the same things :KS that works awesome for me cause then i can just use code and will have no problems with going btwn something like eclipse(home) and MS visual studios(school) but ive only ever used GUI's to make things like a button and drop down boxes  so now i need a TuT on how to make them with just code and what do i search to find more on it maybe something like C++ code or C++ consul???:confused:
There is wxDesigner which can help you build GUI by point and click if is that what you are searching for.

---

### Post by WiKiDCLown456 on 2011-05-19
thank you i will give wxWidget a try but i would also like to learn how to make visuals(like a ball in pong) useing only code any suggestions on where to start to learn how

---

### Post by cgroza on 2011-05-19
> **WiKiDCLown456 said:**
> thank you i will give wxWidget a try but i would also like to learn how to make visuals(like a ball in pong) useing only code any suggestions on where to start to learn how
You want to do drawing? wxWidgets provides this feature too, although if you are in anything serious, I would use a specialized library.
This is a quick sample of what a google search showed up:
[http://wiki.wxwidgets.org/Drawing_on_a_panel_with_a_DC](http://wiki.wxwidgets.org/Drawing_on_a_panel_with_a_DC)

---

### Post by WiKiDCLown456 on 2011-05-19
ok i must not be understanding something here explane how this works without drag and drop GUI(so useing only code) say i wanted to add in my drop down list before id drag and drop a dropdown box onto my fourm then click the arrow and add in the list i want to appear in that drop down box so how do i do something like that useing only code (no visual)

---

### Post by slooksterpsv on 2011-05-19
> **WiKiDCLown456 said:**
> ok i must not be understanding something here explane how this works without drag and drop GUI(so useing only code) say i wanted to add in my drop down list before id drag and drop a dropdown box onto my fourm then click the arrow and add in the list i want to appear in that drop down box so how do i do something like that useing only code (no visual)

I don't know exactly, but its something like:
wxSize size = new wxSize(200,200);
wxSpinButton spinbutton = new wxSpinButton(my_window, WX_WINDOW, wxDefaultPosition, size, wxSP_HORIAONTAL, "spinButton");

That may not be correct, but you'd do something like that. my_window would be an initialized variable of wxWindow, and yeah it flows something like that. Tougher? Yes. Worth it? Yes. Why? Cause sometimes the GUI Editors can be a pain to work with to get things set specifically (in VisualBasic I was modifying the code rather than modify it in GUI).

---

### Post by WiKiDCLown456 on 2011-05-19
> **slooksterpsv said:**
> I don't know exactly, but its something like:
wxSize size = new wxSize(200,200);
wxSpinButton spinbutton = new wxSpinButton(my_window, WX_WINDOW, wxDefaultPosition, size, wxSP_HORIAONTAL, "spinButton");

That may not be correct, but you'd do something like that. my_window would be an initialized variable of wxWindow, and yeah it flows something like that. Tougher? Yes. Worth it? Yes. Why? Cause sometimes the GUI Editors can be a pain to work with to get things set specifically (in VisualBasic I was modifying the code rather than modify it in GUI).

ok i thank you cause you understand what im geting at but i dont really understand the code part of what you sead and how it works what would i google so i know what to call this type of codeing and whats a good referince (and program) to learn how to do this im very intrested in learning to make and position or scale things like buttons and text boxes or even a pic:D

---

### Post by slooksterpsv on 2011-05-19
> **WiKiDCLown456 said:**
> ok i thank you cause you understand what im geting at but i dont really understand the code part of what you sead and how it works what would i google so i know what to call this type of codeing and whats a good referince (and program) to learn how to do this im very intrested in learning to make and position or scale things like buttons and text boxes or even a pic:D

I would just google like wxWidget tutorial or <gui api name> tutorial where <gui api name> is like wxWidget, qt, fltk, etc. I personally like qt  because it looks nice, has a great designer, and is really easy to use with Python, but you can use it with C++ and that.

EDIT: I've been through this tutorial, it's good, I like how you make tetris at the end too. [http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)

---

### Post by WiKiDCLown456 on 2011-05-19
> **slooksterpsv said:**
> I would just google like wxWidget tutorial or <gui api name> tutorial where <gui api name> is like wxWidget, qt, fltk, etc. I personally like qt  because it looks nice, has a great designer, and is really easy to use with Python, but you can use it with C++ and that.

EDIT: I've been through this tutorial, it's good, I like how you make tetris at the end too. [http://zetcode.com/tutorials/wxwidgetstutorial/](http://zetcode.com/tutorials/wxwidgetstutorial/)

o ok i think i understand now wxWidget is like a plug in(or layer) that i can use in a program like qt (and maybe eclipse but probably not since theres no disign) and then i can use them to program in different languages like Python[never heard of it b4 now :(],Java,C++,fltk(also never heard of) or whatever i want. Is this correct?

---

### Post by cgroza on 2011-05-19
wxWidgets is a graphical user interface toolkit. Qt is doing exactly the same job as WxWidgets, it is his best competitor so far.

Both toolkits offer a way to create all those buttons, lists and menus. They are event driven, so when a user clicks a button, the toolkit calls a function that you specified before.

This is basically the way it works.

---

### Post by WiKiDCLown456 on 2011-05-19
> **cgroza said:**
> wxWidgets is a graphical user interface toolkit. Qt is doing exactly the same job as WxWidgets, it is his best competitor so far.

o ok thank you for clearing that up and helping me so much even with such beginner things

---

### Post by cgroza on 2011-05-19
> **WiKiDCLown456 said:**
> o ok thank you for clearing that up and helping me so much even with such beginner things
No problem, I am just doing the thing this community has done for me all this time.

---

### Post by slooksterpsv on 2011-05-19
> **WiKiDCLown456 said:**
> ...
then i can use them to program in different languages like Python[never heard of it b4 now :(],Java,C++,fltk(also never heard of) or whatever i want. Is this correct?

FLTK is a toolkit/gui API - actually it stands for **F**ast-**L**ight **T**ool**K**it

Java, C++, and Python are programming languages.

There's tons out there:
[http://en.wikipedia.org/wiki/List_of_programming_languages](http://en.wikipedia.org/wiki/List_of_programming_languages)

That I think is almost if not all of them.

---

### Post by WiKiDCLown456 on 2011-05-19
> **slooksterpsv said:**
> FLTK is a toolkit/gui API - actually it stands for **F**ast-**L**ight **T**ool**K**it

Java, C++, and Python are programming languages.

There's tons out there:
[http://en.wikipedia.org/wiki/List_of_programming_languages](http://en.wikipedia.org/wiki/List_of_programming_languages)

That I think is almost if not all of them.

wow give warning helmet needed for link #-o :lol:

---

### Post by slooksterpsv on 2011-05-19
> **WiKiDCLown456 said:**
> wow give warning helmet needed for link #-o :lol:

Well the most common that I always hear about are:
Python, Perl, C++, C, Java, C#, Objective-C, Haskell, REALBasic, Visual Basic, and PHP. 
That's why I can bring those up so quick.

---

