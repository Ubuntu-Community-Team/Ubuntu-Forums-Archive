---
title: "Starting Programs At Boot"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by stuart264 on 2008-07-06
Ok, I am reasonably new to Ubuntu but picking stuff up quickly, but I have 2 problems with starting programs at boot as I have installed Mediatomb which works fine but I have to open up a console and start the server manually after a reboot and the same with the fancontrol script I set up with pwmconfig.

Can anyone tell me how to start the fancontrol script and Mediatomb at boot?

Stuart

---

### Post by HalPomeranz on 2008-07-06
The easiest thing to do is to put the start-up commands for your programs in /etc/rc.local.

---

### Post by dominiquec on 2008-07-06
Normally, you would create a startup script in /etc/init.d.  You can use the scripts there as a model.

Then, you would create a link to the script you created in /etc/rc5.d and /etc/rc3.d directory using the format S99nameofscript.  /etc/rc5.d and /etc/rc3.d refer to the run levels (5 being GUI and 3 being console).  

Have a look at [http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html) for additional explanation.

---

### Post by dominiquec on 2008-07-06
Hmmm...mea culpa.  I'll have to defer to Hal's advice.  It's more sound.  My info is outdated.  Apologies.

---

### Post by stuart264 on 2008-07-06
Can I have that in the slightly simpler step by step version, I am picking this up quick but still learning

---

### Post by damis648 on 2008-07-06
> **stuart264 said:**
> Ok, I am reasonably new to Ubuntu but picking stuff up quickly, but I have 2 problems with starting programs at boot as I have installed Mediatomb which works fine but I have to open up a console and start the server manually after a reboot and the same with the fancontrol script I set up with pwmconfig.

Can anyone tell me how to start the fancontrol script and Mediatomb at boot?

Stuart

Here is what you would want to do the easiest way:
Open Text Editor and type
```
#!/bin/bash
```
at the top. Skip a line and start writing all the commands you type in terminal to get your stuff up and running. Save it somewhere and call it "boot" or something. Now find it and right-click it and go to the properties. Go to permissions and make it executable. Close that window.
Go to System>Preferences>Sessions and click "add". For the name, put whatever you want. I would put "fan_mediatomb". For the command, put the path to your "boot" file that we made earlier. Close that and there you go!

---

