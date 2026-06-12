---
title: "[java+netbeans] can someone help me find this bug"
date: 2009-02-28
forum: Programming Talk
---

### Post by Choad on 2009-02-28
for some reason when i move the player left it hangs. presumably stuck in an infinite loop.

i can't even figure out how to find (for want of better words) "where the program is at" when i pause it in debug mode

so yeah, firstly can someone help, and secondly can someone tell me how to use the debug mode of netbeans properly lol

thanks!

edit: oh and the whole game is a bit screwy atm coz i have been rewriting significant chunks of it and moving code from one class to another etc. etc. trying to clean it up, and also have just recently moved the coordinate system from int to float so if you're wondering why you can't even jump over 1 block, that's why!

---

### Post by jonofan on 2009-02-28
Yes I don't find the netbeans debugger particularly readable. I find if you run in debug mode with a breakpoint you are confident it will make it to, you can use F7 to step through the rest.

It appears to be getting stuck on in the Element class in isCollidingAt().

if( elLeftSide < rightSide ) -> always returns false.

---

### Post by kavon89 on 2009-02-28
> **Choad said:**
> for some reason when i move the player left it hangs. presumably stuck in an infinite loop.

i can't even figure out how to find (for want of better words) "where the program is at" when i pause it in debug mode

so yeah, firstly can someone help, and secondly can someone tell me how to use the debug mode of netbeans properly lol

thanks!

edit: oh and the whole game is a bit screwy atm coz i have been rewriting significant chunks of it and moving code from one class to another etc. etc. trying to clean it up, and also have just recently moved the coordinate system from int to float so if you're wondering why you can't even jump over 1 block, that's why!

Best way I've found NetBean's debugger useful is the line breakpoints. The program will stop once the code gets to those instructions. To make a breakpoint, click on the left side of the text field where those icons usually appear and a red line with a stop symbol will highlight the line. Then run the program in debugger mode.

You'll be able to check what values your primitive & string values your variables hold once you go down the tree list. Once you're done verifying that everything is fine, hit Continue, and it'll go till the next breakpoint (if you put the breakpoint in a loop, you can check each iteration).

 It has helped me dozens of times, most recently when I was getting random null pointers and I found the root of the problem was that in an array that should have been fine, one of the indexes was becoming null.

---

### Post by supirman on 2009-02-28
I made a quick screen cast of using the debugger.  Basically, start your app in debug mode.   When you move your player left and it hangs, press pause.  On the left panel, the debug view should be showing.  Look in the AWT-EventQueue, and you'll see your call stack.  Also, you can right click on a variable and go to "Watch", then it will show you the variable in the bottom of the screen and you can inspect all of its elements.

I didn't try to track down what is causing your issues, but Actor.java:70 always seems to return block 118, then Actor.java:62 returns 118 as well, hence you're stuck in a loop.


See the screencast (it's an AVI recorded with camstudio - hopefully you can view it) here: [http://erafx.com/tmp/netbeans_debug.avi](http://erafx.com/tmp/netbeans_debug.avi)

---

### Post by Choad on 2009-03-01
thanks all i found the bug. you are right supirman, it was how i was detecting the colisions. i had it so if i was hitting a corner it would not immediately adjust the speed so it would keep hitting that same corner forever (block 118 ), so to fix it i just temporarily move the corner 300 pixels away, finish detecting colision with everything else and then move it back. a bit hackish but it works!

i had actually already discovered this bug but i stopped coding for a week and forgot. doh!

new problem tho... since moving to floats, my character can't fit through a 1 block gap. any suggestions on how to fix this? im guessing it's a problem with the inaccuracy of floats

slightly less broken version attached :)

---

### Post by supirman on 2009-03-01
This probably isn't the best way to address this, but it makes it (appear) to work pretty well.

```
	public boolean isCollidingAt( float x, float y, Element el ) {         
	    float elLeftSide = el.getX();
	    float rightSide = x + (float)getWidth();

	    if( elLeftSide < rightSide ) {
                float leftSide = x;
                float elRightSide = el.getX() + el.getWidth();
                
                if( elRightSide > leftSide [COLOR="Red"]+ .8f[/COLOR] ) {
                    float elTop = el.getY();
                    float bottom = y + getHeight();
                    
                    if( elTop < bottom ) {
                        float top = y;
                        float elBottom = el.getY() + el.getHeight(); 
                        
                        if( elBottom > top [COLOR="Red"]+ .8f[/COLOR] )
                            return true;
                    }
                }
            }       	    
	    return false;
	}
```

---

### Post by kavon89 on 2009-03-01
> **Choad said:**
> new problem tho... since moving to floats, my character can't fit through a 1 block gap. any suggestions on how to fix this? im guessing it's a problem with the inaccuracy of floats

I had always thought floats were suppose to be accurate. Why not use double? I don't remember doubles having issues like 1.00000000000001214, or do I have it backwards?

---

### Post by Choad on 2009-03-01
it was to do with my crappy colision detection again lol! i was just reducing the speed by 1 until the object didn't colide any more... which resulted in ending up at y = 32.3 or whatever... so i replaced that with some code to move to exactly touching the block i'm coliding with and it works fine :) also cut's down on the amount of processing necessary :D

---

### Post by Choad on 2009-03-01
ok just for fun and because i find their movement really amusing (probably just because i made it, you might not find it as entertaining) i will upload the current, working project

load the second level and look at all the little critters bounce around :D

thanks all for helps, i am sure i will need help again!

---

### Post by supirman on 2009-03-01
> **Choad said:**
> ok just for fun and because i find their movement really amusing (probably just because i made it, you might not find it as entertaining) i will upload the current, working project

load the second level and look at all the little critters bounce around :D

thanks all for helps, i am sure i will need help again!

I've never even considered making a game before, but this has sparked my interest a bit.  I look forward to see what you end up with -- the jumping critters are pretty neat!

---

