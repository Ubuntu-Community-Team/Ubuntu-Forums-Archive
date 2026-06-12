---
title: "X11/Motif SDK"
date: 2013-01-16
forum: Programming Talk
---

### Post by kuifje09 on 2013-01-16
Does someone know a SDK to design grafical applications with X11-libs.
I have searched a lot but cannot find one, unless I want to buy one.

I want X11 or Motif programming because X11 is the basic system where linux and unix is running on. So any program could run everywhere.

So, No python, Gambas, WXwidget etc...  But 

XtCreateManagedWidget  and so on....   

Doing that by hand is just to much for me...   
Thus grafical UI design and CodeCompletion is a must for me.

---

### Post by tgalati4 on 2013-01-16
Open a terminal:

```
apt-cache search motif
```

Open Motif 4 is installed in latest Ubuntu distro, but you can also add Motif 3 for backward compatibility.  I had to do that to get qtdmm to work with my voltmeter, since it relies on libmotif3 and that's not included in 12.10, but you can simply install libmotif3 from a 12.04 repository without a problem (so far).

[http://www.opengroup.org/openmotif/](http://www.opengroup.org/openmotif/)

---

### Post by kuifje09 on 2013-01-16
Thanks for this very quick reply, but I think I do not understand what you try to say.

I did this on my system :

apt-cache search motif | grep -i sdk

Wich gave no output at all, while without the grep gave 64 answers.
But all about tk, Gtk, wxwindows, lot of libs and so on.

I try to find a GUI-SDK to develop in X11/Motif

Maybe I should ask, which program do you use to do so?

---

### Post by tgalati4 on 2013-01-17
I would start with [http://www.eclipse.org](http://www.eclipse.org).

---

### Post by kuifje09 on 2013-01-17
Well, Its not what i was looking for, maybe I go back, have a look again on WxFormBuilder.

Wich mean, designing is at least a 2-step action.

After the design,  Design the Gui with WxFormBuilder,  then add actual code within another "IDE". Probable eclipse.
But Eclipe is so very big....  I think there is none else.

Thanks anyway.

---

### Post by dwhitney67 on 2013-01-17
> **kuifje09 said:**
> Does someone know a SDK to design grafical applications with X11-libs.
I have searched a lot but cannot find one, unless I want to buy one.

I want X11 or Motif programming because X11 is the basic system where linux and unix is running on. So any program could run everywhere.

So, No python, Gambas, WXwidget etc...  But 

XtCreateManagedWidget  and so on....   

Doing that by hand is just to much for me...   
Thus grafical UI design and CodeCompletion is a must for me.
I've used X-Designer ([http://www.ist.co.uk/xd/](http://www.ist.co.uk/xd/)) in the past; it works quite well.

---

