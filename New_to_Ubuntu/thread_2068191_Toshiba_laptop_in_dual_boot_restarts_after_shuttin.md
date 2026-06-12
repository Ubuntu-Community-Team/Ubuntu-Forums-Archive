---
title: "Toshiba laptop in dual boot restarts after shutting down Xubuntu"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Yannanael on 2012-10-08
Hello,
I bought a new Toshiba Satellite C870-15J with Windows 7 installed.
Made a dual boot with Xubuntu 12.04.
When I shut down Xubuntu, the system seems to turn itself completely off, but after some seconds I hear a click, and the system reboots itself.
The same when I shut down via the terminal with "sudo shutdown -h now".
In the power manager I changed the value for the onn-off button to shut off, but still the same problem.
I also entered the bios and made sure every Wake-on-LAN-like-function is disabled.
In grub I changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="acpi=force quiet splash" as suggested in another thread.  To no avail...
When I use the "Windows-side" and shut off, it stays off, which is why I think it can't be a hardware problem.
Can anybody help me? It is a new laptop and it's rather annoying it won't work as it should...
Thanks,
Yann

---

### Post by will1982 on 2012-10-08
Did you use Wubi?

---

### Post by daslinkard on 2012-10-08
> **Yannanael said:**
> Hello,
I bought a new Toshiba Satellite C870-15J with Windows 7 installed.
Made a dual boot with Xubuntu 12.04.
When I shut down Xubuntu, the system seems to turn itself completely off, but after some seconds I hear a click, and the system reboots itself.
The same when I shut down via the terminal with "sudo shutdown -h now".
In the power manager I changed the value for the onn-off button to shut off, but still the same problem.
I also entered the bios and made sure every Wake-on-LAN-like-function is disabled.
In grub I changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="acpi=force quiet splash" as suggested in another thread.  To no avail...
When I use the "Windows-side" and shut off, it stays off, which is why I think it can't be a hardware problem.
Can anybody help me? It is a new laptop and it's rather annoying it won't work as it should...
Thanks,
Yann
Does the PC shutdown correctly when you run the following sudo command:
```

sudo shutdown -h now
```

---

### Post by audiomick on 2012-10-08
try

```
sudo shutdown -P now
```

I think that should shut it down properly. I doesn't answer the question as to why it is re-starting, but it might help you out until you find a proper solution.

---

### Post by sneaky1 on 2012-10-08
Hi. I bought a Toshiba Satellite Pro C850 a week ago and have had the same issues & symptoms, also with a Win7 dual boot setup. I use regular Ubuntu 12.04 though, installed from a cd.

None of the commands mentioned above worked for me, and I also tried "sudo poweroff" with the same results. I also tried rebooting, then shutting down from the login screen, but nope. I also tried a few shutdown-timer applications, with the same result - a reboot, not a shutdown.

I'm a newb & don't want to muscle in on someone else's thread, but if there's any way I can help to find a solution, please let me know. Thanks!

---

### Post by daslinkard on 2012-10-08
What happens when you run the following commands:

```
sudo vi /etc/default/grub
```   set
  ```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"
```   then 
  ```
sudo update-grub
```

---

### Post by sneaky1 on 2012-10-08
> **daslinkard said:**
> What happens when you run the following commands:

The problem persists for me. Cheers.

---

### Post by Yannanael on 2012-10-09
Thanks for the tips, but they don't resolve the problem... Neither the "shutdown -P now" nor the 
GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"The only way to shut down completely is waiting till the restart and then hitting the on-off button again... A way I don't really like.

---

### Post by Orphyrion on 2012-10-11
Same problem here. 

Bought and Acer Aspire v5-531g. Installed ubuntu 12.04 LTS next to windows 7. When I shut down ubuntu, my laptop shuts down, and a few seconds later boots up again. I can only properly shut down the laptop when i shut down through windows.

Reading that the above option hasnt worked for anyone, I havent tried it yet.

---

### Post by daslinkard on 2012-10-11
Let's go a different route as my wife's PC was having a similar issue in which it would not reboot nor shutdown.  How I fixed it was as follows:

Type in terminal:
 ```
1. sudo gedit /etc/default/grub
 
``````
2. Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
```
  3. Change this to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
 
``````
4. Save the file and close the file.  5. Finally, in terminal: sudo update-grub
```

Let me know if this works for you.

---

### Post by Yannanael on 2012-10-11
Doesn't work... and it gets stranger: I discovered the laptop does not show this behaviour when working on accu only: when I pull out the power cable before shutting off, it stays down, like it should.
I don't know if this could be a "solution" too for Sneaky1 and Orphyrion?

---

### Post by Orphyrion on 2012-10-13
Didnt work for me either Daslinkard.

Not sure what Yannanael means, I tried a few things with my power cable but it keeps rebooting. If it works it sounds more like a workaround than a fix :(

---

### Post by sneaky1 on 2012-10-14
Wow! Yes that works for me, Yannanael. Thanks for that! I also tried Das' suggestion but no difference. Thanks too!

Orphyrion, what they meant was when you want to shut down, simply disconnect the power lead, then shutdown, and for us at least, it works as it's supposed to then. Definitely a workaround, but good enough for me. Best of luck.

---

### Post by Orphyrion on 2012-10-14
Mine restarts regardless I have the power cord plugged in.

---

### Post by craigparker on 2012-10-25
No fix for this yet, eh?  I've got an Acer Aspire V5-571-6605 that's doing this too with Xubuntu 12.04.  Getting the laptop was such a ruckus to begin with, I think my customer is going to kill me when I say "Oops -- too bad"
I installed laptop-mode-tools and found that a sudo shutdown -h now shut it down consistently with the power cord plugged in.  On battery, no love.  With the grub entry mentioned earlier, I had to hit the power button after the system halted.  This may have to be the answer for now; I don't want them to have to type in their password to shut down (if I make a launcher for the shutdown -h command)  But if anyone conjures up a fix for this, I'd be in love.  Pepe Le Pew and a Cat kind of love.  I might even send flowers!

---

### Post by bonzodog on 2012-12-05
Hey guys, i was googling around for a solution to this, and someone using Fedora is suffering the same thing, but found out the cause; its connected to the USB Bus not powering down correcty.

He made a shutdown script adaption, however, its for Systemd based systems, not ubuntu.

If anyone can figure out how to implement this into Ubuntu, let me know.

[http://www.pbehnke.com/main/node/11](http://www.pbehnke.com/main/node/11)

---

### Post by kiro1000 on 2013-02-08
I had the same problem on my Toshiba Satellite C670D-10L and after days of search this works for me: 

Open a terminal: Accessories/Terminal or Ctrl+alt+t 

1. In the terminal type:

```


sudo gedit /etc/rc.local


``` 


2. In the rc.local file add, after comments:

```


echo " LID" > /proc/acpi/wakeup


```


like this:
.
.
# By default this script does nothing.
echo " LID" > /proc/acpi/wakeup
exit 0

3. Save and Restart

---

