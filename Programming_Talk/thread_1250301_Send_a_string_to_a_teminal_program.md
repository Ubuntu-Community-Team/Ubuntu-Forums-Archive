---
title: "Send a string to a teminal program?"
date: 2009-08-26
forum: Programming Talk
---

### Post by marius_vt on 2009-08-26
Hi Guys,

Need to know if one can send a string of commands to a program.

The program is called Dynamips, 

After I launch the program it comes up with "->"

The command I want to send to the terminal is "start R1" and "start R2" you get the picture. 

Also want to know if it can sleep for 5 sec and then send the second string.

I did try to echo it but the echo only comes trough when u exit the program.

Any ideas

Regards

---

### Post by NoaHall on 2009-08-26
start R1 && start R2

---

### Post by marius_vt on 2009-08-26
Sorry,I need to do this from a script,

Here is my script;

#!/bin/bash
echo c1sc0 | sudo -S tunctl
#sudo tunctl
sleep 1 
sudo ifconfig tap4 192.168.255.1 netmask 255.255.255.0 up
sudo /home/marius/./start.lab.sh
sleep 1
sudo /home/marius/Dynamips/IE/./start_lab.sh

Regards

---

### Post by apmcd47 on 2009-08-26
> **marius_vt said:**
> Hi Guys,

Need to know if one can send a string of commands to a program.

The program is called Dynamips, 

After I launch the program it comes up with "->"

The command I want to send to the terminal is "start R1" and "start R2" you get the picture. 

Also want to know if it can sleep for 5 sec and then send the second string.

I did try to echo it but the echo only comes trough when u exit the program.

Any ideas

Regards

Sounds like a job for *expect*, **if** you can work it out.

Andrew

---

### Post by marius_vt on 2009-08-26
Hi Guys,

Need to know if one can send a string of commands to a program.

The program is called Dynamips, 

After I launch the program it comes up with "=>"

The command I want to send to the terminal is "start R1" and "start R2" and so on.

Also want to know if it can sleep for 5 sec and then send the second string.

I did try to echo it but the echo only comes trough when u exit the program.

I want to do this via the script I have,

Here is my script.

#!/bin/bash
echo c1sc0 | sudo -S tunctl
#sudo tunctl
sleep 1 
sudo ifconfig tap4 192.168.255.1 netmask 255.255.255.0 up
sudo /home/marius/./start.lab.sh
sleep 1
sudo /home/marius/Dynamips/IE/./start_lab.sh

Any ideas, can this be done?

Regards

---

### Post by unutbu on 2009-08-26
I think the "expect" program may be what you are looking for. It allows you to write scripts that can interact with other programs (like telnet, or in your case, Dynamips.)

Here is an example of how it is used: [http://ubuntuforums.org/showthread.php?t=192929](http://ubuntuforums.org/showthread.php?t=192929)

The expect package is in the official repos, and its homepage is here:  [http://expect.nist.gov/](http://expect.nist.gov/)

---

### Post by soltanis on 2009-08-26
As unutbu said, you should use the expect program. Get it from the repositories.

---

### Post by Sporkman on 2009-08-26
Did you try doing this:

dynamips < commands

where "commands" is a file containing what you want typed..?

---

### Post by marius_vt on 2009-08-27
Hi Sorkman,

Nope I did not try that, this is my first script, don't know much :)

I'm not sure what u mean,

Do I add this to my startup script

 dynamips < "start dev"

start dev file contains the following,

start R1
start R2

Regards

---

### Post by Sporkman on 2009-08-27
> **marius_vt said:**
> Hi Sorkman,

Nope I did not try that, this is my first script, don't know much :)

I'm not sure what u mean,

Do I add this to my startup script

 dynamips < "start dev"

start dev file contains the following,

start R1
start R2

Regards

Yes, give that a try.

---

### Post by scragar on 2009-08-27
Write a function for it?

```

function startR1R2{
  echo "start R1";
  sleep 5s;
  echo "start R2";
}


startR1R2 | dynamips

```

---

