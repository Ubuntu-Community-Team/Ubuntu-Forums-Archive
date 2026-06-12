---
title: "gtk toolbar question"
date: 2007-11-07
forum: Programming Talk
---

### Post by jondecker76 on 2007-11-07
I'm writing my first application to get familiar with development in Linux. I'm going to go with Python and Glade (both of which I'm just learning). I do have plenty of c/c++ experience along with a hand full of other scripting  languages.

I've seen applications in Gnome that have toolbars with buttons that act like radio buttons (only one of a grop can be selected and active at one time)
Can I set this up in glade, or do I need to code something in Python that gets a signal when one is clicked on, sets it as active and sets the rest as inactive?

thanks,

Jon

---

### Post by AlexThomson_NZ on 2007-11-07
In Glade, create a toolbar and right-click it, select "Edit" and it takes you to a screen where you can add buttons, dividers, etc.

Create some buttons, select them and change the type to "Radio".  I'm sure you can work it out from here.

HTH

---

### Post by jondecker76 on 2007-11-07
Thanks, got it now!

Now I just have to learn how to process signals in python and I'm set

---

### Post by jondecker76 on 2007-11-07
Another question...

I have a toolbar with 5 GtkRadioToolButtons grouped together. Now I am trying to process the signals in Python. 

I've tried the on_button1_toggled signal, and it works - just not how I want it to.. Right now, it fires any time that button changes (on or off).. I want to detect it only if it is changed to On only.

Any idea what I can use to detect that?

thanks

---

### Post by Quikee on 2007-11-08
> **jondecker76 said:**
> Another question...

I have a toolbar with 5 GtkRadioToolButtons grouped together. Now I am trying to process the signals in Python. 

I've tried the on_button1_toggled signal, and it works - just not how I want it to.. Right now, it fires any time that button changes (on or off).. I want to detect it only if it is changed to On only.

Any idea what I can use to detect that?

thanks

When the event is fired just filter with if statement. Something like this:

```
if button.get_active() == True:
  buttonHasChangedToOn();

```

---

### Post by jondecker76 on 2007-11-08
thanks, worked like a charm

---

