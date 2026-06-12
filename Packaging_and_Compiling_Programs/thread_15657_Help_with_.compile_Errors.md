---
title: "Help with ./compile Errors"
date: 2005-02-15
forum: Packaging and Compiling Programs
---

### Post by BarbiGirl8 on 2005-02-15
I am trying to compile my very first download of an application outside of Synaptic and I keep getting the following error.

checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.0... Package gtkmm-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtkmm-2.0.pc'
to the PKG_CONFIG_PATH environment variable

I have googled, and searched, but I cannot seem to find 
a) A basic explanation of what this error means and
b) A basic explanation of what to do with it once I know what it is.

This is starting to drive me bonkers. And I don't like bonkers, My sanity already has  one foot in a handbasket on my its way to somewhere very warm.

Thanks

---

### Post by Xian on 2005-02-15
[QUOTE=BarbiGirl8]checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.0... Package gtkmm-2.0 was not found in the pkg-config search path.[/QUOTE]
Do you have the libgtkmm2.0 and libgtkmm2.0-dev packages installed?

---

### Post by rufius on 2005-02-15
[QUOTE=BarbiGirl8]I am trying to compile my very first download of an application outside of Synaptic and I keep getting the following error.

checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.0... Package gtkmm-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtkmm-2.0.pc'
to the PKG_CONFIG_PATH environment variable

I have googled, and searched, but I cannot seem to find 
a) A basic explanation of what this error means and
b) A basic explanation of what to do with it once I know what it is.

This is starting to drive me bonkers. And I don't like bonkers, My sanity already has  one foot in a handbasket on my its way to somewhere very warm.

Thanks[/QUOTE]
 Try installing the dev package to whatever its searching for.

---

### Post by BarbiGirl8 on 2005-02-15
Ok, Now i'm starting to get the hang of this. Downloaded some lib's and restarted gnome. Now it finally compiled and it went through make just fine. Now if i can figure out how to use the install command i think I just might be good to go.

---

### Post by Xian on 2005-02-15
[QUOTE=BarbiGirl8]Now i'm starting to get the hang of this. Downloaded some lib's and restarted gnome. Now it finally compiled and it went through make just fine. Now if i can figure out how to use the install command i think I just might be good to go.[/QUOTE]
You shouldn't have to restart gnome after installing libs (thankfully this isn't like M$). Just go back and continue with your compiling. It should immediately pick up on what you just added via synaptic.

---

### Post by BarbiGirl8 on 2005-02-15
I thought I would give that a shot after my second round of restarting and saw that it worked. *Oh happy day*. I was finally able to install the 2 packages that I was trying to. Now I think i'm starting to get the hang of this... Thanks

---

