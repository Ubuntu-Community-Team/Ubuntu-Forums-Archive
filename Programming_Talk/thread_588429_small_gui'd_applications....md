---
title: "small gui'd applications..."
date: 2007-10-23
forum: Programming Talk
---

### Post by hardyn on 2007-10-23
I have never created a gui'd application before, and i was curious the best way to go about it?

I have no intention for the program to ever be run without a gui, but its a better work flow to design my program as CLI and they add a gui front end? or just create it as a gui only?

The program will be written in python, and i was poking around with glade as the window editor, although i don't find it particularly easy... is there a better tool that i should be using for creating the windows for a python program?  its a very simple window with some check boxes and a slider or two, very similar to the power management control.

---

### Post by vambo on 2007-10-23
If you're going to use Python, then you might want to consider pyGTK for the GUI - [http://www.pygtk.org/]("http://www.pygtk.org/")

---

### Post by Wybiral on 2007-10-23
It's good practice to write your application first and get it all tested before adding a GUI. Glade should be fine for the GUI you describe. What were you having trouble with?

---

### Post by pmasiar on 2007-10-23
easygui is the simplest GUI toolkit, although with limited functionality: no events, no problems! :-)

---

### Post by LaRoza on 2007-10-23
If you are using Python (which makes the creation of a GUI easier than many other languages), my wiki has resources for EasyGUI, wxPython, Tkinter, and PyGTK. I wouldr recommend wxPython, but that really doesn't mean anything.

---

### Post by 1337455 10534 on 2007-11-09
So I downloaded the easygui zip from your site, and I found documentation (very good one) and the actual .py. Do I make it into a mod so that IDLE can import it?
edit> nvm: i put the mod in teh wrong dir

---

### Post by slavik on 2007-11-09
> **hardyn said:**
> I have never created a gui'd application before, and i was curious the best way to go about it?

I have no intention for the program to ever be run without a gui, but its a better work flow to design my program as CLI and they add a gui front end? or just create it as a gui only?

The program will be written in python, and i was poking around with glade as the window editor, although i don't find it particularly easy... is there a better tool that i should be using for creating the windows for a python program?  its a very simple window with some check boxes and a slider or two, very similar to the power management control.
It's always nice to pretend that there is hardware there that might not actually be there. :)

I also wish that there was a GUI for ls, cd and other utilities. Then Unix can be just like Windows. :-D

---

### Post by LaRoza on 2007-11-09
> **1337455 10534 said:**
> So I downloaded the easygui zip from your site, and I found documentation (very good one) and the actual .py. Do I make it into a mod so that IDLE can import it?
edit> nvm: i put the mod in teh wrong dir

No, just put it in the directory of your script and import it there. It requires Tcl and Tkinter. Which you probably have.

---

### Post by RetiredInMaine on 2007-11-09
On the question of how to design your program, as a gui or as a cli first. A cli program is is driven by the code, usually by testing the input.  However a gui is event driven, usually by a click event.  You can code and test routines as a cli but the actual program design needs to react to events. The user may not enter data in the sequence or manner that you expect. 

For anything other than a trivial program you should first design the user interface, then code the events that will be triggered. Always keep in mind that the user has complete control over what order to trigger events. 

One way to control the order of events is to have multiple screens and show the screens in the order you want the user to react to. But this is cumbersome and is not foolproof. Never underestimate the ingenuity of the user.

.Actually when I was a Windows programmer I usually did the gui first  using VB and then the back end in c.  Linux does not have VB but it does have gambus (gambus is almost basic) but I have not had enough experience with gambus to know if that approach is viable.

This is one mans opinion, others may disagree. I hope you find this discussion useful.

---

### Post by slavik on 2007-11-09
> **RetiredInMaine said:**
> On the question of how to design your program, as a gui or as a cli first. A cli program is is driven by the code, usually by testing the input.  However a gui is event driven, usually by a click event.  You can code and test routines as a cli but the actual program design needs to react to events. The user may not enter data in the sequence or manner that you expect. 

For anything other than a trivial program you should first design the user interface, then code the events that will be triggered. Always keep in mind that the user has complete control over what order to trigger events. 

One way to control the order of events is to have multiple screens and show the screens in the order you want the user to react to. But this is cumbersome and is not foolproof. Never underestimate the ingenuity of the user.

.Actually when I was a Windows programmer I usually did the gui first  using VB and then the back end in c.  Linux does not have VB but it does have gambus (gambus is almost basic) but I have not had enough experience with gambus to know if that approach is viable.

This is one mans opinion, others may disagree. I hope you find this discussion useful.
or what you do is write a CLI program making use of the getopt library and add options for any type of input you might want ... such as where to output the compressed file, how to compress it, whether to be verbose, whether to preserve permissions and which file/directory to compress/archive and THEN someone can write a gui for it, or 2 ...

For the "special people", look at tar, File-Roller and Ark. :)

---

### Post by pmasiar on 2007-11-09
One of nice features of easyGUI is that it does not have events at all - this is why it is easy :-) So starting with plain commandline is simpler, then add easyGUI interaction for input, done.

---

### Post by 1337455 10534 on 2007-11-09
Umm, sorry to disappoint, but I'm just a kid..
I've already written all of my (very) functional file-shredding code, I just need to make a simple GUI.

---

### Post by slavik on 2007-11-10
> **1337455 10534 said:**
> Umm, sorry to disappoint, but I'm just a kid..
I've already written all of my (very) functional file-shredding code, I just need to make a simple GUI.
the younger they are, the better. I suggest you start looking for glade/gtk tutorials :)

---

### Post by 1337455 10534 on 2007-11-10
> 
the younger they are, the better. I suggest you start looking for glade/gtk tutorials 

thx for the trust! But no, seriously, im barely a freshman in High school.
I will look into those though!

---

### Post by slavik on 2007-11-10
> **1337455 10534 said:**
> thx for the trust! But no, seriously, im barely a freshman in High school.
I will look into those though!
even better.

I just finished college and some of my friends would write small BASIC programs on a Commodore64 when they were younger than you ...

---

### Post by 1337455 10534 on 2007-11-10
Heh heh/
When I was an 8th grader, I got second place in my state science fair for writing a BASIC program that can solve any (non-word problem) question in my Algebra 1, 2, and Trigonometry books.
The US army gave me a $50 bond (odd, no?), but nothing much else happened...

---

### Post by slavik on 2007-11-10
start exploring :)

glade is very easy to use (once you understand the concept of containers and why they are there).

---

