---
title: "Indenting in python? Quick Question..."
date: 2008-11-02
forum: Programming Talk
---

### Post by elbarto_87 on 2008-11-02
Just a quik question about code indenting in python.
lets say I have a code such as:
[PHP]
for i in range(0,10):
    #Do this[/PHP]

How do I add another statement above this? Is the only way to do this is indent everything?
ie

[PHP]if j==1:
    for i in range(0,10):
    #Do this[/PHP]

The problem I am having is that when I write a few lines of code and realise that I need to put them inside another statement, I have to go back through my script and indent everything manually (like above) which takes quite a bit of time. I was just wondering if there was an easier way to do this?

Regards Elbarto

---

### Post by Greyed on 2008-11-02
> **elbarto_87 said:**
> How do I add another statement above this? Is the only way to do this is indent everything?

Yes.

> I have to go back through my script and indent everything manually (like above) which takes quite a bit of time. I was just wondering if there was an easier way to do this?

Yes, get a programmer's editor which has functions to indent blocks.  Personally I use vim so to indent a block is a simple matter of marking it with **V**isual highlight line and **>>** intent.

---

### Post by Metaleks on 2008-11-02
> **elbarto_87 said:**
> The problem I am having is that when I write a few lines of code and realise that I need to put them inside another statement, I have to go back through my script and indent everything manually (like above) which takes quite a bit of time. I was just wondering if there was an easier way to do this?
Most editors will allow you to select a block of code, and then just hit tab to move everything over.

---

### Post by elbarto_87 on 2008-11-02
Thanks Greyed,
I am useing IDLE at the moment so I will see if I can do a similar thing in that editor. I do not mind IDLE so hopefully there is some support available. I find that indenting the code makes it nice and clean to read but since the script requires both correct formatting and syntax to run then adding bits and pieces can be a pain. 

Elbarto

---

### Post by elbarto_87 on 2008-11-02
> **Metaleks said:**
> Most editors will allow you to select a block of code, and then just hit tab to move everything over.

:) Exelent!!!! That works in IDLE. Is there away I can reverse an indent using a similar command (just out of curiosity)? 

Thanks for the help.

---

### Post by nvteighen on 2008-11-02
Just for curiosity... what editor were you using that didn't have automatic indentations? I'm pretty sure Gedit does it (I guess through a plugin...).

---

### Post by elbarto_87 on 2008-11-02
My editor (IDLE) does automatically indent if I type a statement, but if I put the previous typed statement inside another statement I have to indent everything in the body manually. I hope that makes sense?

---

### Post by LaRoza on 2008-11-02
> **elbarto_87 said:**
> :) Exelent!!!! That works in IDLE. Is there away I can reverse an indent using a similar command (just out of curiosity)? 

Thanks for the help.

Shift + Tab

I actually don't like auto-indents so I never have that enabled.

---

### Post by sheto on 2008-11-02
Elbarto, as I have told you before you may want to shift to Stani's Python Editor. You just have to highlight the code to indent and press Shift-Tab.

---

