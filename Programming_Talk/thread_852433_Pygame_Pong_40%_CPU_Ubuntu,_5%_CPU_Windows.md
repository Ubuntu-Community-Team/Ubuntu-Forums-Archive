---
title: "Pygame Pong: 40% CPU Ubuntu, 5% CPU Windows?"
date: 2008-07-07
forum: Programming Talk
---

### Post by martinw89 on 2008-07-07
Hello all,
Over the weekend I wrote a Pong game in Python/Pygame to freshen up on my Python (it is attached to this post).  I have not put much thought into optimization, I just wrote something to get a playable pong game.  I took it into work today to mess around with it while I waited for customers.  I expected to see the same ~40% CPU usage as at home, but instead saw that at work the python process was only using around 5% CPU.  Why the big difference?  I had the thought that Windows may have access to page flipping while Ubuntu might be limited to a software display, so I changed "pygame.display.flip()" to "pygame.display.update()".  However, with this change the Windows python process is still using around 5% CPU.  Below is a comparison of the two computers:

[LIST]
[*]Home computer is on Ubuntu Hardy
[LIST]
[*]Work computer is XP Pro SP3
[/LIST]
 
[*]Home computer is a 1.8GHZ Core 2 Duo w/ 2GB of RAM
[LIST]
[*]Work computer is 2.2GHZ Core 2 Duo w/ 2GB of RAM
[/LIST]
 
[*]On home computer, multiple programs are using Python
[LIST]
[*]On work computer, my Pong game is the only program using Python
[/LIST]
 
[*]Python is version 2.5 on home computer
[LIST]
[*] Python on Work computer is PortablePython using Python 2.5
[/LIST]
 
[*]Pygame on home computer is the version in the Hardy repos (1.7)
[LIST]
[*]Pygame on the work computer is version 1.8
[/LIST]
 
[/LIST]
I am very puzzled why the two similar computers have such different CPU usage for a simple little Pong game.  Does pygame 1.7/1.8 make such a big difference?  Is pygame currently much more efficient on Windows?

My pong game is attached to this post along with the necessary textures.  I apologize for any sloppiness, this was only intended to be something I messed around with.  Thank you in advance for any help!

**Edit:** This issue has been resolved.  For anyone who has similar performance differences in different versions of Pygame, don't use "pygame.time.Clock.tick()", this function is a busy loop in Pygame 1.7, as opposed to Pygame 1.8 where it uses SDL_Delay.

---

### Post by tamoneya on 2008-07-07
can we see your code.  I think it may have to do with blit time.  Most likely the blit time is increased in linux because you have improper graphics drivers or something.  By looking in the code we can try to optimize around the slow blits.  Since pong is fairly simplistic the code should be managable in these forums.

---

### Post by LaRoza on 2008-07-07
> **tamoneya said:**
> can we see your code.

It is attached.

---

### Post by martinw89 on 2008-07-07
> **tamoneya said:**
> can we see your code.  I think it may have to do with blit time.  Most likely the blit time is increased in linux because you have improper graphics drivers or something.  By looking in the code we can try to optimize around the slow blits.  Since pong is fairly simplistic the code should be managable in these forums.

Yes my code is definitely slow at blit time, but in a way that should affect both Windows and Linux.  I just wipe the whole screen and then blit every sprite, regardless of if it's moved yada yada.  So this is slow, but that is not my concern at the moment.

Regarding linux drivers.  My home computer on Hardy has an Nvidia 8400 mobile and the appropriate Linux drivers (which I know for sure work fine).  I am NOT running Compiz.

Thanks!  (And thanks LaRoza for noticing the attachment).

---

### Post by drubin on 2008-07-07
Ye very high cpu usage on my computer as well...

---

### Post by slavik on 2008-07-07
if PyGame uses OpenGL, there are three explanations I can come up with off the top of my head.

1. In Python, the OpenGL bindings call glError() after every OpenGL call (to provide support for exceptions). As much as I wish this were true, I doubt it.

2. You don't have OpenGL accelaration. The drawing is done in software.

3. Some other software renderer is used (not OpenGL).

I am inclined to think that your issue is #2. Can we get output of the following command? 'glxinfo | grep direct'

Also, what driver and what video card do you have/use?

---

### Post by LaRoza on 2008-07-07
> **slavik said:**
> if PyGame uses OpenGL, there are three explanations I can come up with off the top of my head.


It uses SDL, not OpenGL.

---

### Post by martinw89 on 2008-07-07
> **slavik said:**
> I am inclined to think that your issue is #2. Can we get output of the following command? 'glxinfo | grep direct'

Also, what driver and what video card do you have/use?
Thanks for your reply.  As I mentioned in my previous post, there are no graphics issues here.  So for anyone joining in on the discussion, this problem is absolutely 100% totally not related to a video hardware/driver issue.

And as mentioned in LaRoza's previous comment, video card drivers are a non-issue as Pygame is just a wrapper for SDL.  You have to specify if you want to use OpenGL for your display.  And as I said in the original post, I am using a software screen with the software update method "pygame.display.update()".


I just ran the Pong game for a little, and actually top says that python is at 70% to 80% cpu usage with the game running.  Just to clarify, top reports that python stays below 1-2% CPU usage normally.  I am still quite lost as to what is causing the huge CPU usage gap (remember, the python process is around 5% CPU usage when running my pong game on Windows).

Thanks for your replies everyone :)  Can anyone else think of an explanation for this difference?

---

