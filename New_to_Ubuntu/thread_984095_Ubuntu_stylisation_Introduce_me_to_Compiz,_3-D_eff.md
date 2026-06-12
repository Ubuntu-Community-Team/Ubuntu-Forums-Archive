---
title: "Ubuntu stylisation: Introduce me to Compiz, 3-D effects, docks, themes, icons, etc."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Obero on 2008-11-16
Styling Linux is one of the most interesting things that attracted me to make the switch from Windows. Compiz, 3-D effects, docks, themes, icons, etc. are all fun and creative gadgets used to make the user feel more comfortable and open to Linux.

So first of all, I'd like to ask, how do I check if I'm able to use Compiz or the 3-D effects? Would it bust my computer? What specs do I need? How do I check if I have those specs?

Docks, themes, icons, etc., tell me which ones you use and how to get it!

Thanks in advance.

---

### Post by Peter09 on 2008-11-16
Download the LiveCD, this allows you to use Ubuntu without changing your system (it runs from the CD). This will give you an idea of how it will work. Although the Live CD may be limited in some respects it a good start.

---

### Post by DoubleMcLovin on 2008-11-16
I've been able to run Compiz-fusion (though very poorly) on a laptop with a 256MB GPU and a 2.7GHz CPU and 1.5GB RAM. These are the 3 factors you really wanna look at, but most importantly is the GPU.

So lets start by looking at your video card, firstly make sure you have the proper proprietary drivers installed (usually done easily in "System-->Administration-->Hardware Drivers" and enabling/installing the one flagged as "Recommended") Now if you know that you don't have a graphics card thats at least 256MB in the machine, you may just want to go buy one before attempting this as compiz will run poorly.

If all of that goes well, lets get the Compiz-settings-manager to make configuring compiz much easier.
Open a terminal and run:```
sudo apt-get install compizconfig-settings-manager simple-ccsm
```

After this, you can go to "System-->Preferences-->Simple CompizConfig Settings manager" and get a basic feel for the program there, once you have a grasp on its concepts, you can further config your system by looking in "System-->Preferences-->CompizConfig Settings Manager"

Hope this helped =]

---

### Post by Obero on 2008-11-16
Actually, I'm more interested in the themes, docks, and icons, moreso than the Compiz. I don't think Compiz will be a good idea, lol.

---

### Post by DoubleMcLovin on 2008-11-16
Ok then, for most customization you can look at [http://www.gnome-look.org/]("http://www.gnome-look.org/") They will have plenty of themes to customize your setup and such. Also for a dock theres always the one in "Applications-->Accessories-->SimDock"

---

