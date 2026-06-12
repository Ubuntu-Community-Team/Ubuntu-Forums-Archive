---
title: "'Fn' key acting like its always held down"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by HDBeast on 2012-09-29
So, I put this computer away for a few months, and when I took it out today, the 'Fn' key acts like its always held down. I can hold down the Fn key to type, buts it's a real pain. With this keyboard problem, "Hello, how are you?" looks like: "He336, h6w are y64+"

Is this a well-known glitch, or is there an easy fix for it? I'm really a Windows person, this is just my work computer, and I haven't had to use it for a while. I need to get this fixed by Monday, so is there a solution to this?

Thanks,
-HD

More examples:
"The quick brown fox jumped over the lazy dog."
"The q45c2 br6wn f6x 140*ed 6ver the 3azy d6g."

"How do I fix this problem?"
"H6w d6 f5x th5s *r6b3e0+"

---

### Post by cbanakis on 2012-09-29
This may work.

If not it should be easy to undo.

Open terminal, and type
```
sudo gedit /etc/pbbuttonsd.conf
```

Type your password, then hit enter.  (A note pad will open)

Enter this into the document
```
KBDMode = fkeysfirst
```

Save / Exit / Reboot

If that does not work, repeat the above, except this time delete the line you added.

---

### Post by cbanakis on 2012-09-29
There also might be an option in your bios to change this, but I have never seen one before.
("They" say, there is usually an option in bios)

---

### Post by HDBeast on 2012-09-29
Okay, tried this, but it is telling me wrong password when i try to type it in terminal. i used it to log on, so I'm not understanding this. Something I'm doing wrong, or what?

EDIT:
It worked, I just give up too easily :P

---

### Post by HDBeast on 2012-09-29
Rebooting, be back in a minute, and I'll see what happens.

---

### Post by HDBeast on 2012-09-29
Back from reboot, and it doesn't seem to work. What is this 'bio' thing you're saying I can do something with?

---

### Post by cbanakis on 2012-09-30
When you first turn your computer on, it should say "Press (X) Key to enter setup"

X usually = F2, Del, Esc, F12...

Depends on your computer, but it will tell you which key to press.

You might have to turn it off and on a couple times, till your able to make out which key.
(Some computers don't give you a lot of time)

Once in BIOS, be very careful not to change any settings, unless you know exactly what your doing.

Cycle through all the categories, and look for any options related to the fn key.

Not even sure if there is one, but if its there, you should know it when you see it.

If there is no option there, then you got me.

I have found other people with the same problem, but they are using Apple keyboards.

I'm sure there is a solution either way, just not sure what else to try.

I am by no means an expert with Linux, or Ubuntu.

PS. 
If you did not already, make sure you undo the line you added in the file earlier.
(Dont want that causing additional problems)

---

