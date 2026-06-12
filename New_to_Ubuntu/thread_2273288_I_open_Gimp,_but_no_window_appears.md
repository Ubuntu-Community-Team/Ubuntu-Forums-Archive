---
title: "I open Gimp, but no window appears"
date: 2015-04-11
forum: New to Ubuntu
---

### Post by ghn2 on 2015-04-11
I'm new to Ubuntu, and the transition is going mostly well, but a problem has popped up. Or perhaps it is that a desired window does NOT pop up when I start the program is a better description.
As I mentioned, I get no window when I launch Gimp. I'm not sure if the problem is with Gimp or Ubuntu - I may have clicked on something I shouldn't, since the program did work as desired, until it suddenly didn't.
When I try to start the program, I get the "startup screen", then it disappears and nothing else will appear
When I enter alt+tab, I see that the program seems to be running in the background, but I can't get at any windows, nor can I open any pictures.
In the launcher I can see the icon, but it doesn't have the little triangle next to it that a running program should have, instead it has a "hollow" triangle, like this >

I hope somebody can figure this out!

---

### Post by steeldriver on 2015-04-11
Hello and welcome to the forums

Have you tried opening a terminal (Ctrl-Alt-t) and running gimp from the command line? you may get some useful error messages

---

### Post by ghn2 on 2015-04-11
Exactly the same thing happens as when I use the launcher, I get the splash screen, and then it just seems to sit there in the background without doing anything useful, and with the same hollow triangle instead of a filled triangle. No error messages either.

---

### Post by deadflowr on 2015-04-12
It sounds like it's running, but not in the current workspace. (the > arrow as is on the left side is usually an indication that the app is running but not where the current workstation is).
Have you tried clicking on the icon? That sometimes helps move you to the apps current workspace.
Alternatively, you can try the ctrl +alt + up/down/left/right to move around workspaces and see if it appears in any of them.
 
It is unclear what you meant by *I may have clicked on something i shouldn't*, could you be clearer?
Did you try doing any desktop customizations? Like using unity-tweak, or ccsm?

---

### Post by ghn2 on 2015-04-12
The only thing I've been doing with Gimp is to do some editing, and also resizing the windows. I'm creating a knitting pattern (of all things), and I'd been creating the various pattern elements before copying the results to Calc, a tedious process which means I had the Calc window and the gimp window side-by-side. Certainly I haven't customized anything, and don't even know what unity-tweak or ccsm mean (yes, I'm thatmuch of an Ubuntu-virgin)

---

### Post by ghn2 on 2015-04-12
With your comment about workspaces, you gave me an idea that led me to where the problem was so I could fix it! It turned out that there was a problem with the displays setting on the computer, it had an "unknown display" setting on where Gimp was hiding (NOT something I had set) so I turned that off. 

Thank you! :D

---

### Post by deadflowr on 2015-04-12
Sounds like you figured something out.

For what it's worth:
Typically a hollow arrow on the left side means the app is working, but as mentioned in means it is working in another area than where you currently are.
If the app was running in the area you currently are working, then that arrow would be solid.
And the window that you would be currently working with; the one on top or in-focus, would have an arrow on the right side, which is always solid.
If no arrow ever showed, then the app would not be running.

If the app had a problem, then when you clicked on it the icon would blink the arrow would show, and then disappear.
When this happens, trying to open the app in the terminal is always a good idea, as the terminal should give a reason why it wasn't opening.
(A poor man's debugging, if you will)
Most apps use the name you would think, so for gimp, simply typing gimp would work.
Others might be more oddball, but you can always ask in a thread if you do not know.
Hope this helps
[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]
If you feel you have solved you problem, please feel free to mark this thread as such.[/URL]

---

