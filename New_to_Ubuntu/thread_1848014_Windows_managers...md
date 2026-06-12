---
title: "Windows managers.."
date: 2011-09-21
forum: New to Ubuntu
---

### Post by Bob555 on 2011-09-21
Ok I'm tired of this happening, I accidently run the --replace option in the terminal, for example "metacity --replace". Then I close the terminal and it closes the WM making the GUI almost unusable.

How am I supposed to replace the WM from the terminal without it being killed when I close the window. 

Also does anybody know a good way to restore the WM somehow in an emergency. Ideally without using any UI (since its not reliable)

Maybe it's just me but this seems like this is a big problem, like there would be an easy solution for it. 

Thanks

edit2: Ok I figured it out, in case people want to know you can do it from terminal with
```
nohup metacity --replace & 
```or
```
screen metacity --replace
``` (then press ctrl+a+d)

And to do it from the tty* terminal run this
```
metacity --replace --display :0.0 
```

---

### Post by wojox on 2011-09-21
Did you add the ampersand?

```
metacity --replace &
```

---

### Post by Frogs Hair on 2011-09-21
How do you accidentally  run the metacity  --replace command in the terminal ? That is deliberate command .  Are having a problem that requires restarting the window manager often ? 

There is a window manager icon that can be enabled on the main menu under the other category and used in place of the terminal command .

---

### Post by IWantFroyo on 2011-09-21
> **Frogs Hair said:**
> How do you accidentally  run the metacity  --replace command in the terminal ? That is deliberate command .  Are having a problem that requires restarting the window manager often ? 

There is a window manager icon that can be enabled on the main menu under the other category and used in place of the terminal command .

I think he means that he runs the command, but then closes the terminal by accident later.

I know whenever I have a bunch of terminals cluttering up my taskbar, I get rid of them.

---

### Post by Bob555 on 2011-09-21
> **wojox said:**
> Did you add the ampersand?

```
metacity --replace &
```



Yeah I tried, it still closes the WM as soon as the terminal closes

I did find a way using
> nohup metacity --replace &
Somehow it works, I don't know why but at least it's something.

But that's only half the problem, since it could still happen I want to know a for sure way of getting the WM back up (resarting gdm works but closes everything I have open, that's not ideal) I'm thinking I need a way to do it from the tty* (the ctrl+alt+F1)) but running it says "unable to open X display 0"

---

### Post by kukibird1 on 2011-09-21
Are you able to run metacity --replace  from the run dialog  Alt-F2 .

---

### Post by Bob555 on 2011-09-21
> **kukibird1 said:**
> Are you able to run metacity --replace  from the run dialog  Alt-F2 .

Yes that works, but ideally I want to do it from the terminal. It seems silly to have to rely on a dialog window just to do something so basic. And that run dialog might not always be available for whatever reason. The terminal is pretty much universal so I prefer to learn it that way.

---

### Post by wojox on 2011-09-21
> **kukibird1 said:**
> Are you able to run metacity --replace  from the run dialog  Alt-F2 .

That would be my next try depending on what version your using?

---

### Post by wojox on 2011-09-21
You could try installing screen and running it as a wrapper

```
screen metacity --replace
```

Then press Ctrl+A+D to detach from the screen process.

---

