---
title: "bash output to desktop ?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by tedw on 2008-07-11
OK, no secrets.  I'm new to the desk top. 
I have a bash script on the Desktop that works.  
Profound stuff !

Named: bashtst

Contains two lines...

#!/bin/bash
echo Hello Folks !

I give chmod +x bashtst to make it executable.

From a terminal window,  ~./Desktop/bashtst
says...
Hello Folks !

OK, that's very rewarding but not yet exactly what I want.  :>) 

Here is the question: 

How do I make the output of the bash script visible on the Desktop ? 

I double click on the file bashtst on the Desktop.
I choose either 'Run' or 'Run in Terminal' but in 
both cases nothing is seen in the desktop. 
I have proved (by including the line "ls > ~/Desktop/tstOP" ) 
that the script does in fact run. 
I just see nothing on the Desktop ! 

Any tips would be appreciated.  Thanks !

---

### Post by aktiwers on 2008-07-11
Do you want it in a Window?

Then you should look into Zenity

---

### Post by hyper_ch on 2008-07-11
edit: missunderstood the question ;)

---

### Post by fatality_uk on 2008-07-11
+1 for Zenity. If you want to do is "pop" up a window.
Were you looking for something more integrated, such as Conky that will *"sit"* on your desktop?

---

### Post by tedw on 2008-07-11
Thank you. 

Yes, this does create a file on the desktop but the file has first to be opened (perhaps not immediately obvious to an unskilled user?) before we see the message inside. 

I was hoping that perhaps by launching the gnome-terminal and the scriptname I could open the actual running script ? 

I have so far not had any luck getting the command gnome-terminal to accept an argument. 

Appreciate your reply.  cheers !

---

### Post by tedw on 2008-07-11
Many thanks to you all ! 

The problem (for me at least) is solved !!  Yipee !! 

The answer was  "gnome-terminal -x bashtst" 

That throws open a terminal which can display the 
bash output just as it always was. 

Quick and dirty, yes.  I need it quick and there we have it. 

Thanks again for all the suggestions. 

Have a great weekend.

---

### Post by The Cog on 2008-07-11
I thnk your program is finishing so the window closes again - fast.
You can have your script wait for a key like this:
[B]echo "Press Enter to continue..."
read[/B]

---

### Post by tedw on 2008-07-11
Interestingly enough, I tried that and was surprised to find that the 
script waited on the read statements in terminal mode but NOT when run 
from the Desktop.  That could be very useful because, if you do want to run a bash script blind, you certainly do not want it to hang waiting for input from a terminal which is not there.   :>)

---

