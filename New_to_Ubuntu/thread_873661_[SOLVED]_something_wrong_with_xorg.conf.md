---
title: "[SOLVED] something wrong with xorg.conf"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by im new here on 2008-07-29
every time i try to edit xorg.conf  when i try to save the changes it says Can't open file to write when using mousepad 
and Writing error when attempting to save /etc/X11/xorg.conf when using when using abiword 

so what is the solution ?  remember that im using xununtu with xfce desktop 

thanks

---

### Post by northern lights on 2008-07-29
You can't save it cause you don't have permission to.

Open it as root ```
gksu abiword /etx/X11/xorg.conf
```
and you'll be allowed to save it.

N.B. that protection isn't meant as a nuisance but rather because you can screw up rather quickly by editing that file. Make sure you know what you're doing.

I'd rather advise you not to.

---

### Post by im new here on 2008-07-29
well northern lights when i entered "gksu abiword /etx/X11/xorg.conf"

 it opened an untiled abiword file so .......... ?

---

### Post by coffeecat on 2008-07-29
> **northern lights said:**
> ```
gksu abiword /etx/X11/xorg.conf
```

Why advise him to use Abiword, when a simple text editor will do the job perfectly, and he may not have Abiword installed?

```
gksu mousepad /etc/X11/xorg.conf
```... should do.

Oh, and it's /etc, not /etx

---

### Post by northern lights on 2008-07-29
> **coffeecat said:**
> Why advise him to use Abiword, when a simple text editor will do the job perfectly, and he may not have Abiword installed

compare

> **im new here said:**
> every time i try to edit xorg.conf  when i try to save the changes it says Can't open file to write when using mousepad 
and Writing error when attempting to save /etc/X11/xorg.conf when using when using [COLOR="Red"]abiword[/COLOR]

etc/etx typo.

I'd use nano, for the sake of completion.

---

### Post by im new here on 2008-07-29
well coffecat gksu abiword /etx/X11/xorg.conf also opened a mousepad empty page ????


and i have abiword installed and i corrected the mistake in the line before typing it

---

### Post by im new here on 2008-07-29
any solutions ?  ?

---

### Post by eightmillion on 2008-07-29
How about,

> sudo nano /etc/X11/xorg.conf

Remember, this is case sensitive. Make sure that first X is capitalized.

---

### Post by stevoo on 2008-07-29
or ... try this

type 
sudo gedit /etc/X11/xo
and the press tab ....
it should fill it up and press enter.
If it doesnt, then try double tapping see if the the file is there

---

### Post by im new here on 2008-07-29
also blank in terminal

---

### Post by eightmillion on 2008-07-29
Can you post the output of this command?
> ls -l /etc/X11/

---

### Post by coffeecat on 2008-07-29
> **im new here said:**
> well coffecat gksu abiword /etx/X11/xorg.conf also opened a mousepad empty page ????


and i have abiword installed and i corrected the mistake in the line before typing it

Apologies for missing the Abiword bit, but your problem stems from:

> /et[COLOR=red]x[/COLOR]/X11/xorg.conf
It should be:

> /et[COLOR=red]c[/COLOR]/X11/xorg.conf

**Edit:** You got it right in your first post (except for the gksu bit) but a typo crept into the thread somewhere. Repeat, that's 'x', not 'c' in etc.

---

### Post by im new here on 2008-07-29
dosent any body have a solution here?  ?? ? ?

---

### Post by eightmillion on 2008-07-29
im new here, Can you please post the output of this command?
> ls -l /etc/X11/

---

### Post by im new here on 2008-07-29
ok 8000000 ill post it just a sec

---

### Post by im new here on 2008-07-29
how could i copy and paste the out put here ?

---

### Post by im new here on 2008-07-29
any sloutions here ?  
hello

---

### Post by phidia on 2008-07-29
Sometimes it easier to cd to the directory with the file you want to edit-well it's just a preference; cd stands for change directory so in a terminal window type:
> cd /etc/X11 and press enter. Note command line completion works so you only have to type the X and press tab and it should fill in the rest for you.
when you are in the /etc/X11 directory type "ls" that should show a bunch of files one of which will be xorg.conf
Type > sudo nano xo and press tab or use gksu abiword if you like that better. Just let the terminal complete the line for you because then you will know the file is there-if it doesn't auto fill when pressing the tab key the file isn't there/you are typing the wrong letters.

---

### Post by philinux on 2008-07-29
sudo gedit /etc/X11/xorg.conf


Dont type it but Copy and paste the command in a terminal.

---

### Post by im new here on 2008-07-29
i got this sudo : gedit : command not found

---

### Post by im new here on 2008-07-29
does every body here notice that im using xubuntu

---

### Post by northern lights on 2008-07-29
> **philinux said:**
> sudo gedit /etc/X11/xorg.conf
I hate to be persnickety, but please run graphical apps with 'gksu' if you must run them as root.

```
gksu gedit /etc/X11/xorg.conf
```

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

[EDIT]
@"i am new here":
instead of gedit, insert any text editor - evim, ed, emacs, your initial abiword, whatever you have installed...
[/EDIT]

---

### Post by philinux on 2008-07-29
You're right gksudo for gedit I need more coffee.

---

### Post by philinux on 2008-07-29
> **im new here said:**
> does every body here notice that im using xubuntu

Arrrggghh


gksudo mousepad /etc/X11/xorg.conf

---

### Post by northern lights on 2008-07-29
> **philinux said:**
> Arrrggghh
More coffee 2morrow...
;)

---

### Post by im new here on 2008-07-29
gksu gedit /etc/X11/xorg.conf

this one worked finally thanks alot

---

