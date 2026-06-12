---
title: "javascript -&gt; dll"
date: 2007-06-18
forum: Programming Talk
---

### Post by desijays on 2007-06-18
Im not sure if what im trying to do is unusual. You decide.

Im trying to call a dll file ( or more specifically a function in a dll file ) from javascript code embedded in an html file. Would anyone know how to do it? 

Ive been trying to figure out how to do it since morning and its evading all attempts. Even a hint in the right direction would be useful.

---

### Post by Max_Might on 2007-06-18
It definetly sounds unusual ... for me at least. I don`t think this could be possible. Maybe you could try to recreate this function with JavaScript or some of the server side programming languages and then use AJAX to pass the result to the webpage.

---

### Post by SishGupta on 2007-06-18
I really doubt it is possible. JS is client side, so you would want to call a dll on someones browser. Doesn't that sound like a major disaster to you?

---

### Post by dpsleep on 2007-06-18
Maybe try php? I've done something similar to that with php...

---

### Post by desijays on 2007-06-18
okie, this is what im trying to do.

I have an external circuit that has a small electric motor on it. The electri motor is controlled by an AT89C51 micro-controller. 

And im using the serial port on the micro controller to connect to the serial port of my computer( yes my rig is old :( ) that has XP. Ive written the device driver for XP that communicates with the external device. 
My goal is to switch on and off the motor from the PC.

Im also trying to control its speed, but ive run into problems :( so, i just want to test what i've done so far. Writing DD in XP seemed more harder than I thought. Most of the hardware is virtualized :(

I've written a dll that has the provision to send only 2 commands to the device driver thru the OS. start and stop. And now I have to write an app that can access the dll. 

But for a moment, I thought it will be cool if I could control it with my web browser. That's what has lead me this far...

so i want to use MY browser on MY comp to control MY motor. The reason I capitalized 'MY' was to emphasize that it doesn't involve any other client or server.

I hope i came across clear. Since most browsers have javascript installed on them, i thought i could use javascript to call the dll to control the motor.

---

### Post by cdenley on 2007-06-18
If you're trying to send commands to the serial port, why not write to /dev/ttyS0 using php or python? You're not going to be able to use a DLL with javascript alone. If you want to run a DLL from a web page on Windows XP, you could probably use dllimport in ASP.NET. You would need to run a web server, and the DLL would be called from the server.

---

### Post by 3rdalbum on 2007-06-18
It may (that's a *MAY*) be possible on IE 6, but not on any browser made by a company with half an ounce of security sense. Not even on Safari.

You could write a simple server in Python, and a wrapper for the DLL (I think there's a module that lets you call DLLs directly, or am I thinking of MacPython here?); or you could stretch a thin GUI layer over your Python program using something like Pythoncard. But I don't think Javascript has the necessary links to call DLLs directly.

---

### Post by desijays on 2007-06-20
thanks you all, for the hints so far !!

> **3rdalbum said:**
> It may (that's a *MAY*) be possible on IE 6, but not on any browser made by a company with half an ounce of security sense. Not even on Safari.


i anticipated that one :)

ok, so i get it that I can't call the dll from javascript unless Im willing to bend and break a lot of things. And Im not willing to start an R&D department over this.

but wouldn't the following be possible.

The 'dll' that I was talking about, like I said, has only 2 functions. One for starting the motor and another for stopping it. So, what if i re-write the entire dll, into an intermediate form( whatever it is), that javascript is comfortable calling or using.

Like a plugin for instance; that can forward the call to XP and the rest is taken care off since the device driver is already in place. I don't know how it would work though. Im a little rough on web programming. But Im willing to figure it out and re-write the whole thing if I knew how..

---

### Post by FuturePast on 2007-06-20
You could probably do this by implementing the dll as an XPCOM component for Mozilla/Firefox.
You can then call methods of the component from JS.

---

### Post by RawMustard on 2007-06-20
If you don't need feedback into the browser, you can use firefox's protocol handler to execute local files.  This would only be good for your own machine though, it won't work across the net and it shouldn't :)

---

### Post by desijays on 2007-06-21
> **FuturePast said:**
> You could probably do this by implementing the dll as an XPCOM component for Mozilla/Firefox.
You can then call methods of the component from JS.

if i manage to implement the dll as an XPCOM component, would that be equal to a plugin or something?

plz overlook my newbish question. !!!

---

### Post by FuturePast on 2007-06-21
> **desijays said:**
> if i manage to implement the dll as an XPCOM component, would that be equal to a plugin or something?

plz overlook my newbish question. !!!
Not quite a plugin. Plugins allow the browser to display different kinds of content.
You'd be implementing an extension i.e. adding new functionality to the browser UI.
There's plenty of documentation at [http://developer.mozilla.org/en/docs/XPCOM](http://developer.mozilla.org/en/docs/XPCOM)

---

