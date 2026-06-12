---
title: "Ubuntu Studio Installtion Problem"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Darkshrimp on 2008-07-01
I spent hours partitioning and installing Ubuntu studio. But after installation, it goes to the normal black screen loading... and then.. it shows

user:
password:

Or something along the lines of that, once I log in...

it goes

andu@andu-laptop: 

and then that's it, how do i actually get to the real OS? 

thanks for all the help

---

### Post by lenards on 2008-07-01
First off - that totally sucks, you must be frustrated.  

I don't have your answer - but a place to start would be some information on the hardware that you're install ubuntu studio.  Desktop? Laptop? CPU architecture/brand? Stuff like that.

---

### Post by Darkshrimp on 2008-07-01
well, it's a NEC laptop.

Motherboard Chipset	Intel Odem i855PM-333

hows that, haha, i dunno what else you would need

---

### Post by avtolle on 2008-07-01
> **Darkshrimp said:**
> I spent hours partitioning and installing Ubuntu studio. But after installation, it goes to the normal black screen loading... and then.. it shows

user:
password:

Or something along the lines of that, once I log in...

it goes

andu@andu-laptop: 

and then that's it, how do i actually get to the real OS? 

thanks for all the help

You are at the real OS, just at the CLI, not a GUI. First thought; after logging in, type startx at the prompt, and see what happens.

---

### Post by Inxsible on 2008-07-01
you probably installed the server version. The server version does not have a GUI.

But we can check that. Once you login issue this command to see if the GUI starts up```
startx
```


EDIT : Dammit..too late ;)

---

