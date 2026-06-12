---
title: "Python pygame won't launch from panel"
date: 2010-05-16
forum: Programming Talk
---

### Post by dsr3 on 2010-05-16
Hi there-

I have a Pygame game that launches just fine from a terminal, but refuses to launch when linked to a launcher in the panel.

If anyone could suggest a place to start looking as to why this happens I'd appreciate it.

I create a custom launcher that uses ```
python /path/to/game.py
```

I had also created a bash script that cd'd into the game's directory and launched it, but that's not working either....

---

### Post by DangerOnTheRanger on 2010-05-16
Could I see the source code?

---

### Post by dsr3 on 2010-05-16
Certainly. It's attached.

I did also try changing the shebang line to #!/usr/bin/env python.

Oh. And if you'd like all the stuff (images, etc.) here's a link:

[http://bitbucket.org/dsr/cupcake/get/tip.tar.bz2]("http://bitbucket.org/dsr/cupcake/get/tip.tar.bz2")

---

### Post by soltanis on 2010-05-17
(1) What is the invocation if you run it from the command line?
and (2) What happens when you run the launcher command exactly as-is (copy and paste it) from a terminal?

---

### Post by Tony Flury on 2010-05-17
Does your python script make assumptions about the current working directory - that has tripped me up before.

When you run it in the terminal - make sure your have your current directory set to ~ (i.e. your home), and not the directory of the script.

---

### Post by dsr3 on 2010-05-17
If I leave the launcher set to "Application in Terminal", the following works:

```
python  /home/dan/cupcake/Cupcake.py
```

That also works from the command line.

I don't really want a terminal window spawned though....

---

### Post by Tony Flury on 2010-05-17
which directory are you in when you run your python <path> command in the terminal ?

---

### Post by dsr3 on 2010-05-17
The user home directory that terminal is initially in when it opens.

---

### Post by Tony Flury on 2010-05-17
Very odd - 
The only thing I can suggest is that you mod your script to keep a detailed log file - so you can see what it does.

---

### Post by Tony Flury on 2010-05-17
As a matter of interest - does the code you posted in the zip file actually work - I am getting syntax and attribute Errors

---

### Post by dsr3 on 2010-05-17
Errr.....yeah, it should. I haven't run into any trouble.

By zip file do you mean the file from bitbucket?

---

### Post by Tony Flury on 2010-05-17
Yes - the one from bit bucket gave me a syntax error - one line had telif (and not elif) and when i corrected that it failed in pygame library.

```

  File "/home/tony/cupcake/Cupcake.py", line 366, in <module>
    reward_group.draw(screen)
  File "/usr/lib/python2.5/site-packages/pygame/sprite.py", line 313, in draw
    self.spritedict[spr] = surface_blit(spr.image, spr.rect)
AttributeError: 'GroupSingle' object has no attribute 'spritedict'

```

The version from the attachement (i.e. not from bitbucket - did not have the "telif" error - but generate the same issue as above

---

### Post by dsr3 on 2010-05-17
Well that's certainly odd. What version of pygame do you have?

---

### Post by Tony Flury on 2010-05-17
pygame 1.7

---

### Post by Tony Flury on 2010-05-17
Removed - browser/wifi ****-up

---

### Post by dsr3 on 2010-05-17
I'm using 1.9 so I wonder if that's it?

---

### Post by Tony Flury on 2010-05-17
sounds like it might be ...

---

### Post by dsr3 on 2010-05-17
So if I wanted to watch a system log or something for errors, where would I find that?

---

### Post by Tony Flury on 2010-05-18
Unless your application generates it's own logs, i don't think there is a generic log that records everything.

---

### Post by dsr3 on 2010-05-18
And it's not like there are errors when I launch the game through terminal.

Would there be additional errors that could be written to a log?

---

### Post by soltanis on 2010-05-18
If you're running 1.9 and the game runs in 1.9, I doubt that a pygame version problem is the source of the issues. Perhaps you should try to disable all exception handling in your code: sometimes you make the mistake of catching all exceptions in a try/except block, and that might be masking the problem in your program.

---

### Post by Tony Flury on 2010-05-18
> **dsr3 said:**
> And it's not like there are errors when I launch the game through terminal.

Would there be additional errors that could be written to a log?

No - what i mean is that you write your program so it open a text file and outputs messages to the file each time something important happens in the programm - a class is created, a window is opened, a function is called - and at least that way you can see how far your program is getting.

---

### Post by Tony Flury on 2010-05-18
> **soltanis said:**
> If you're running 1.9 and the game runs in 1.9, I doubt that a pygame version problem is the source of the issues. Perhaps you should try to disable all exception handling in your code: sometimes you make the mistake of catching all exceptions in a try/except block, and that might be masking the problem in your program.

I think his comment about running 1.9 was in reference to me running 1.7 and not being able to get his code to run :-)

---

### Post by dsr3 on 2010-05-18
> **Tony Flury said:**
> No - what i mean is that you write your program so it open a text file and outputs messages to the file each time something important happens in the programm - a class is created, a window is opened, a function is called - and at least that way you can see how far your program is getting.

Ohhhh....sure. Good call. I think I'll try that.

And yes, I was referring to pygame 1.7 vs 1.9 in respect to the errors Tony saw.

---

### Post by dsr3 on 2010-05-21
Turns out my game is failing to launch from the panel because of this:
```
user_name = os.getlogin()
```

If I take that line out, everything's cool.

??????

---

### Post by OgreProgrammer on 2010-05-21
> **dsr3 said:**
> Turns out my game is failing to launch from the panel because of this:
```
user_name = os.getlogin()
```If I take that line out, everything's cool.

??????

> On linux, getlogin() returns the name of the "user logged in on the  controlling terminal of the process."  It therefore fails when there is  no controlling terminal, e.g., in a mod_python application. – [Vebjorn Ljosa]("http://stackoverflow.com/users/17498/vebjorn-ljosa") Nov 10 '09 at  23:56

as per this page, [http://stackoverflow.com/questions/842059/is-there-a-portable-way-to-get-the-current-username-in-python](http://stackoverflow.com/questions/842059/is-there-a-portable-way-to-get-the-current-username-in-python) , which also has some alternate ideas.

---

### Post by dsr3 on 2010-05-21
Thanks for providing an explanation. That's the part that was confusing me.

---

### Post by OgreProgrammer on 2010-05-22
Its a gotcha that I wouldnt have know either. I'm glad to have learned it.

---

