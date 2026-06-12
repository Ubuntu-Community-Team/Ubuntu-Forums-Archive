---
title: "How Can I Tell What Hardware I'm Using?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-26
I've got several things about my current Compaq Presario 2100 laptop that aren't working as well as they might.  I get NO visual effects, my ethernet doesn't work, etc.  However, the computer is old and I don't know what hardware I'm dealing with.  Is there a way Ubuntu can read what I have and identify it?

Thanks,

Eric

---

### Post by llamakc on 2008-06-26
Graphical way:

I don't know. I don't use those tools. Somebody else will reply with that answer most likely.

Terminal way:

1) Open a Terminal (Applications > Accessories > Terminal) or ALT-F2 and type in gnome-terminal to start the Terminal.

In the terminal type:

```

sudo lshw

```And you can create html output with:

```

sudo lshw -html > mysystem.html

```And then open the file mysystem.html in a web browser.

And for an explanation of what that last one does:

"sudo lshw -html" runs the program lshw with the option to output html. 

">" redirects the output from stdout (the terminal in this case) to a file named 'mysystem.html'

HTH

---

### Post by uberlube on 2008-06-26
I cant exactly remember what its called but if your using Gnome, you should look under System/Admin (or Preferences) to get a tool to show your your hardware.

---

### Post by XVII on 2008-06-26
I recommend installing sysinfo.

```
sudo apt-get install sysinfo
```

---

### Post by UbuntuNerd on 2008-06-26
try some of this
I stumbled upon the nifty “lshw” tool today. lshw lists your hardware. Try it now:


$sudo lshw

You can get specific details by using the -C flag


$sudo lshw -C disk

It create an html page with your hardware details if you do a:
$sudo lshw -html > your-file-name.html


hope it works!!

---

### Post by overdrank on 2008-06-26
i Recommend Installing Sysinfo.


+1
:)

---

