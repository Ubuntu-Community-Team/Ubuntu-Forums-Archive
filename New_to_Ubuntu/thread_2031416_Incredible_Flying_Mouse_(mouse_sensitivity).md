---
title: "Incredible Flying Mouse (mouse sensitivity)"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by Draexo on 2012-07-21
I have a Logitech M205 mouse.  I have the sensitiviy set as low as it can go, but it is still flying all over the screen.  It is actually fairly difficult to control.  Are there adjustments besides mouse sensitivity somewhere else in the system?

---

### Post by NikTh on 2012-07-22
Hi  , 
please open a terminal (ctrl + alt +t ) and copy-paste this command 
```
 xset -q | grep accel 
``` 

give the results back here. 

Thanks

---

### Post by NikTh on 2012-07-22
[QUOTE=Draexo]Hello
I attempted to respond in the thread, but the forums keep timing out and  it seems to just be that thread of mine, not any others.

My results are 
```
drew@drew-System-Product-Name:~$  xset -q | grep accel
  acceleration:  2/1    threshold:  4
drew@drew-System-Product-Name:~$ 
```Sorry to bug you with a PM![/QUOTE]

Hi , 
i quoted your PM , so others can see the results of command . 

Ok, open a terminal and write this 
```
 xset m 2/4 
``` and if this value serve your needs , you need to create a simple script and add to startup applications. 

Like this .
```
gedit mousespeed.sh
```and you put this inside 
```
#! /bin/sh 
xset m 2/4
exit 0
```you save the script , and give execute permission like this 
```
chmod a+x mousespeed.sh
```then open statup application and add this to the command box 
```
/home/username/mousespeed.sh
```username= your user name 
Reboot for script to take place. 

Thanks

---

### Post by Draexo on 2012-07-22
Thanks!
My mouse is now manageable! I just need to set up the script!

---

### Post by Draexo on 2012-07-23
> **NikTh said:**
> Hi , 
i quoted your PM , so others can see the results of command . 

Ok, open a terminal and write this 
```
 xset m 2/4 
``` and if this value serve your needs , you need to create a simple script and add to startup applications. 

Like this .
```
gedit mousespeed.sh
```and you put this inside 
```
#! /bin/sh 
xset m 2/4
exit 0
```you save the script , and give execute permission like this 
```
chmod a+x mousespeed.sh
```then open statup application and add this to the command box 
```
/home/username/mousespeed.sh
```username= your user name 
Reboot for script to take place. 

Thanks
I could use some help in setting this up as an automatic entry in startup.  I believe I have done everything correctly, and the script works if I actually run it from terminal, but it does not seem to execute on startup.  I have the "/home/username/mousespeed.sh" where username is my name (drew).  oy!  I think I did not give it permission!

---

### Post by NikTh on 2012-07-24
Hi , 
i think its not necessary to reboot all the time , to see if script works. You can logout - login . 

If its not work , then at command box (on startup applications) try **./mousespeed.sh** as you see it. (with dot and slash) . 

Also you can add a delay to your script , maybe that helps.. 
open you mousespeed.sh again .. 
```
gedit mousepeed.sh
``` and make it like this.. 
```
#! /bin/sh 
**sleep 10 **
xset m 2/4
exit 0
``` 
we added sleep 10 for a 10 secs delay.. 

Thanks

---

### Post by Draexo on 2012-07-24
> **NikTh said:**
> Hi , 
i think its not necessary to reboot all the time , to see if script works. You can logout - login . 

If its not work , then at command box (on startup applications) try **./mousespeed.sh** as you see it. (with dot and slash) . 

Also you can add a delay to your script , maybe that helps.. 
open you mousespeed.sh again .. 
```
gedit mousepeed.sh
``` and make it like this.. 
```
#! /bin/sh 
**sleep 10 **
xset m 2/4
exit 0
```we added sleep 10 for a 10 secs delay.. 




Thanks
The script works, it just seems I had to run it from terminal each reboot.  I am trying to automate it at startup.  I am going to add the delay just to check.
Thanks

---

### Post by Draexo on 2012-08-01
> **Draexo said:**
> The script works, it just seems I had to run it from terminal each reboot.  I am trying to automate it at startup.  I am going to add the delay just to check.
Thanks
This delay seems to have done the trick.  I have no idea why!
Now my mouse is fine a boot up!

---

