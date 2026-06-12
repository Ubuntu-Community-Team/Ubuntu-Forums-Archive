---
title: "One script to rule them all"
date: 2009-03-03
forum: Programming Talk
---

### Post by derelict888 on 2009-03-03
I'm a jr net admin for a small company, and I have written several scripts to check my work; one script gathers up all IPs and domains currently in use, then one pings IPs, one checks forward and reverse DNS (using dig), and another checks for websites we host (using wget and grep for specific keywords). I now want to tie these altogether with a script that calls them, and then runs them in separate instances of terminal. I need to do it this way cause we have a lot of domains and IPs, and any one of these scripts can take over an hour to complete - I'd rather run them side by side in parallel not in series. Any ideas how to do that? I have all these scripts in one folder so I guess I could do a for loop;
```
For script in " > /[location]/*.sh " do;
gnome-terminal $script

```
I know this code isn't exact, thats partly cause I'm lazy and partly cause I don't know what I need. I know how to code the for loop, but not the terminal code part (so I get multiple instances of terminal running these different scripts simultaneously). I do have VNC setup on the box these scripts will run from, and I do like to visually see the progress of my scripts.

Any ideas?

---

### Post by tad1073 on 2009-03-03
I know nothing about scripting, but if want those scripts to run at certain times couldn't you make crotabs or cronjobs (or what ever they're called) to run the scripts parallel.

---

### Post by digital_x on 2009-03-03
Just run them in the background

after gnome-terminal $script 

put an ampersand, so 
gnome-terminal $script &

EDIT:

you will also need the -e flag for gnome-terminal, hence

gnome-terminal -e $script &

---

### Post by derelict888 on 2009-03-03
I was hoping to be able to remote into this machine via VNC and see the scripts running. I guess I could do the same if I do a tail -f on a running script?

By "see" I mean I want to see what IP the script is currently pinging, I want to see what domain I'm currently checking, etc... my scripts echo out all info as they run through for loops

---

### Post by eightmillion on 2009-03-03
You should probably look into ssh and screen.

---

### Post by digital_x on 2009-03-03
Correct, so wrap what I gave above and it would open up a gnome-terminal for each new script, and you could monitor each as they ran.  Of course once they are finished, the gnome-terminal gui would close, so you might also want to use the tee command  to send the output to a file as well for later analysis.

EDIT:

By the way, in case it is not clear, by sending them to the background in the for loop, this will allow the script to open each one immediately, so you will have windows open concurrently executing each of your scripts.

For a quick demonstration try the following command

for i in 1 2 3; do gnome-terminal -e top; done

Also, it appears that gnome-terminal returns control to the terminal immediately so you would even need the ampersand to run the app in the background.

---

### Post by derelict888 on 2009-03-05
I'll have to try a few things out when I have time, for now I have fires to put out. Thanks guys.

---

