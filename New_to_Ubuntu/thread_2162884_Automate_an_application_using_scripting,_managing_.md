---
title: "Automate an application using scripting, managing multiple terminals"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by anzal on 2013-07-16
Hi

I am new to Ubuntu and Bash scripting. I am working on a project to give a demo on an SDN application to my class. I need some help in scripting to create the demo. Please help in case if you have any idea on what am asking.

The demo uses a tool called mininet. I need just one script so that I can automate the whole of my demo.

The commands I need to run are given in order below.

1. Run "sudo mn"  on the terminal. This changes the prompt from 

/mininet$ sudo mn

to

mininet>

2. Now on this terminal where the prompt is 'mininet>'  , I need to run "xterm h1" followed by "xterm h2" to create separate terminals for two hosts created by mininet.

3. I have to access the xterm terminal for h1 and run a command there . eg: ifconfig

4. I have to access the xterm terminal for h2 and run a command there . eg : set ip address

5. I have to run a ping in xterm terminal for h1 and while this is happening, i want to access terminals of h2 and start a ping in xterm terminals of h2.

6. I have to go back to the previous terminal from where the xterm terminals were spawned. 'mininet>' prompt one. and run "exit" and then when the promp goes back to normal '/mininet$' i have to "sudo mn -c" .


All of this should be done from one script. Please ignore the specific command mentioned and give a generic solution or clues.

---

