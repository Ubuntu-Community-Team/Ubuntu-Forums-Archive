---
title: "How do I start Skype and gXNeur automatically at startup?"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by ruslan kim on 2012-08-18
Hey guys!

Thank you all for your posts, I really appreciate all the help from any of you. It helps me get along with Ubuntu quicker and more comfortable)

I have got another question now. I know the answer is simple, but I can't find it myself.

I want to make Skype and gXNeur start automatically when I turn the PC on. How do I do that? I guess it has smth to do with Startup Applications, but what exactly?

Many thanks in advance!

---

### Post by ads52 on 2012-08-18
I see you have found 'Startup Applications', perhaps have a read here:

[https://help.ubuntu.com/community/AddingProgramToSessionStartup#ADD](https://help.ubuntu.com/community/AddingProgramToSessionStartup#ADD)

and this should guide you through adding your own applications :).

---

### Post by ruslan kim on 2012-08-22
> **ads52 said:**
> I see you have found 'Startup Applications', perhaps have a read here:

[https://help.ubuntu.com/community/AddingProgramToSessionStartup#ADD](https://help.ubuntu.com/community/AddingProgramToSessionStartup#ADD)

and this should guide you through adding your own applications :).

Thank you, but I still can not find the command in the "Command Field". It is said that I should right-click on the icon, but there is no "Properties" dialogue box... Where am I to find it? Kindly see the example below:

[I]As an example consider the Evolution mail client. Imagine you want to load Evolution every time you start up, instead of clicking on the "Evolution Mail" icon in the panel bar to launch the program. You can add the appropriate command to the Startup Programs tab.
Find the icon for Evolution in the panel bar at the top of the screen. Right click on it, and select "Properties." This will bring up the "Launcher Properties" dialog box. Notice the command in the "Command field." It may be necessary to place a cursor in the field by clicking on the line. Then use the arrow key to move right, to see the entire command.[/I]

---

### Post by newb85 on 2012-08-22
That help page very badly needs to be updated.  The "panel bar" it's talking about is the gnome-panel, which hasn't been part of the Ubuntu interface by default since Maverick, which has reached the end of its life.

You can very easily manually add the programs to Startup Applications.  Click "Add".  For "Name", put the name of the program (like "Skype").  It doesn't have to be exact, as this is only for your reference later.  "Command" does have to be exact, and it should be the command that will launch the program in question.  For example, if you enter "skype", skype will launch at startup.  The "Comment" field is also only for your reference, and you can leave it blank.

Now all you have to do is find the command that will launch gXNeur.

---

### Post by ravinfy on 2012-08-22
ruslan kim: Thanks for posting this question - I have been trying to set up some programs to automatically start up too!! 

newb85: MANY thanks for explaining the process is great detail. I`m ONE step away from knowing the solution though - and my question is: 
How do I know the "Command" for any program that I already have installed in my machine? (given there is no Properties dialogue box when we right click on any icon)

---

### Post by ruslan kim on 2012-08-22
The problem is solved!
It is so simple, check out this video:
[http://www.youtube.com/watch?v=w8vHybUuulc](http://www.youtube.com/watch?v=w8vHybUuulc)

---

### Post by newb85 on 2012-08-22
> **ruslan kim said:**
> The problem is solved!
It is so simple, check out this video:
[http://www.youtube.com/watch?v=w8vHybUuulc](http://www.youtube.com/watch?v=w8vHybUuulc)

Wow, I didn't realize they'd made it so simple.  Good find!

---

### Post by blackmail on 2012-08-22
Look at the screenshots:
Screenshot 1 will let you see the startup applications pannel.
Screenshot 2 will let you see the correct command.
Screenshot 3 will let you see the correct part to the skype applicatoin (```
/usr/bin
```)

The way to find a command for an app is a good question. FIrst you need to see in terminal, type the name of the program, example ```
skype
``` and if it cannot find the command it means that it is another command, also try to find the program using the aptitude application in terminal.

let us say you would like to install cairo dock. Well install aptitude
```
sudo apt-get install aptitude
```

then search for the app:
```
sudo aptitude search cairo | grep dock
```

there will be quite some data available. you can install cairo dock using:
```
sudo apt-get install cairo-dock
```

and launch it using ```
cairo-dock
```

as a good training play with the compiz, and install it from terminal using the above ethod i just mentioned.

As a hint, sometimes you will not be able to filter using grep because you are not sure what you are looking for then you need to look theough the whole search output. if there is a long list try ```
sudo aptitude search cairo | less
```

The less command will sve your life as it will output just as much as you can see on the screen. hope this helped a bit, and from here on it is reading and playing in the terminal. None of us have our heads as junk containers, meaning that it is meaningless to try and memorize the starting command of every program, just the way to find it :lolflag:

---

