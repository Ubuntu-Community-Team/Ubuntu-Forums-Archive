---
title: "Script &quot;steals&quot; the terminal"
date: 2009-10-15
forum: Programming Talk
---

### Post by gbablon on 2009-10-15
Hey all,

I have a Python script that uses the SOAPpy library to create a SOAP server on an Ubuntu server. Problem is, the script is set to listen for incoming connections so it never terminates once it has started running.

When I was running the script in an Ubuntu with a GUI, the fact that my SOAP script effectively "stole" the terminal window I executed it in was not a problem - I could just open a new one.

However, now that I'm running it on a server where the terminal window that loads at boot-up is the only one I'll ever get, I can't afford to have it "stolen" by the script, or I'm reduced to not being able to do anything with that computer.

How could I make the script run in the background but without taking over? I figure this is possible - for instance, if you have Apache running, it's constantly running and listening for incoming connections, and yet it doesn't prohibit you from doing other things with your computer.

Thanks for any suggestions!

---

### Post by Dejai on 2009-10-15
Say your script is called myScript, I am guessing you run it with ./myScript or python myScript to get back your terminal just add an &. e.g python myScript & or ./myScript &

---

### Post by gbablon on 2009-10-15
Perfect. Thanks Dejai.

---

