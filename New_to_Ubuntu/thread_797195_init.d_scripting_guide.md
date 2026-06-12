---
title: "init.d scripting guide"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by minuxx on 2008-05-17
Hi there!

I have just installed a BF2-Server with mono and 'bf2ccd.exe'.
Everything is just working as intended. Now the next step would be to write an init.d script for mono to trigger 'bf2ccd.exe' but unfortunately I couldn't find any proper newbie guide on init.d scripting.
I know at '/etc/init.d/' is a pattern file called 'skeleton' to make your own script.
Thing is most of the stuff is gibberish to me and I doubt there is anything included about triggering an executable in the way I need it.
So my question goes like this:
Is there any 'grounded' de-nerded easy-to-get-your-head-around guide on init.d script?

Thank you for your replies ! :)

---

### Post by Xiong Chiamiov on 2008-05-17
I'm not quite sure what you're doing with an .exe, but you can create a symlink to the app in your home folder.  For me, it's something along the lines of
```

ln -s [path to app] ~/.kde/Autostart/

```
It should be something similar in GNOME, but I'm not sure quite what it is.

---

### Post by minuxx on 2008-05-17
Well apparently the dedicated server configurator is only available in .exe format which again would need NetFrameWork which is provided by mono.
So to start the exe my syntax is like this:
```

/home/bf2pr/bf2server/mono bf2ccd.exe

```

And that code I have to somehow integrate into an init.d script.

So I am not quite sure at what you are getting there. How would a symlink help me? Man what is even a symlink ? :)

---

### Post by Xiong Chiamiov on 2008-05-17
A symlink is just a link from one place to another, making Ubuntu think that a file exists where it doesn't.  There is a folder in your home directory somewhere that will cause anything in it to be loaded when you log in.  If you don't need it until you login, then that would be a simpler solution, I think.

---

### Post by Xiong Chiamiov on 2008-05-17
From a brief look, the init.d scripts are just shell scripts, so you should be able to do something like:
```

#!/bin/bash
/home/bf2pr/bf2server/mono bf2ccd.exe
exit 0

```
You might have to give it executable permission (chmod +x [filename]).

---

