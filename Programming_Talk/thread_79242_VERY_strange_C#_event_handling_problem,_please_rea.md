---
title: "VERY strange C# event handling problem, please read."
date: 2005-10-19
forum: Programming Talk
---

### Post by jerome bettis on 2005-10-19
Hi

I'm writing a simple app in C# that communicates with an activeX control for a fingerprint reader.  In my app, I call a function of the activeX control, then I have to sit and wait for the corresponding event to happen before i can continue executing, or I won't get the correct result from the reader.

To do this waiting, I used an AutoResetEvent.  Right after I call the control's function, I say wait for an autoevent to be signaled.  In the event handler function, I set the autoevent.

This works absolutely perfect for every event except one, and I can't figure out why.  The event handler for one event doesn't run (yes I have the event += event_handler thing in the windows forms code.

```
public string Identify()  {
    bioPlugin.IdentifyQuick();     // activeX control's function
    signals.identify.WaitOne();   // wait for the event
    return result;                     // now result is what it should be
}
private void bioPlugin_OnIdentify(object sender, System.EventArgs e) {
    SetResult();                     // store the result somewhere
    signals.identify.Set();        // set the signal
}
```

This works perfect.  Some other form calls the Identify() function when a button is clicked.  The Identify() function calls the IdentifyQuick() method of the active X control, and we sit and wait until the identify signal is set.  This signal is set when the event handler for that event executes.  Everything is great.

```
public void Register(string name)  {
    bioPlugin.RegisterSinglePrint(name);  // activeX control's

    // MessageBox.Show("if we do this, everything works");

    //  this should work and it doesn't. something is borked.
    signals.register.WaitOne();  // waits forever
}
// this code never runs.
// it's linked to the event and it should run - the other events work fine
private void bioPlugin_OnRegister(object sender, System.EventArgs e) {
    SetResult();
    signals.register.Set(); 
}
```

This is the exact same thing here.  The Register() function is called when a button is clicked, we call the RegisterPrint() function of the activeX control, and sit and wait on the right signal.  However, it sits here forever and the event handler code just flat out doesn't run.  It's not a bug in the activeX control, it works just fine in VB and the activeX tester thing.  And I really think I have everything right.

Down at the bottom I do have
```
this.bioPlugin.OnRegister += new System.EventHandler(this.bioPlugin_OnRegister);
this.bioPlugin.OnIdentify += new System.EventHandler(this.bioPlugin_OnIdentify);
```

so the event handlers are linked to the events.  What's really really bizzare is if I show a message box in between calling the active X control and the waiting, everything works.

WTF is going on here??  I need either a) a way to fix this  b) a way to do what ever the message box does without the user seeing a message box or c) an entirely different way of waiting for these event's to execute.

Thanks for reading, any help is greatly appreciated as I'm at a loss.  Could it possibly be a bug in .NET or the threading model or something like that?  I really think it's my code but I'm out of ideas.

---

### Post by LordHunter317 on 2005-10-20
I'm assuming this is all occuring on different threads, right?  I.e., the ActiveX control is running on it's on thread that's not the GUI event/paint thread?

In which case, the first thing to do is to via printing or a flag, verify that the Event isn't occuring before you call signals.register.WaitOne().

---

### Post by jerome bettis on 2005-10-21
nope the problem was the entire program was single threaded. i switched the control to it's own thread and it works great now.

sigh

thanks for your help

i spent some time reading and i learned that it's very easy to make a mistake in a .net gui application and single threaded programs won't cut it.

---

