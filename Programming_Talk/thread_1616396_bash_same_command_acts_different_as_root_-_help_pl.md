---
title: "bash same command acts different as root - help please"
date: 2010-11-08
forum: Programming Talk
---

### Post by jahst on 2010-11-08
Hello,

Trying to figure out why this same command behaves differently when run as a normal user than it does when run as root. 

Here is the code:


```
for i in 0{5..6}; do gnome-terminal -x sh -c "echo hello $i && sleep 10" ; done
```


When run as a normal user, it pops up 2 separate terminals at the same time, both echo the respective 5 and 6, and then both close after 10 seconds. Total time = 10 seconds for both terminals as they run simultaneously.

However, when I change to root... 

sudo su

then post the same command, it opens one terminal. runs the command for 5.. closes the terminal after 10 seconds... then opens another terminal and runs the command for 6.. and closes after 10 seconds. Total time = 20 seconds, as they run sequentially.


Why is this so? .. and how do I make it run simultaneously as root like it does for normal user?



Another thing...
my terminal as normal user looks like this

user@hostname:~$

and as root it looks like

root@hostname:/#

Granted.. I've never taken much time to look at the root terminal prompt.. but shouldn't it be more like:

root@hostname:~$    or
root@hostname:~#    


Thanks,

---

### Post by Arndt on 2010-11-08
> **jahst said:**
> Hello,

Trying to figure out why this same command behaves differently when run as a normal user than it does when run as root. 

Here is the code:


```
for i in 0{5..6}; do gnome-terminal -x sh -c "echo hello $i && sleep 10" ; done
```


When run as a normal user, it pops up 2 separate terminals at the same time, both echo the respective 5 and 6, and then both close after 10 seconds. Total time = 10 seconds for both terminals as they run simultaneously.

However, when I change to root... 

sudo su

then post the same command, it opens one terminal. runs the command for 5.. closes the terminal after 10 seconds... then opens another terminal and runs the command for 6.. and closes after 10 seconds. Total time = 20 seconds, as they run sequentially.


Why is this so? .. and how do I make it run simultaneously as root like it does for normal user?




To see the different behaviour, you only need to invoke the command "gnome-terminal".

If you provide the option --disable-factory, it will behave in the non-su case as it does for su. This doesn't help you, since you wanted it the other way around, but maybe it's a pointer to a solution. I don't know what the "activation nameserver" is, which the help text for this option mentions.

---

### Post by jahst on 2010-11-08
Simply invoking gnome-terminal doesn't show me the commands are getting passed to the new terminal.

hence my simple "echo" portion of script.

You are correct though, that just gnome-terminal, behaves the same.
Normal user opens 2 terminals simultaneously, while root opens one-at-a-time.


It should be able to run more than one instance because I can call and run individual scripts simultaneously using something like this.


```
sudo gnome-terminal --tab -e "sudo sh 05.sh" --tab -e "sudo sh 06.sh"
```


This works fine.. however, I am attempting to write a loop script that doesnt require individual script files. I just want to loop the command each script contains.

so for example... 05.sh contains code "echo this is 05" and 06.sh contains the code "echo this is 06".

I should just be able to loop that code right inside the terminal without having to read each .sh script file.

There are some --tab-with-profile=PROFILENAME and --window-with-profile=PROFILENAME

I'll start looking into these as well.

Any other ideas please.

---

