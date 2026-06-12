---
title: "Unity Launcher"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by fblud on 2012-08-02
Hi,

My Unity Launcher won't reappear once I hide it.  The hide function works.  It just won't reappear.

I'm running 12.04 on a G4 PowerPC laptop.

If you need more info I will do my best to supply it.

Please help.


fblud

---

### Post by levlaz on 2012-08-02
What happens when you move your mouse cursor to the top left portion of the screen? 

What happens when you hit the "apple" button ... I believe its called command.

---

### Post by Frogs Hair on 2012-08-02
The launcher is set to appear by moving the cursor to the side and not the top by default. So if you move the cursor to the top left corner the launcher won't appear.

This can be changed in appearance > behavior. Try turning on and off the auto hide from the same location and see if that gets the launcher to appear. If you have not logged out and back in since changing the setting try that also.

---

### Post by fblud on 2012-08-02
Sorry levlaz,

I should have elaborated in my first post:  The left side or the top left corner won't make it reappear.

Using the command key makes it reappear.  But, it also calls up Dash Home on the rest of the screen.

Any suggestions?

---

### Post by levlaz on 2012-08-02
> **Frogs Hair said:**
> The launcher is set to appear by moving the cursor to the side and not the top by default. So if you move the cursor to the top left corner the launcher won't appear.

This can be changed in appearance > behavior. Try turning on and off the auto hide from the same location and see if that gets the launcher to appear. If you have not logged out and back in since changing the setting try that also.

Thanks -- I am still using 10.04 but I thought that the last time I tried unity (when it first came out) the top left was the place to be. :) 

Thanks for the tip!

---

### Post by fblud on 2012-08-02
I just tried logging out but it didn't help.

I said the following, "The left side or the top left corner won't make it reappear...", because I tried both options in Behavior.  Even with sensitivity set the high it doesn't work.

The only thing that works is the command key.  But, I want to just to mouse over it and have to appear.

Oh, and when I hold the command key I appears with numbers over the processes (I know there is a name for that function.  I haven't had enough time with the machine to commit it to memory).  When I tap it, that's when Dash Home appears as well.

Further suggestions?

---

### Post by vasa1 on 2012-08-02
> **fblud said:**
> I just tried logging out but it didn't help.

I said the following, "The left side or the top left corner won't make it reappear...", because I tried both options in Behavior.  Even with sensitivity set the high it doesn't work.

The only thing that works is the command key.  But, I want to just to mouse over it and have to appear.

Further suggestions?
Did you move the mouse up and down against the left side?

---

### Post by fblud on 2012-08-02
I just tried it.  Still nothing.  FWIW, it doesn't work on the LiveCD either,  I mean when I was testing out the OS.  Is there something my machine is lacking?

---

### Post by Frogs Hair on 2012-08-02
Try a restart and see what happens.

---

### Post by dwhite on 2012-08-02
Hi-hope this helps

the launcher is designed **not** to appear if the cursor is just placed on the left edge, you must place the cursor at the left edge and then **try to push the cursor past the left edge**, it won't move past the left edge of course but if you continue to push left the launcher will appear. (if the sensitivity is set to "low" it can be difficult or nearly impossible to get the launcher to appear, to get it to appear more easily set the sensitivity higher, see attached thumbnail)

i understand that this feature was added to stop the launcher from appearing at unwanted times when the cursor has to be on or near the left hand edge for some other reason.

---

### Post by fblud on 2012-08-02
I tried your suggestion to restart and it didn't work.

Then I tried the other suggestion to try and move the cursor past the edge.  It didn't work.

Right now the only thing that does is the command key.  Once I get my track pad up and running I should be able to trash with a secondary click, no?  So, that and the command key should suit my needs.  I just want to auto-hide because I'm on a small screen and real estate is at a premium.

If, for some strange reason, it begins to appear and try to re-create the situation in which it did and post my results.  Maybe somebody else will use them.  _If..._  ;)

Thanks for all your help!
 

fb

---

### Post by vasa1 on 2012-08-02
What about running **unity --reset** in a terminal?

---

### Post by fblud on 2012-08-02
vasa1

I ran unity --reset in a terminal.  It said it was changing to metacity while changing the value.  Then the terminal window flashed then filled up the whole screen with "untitled window" in the menu bar.  'Terminal' then came up where "untitled window' was.  It still blocked the whole screen.  I had to try twice but I was able to get Terminal to close.  There was my desktop under it.  However, after a short delay two menu bars came up, one directly below the usual one.  The second had nothing on the left, meaning it didn't say 'Ubuntu Desktop'. Unity was still not there when I moused past the left side of my screen.

Next I tried logging out to see if it would help.  When I was back in everything was as before.  Unity was still hidden though with no intention of appearing.

I tried the command again.  All of the same as above happened.  Instead of logging out, this time I shut down the machine.  Nothing...

I'm guessing because I reset Unity all the flashing and double menus were par.  What I don't understand was why Unity didn't appear after the logout/shut down.

Sorry if this is too thorough of an explanation.  I want to be so I can solve this **basic** issue.

Thanks for your suggestion.

fblud

---

