---
title: "problem in Glade interface designer of Ubuntu 9.10"
date: 2009-11-27
forum: Programming Talk
---

### Post by brijith on 2009-11-27
Hi all,

When I take a glade file ( which is designed in Ubuntu 9.04  ) in Ubuntu 9.10 every thing in coming distorted. Can any one help me in solving this .... Only because of this issue we are not able to use ubuntu 9.10 in our office...

**[COLOR="Sienna"]Thanks in avdance[/COLOR]**

---

### Post by days_of_ruin on 2009-11-28
Was the 9.04 one in LibGlade or GtkBuilder format?

---

### Post by brijith on 2009-11-28
> **days_of_ruin said:**
> Was the 9.04 one in LibGlade or GtkBuilder format?

I don't know What it is....
I have the glade files ....
Is there any way to get its format from the files ...

**[COLOR="DarkOrange"]Thanks for your Reply[/COLOR]**

---

### Post by Virtual Liberty on 2009-11-28
> **brijith said:**
> 
When I take a glade file ( which is designed in Ubuntu 9.04  ) in Ubuntu 9.10 every thing in coming distorted.**[COLOR=Sienna][/COLOR]**

Please be more specific - language, examples of what's not working, etc. ;)

---

### Post by brijith on 2009-11-28
> **Virtual Liberty said:**
> Please be more specific - language, examples of what's not working, etc. ;)

Oky...

Please check the attached screen shots

The first one is how the interface actually look

The second one is how it looks when I open the glade file in Glade interface designer ...

---

### Post by nvt on 2010-01-07
Hi brijith,

After switching to 9.10, I got similar problem.
Have you found any solution?

Thanks for you help

---

### Post by giuspen on 2010-01-07
I had the same problem but it's not a big deal, it's just a couple of vbox that turn into hbox or vice versa.

It takes less than one minute: find the vbox/hbox that behaves bad and change the parameter ORIENTATION (tab general, from horizontal to vertical or vice versa) you'll see everything gets fixed.

Once you fix it, if you open again with an older glade it will be still good... you will not need to change again the orientation.

---

### Post by brijith on 2010-01-08
Thanks ...
did it worked for you ? 
I will check it in my system .

---

### Post by Flimm on 2010-01-08
> **giuspen said:**
> I had the same problem but it's not a big deal, it's just a couple of vbox that turn into hbox or vice versa.
That's exactly the problem, thanks giuspen. All vertical type widgets (VBox, VPane, VScrollbar, etc) are assumed to be horizontal when <property name="orientation"> is not included in the source of the glade file, which seems to be the case for most old glade files.

I made a script that automatically fixes this, it's attached. To run:
```
python fix_glade_3.py filename.glade
```
A backup named *filename.glade~script~* is automatically created.

UPDATE: I've updated the script so that it handles glade files built with libglade and GtkBuilder.

---

### Post by nvt on 2010-01-09
Thanks all for your help,
and thanks Flimm for the script!

It seems to work for me, and I have check "back port" 9.10->8.04.
However, problem seems to be deeper. In older versions (<9.10)
glade-3 was in main repository, but in 9.10 glade is excluded 
from the main repository and there is no glade-3 at all! 

Best regards, nick

---

### Post by djtarki on 2010-01-28
:p

I was pretty scared at the beginning when I saw the behaviour of the Glade project in Ubuntu 9.04

---

