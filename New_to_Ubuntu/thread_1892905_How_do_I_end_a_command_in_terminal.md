---
title: "How do I end a command in terminal"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by 450rOOST on 2011-12-09
for instance,

I run conky, my conky shows up, then how do I close the terminal.  If I just click on the 'X' to close the terminal, it will say 'command still running, are you sure you want to close terminal' or something close to that?

Thanks.

---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> for instance,

I run conky, my conky shows up, then how do I close the terminal.  If I just click on the 'X' to close the terminal, it will say 'command still running, are you sure you want to close terminal' or something close to that?

Thanks.

```
exit
```
sldo try to run conky ```
conky & 
```
the & means run program in background but still let me use terminal

---

### Post by 450rOOST on 2011-12-09
> **josephmills said:**
> ```
exit
```
sldo try to run conky ```
conky & 
```
the & means run program in background but still let me use terminal

sweet, your helping me all over the place.

---

### Post by pakopako on 2011-12-09
Conky, that's a monitor isn't it? When you close the window, the service ends. That's what you want, right?

So if you don't get the chance to type EXIT, clicking 'X' to end the program is fine.

You can terminate the program other ways, like CTRL-C if you want to regain use of the terminal window.

---

### Post by 450rOOST on 2011-12-09
I dont want the service to end, after I run conky, I want to get to a fresh 'command line' if you will.

I just get a flashing cursor.  
exit appears to do the same thing and clicking the 'X'.

---

### Post by 450rOOST on 2011-12-09
> **josephmills said:**
> ```
exit
```
sldo try to run conky ```
conky & 
```
the & means run program in background but still let me use terminal

it doesn't let me still use the terminal when I run > conky & 


this is what I get:

> smoker@smoker:~$ conky
Conky: desktop window (2400095) is subwindow of root window (61)
Conky: window type - desktop
Conky: drawing to created window (0x5c00001)
Conky: drawing to single buffer
**flashing cursor here**


---

### Post by josephmills on 2011-12-09
> **450rOOST said:**
> it doesn't let me still use the terminal when I run  


this is what I get:
type "ls" or any other command

---

### Post by stinkeye on 2011-12-09
With conky you can change this setting in your conky config above "TEXT".
```
background no
```
to
```
background yes
```
Add it if there isn't a *background* setting. (Defaults to "no").

This will Daemonize Conky, ie fork to background.

Then you can just close the terminal or if you want to 
keep using hit ctrl+c.(Conky will continue to run in both cases).

---

