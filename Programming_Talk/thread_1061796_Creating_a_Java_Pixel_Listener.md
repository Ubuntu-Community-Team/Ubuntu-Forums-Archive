---
title: "Creating a Java Pixel Listener"
date: 2009-02-06
forum: Programming Talk
---

### Post by Pyro.699 on 2009-02-06
I'm not exactly 100% sure I'm even using the term **listener** properly but from how i understand it works is that it waits for an event to happen and then will take proper action once that has happened. Before this thought came to me i had the idea of using a loop:

```

while(true){
//Code goes here
}

```

But i didn't even try it because i knew it would eat up system resources. I already have the method written to extract the RGB values at a given point, i just need a way to "listen" for them to be set and make an action based on that.

Thanks
~Cody Woolaver

---

### Post by Zugzwang on 2009-02-06
Where do the pixels come from? Do you extract them using this XTEST framework?

The term "listener" is correct but you can only apply listeners to event handlers that support listeners. If that's not the case then you can either:
[LIST=1]
[*]Rewrite the application that generates this events in order to add listening support
[*]Do the polling as you already do. BTW: Adding some sleep(1) command or so reduces system load. At least a Thread.yield() should be done in your loop!
[/LIST]

---

### Post by Pyro.699 on 2009-02-06
The pixles come from a method i wrote. It uses the Robot class and used the method getPixel(x,y)

```

        Robot r = new Robot();
        Color col = r.getPixelColor(1, 2);
        
        int red = col.getRed();
        int green = col.getGreen();
        int blue = col.getBlue();

```
(not my real method, but almost the same)

How do you create a class that generates events?

---

### Post by Zugzwang on 2009-02-06
You've got the problem that Robot doesn't generate these events. I guess you have four possibilities here:

[LIST=1]
[*]Leave the polling as before
[*]Generate a native watcher program that watches for changes (by polling again) such that system load is decreased and let it communicate with your program by -for example- network sockets.
[*]Change something in code of the XServer, the XTEST framework (which is used by Robot) and the Robot implementation to let you detect changes.
[*]Probably, if you are lucky, then there's some built-in way to detect changes in the X-Server. You could also use a custom X-Server that supports this function (if existing).
[/LIST]

---

### Post by Pyro.699 on 2009-02-06
I guess im going to go with the first one, but as stated before i havnt made the class yet. Is there a way i could do something like:

-the method is started
-Event A is true (returns something, but continues on in the loop)
-Event B is false, keep going
-Event C is true (returns true, be keeps going)
-loop over, restart

And that runs the entire duration of the script being run

---

### Post by Zugzwang on 2009-02-06
> **Pyro.699 said:**
> Is there a way i could do something like:

-the method is started
-Event A is true (returns something, but continues on in the loop)
-Event B is false, keep going
-Event C is true (returns true, be keeps going)
-loop over, restart


I don't understand your post. What do you mean by an event to be true?

---

### Post by Pyro.699 on 2009-02-06
```

public boolean EventA(int x, int y){
//code to see if the color is correct at pos x,y
}
public boolean EventB(int x, int y){
//code to see if the color is correct at pos x,y
}
public boolean EventC(int x, int y){
//code to see if the color is correct at pos x,y
}

```

I probally should have used another term than Event... sorry

---

### Post by cl333r on 2009-02-06
I also don't understand. IMO you're explaining too low level.
What are you trying to achieve at the global level? A basic drawing-like application? A visual kind of sniffer?
I mean what will your application be good for?

> **Pyro.699 said:**
> I guess im going to go with the first one, but as stated before i havnt made the class yet. Is there a way i could do something like:

-the method is started
-Event A is true (returns something, but continues on in the loop)
-Event B is false, keep going
-Event C is true (returns true, be keeps going)
-loop over, restart

And that runs the entire duration of the script being run

---

### Post by Pyro.699 on 2009-02-06
The application i am creating is a simple bot for an emulator. I want the bot to take actions based on the locations of colored pixels. If a text dialogue appears on the screen i want the "a" button to be pressed (by simulating a keystroke)

---

### Post by cl333r on 2009-02-06
I would find a way to query Gnome (or the X server) for the currently displayed dialogs, probably C is to be used. Analyzing the colors on the screen and figuring out whether that's a dialog, I think, isn't a good nor easy task.

---

### Post by Zugzwang on 2009-02-07
> **cl333r said:**
> I would find a way to query Gnome (or the X server) for the currently displayed dialogs, probably C is to be used. Analyzing the colors on the screen and figuring out whether that's a dialog, I think, isn't a good nor easy task.

I would assume that the application is meant to be run in full-screen mode. This way, things always appear at the same position.

@OP: Anyway, if you want to use Java and want to maintain cross-platformness, your polling loop is probably the only (or at least only easy) way to go. In order to reduce system load, use something like "Thread.sleep(50)"after every check.

---

