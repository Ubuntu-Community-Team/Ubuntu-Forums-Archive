---
title: "script to terminate a process"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by ub007 on 2008-09-15
Hi,

I ssh into my remote client machine to run test scripts...

> $ssh [email]david@ubuntu.surey.ac.uk[/email]
password:*****

david@ubuntu$python test.py //this is the test script 

Now could anyone plz help me out with a script that would cleanly terminate test.py //lets say its clean.py and resides on ubuntu.surey.ac.uk

so all i have to do is 
david@ubuntu$python clean.py //test.py is terminated....

---

### Post by roquefilipe on 2008-09-15
why not use the "kill" command. It sends any signal you want to the process given bu its PID

But why does your script needs that treatment?

---

### Post by bodhi.zazen on 2008-09-15
make a ssh key

then use ssh-agent to load the key

then use ssh

ssh user@server command

where command is to be run on the server.

so ...

ssh user@server kill -9 `pidof foo`

now alias that or put it into a script.

---

### Post by ub007 on 2008-09-16
Thank you so much ..

I have already enabled ssh using dsa keys and using them through a php web interface


> But why does your script needs that treatment?

i have created a testbed thats got a master node with a browser interface.i select the no of machines i need to run the test from and click START,thsi would ssh into those machines(using ssh keys & php code) and run the load testing scripts,which in turn are coded to stress a web server...Now i need a stop button that could terminate the running scripts as and when required.The test scripts are on a infinite loop and may crash the server if left running for a long time....i could manually ssh into the terminals,get the process id & use the kill command....but that would be tedious...hence looking for a script that could do the job and link it to a STOP button...

>  kill -9 `pidof foo`

thats fine,but i would need to automate that....how do i get the pid without manually looking for it?

---

### Post by roquefilipe on 2008-09-16
heave you script log its pid to a file. Many programs seem to use that simple approach. 

checkout os.getpid() - [http://docs.python.org/lib/os-procinfo.html](http://docs.python.org/lib/os-procinfo.html)

---

### Post by bodhi.zazen on 2008-09-16
> **ub007 said:**
> Thank you so much ..

I have already enabled ssh using dsa keys and using them through a php web interface




i have created a testbed thats got a master node with a browser interface.i select the no of machines i need to run the test from and click START,thsi would ssh into those machines(using ssh keys & php code) and run the load testing scripts,which in turn are coded to stress a web server...Now i need a stop button that could terminate the running scripts as and when required.The test scripts are on a infinite loop and may crash the server if left running for a long time....i could manually ssh into the terminals,get the process id & use the kill command....but that would be tedious...hence looking for a script that could do the job and link it to a STOP button...



thats fine,but i would need to automate that....how do i get the pid without manually looking for it?

those are bac tics ` , on the keyboard by the number 1, not single quotes ' 

`pidof foo` returns the pid of foo

kill -9 `pidof foo` kills foo

---

