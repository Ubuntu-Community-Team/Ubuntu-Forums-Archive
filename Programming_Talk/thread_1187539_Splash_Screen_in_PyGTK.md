---
title: "Splash Screen in PyGTK"
date: 2009-06-14
forum: Programming Talk
---

### Post by master_kernel on 2009-06-14
Does anybody know how to do this? Last I had heard the developers never *actually* finished it - they gave up because it was too hard. This is what I am looking for:

[LIST]
[*]User starts program
[*]Splash screen loads while myCode() executes in the background
[*]Splash screen disappears and main() shows
[/LIST]

in PyGTK/Python & Glade. Thanks!

---

### Post by monraaf on 2009-06-14
IMHO splash screens are annoying, but if you insist. Just create an undecorated window as your splash screen, put an image in it, show it then add an idle handler with your code and at the end hide or destroy the splash screen and show your main window.

---

### Post by Tony Flury on 2009-06-15
In my honest opinion a splash screen can be useful if the startup time for the main application is very long.

The expectation from many users is that double clicking will do "something" soon (sub 5 seconds or so).

If re-engineering your application to shorten the start up time is not an option, then adding in a simple splash screen might be something worth while.

For instance GIMP has a splash screen, with a progress bar, and that i find is a good idea.

I use Secondlife a lot, and that has a long start up time - and no splash screen - O often find myself opening multiple instances because I am not sure if it is actually doing anything or whether I did actually double click.

---

### Post by master_kernel on 2009-06-15
Thanks for the replies!
I just couldn't find a module/function in gtk.Assistant for automatically starting a process once a forward button was pressed, so that leaves a splash screen as the only other option for running the process without freezing up on the user.

---

### Post by master_kernel on 2010-06-05
Solved - example code can be found in KernelCheck Delta.

---

