---
title: "terminal question"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by godfreezone on 2012-07-20
Just ran my first successful command at prompt without leading to multiple re-installs or recourse to any drugs prescribed or proscribed.

However, this has led to a question so basic I *almost* fear to ask it, but I take my heart in my hand and .....

I entered 
"gufw" 
at prompt (without quotes) and launched that program... 
but now that terminal is outputting things like:

```
Traceback (most recent call last):
  File "/usr/share/pyshared/gufw/view/guiGufw.py", line 736, in on_btnAddWindow_clicked
    def on_btnAddWindow_clicked(self, widget):
KeyboardInterrupt

```

 which i presume is part of its normal functioning (no, i'm really not on medication for *anything* including paranoid ideation) but how does one normally shut down a terminal and keep a session going online? just leave the terminal open for the duration of session, ensuring that UFW is doing its firewall thing? or what?

casually God-free

---

### Post by jmfal on 2012-07-20
You can close the terminal if you want.

Or  press the "esc" key

That should return you to the command prompt.

---

### Post by godfreezone on 2012-07-20
> **jmfal said:**
> You can close the terminal if you want.

Or  press the "esc" key

That should return you to the command prompt.


Interesting. I tried escape and all i got was:
KeyboardInterrupt
KeyboardInterrupt

so, i go to close it and I get:
" There is still a process running in this terminal. Closing the terminal will kill it."

So I hold off. Just for the learning experience.
?
thx

---

### Post by jmfal on 2012-07-20
Did you install gufw?
I googled it and it shows a gui
Its in software center, synaptic or from terminal:

```
  sudo apt-get install gufw
```

To open gufw from terminal

```
 gufw  
```

---

### Post by godfreezone on 2012-07-20
> **jmfal said:**
> Did you install gufw?
I googled it and it shows a gui
Its in software center, synaptic or from terminal:

```
  sudo apt-get install gufw
```To open gufw from terminal

```
 gufw  
```


Yeah, I did that, opened it successfully, got it running, but then noticed i coudn't close terminal without it generating an error message, as described above

---

### Post by jmfal on 2012-07-20
I don't know never messed with it.
Can you configure it from gui?

---

### Post by c2tarun on 2012-07-20
I think the answer you are looking for is following command:
 
```
gufw&
```

---

### Post by codemaniac on 2012-07-20
> **godfreezone said:**
> Interesting. I tried escape and all i got was:
KeyboardInterrupt
KeyboardInterrupt

so, i go to close it and I get:
" There is still a process running in this terminal. Closing the terminal will kill it."

So I hold off. Just for the learning experience.
?
thx

When you launch a program in the terminal , terminal process is the parent process of the forked gufw process .Hence killing the terminal will kill the gufw process as well .

---

### Post by godfreezone on 2012-07-20
> **c2tarun said:**
> I think the answer you are looking for is following command:
 
```
gufw&
```


thx, tried that, still no action....

    ```
def on_btnAddWindow_clicked(self, widget):
KeyboardInterrupt
^[
^C^Mgufw&   
gufw&
```

puzzled...

---

### Post by codemaniac on 2012-07-20
> **godfreezone said:**
> thx, tried that, still no action....

    ```
def on_btnAddWindow_clicked(self, widget):
KeyboardInterrupt
^[
^C^Mgufw&   
gufw&
```puzzled...

```
gufw&
```

This will put gufw in the background and enable you to continue using your terminal.
  Note that this will still leave gufw as a sub-process of your  terminal, and when you exit the terminal it will also exit gufw .  To  avoid this, type:


```
(gufw &)
```


The parentheses tell the terminal to detach the gufw process from the terminal.

---

### Post by dcsoldschool53 on 2012-07-20
When you run the code```
gufw &
```Did you put a space between the w and the &, because that should have worked.

---

### Post by LordEager on 2012-07-20
Every time you run a daemon through terminal, terminal instance needs to stay open in order to let the daemon run. Usually i make an easy script to launch daemons which i want keep not linked to terminal sessions.
For example in this case you could write in a text file (gedit, kate, nano wheter you prefere):

[B]#!/bin/sh

gufw[/B]

and save it with name like for example UFW_start.

In this way you can launch it just by clicking on and choose run from the dialogue window.

Otherwise if you prefere to launch the bin automatically with pc boot, you can add to 
/etc/rc.local  the line:

**gufw**

which will launch the firewall as X server starts...

Hope it helps.

Note: You can add even all the options you prefere to the script and to the rc.local.

---

### Post by BoogeyOfTheMan on 2012-07-20
There is an easier way to do this, if I am understanding things correctly.

Alt+F2 Opens the Unity launcher run command
type in your command
done

No terminal session to leave open. I used to have a shortcut to the run dialog box in older versions of Ubuntu just for such issues. Mainly back before conky would restart itself if you closed the terminal session.

Anyway, thats how I do it, if there is a reason why you shouldnt do it that way, someone please let me know, lol.

---

### Post by jmfal on 2012-07-21
When you change sessions sometimes you lose the settings.

---

