---
title: "[SOLVED] Help me to make .exe with py2exe and check out my awesome game!"
date: 2008-09-02
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-02
I made a simple game with pygame. It firsts asks an image file from the user. Then it makes a window, and sets the image as background.
When the user clicks left mouse button, there will appear a bloody hole on the image, and blood splatters all around the window, and it plays a gun shooting sound.

Because all my friends use windows, I want to make a windows executable from this game.
But I have tried it all over and over again, I never manage to make it. Can somebody make me a windows executable from those files?

The attached zip contains the game itself (.py file), three sprites, a sound file and an icon I want to use with the exe.
(Default.jpg and icon.ico are really not necessary!)

Or if nobody wants to do this, could you give me good instructions?
If I try to install python or pygame on windows/wine, python console commands don't work and it can't find pygame.

I'd be VERY happy if somebody could do this..

---

### Post by WW on 2008-09-02
Awesome! (But a bit gruesome.)

Sorry, I can't help you with py2exe, I've never used it. :(

---

### Post by LaRoza on 2008-09-02
I'll reboot into Windows later to try py2exe, but what problems did you have? It shouldn't be hard.

It is easier I think to install Python and PyGame in Windows than to try to make a .exe.

Also, when making an archive, you should archive a folder, not a bunch of files. You used .zip so the term doesn't really fit, but that is a "tar bomb". You open it and it spreads files all over the place.

---

### Post by Cybergod on 2008-09-02
I was playing with this the other day and had trouble.  See the below website for a brief tutorial, it sure helped me.

[http://www.py2exe.org/index.cgi/Tutorial]("http://www.py2exe.org/index.cgi/Tutorial")

---

### Post by LaRoza on 2008-09-02
Now that I used it (sorry, didn't go into Windows), it is a cool game. Perhaps you should have some other images to use so users can select from a list?

I'd recommend popular targets like Emacs, Microsoft butterfly, Firefox, etc.

---

### Post by jinksys on 2008-09-02
It would be cool if there were more weapons.  Having a machine gun or shotgun would be nice :)

---

### Post by cmay on 2008-09-02
i have just tested the game. its cool. i think i have some old pictures that can be fun to test the game whit tonight. but there is one little problem whit the game. when i had to select the file to use i had to rename it and drop it the folder where the game is.it did not work so good whit he danish keybord keys. but other than that its a fun little game. good work. :)

---

### Post by OutOfReach on 2008-09-02
Wow very very nice game. Nice job :). I had a lot of fun with it :twisted:. Unfortunately I can't really help you with your py2exe thing, since I have never used it before.

---

### Post by mssever on 2008-09-02
> **LaRoza said:**
> Firefox.
Opera :)

@OP:
I didn't recognize the language the prompt/titlebars are in. Care to tell me? EDIT: nevermind, you said earlier that you're Finnish.

---

### Post by crazyfuturamanoob on 2008-09-03
> **Cybergod said:**
> I was playing with this the other day and had trouble.  See the below website for a brief tutorial, it sure helped me.

[http://www.py2exe.org/index.cgi/Tutorial]("http://www.py2exe.org/index.cgi/Tutorial")
Thanks, but I don't know how to install python and pygame on windows!
I ran the python installer, but command "python" doesn't work in console.
Then I installed pygame into C:\Python25 where my python installation is located. But it can't find pygame!

And this crap windows doesn't recognize spaces when I try to read that shooter.py with notepad!
All the text is in one line, without spaces, but with gedit on ubuntu, the spaces are there, and it is on multiple lines.

---

### Post by Zugzwang on 2008-09-03
> **crazyfuturamanoob said:**
> And this crap windows doesn't recognize spaces when I try to read that shooter.py with notepad!
All the text is in one line, without spaces, but with gedit on ubuntu, the spaces are there, and it is on multiple lines.

It *does* recognize spaces, just the newlines are different. Use a different editor, almost all of them *except* notepad work well with Unix newlines.

Note that the converse is also true: You could call the Linux editors crap since they are unable to write text files that can be correctly read in Windows. Also at least BASH cannot read Windows text files correctly. But both points of view are more or less incorrect: It's just different!

Same holds for the fact that typing "python" in Windows doesn't start the interpreter. That's because the python path is not in the PATH environment variable (same as in linux). It isn't because putting the exeutables in some special folders like /usr/bin or /bin like in Linux is a no-no in Windows (some programs do it anyway, but that's bad practice). You will need to start it using the full path *or* change your PATH variable accordingly.

As far as pygame is concerned: I don't know how to fix that.

---

### Post by cmay on 2008-09-03
[http://www.jrsoftware.org/isinfo.php](http://www.jrsoftware.org/isinfo.php)
this is just a suggestion until you find something out.
i used to use this setup program for windows when i had something i wanted to share whit freinds. maybe you can start whit that. (its free) and then until you have found a way to install python and pygame on windows you can at least distribute a exe setup file that installs the game in a folder in windows where your freinds then have to find out how to make python work.

---

### Post by pmasiar on 2008-09-03
> **crazyfuturamanoob said:**
> I ran the python installer, but command "python" doesn't work in console.

As I told you, use ActiveState Python installer, which sets environment correctly.

You either follow instructions or solve problems - but don't complain "it does not work' when problem is obviously between chair and keyboard :-)

---

### Post by eragon100 on 2008-09-03
The attached picture seemed like a good thing to shoot to pieces, great game! :lolflag:

---

### Post by crazyfuturamanoob on 2008-09-04
> **eragon100 said:**
> The attached picture seemed like a good thing to shoot to pieces, great game! :lolflag:

Thanks :D I am willing to make a better version of it, but I haven't decided anything yet.

BTW I just noticed that if you roll your mouse wheel up/down it shoots full auto x

Edit: I managed to install python + pygame + py2exe correctly on windows :) Now I can make the .exe myself.

---

