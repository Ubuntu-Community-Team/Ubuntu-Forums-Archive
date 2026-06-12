---
title: "A number of 8.04 problems."
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ftaylor on 2008-05-06
I have been using Ubuntu since 7.10 was released, last October. The change from 7.10 to 8.04 has broken a number of features. Any advice greatly appreciated.

-If I am using rhythmbox/any music player and I try to watch a video on Youtube or visit any website that gives sound feedback; the sound on the website will not play unless I close rhythmbox.

-FGLRX Driver dodgy as hell! The screen flashes black every couple of seconds on screensaver or any other graphics consuming features - glxgears flashes constantly.

-I mount my windows partition and it always unmounts when I restart my laptop.

-OpenOffice opens really slowly.

Any help with any of these points would be greatly appreciated folks!

---

### Post by inportb on 2008-05-06
let's see...

- looks like the audio device is not being shared properly. i have no clue about this one.
- fglrx is dodgy as hell... by design. i use it and idk if i should love it or hate it.
- that sounds like normal mount behavior (correct me if i'm wrong). have you added a fstab entry?
- disable oo.o java and reduce the number of undo steps.

---

### Post by hyper_ch on 2008-05-06
> **ftaylor said:**
> -I mount my windows partition and it always unmounts when I restart my laptop.
Make an entry in your fstab to moutn it.

> **ftaylor said:**
> -OpenOffice opens really slowly.
[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

---

### Post by ftaylor on 2008-05-06
What's an FSTAB entry?

How do I disable oo.o java?

---

### Post by inportb on 2008-05-06
like hyper_ch said, [http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu) is useful for speeding up oo.o

more about fstab: [http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by ftaylor on 2008-05-06
Thanks very much for your help folks!

---

### Post by inportb on 2008-05-08
I'm glad it worked. btw, OO.o 3.0 beta is out, though it's not the most efficient as of now.

---

### Post by santiagoward2000 on 2008-05-08
> **ftaylor said:**
> -FGLRX Driver dodgy as hell! The screen flashes black every couple of seconds on screensaver or any other graphics consuming features - glxgears flashes constantly.

I'm having the same problem. It's way slower than when I used it in Gutsy with XGL. Personally, I'm not using Compiz any more.
Still, if there's any solution, I'd like to hear it too.
Thanks!

---

### Post by ftaylor on 2008-05-09
Hey,

DONT use XGL in Hardy.  I initially made that mistake and it just completely breaks the graphics card and everything goes incredibly slow.

It is odd - my graphics render just as fast, but it flashes black all the time.

---

### Post by Cornova on 2008-05-09
> **ftaylor said:**
> Hey,

DONT use XGL in Hardy.  I initially made that mistake and it just completely breaks the graphics card and everything goes incredibly slow.

It is odd - my graphics render just as fast, but it flashes black all the time.

This may be why my system is dragging eversince I upgraded to Hardy. What is XGL and how do I remove it?

---

### Post by ftaylor on 2008-05-09
xserver-xgl is a package designed to boost the performance of your graphics card. It is generally not installed by default.

You can type

```

sudo dpkg -r xserver-xgl

```

---

### Post by Cornova on 2008-05-09
> **ftaylor said:**
> xserver-xgl is a package designed to boost the performance of your graphics card. It is generally not installed by default.

You can type

```

sudo dpkg -r xserver-xgl

```

Just tried this and when I rebooted my screen was almost completely white. ](*,)

---

### Post by ftaylor on 2008-05-09
```

sudo apt-get install xserver-xgl

```

Some people need it.

What kind of graphics card do you have?

---

### Post by Cornova on 2008-05-09
> **ftaylor said:**
> ```

sudo apt-get install xserver-xgl

```

Some people need it.

What kind of graphics card do you have?

ATI Radeon X800 XL.

---

### Post by ftaylor on 2008-05-09
I don't know.

When I installed xgl everything went wrong.  You must need it.

ftaylor

---

### Post by santiagoward2000 on 2008-05-09
> **ftaylor said:**
> Hey,

DONT use XGL in Hardy.  I initially made that mistake and it just completely breaks the graphics card and everything goes incredibly slow.

It is odd - my graphics render just as fast, but it flashes black all the time.

Hi!
In Gutsy I was using XGL because I had no choice. Now in Hardy I didn't install it. Still, everything is really slow when I use Compiz. Not Compiz itself, the display is quite smooth, but almost every application I open freezes after a few minutes.

---

### Post by ftaylor on 2008-05-09
I have been finding that myself actually.  Applications randomly freeze.  I think I'm going to do a fresh install of Hardy and stay away from Compiz.

---

### Post by santiagoward2000 on 2008-05-09
> **ftaylor said:**
> I have been finding that myself actually.  Applications randomly freeze.  I think I'm going to do a fresh install of Hardy and stay away from Compiz.

That was my solution too. :(
I miss Compiz...

---

### Post by Cornova on 2008-05-09
How does one reinstall XGL and uninstall compiz? Can I do it in safemode?

---

### Post by Cornova on 2008-05-09
> **ftaylor said:**
> I don't know.

When I installed xgl everything went wrong.  You must need it.

ftaylor

For some reason compiz/visual effects needed it. I disabled effects and then removed xgl and now everything is running fast and smooth.

---

### Post by ftaylor on 2008-05-10
```

sudo dpkg -r compiz-core compiz

```

^should say "these need to be removed too".

You can do it in the package manager through a GUI if you want.

---

