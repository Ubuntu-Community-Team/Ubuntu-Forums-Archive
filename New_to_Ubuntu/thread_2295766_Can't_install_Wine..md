---
title: "Can't install Wine."
date: 2015-09-21
forum: New to Ubuntu
---

### Post by Nurunnabi on 2015-09-21
Hello Ubuntu expert, 
I'm Nurunnabi, Live in Bangladesh. I'm Ubuntu new user. I can't install any software terminal panel says.....  

[COLOR=#006400]nurunnabi@nurunnabi-DREAMSYS:~$ sudo apt-get install wine
[sudo] password for nurunnabi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
[/COLOR][COLOR=#ff0000]E: Unable to correct problems, you have held broken packages.[/COLOR][COLOR=#006400]
nurunnabi@nurunnabi-DREAMSYS:~$[/COLOR]


I don't understand it. please help me. 

Thanks, 
Nurunnabi

---

### Post by Sweet_Baby_Jamie on 2015-09-21
Which version of Ubuntu do you have?  On what kind of computer?  This is information we need in order to help you.

---

### Post by Bucky Ball on 2015-09-21
Welcome. You can't install any software, or just Wine? Run these commands pressing enter after each and waiting for the process to complete:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install wine
```	

Post back any and all errors messages, thanks. 

PS: Please use code tags for terminal output. See the last link in my signature for how. I have also changed the thread title to give you more chances of support. 'Please help' is generic as 99% of users here want help and it tells us nothing about your problem so won't attract the people who can help most. :)

---

