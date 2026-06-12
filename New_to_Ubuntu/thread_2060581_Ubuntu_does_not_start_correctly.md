---
title: "Ubuntu does not start correctly"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by Sporttherm on 2012-09-20
Hello,

I am very happy with my the Ubuntu, but:
When starting, it goes to the desctop view (in german Arbeitsflaeche) and then it connects to internet and I can see one folder (which opens the file manager). But no other programs like terminal or software center visible. Neither the system info like Clock on top right is visible.

Starting by cd works, however I need my local emails.

What is to do ?

Timo

---

### Post by Bucky Ball on 2012-09-20
Welcome.

What version of Ubuntu are you using?

Boot to the second entry on the list at startup, the recovery kernel, and when you get to the options choose, 'Fix broken packages' (from memory) then 'Normal Boot' when it's finished. See if that makes a difference. If not, try again, drop to root shell and type:

```
startx
```... then hit return. What happens?

PS: If you are not getting a list of choices to boot at startup, hit the shift key after the BIOS screen at boot. That should give you the list.

---

### Post by jerrrys on 2012-09-20
Welcome to the forums :)

Really don't know whats going on, so lets go fishing.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

Get any errors?  If you do, please post them (german is fine I hope)

---

### Post by Bucky Ball on 2012-09-20
> **jerrrys said:**
> Welcome to the forums :)

Really don't know whats going on, so lets go fishing.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update



Don't think OP can open anything. Might need to be done from recovery kernel (see post #2). Also wondering if an update is what caused this in first place. ;)

---

### Post by philinux on 2012-09-20
> **Sporttherm said:**
> Hello,

I am very happy with my the Ubuntu, but:
When starting, it goes to the desctop view (in german Arbeitsflaeche) and then it connects to internet and I can see one folder (which opens the file manager). But no other programs like terminal or software center visible. Neither the system info like Clock on top right is visible.

Starting by cd works, however I need my local emails.

What is to do ?

Timo

Can you open a terminal with ctrl+alt+t ?

---

### Post by Sporttherm on 2012-09-21
Terminal works now, great.
I can start in recovery modus and then start normal, this is good. All data appears, however, the OS font looks like recovery which I know from windows (broader than in normal mode)

But when I again start the OS, it only shows desktop as before and no dash to select programmes. So I am forced to do shift to boot differently.

When I write startx in console (only having desktop), an error message occurs: Server already active for display 0..Fatal io errors, consult [www.wiki.x.org](www.wiki.x.org).
Do you need more info ?

Seems difficult.
Timo

*Don't think OP can open anything. Might need to be done from recovery kernel (see post #2). Also wondering if an update is what caused this in first place*

What is OP ? I suppose abbreviation for open in terminal. I think my mistake was that the battery had no power so I did not load the battery.
It seems to me that recovery kernel did not fix the problem.

My Ubuntu is 12.04, the actual version.
apt-get update installed the updates, but no change.
Maybe I should always start with recovery kernel because it works ?

PS My idea is that I can work only with terminal and start programs or do configurations. However, I do not have a switch board to change between programmes, as I do normally with alt plus tab. By using terminal, I learn quite rapidly ..

---

### Post by NikTh on 2012-09-21
> **Sporttherm said:**
> What is OP ? I suppose abbreviation for open in terminal.  Original Poster = You are  . :) 

> **Sporttherm said:**
> My Ubuntu is 12.04, the actual version.
apt-get update installed the updates, but no change.
Maybe I should always start with recovery kernel because it works ?

apt-get update not install anything. Just re-load and refresh the sources. Where Ubuntu sees what packages (versions ..etc) are available. 

Try to do this .. 

Boot from [Recovery Mode] and when the window with options opens , select "Dpkg - Repair broken packages" , then select Yes in the warning (Tab key and Enter) and leave it to do the job. 

When finish click on ROOT and then give these commands 

```
apt-get update 
apt-get dist-upgrade 
```leave it to finsish and then click "Resume boot" (Is the first choice I don't remember the title)

Thanks

---

