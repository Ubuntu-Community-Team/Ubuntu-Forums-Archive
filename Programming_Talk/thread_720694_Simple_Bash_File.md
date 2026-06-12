---
title: "Simple Bash File"
date: 2008-03-10
forum: Programming Talk
---

### Post by perito on 2008-03-10
First of all, this is my FIRST Bash file, I program in different languages but Ive never done anything related to Linux... and Im just starting to learn.
I want to make a .sh file so that each time I double click on it, it changes my IP to a static IP address having 192.168.0.3 as IP
so is this correct?
```
#!/bin/bash
sudo nano /etc/network/interfaces

auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
sudo /etc/init.d/networking restart
```

Ive never done this, so I have no idea if this is right or extremely wrong
so after I write this in a text editor, i save it as .sh and click on it and it would work?

thx

---

### Post by Siph0n on 2008-03-10
One easy way to test it, is to run it :) See if it changes your ip?

---

### Post by lapubell on 2008-03-10
do you need to change your IP on demand or do you want to keep that ip on every boot?  you can set it up so that you don't get your ip via DHCP but request that ip at boot.  is that what you want to do or do you need to change it on will?

---

### Post by perito on 2008-03-10
i want to change the IP at will
basically, I want to create 2 .sh files, want to change my IP to a static IP address 192.168.0.3 and the other to return it to normal, not static IP

I'm just wondering if the code above does the first job...
thanks

---

### Post by lapubell on 2008-03-10
I can't run the code to check, but the only thing I might change is the sudo in the command.

First, I don't think you are supposed to put sudo in your script, but to run the script as root.
so I would remove the sudo from the files and then run the script with something like gksu.  this lets you run things as root with a gui popup for the root password.

if you plan on double clicking the file, your sudo will sit there asking you for a password that you will never see because that is the command line fakeroot command.

---

### Post by Siph0n on 2008-03-10
Wouldn't just:

```

#!/bin/bash
ifconfig eth1 192.168.0.3
/etc/init.d/networking restart

```

work? Because you don't have to edit the file, just run the command? Though I don't know bash :)

---

### Post by mssever on 2008-03-10
I'm guessing that Siph0n's code will work.

I do want to point out a few things, though. First, nano is an interactive program. If you try running your script (you should; the best way to learn programming is by trying things and discovering what works and what doesn't), you'll discover that nano will sit there waiting for you to manually type your data. Once you save and exit, bash will start to throw errors at you because it doesn't know the commands auto, iface, address, etc.

A bash script is simply a list of things you can type at a command prompt. If it doesn't work when you type it on the command line, it won't work in a bash script. To be more specific, it needs to work when typed at an actual bash prompt. If another program is issuing a prompt (such as a password prompt) or if you've got an editor up (such as nano), then that doesn't count. Such a situation will require manual intervention.

Read up on the cat and echo commands, file descriptors, redirection, and stdin, stdout, and stderr to see how this all goes together.

---

### Post by perito on 2008-03-11
> **Siph0n said:**
> Wouldn't just:

```

#!/bin/bash
ifconfig eth1 192.168.0.3
/etc/init.d/networking restart

```

work? Because you don't have to edit the file, just run the command? Though I don't know bash :)

Im getting permission denied...
can I enter my password somewhere to be able to make the change?

---

### Post by Siph0n on 2008-03-11
Did u run the bash script as root? If so, maybe you need sudo in the bash script? I never wrote a bash script before tho, so sorry :(

---

### Post by perito on 2008-03-11
> **Siph0n said:**
> Did u run the bash script as root? If so, maybe you need sudo in the bash script? I never wrote a bash script before tho, so sorry :(

how to run the script as root? :S

---

### Post by Siph0n on 2008-03-11
from the directory u are in, 
```
sudo ./nameofscript.sh
```
Does that work? :) This is of course from the terminal.... I am not sure how to do it gui wise....

---

### Post by DenKain on 2008-06-17
I know that this is an older post but would it not be more simple just to add sudo in the bashfile instead of running it as sudo?

```

#!/bin/bash
sudo ifconfig eth1 192.168.0.3
sudo /etc/init.d/networking restart

```

This way you just type ./bashfilename.sh and then it just asks you for your sudo password. I like to cut out steps if I can....just my two cents.

---

