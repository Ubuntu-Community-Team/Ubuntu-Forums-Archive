---
title: "[bashscript] input doesn't work?"
date: 2007-11-13
forum: Programming Talk
---

### Post by Digitz on 2007-11-13
Hi y'all,

i'm pretty new to the whole bashscript thing, so my following question probably is stupid. Sorry for this. 

I have this test code:

```

#!/bin/bash

echo -n "enter your name: "
read name
echo "Your name is $name"

```

I made this little script executable and when it opens up in the terminal I can see the 'enter your name: ' phrase. Now when I enter something and press enter, my terminal just closes itself...

What is it that I'm doing wrong?

---

### Post by meatpan on 2007-11-13
I ran your script and did not have any problems.  After re-reading your post, it sounds like you are executing this script from outside a terminal.  Is this correct?

If so, consider opening up a terminal and manually running the command.   

Another experiment is to add 'sleep 10' as the last line in your script.  Run the program as you originally did. I think this will cause the script output to remain displayed for 10 seconds after the name is echo'd.

---

### Post by Digitz on 2007-11-13
> **meatpan said:**
> I ran your script and did not have any problems.  After re-reading your post, it sounds like you are executing this script from outside a terminal.  Is this correct?

If so, consider opening up a terminal and manually running the command.   

Another experiment is to add 'sleep 10' as the last line in your script.  Run the program as you originally did. I think this will cause the script output to remain displayed for 10 seconds after the name is echo'd.

Yes you're correct, i'm executing my script by double clicking on it. But the sleep 10 made it stay open for 10 secs indeed! Now if i just add another 'read var_name' as last line, it wil just stay open if that's what I want. 

Thnx for your help!!!

---

### Post by bigboy_pdb on 2007-11-13
I was going to suggest doing what you stated Digitz (about using read at the end of the script to keep it open). You might also want to "echo" a statement about pressing the enter key to close the program.

If you were to become accustomed to using the terminal, you might find those kinds of messages irritating. It might be a good idea to allow the user to input an option (such as "-p") which invokes a "press enter to continue" message. It would also be a good exercise if you're new to scripting.

---

