---
title: "Monodevelop Problem"
date: 2011-02-18
forum: Programming Talk
---

### Post by etdsbastar on 2011-02-18
Hello Friends,

I am using Monodevelop for my C# Programming needs. I stuck in a problem. I want to add some code in the Window (Form) OnLoad Event. I don't know how to do this. Anyone Please help.

```
using System;
using Gtk;

public partial class MainWindow : Gtk.Window
{
    public MainWindow () : base(Gtk.WindowType.Toplevel)
    {
        Build ();
    }

    protected void OnDeleteEvent (object sender, DeleteEventArgs a)
    {
        Application.Quit ();
        a.RetVal = true;
    }
}
```

---

### Post by muteXe on 2011-02-18
What happens when you double click the form in design mode?

---

### Post by etdsbastar on 2011-02-19
> **muteXe said:**
> What happens when you double click the form in design mode?

nothing..

For writing signals (code) I have to access them through the Signal Pad by double clicking on a particular signal name.

---

### Post by PaulM1985 on 2011-02-19
After looking it up, it doesn't appear that Gtk Window has an OnLoadEvent like the Windows equivalent.

Here is the API I used:

[http://www.go-mono.com/docs/index.aspx?link=root:/classlib-gnome](http://www.go-mono.com/docs/index.aspx?link=root:/classlib-gnome)

You can still use windows forms in Mono.  You need to add the reference to your project.  Then you could use the OnLoadEvent for this.

I prefer to add event handlers to my events than override them.  I sometime wonder if I am preventing them from doing something important, so in this case I would do something like:

```

this.LoadEvent += new EventHandler(MainWindow_LoadEvent);

```

and define the MainWindow_LoadEvent function.

Alternatively, if you do not want to use Windows forms, is it not possible to put the load event code in the constructor?

Paul

---

### Post by etdsbastar on 2011-02-19
> **PaulM1985 said:**
> After looking it up, it doesn't appear that Gtk Window has an OnLoadEvent like the Windows equivalent.

Here is the API I used:...

I couldn't find any event list in this.?

Is there any other way for OnLoad Event. If it is not possible then how it is being done for the programs developed in C# using monodevelop. 

Awaiting...

---

### Post by PaulM1985 on 2011-02-19
No.  There isn't one for Gtk.  Why not try Windows Forms?  Or alternatively putting that code in the constructor?

Paul

---

### Post by etdsbastar on 2011-02-19
> **PaulM1985 said:**
> No.  There isn't one for Gtk.  Why not try Windows Forms?  Or alternatively putting that code in the constructor?

Paul

Thanks Paul for your support. I will try as you told.

---

### Post by directhex on 2011-02-21
You would be well served by trying some GTK# tutorials.

---

