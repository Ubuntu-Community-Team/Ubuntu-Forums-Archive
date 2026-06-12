---
title: "Problem with Desktop"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by jnmyk on 2011-10-29
Hi

Sorry to trouble you all again.  

About a week ago I had a problem and it was solved by downloading Compiz and changing something.  All went well.  Foolishly I thought I would investigate Compiz, my problem is that I have changed something that has changed the desktop.  The desktop is now background with only a bar across the top, that will only allow me to look at the file system, ie home folder, downloads, documents etc.  Nowhere can I open programs.  

I  am sending this from another computer.  Any suggestions as to how to get back to the standard layout.  Thanks  -  John

---

### Post by roger_1960 on 2011-10-29
Hi

Try this:

You can reset unity or compiz or both by doing the following.

Open a terminal by hitting ctrl+alt+t or alt+f2, if one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity.
> Unity --reset

---

### Post by jnmyk on 2011-10-29
Hi Roger

Opened a terminal no probs, typed in unity --reset.  Got a screen with some 15 errors eg mouse select already defined.  Then 4 initializing lines eg Initializing session options...done.  But after that its gone into sulk mode, computer doesnt appear to be doing anything but the terminal is not showing the directory and symbol, just a square?

ATB  -  John

---

### Post by Frogs Hair on 2011-10-29
Close the terminal and if all goes well the screen may flash a little and unity will restart , I don't know of anything else to  try because you cannot run another command at that point .

---

### Post by roger_1960 on 2011-10-29
Hi

Often changes to compiz need a logout/in.  In your case I think I would reboot.  If you can type into the terminal you try 

> startx

but otherwise I would do a hard reboot.

---

### Post by jnmyk on 2011-10-29
Hi  again

When I tried to close terminal got a message saying Process running in Terminal, it gave me option to close so I did.  Started another terminal and typed  startx,  got messge User not authorized to start X server.  Shut down machine and restarted, seems to have made no difference  -  just the bar across the top, as before.

ATB  -  John

---

### Post by Mark Phelps on 2011-10-31
It's not your problem alone.  Unity in 11.10 is clearly something pushed out too soon.  I've had my desktop crash several times now in only three days.

Look through the link below -- you'll have to remove and reinstall compiz and unity:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

