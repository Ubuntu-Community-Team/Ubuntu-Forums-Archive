---
title: "from python script to an executive GUI"
date: 2008-01-02
forum: Programming Talk
---

### Post by helphope on 2008-01-02
Hi everybody.

I've written a short python script and I'd like to have it as an executive wth a GUI interface.

I've run through a short tutorial on Tkinter, but I don't understand if and how I can  "join" the python script to tkinter ...


:confused:

Thanks for any help

---

### Post by jpkotta on 2008-01-02
Try wxPython with wxglade or boa contructor.

---

### Post by helphope on 2008-01-02
Thanks for replying.

You mean that I cannot do that with Tkinter?

---

### Post by LaRoza on 2008-01-02
You can use any tool kit you want, including wxWidgets and Tkinter.

If it is simple, you can use EasyGUI, see my wiki for information on that.

---

### Post by helphope on 2008-01-02
Thanks,

 but I'm back to the point from which I moved off.
My problem is to "join" the pyhon script to a GUI and then have it as an executive inLinux and possibily also in windows.

The script is quite simple, but for me it is meant to be as a beginning.

Thanks for any help

---

### Post by LaRoza on 2008-01-02
> **helphope said:**
> Thanks,

 but I'm back to the point from which I moved off.
My problem is to "join" the pyhon script to a GUI and then have it as an executive inLinux and possibily also in windows.

The script is quite simple, but for me it is meant to be as a beginning.

Thanks for any help

It depends on how the script was written, a well written script will be easy to give a GUI.

What are your needs?

If browsing the wxWidgets, Tkinter, and EasyGUI sites didn't help, then I don't know what to say.

---

### Post by helphope on 2008-01-02
Thanks Laroza.

I'm browsing your wiki and I got something interesting: maybe (for sure) I took a step too long. I'll go through again the tutorials .

:)

---

### Post by dwblas on 2008-01-04
Just to clarify, you would not necessarily "join" but include Tkinter in the python program.  For example, if you want to display something that you now print, you would replace the print statements with a Tkinter display box.  Here is another reference/tutorial [http://python-eggs.org/?row=2](http://python-eggs.org/?row=2)

---

### Post by helphope on 2008-01-10
Thanks dwblas.
Sorry for replying late.

> you would not necessarily "join" but include Tkinter in the python program.

I've seen this; at the time of the post I dind't now that, now I'm trying to understand how to figure it out

---

### Post by dwblas on 2008-01-10
Post a snippet of what you are doing-before Tkinter-and where you want to add a Tkinter interface.  You can also import a separate Tkinter program which may be more of what you want to do.  This link sends data to a list box.  Note at the end of the program, how ordinary python strings are inserted into a Tkinter listbox.  [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52266](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52266)

---

