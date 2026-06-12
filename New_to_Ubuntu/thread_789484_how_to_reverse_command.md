---
title: "how to reverse command"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by fignig on 2008-05-10
anyone know how to do things in reverse? like an undo command?

---

### Post by Joeb454 on 2008-05-10
I don't think you can if you've run it from the command line.

The CLI assumes you know what you are doing, so it won't usually ask a question (unless you tell it to).

What command did you run?

---

### Post by Journeyman on 2008-05-10
You can cycle through the commands you have run but hitting the UP key in the terminal, it doesn't undo anything.  Not sure if this helps you or not, but it could be useful.

---

### Post by fignig on 2008-05-10
> **Joeb454 said:**
> I don't think you can if you've run it from the command line.

The CLI assumes you know what you are doing, so it won't usually ask a question (unless you tell it to).

What command did you run?

i ran a few, but i think:

sudo apt-get install soundconverter oggconvert

did it. i can't hear anything in any website, but i can hear music thru rhythmbox.

---

### Post by fignig on 2008-05-10
> **Journeyman said:**
> You can cycle through the commands you have run but hitting the UP key in the terminal, it doesn't undo anything.  Not sure if this helps you or not, but it could be useful.

that's probably the stupidest response ever...has nothing to do w/ what i said...

---

### Post by Monicker on 2008-05-10
> **Journeyman said:**
> You can cycle through the commands you have run but hitting the UP key in the terminal, it doesn't undo anything.  Not sure if this helps you or not, but it could be useful.

Typing history at the terminal will also show your most recent commands.

You can even repeat a command prefixing the history number with !

```

history

  560  man zip
  561  ls
  562  vi foo.php
  563  locate vimrc


!562
```


The !562 will repeat the "vi foo.php" command.

---

### Post by spiderbatdad on 2008-05-10
> **fignig said:**
> that's probably the stupidest response ever...has nothing to do w/ what i said...
:confused:

---

### Post by Monicker on 2008-05-10
> **fignig said:**
> that's probably the stupidest response ever...has nothing to do w/ what i said...

How is that stupid???

Often times people may not remember exactly what they typed previously.  Being able to go back and determine exactly what it was is a good thing, in my opinion.

---

### Post by HarryTruman on 2008-05-10
Fignig, it's an embarrassing representation of these forums to see your disrespectful responses highlighted in more than one post -- on the front page.

---

### Post by fignig on 2008-05-10
> **HarryTruman said:**
> Fignig, it's an embarrassing representation of these forums to see your disrespectful responses highlighted in more than one post -- on the front page.

it's hard to get a straight up answer from anyone on these forums, if ppl are that stupid, then i have to post twice to get a single answer..

---

### Post by Journeyman on 2008-05-10
have you tried uninstalling the programs

```
apt-get autoremove soundconverter oggconvert
```

---

### Post by HarryTruman on 2008-05-10
> **fignig said:**
> it's hard to get a straight up answer from anyone on these forums, if ppl are that stupid, then i have to post twice to get a single answer..
Asking a general question and expecting a specific response can do that.  Provide more details so people can get a good idea of what you're wanting to do.

But to answer your question: no.  There isn't a way to undo a command that has just been entered.  That's why you see a lot of guides recommending you make backups of files before they are edited -- so if something *is* messed up and needs reverted you can simply replace the changes you made.

---

### Post by fignig on 2008-05-10
> **HarryTruman said:**
> Asking a general question and expecting a specific response can do that.  Provide more details so people can get a good idea of what you're wanting to do.

But to answer your question: no.  There isn't a way to undo a command that has just been entered.  That's why you see a lot of guides recommending you make backups of files before they are edited -- so if something *is* messed up and needs reverted you can simply replace the changes you made.

so you make backups before every command in the terminal? i didn't think so either...but i was trying to fix the video, and apparently messed up the sound in the process..

---

### Post by kansasnoob on 2008-05-10
fignig,

I'm too stupid to help you!

Try Judge Judy!

---

### Post by inportb on 2008-05-10
Gee, what's with the attitude? You're the one looking for help and being ambiguous. Think before posting next time.

---

### Post by llamakc on 2008-05-10
> **fignig said:**
> that's probably the stupidest response ever...has nothing to do w/ what i said...

Completely uncalled for.

---

### Post by llamakc on 2008-05-10
> **fignig said:**
> so you make backups before every command in the terminal? i didn't think so either...but i was trying to fix the video, and apparently messed up the sound in the process..

Why would you have installed sound programs to fix video?

And while you can not 'undo' or 'reverse' a command, you can issue a command that 'may' correct things.

In this case, if you noticed the problem AFTER installing those two programs, uninstall them (through either apt-get or Synaptic).

---

