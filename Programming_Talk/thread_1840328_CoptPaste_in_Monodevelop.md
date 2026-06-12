---
title: "Copt/Paste in Monodevelop?"
date: 2011-09-07
forum: Programming Talk
---

### Post by iptrix@gmail.com on 2011-09-07
I just can't get it to work in the GUI designer (GTK+ widgets). Paste is never available either as ctrl-v, or from the context menu (it's greyed out).

I have tried checking for glipper/klipper, stopped klipper and tried again as per some google results, but no luck. I can't copy/paste stuff, a button in this case. What with the application I had in mind, not being able to copy would be a huge pita :/

Anyone know why? This is, of course, something of a beta system .. kubuntu 11.10 and Monodevelop 2.6 beta 3.

/Micke, sweden.

---

### Post by WitchCraft on 2011-09-07
Just to be clear: By GUI designer you mean the GTK designer inside MonoDevelop, and not the MonoDevelop IDE ?

If you want to develop GTK# applications, don't design the graphical part inside MonoDevelop. 
MonoDevelop's GTK designer never did quite work well. 
Design the graphical part of the GUI with Glade. 

Then you can use the XML file in your application, and switch to MonoDevelop to write the C#/GTK# code.

---

### Post by iptrix@gmail.com on 2011-09-07
Sorry. I had a feeling I was unclear .. I did a "helloworld" application, selecting gtk#, and on the form (in design mode) placed a background panel thing (absolute positioning something), then a Button on that. This part works nicely, but I seem unable to copy the button to another one - meaning that if I need a lot of buttons with lot of customization, I have to put and fix them one by one, no copying?

So it was the monodevelop IDE, just klicked "design" on the .cs file.

---

### Post by WitchCraft on 2011-09-09
> **iptrix@gmail.com said:**
> Sorry. I had a feeling I was unclear .. I did a "helloworld" application, selecting gtk#, and on the form (in design mode) placed a background panel thing (absolute positioning something), then a Button on that. This part works nicely, but I seem unable to copy the button to another one - meaning that if I need a lot of buttons with lot of customization, I have to put and fix them one by one, no copying?

So it was the monodevelop IDE, just klicked "design" on the .cs file.

Oh well, in that case they improved the designer quite a lot in the meantime. But as you can see, some features are still missing.

But at least nuGet now runs on Ubuntu.
I'd stick with Glade, but you have to know yourselfs how you want to do your things.

---

