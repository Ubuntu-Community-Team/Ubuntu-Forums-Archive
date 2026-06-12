---
title: "Executable text file: Run in Terminal by default. How?"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by yan4 on 2014-04-24
[COLOR=#333333][FONT=UbuntuRegular]I have a code that runs an app in terminal through an executable text file. When I click it, it asks me what I want to do with it: [Run In Terminal] [Display] [Cancel] [Run].

This is so annoying. [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I would like that it always [Run in Terminal]  without to ask me every time...

Thanks![/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-04-24
Which scripting language is it written in?  You could comment out the line(s) where the query is made and then add a line assigning the value used for [run in terminal] to the correct variable.

---

### Post by monkeybrain20122 on 2014-04-24
This is how it should be. You don't want to click a random file and it just executes without prompting you because you may run something malicious by accident. Also you may want to have an option of editing the script by simply opening it by clicking. However, this is not the default, the default is always display, which IS annoying, so you must have changed natutilus' setting already.

Anyway, you can change this (not recommended) by opening Naulilus, go to Files > Preferences and Behaviour.

---

### Post by yan4 on 2014-04-24
> **monkeybrain20122 said:**
> Anyway, you can change this (not recommended) by opening Naulilus, go to Files > Preferences and Behaviour.

Cool, thanks, it worked perfectly!

:guitar:

---

