---
title: "How to activate numlockx in Mate 18.10"
date: 2018-11-01
forum: New to Ubuntu
---

### Post by ray76 on 2018-11-01
Need url on how to avtivate numlockx at login in Mate 18.10

---

### Post by Dennis N on 2018-11-02
All you have to do is add **numlockx** to your startup applications.

---

### Post by ray76 on 2018-11-02
Gave this a try but evidentally have not added proper script in startup application
Thanks for the reply

---

### Post by Dennis N on 2018-11-03
> **ray76 said:**
> Gave this a try but evidentally have not added proper script in startup application
Thanks for the reply
You shouldn't need any script to do this. Just type in the command which would start the program:

Control Center > Startup Applications > Click 'Add' button > In 'command' box, you put **numlockx**

---

### Post by ray76 on 2018-11-03
Dennis 
I put numlockx in startup application It does not turn on numlockx also tried numlockx on it does not turn it on
I can put numlockx on and or numlockx off in  a terminal and it will toggle on and off
What am I  doing wrong that it does not work from startup

---

### Post by Dennis N on 2018-11-03
Well, I thought that suggestion would work but maybe not. 

So, I did a brief experiment:

I have Ubuntu MATE 18.04 installed, not 18.10, and I see numlockx isn't installed in 18.04, and the numlock isn't coming on there either, so I installed numlockx, did not add to startup applications (after reading the description quoted below), manually turned numlock OFF, rebooted, and the numlock came on for a few seconds after I logged in, then went off. Then I manually turned numlock ON, rebooted again, and the numlock came on when I logged in and stayed on.

From apt show numlockx:
> "The package automatically installs session script to enable numlock
 on session start."


So there should be no need to add to startup applications. From my experiment, the inference is if you have numlockx installed and the numlock key ON when you restart, it will stay on after next login. If you don't install numlockx, it will be be OFF after next login regardless of whether you had the key on or off before last log out. Repeated, with same result. Limited evidence, so this observation is not conclusive. 

Do you get similar result?

---

### Post by ray76 on 2018-11-04
Dennis
The numlockx program is installed with the latest program
Tried the experiment you suggested nothing happened still have to turn on manually to login in
As mentioned before I am able to turn on and off from terminal simply typing numlockx on or numlockx off
Are you familiar with this command and can it be used else wheres in combination with some other program
Thanks again for the help

---

### Post by Dennis N on 2018-11-04
I think with MATE 18.04, the way it works is to save the numlock state (on or off) and restore it to the same state when you boot the OS next time.

I then looked at recently installed Lubuntu 18.10, and it too had no numlock on when started. So I installed numlockx on it, and it works differently, in that it is turning on the numlock at login regardless of the way I had it in last session. Strange.

I think most people don't notice numlock not being on because they don't use the numeric keypad much, or don't even have a numeric keypad. If you do a lot of number crunching, you would notice.

To answer your question, you could try a little script to run the command 'numlockx on'.   

```
#!/bin/bash
#turn on numlock key
numlockx on

``` 
Create in text editor. Save it with some name like 'numlockon' in ~/bin (a standard location for personal bash script). Create this folder if necessary. Make the file executable. Then add the script name with full path **/home/user-name/bin/numlockon** (use your actual user-name) in the command box of a new startup application entry, and remove or uncheck any other entry you had made there previously for numlockx.

Reboot, and it should run on login and maybe turn on the numlock for you since you say that command works.

---

