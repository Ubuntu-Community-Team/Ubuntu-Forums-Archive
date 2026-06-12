---
title: "Run a script on startup!"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by Vagelism_Meintasis on 2013-08-04
Hello all!
I made a script that takes with snmp the temperature from a ethernet sensor, store it on a file send the data to a server and also print that to the console as it runs.
This happen periodically every 1 min with a while loop on the script. 
I followed the instructions below to make this script run with the systems start up.
> 
1) first, create a script, and edit it to your needs. Lets say, you call it, autorun.sh
2) copy that script into /etc/init.d
3) run the following commands:
     Code:
     sudo update-rc.d autorun.sh defaults
sudo chmod +x /etc/init.d/autorun.sh 


Works fine but I don't get the screen output that I take when I double click and select "run on terminal".

Any way to fix this?
Thank you!

---

### Post by fffree on 2013-08-04
So you want your script to open a graphical terminal, like xterm, and run inside that?

In this case, you'd want to have your real script somewhere else, e.g. in [FONT=fixedsys]/home/vagelism_meintasis/.scripts/ethernet.sh. [/FONT]Again set mode +x for [FONT=fixedsys]ethernet.sh[/FONT].
The [FONT=fixedsys]autorun.sh[/FONT] script in [FONT=fixedsys]/etc/init.d[/FONT] should then simply be as follows:
```
#!/bin/bash
xterm -e /home/vagelism_meintasis/.scripts/ethernet.sh
exit 0
```
This will open a new xterm and run the [FONT=fixedsys]ethernet.sh[/FONT] script inside it.

I hope this is what you meant :)

P.S.: It just comes to me, that, since this will quite possibly run before you're inside Unity or Gnome or whatever shell you use, it may be better to not have autorun.sh in /etc/init.d but use the shell to run it. Otherwise I have no idea what will happen to xterm (it will probably fail to run, since there's no xserver yet). To do this simply type "Startup Applications" in the search bar in the HUD/GNOME Shell, and add your script to the list there. See also [here]("http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login").

---

### Post by Vagelism_Meintasis on 2013-08-04
Thank you!
This is what I need!

---