### Post by Can+~ on 2008-07-07
[http://ubuntuforums.org/showthread.php?t=404187&page=2](http://ubuntuforums.org/showthread.php?t=404187&page=2)

---

### Post by martinw89 on 2008-07-07
> **Can+~ said:**
> [http://ubuntuforums.org/showthread.php?t=404187&page=2](http://ubuntuforums.org/showthread.php?t=404187&page=2)

Thanks for the reply.  Unfortunately, this did not help.

---

### Post by Wybiral on 2008-07-07
I did a little profiling and found that the "fill" function was pretty costly compared to the rest. I might recommend creating a solid surface and blitting it to the screen instead of filling it each time, something like this:

```

clear = screen.copy()
clear.fill((0, 0, 0))

# To clear:
screen.blit(clear, (0, 0))

```

But even before that, it didn't take more than 20% of my CPU at any given time.

---

### Post by martinw89 on 2008-07-07
Interesting Wybiral, thanks for taking the time to look into what's going on "under the hood".  I will keep this in mind for future Pygame projects.  Ultimately, my plan was to use the "pygame.display.update()" method with a list of only what needs to be updated so I could avoid blitting the entire screen and then blitting each rect.

I tried this change and it unfortunately made a negligible difference.  Also, you mentioned that it never goes above 20% on your computer.  This is really interesting, it further leads me to believe it has something to do with my environment.  What version of Python/Pygame/SDL are you running?

---

### Post by Wybiral on 2008-07-07
Python-2.5.1, PyGame-1.7.1, SDL-1.2, my graphics card: GeForce FX 5200

You can do some quick and dirty profiling just by replacing the bottom of your code with:
```

if __name__ == "__main__":
    import profile, pstats
    profile.run("runGame()", "profile.txt")
    stats = pstats.Stats("profile.txt")
    stats.sort_stats("cumulative") # sort by cumulative time in functions
    stats.print_stats()

```
When you quit your program, it will print out your stats. You can see the difference between using the "fill" each iteration and blitting a pre-filled surface (on my system anyway).

I will also mention that you're using a lot of globals. I would recommend putting things into a "Game" class or something. The reason for this is that access to global variables is slower in Python because it first does a lookup in the local scope and only does the global lookup after that fails. Plus, globals are evil :) I'm sure that's not the problem in this case, but for future reference, in tight loops it can make an impact.

---

### Post by Zugzwang on 2008-07-08
> **martinw89 said:**
> Thanks for your reply.  As I mentioned in my previous post, there are no graphics issues here.  So for anyone joining in on the discussion, this problem is absolutely 100% totally not related to a video hardware/driver issue.

And as mentioned in LaRoza's previous comment, video card drivers are a non-issue as Pygame is just a wrapper for SDL.  You have to specify if you want to use OpenGL for your display.  And as I said in the original post, I am using a software screen with the software update method "pygame.display.update()".


Not necessarily. The graphic card also provides 2D acceleration and you do not need to use OpenGL for that. For example, on my computer, DOSBOX runs *much* *much* slower on Linux than on Windows because I'm using the "nv" open source driver (for Windows, the proprietary driver is used, of course). And Dosbox also doesn't use OpenGL (at least using my settings). I would also assume that that's the problem.

Maybe someone comes up with a C (or C++) SDL 2D benchmark for comparing the results. In this case, we could rule out pysdl as the problem.

---

### Post by martinw89 on 2008-07-08
> **Wybiral said:**
> You can do some quick and dirty profiling just by replacing the bottom of your code with:

Thanks, I didn't know that profile even existed!  And, I also didn't know that globals where checked after locals.  This discussion is definitely helping regarding general optimization.

Profile has helped me find one of my main CPU crunchers, something I believe may not be happening on my work computer:
```
   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        1    0.000    0.000   36.110   36.110 profile:0(runGame())
        1    0.000    0.000   36.106   36.106 <string>:1(<module>)
        1    0.000    0.000   36.106   36.106 ./pypong.py:104(runGame)
**     2968   32.118    0.011   32.118    0.011 :0(tick)**
     2970    0.000    0.000    3.752    0.001 ./pypong.py:77(updateScreen)
    14852    3.688    0.000    3.688    0.000 :0(blit)
...

```(emphasis mine)

In this run, the tick() function used 88.8% of the CPU time!  That's 8.5 times as much CPU time as my updateScreen() function.  This doesn't seem right, tick() is supposed to hand over control to the OS while the loop waits for the next frame.  Doing some calculations, 60FPS is 0.0166 seconds for each frame.  updateScreen() is using 0.001 seconds per call, which leaves 0.0156 seconds for everything else in the loop.  tick() is using 0.011 seconds, which makes it seem like it may be crunching CPU almost the whole time it waits.  What's up with that?

And Zugzwang, I suppose it was slightly premature to rule out graphics card issues.  However, I want to point out again that I have the NVIDIA binaries on my home computer and am not experiencing any issues with them.  The work computer has integrated Intel acceleration and also has the necessary drivers.  For example, Frozen Bubble on my home computer never goes above 15% CPU usage besides the initial loading and runs incredibly smoothly.  Frozen Bubble is of course written much better than my simple little pong game, but I think it helps demonstrate that I am not experiencing driver issues.

**Edit:** I changed the Clock.tick() function to an approximation of what would be 60fps using pygame.time.wait().  This in fact makes a GIANT difference; now the python process never goes above 10% CPU usage when running the pong game.  I will have to test this on the Windows work computer to see if Clock.tick() is so costly on it as well.  Does anyone have any ideas as to why Clock.tick() is being so greedy?

**Edit 2:** Looking into the Pygame 1.7 documentation and the 1.8 changelog I have found the problem.  In 1.7, Clock.tick() uses a busy loop to limit frame rate.  This was changed in 1.8 to an approximation using SDL_Delay.  I have pygame 1.7 on my home computer, 1.8 on my work computer.  Thank you very much Wybiral for mentioning profile, that's what led me to the solution.

---

