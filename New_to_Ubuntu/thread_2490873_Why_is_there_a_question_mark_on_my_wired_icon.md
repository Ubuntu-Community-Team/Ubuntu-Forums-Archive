---
title: "Why is there a question mark on my wired icon"
date: 2023-09-19
forum: New to Ubuntu
---

### Post by johnnybegood2222 on 2023-09-19
To the left of my "sound" icon on top right, why is there a question mark on my icon for my internet connection - which I have plugged in via ethernet - ?

Just curious why...

---

### Post by Rubi1200 on 2023-09-19
Hi and welcome to the forums :-)

You don't mention which version you are on?

Is this a new issue from an upgrade or other change or is this a fresh install?

Try restarting the network manager from the terminal:
```

sudo systemctl restart NetworkManager

```

Let us know what happens.

---

### Post by johnnybegood2222 on 2023-09-19
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

You don't mention which version you are on?

Is this a new issue from an upgrade or other change or is this a fresh install?

Try restarting the network manager from the terminal:
```

sudo systemctl restart NetworkManager

```

Let us know what happens.

I have one of the latest versions of Ubuntu, I think 22.x

Should I go ahead and run that command you gave in terminal now that you know my Operating System?

---

### Post by Rubi1200 on 2023-09-19
Yes please.

---

### Post by johnnybegood2222 on 2023-09-21
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

You don't mention which version you are on?

Is this a new issue from an upgrade or other change or is this a fresh install?

Try restarting the network manager from the terminal:
```

sudo systemctl restart NetworkManager

```

Let us know what happens.


I ran that command, but the little question mark is still over the small icon - hmmmm

---

### Post by johnnybegood2222 on 2023-09-21
Here is what it looks like:

---

### Post by ActionParsnip on 2023-09-21
The question mark icon means that NetworkManager’s connectivity check couldn’t verify if you have an internet connection or not. I’ve also seen it have an exclamation point icon when it determines that it’s down. The question mark is one I’ve usually seen when there’s a web login for a network connection (hotel, airport, etc.).


If you want to disable it, I don’t know of a way to do it in the GUI, but you can try editing, with
```

sudo vi /var/lib/NetworkManager/NetworkManager-intern.conf

```

and add this:
```

[connectivity]
.set.enabled=false

```

Then run:
```

systemctl restart NetworkManager

```

and, if my reading of docs and such is correct, it should no longer attempt to verify the connectivity. If you get no network access, just wind back the edit

---

### Post by johnnybegood2222 on 2023-09-21
After a restart it is looking normal.

Thanks all!

---

### Post by johnnybegood2222 on 2023-09-24
I thought this question mark had permanently gone away, but it's back, so I marked this thread as unsolved again.

It really doesn't affect anything - the computer goes onto the internet via ethernet just fine, I guess I'll just ignore it.

Oh, this only started to show up after I did a clean install of Ubuntu 22.x  lts

---

### Post by MAFoElffen on 2023-09-24
Please post the results of this within CODE Tags:
```

journalctl -p 4 -xb -g '[n,N]etwork'

```
If NULL (no output) just tell us...

---

### Post by johnnybegood2222 on 2023-09-25
> **MAFoElffen said:**
> Please post the results of this within CODE Tags:
```

journalctl -p 4 -xb -g '[n,N]etwork'

```
If NULL (no output) just tell us...

The results are:

> 
michael@michael-HP-EliteDesk-800-G1-SFF:~$ journalctl -p 4 -xb -g '[n,N]etwork'
Sep 25 01:18:31 michael-HP-EliteDesk-800-G1-SFF snap-store[3272]: not handling >
Sep 25 01:18:50 michael-HP-EliteDesk-800-G1-SFF pulseaudio[1121]: GetManagedObj>
lines 1-2/2 (END)



---

### Post by MAFoElffen on 2023-09-25
Those are not related to anything network related(???)

---

