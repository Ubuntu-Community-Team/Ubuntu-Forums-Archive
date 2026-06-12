---
title: "Trying to change Eterm font"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by Odexios on 2012-01-28
Hello everyone!

I'm trying to get a permanent transparent desktop instance of Eterm on my netbook with lubuntu 11.10; after an afternoon of tinkering around, I eventually succeeded.

I didn't like the font, though, so I tried to change it; via the man page I found out I could do it via command line, by calling Eterm with the -F option; but, I don't have the slightest idea of how to find out what the names of the fonts are, and, consequentely, what I should write after the -F option.

Is there anyone able and willing to help me?

EDIT: It seems like I talked too soon. It seemed like everything worked fine, but when I login the terminal is on the desktop where it should be, but the background isn't transparent.

Here's the command I put in /etc/xdg/lxsession/Lubuntu/autostart:

```
Eterm  -0 -O -n "eterm-bg" --scrollbar=false --buttonbar=false
```

Is there a reason for the -0 and -O being ignored?

---

### Post by Rodney9 on 2012-01-28
Cool Idea, I must say.

This should work -
> open Eterm and go to background --> toggle transparency then;
Eterm --> save user settings and save theme settings


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Odexios on 2012-01-28
> **Rodney9 said:**
> Cool Idea, I must say.

This should work -Unfortunately, it doesn't. Don't know why, but at startup the terminal appears, width, height and position are correct, but the background is opaque.



> For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

RodneyThanks! I'm going to dive into those links for a bit XD

---

### Post by Rodney9 on 2012-01-28
I have heard that aterm is more lightweight than eterm, you could give it a try.

Here is a guide on aterm with font and transparency tips - 

[http://linuxreviews.org/software/x11-terms/aterm/](http://linuxreviews.org/software/x11-terms/aterm/)

Rodney

---

### Post by Odexios on 2012-01-29
> **Rodney9 said:**
> I have heard that aterm is more lightweight than eterm, you could give it a try.

Here is a guide on aterm with font and transparency tips - 

[http://linuxreviews.org/software/x11-terms/aterm/](http://linuxreviews.org/software/x11-terms/aterm/)

Rodney
Problem solved!

I still don't understand why I had issues with Eterm, but with Aterm everything worked fine. Well, I guess the important thing is the result.

Thank you very much!

---

