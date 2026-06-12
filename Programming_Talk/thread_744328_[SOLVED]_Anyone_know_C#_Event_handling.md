---
title: "[SOLVED] Anyone know C# Event handling?"
date: 2008-04-03
forum: Programming Talk
---

### Post by bovus on 2008-04-03
I am trying to make an EventHandler for a ToolStripMenuItem Click event, however I would like to do something like this:


The following code is Java:

```

  Frame f = new Frame("Checking the mouse click");
  f.addWindowListener(new WindowAdapter(){
        public void windowClosing(WindowEvent we){
            System.exit(0);
        }
  });

```

is there a way to do this in C#?

something like:

```

ToolStripMenuItem menuJob = new ToolStripMenuItem();

menuJob.Click += new EventHandler(

```

---

### Post by luisromangz on 2008-04-03
In C# this is much simpler than in Java, in fact is one of the points in which C# is a clearly superior language.

The code would be

menuJob.Click += new EventHandler(OnMenuJobClicked);


Then, there should be a method in that class with this structure:

void OnMenuJobClicked(object sender, EventArgs clicked)
{
     // ....
}

You can define your own event types, so you can pass diffent kind of parameters to the event handler.

---

### Post by bovus on 2008-04-03
yea i knew about that, I actually found a way to do what I wanted.  I didnt realize that the "sender" parameter pointed to the actual instance of the object holds the event.  Thought it was the instance of the class the object was in or something.  It makes sense now.  Thanks anyway though

---

