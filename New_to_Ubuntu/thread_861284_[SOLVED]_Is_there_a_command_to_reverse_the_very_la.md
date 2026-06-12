---
title: "[SOLVED] Is there a command to reverse the very last command?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-07-16
And if so what is it?

---

### Post by ByteJuggler on 2008-07-16
What do you mean "reverse"?  Reverse its effects?  If so, then no.

---

### Post by halitech on 2008-07-16
the simple answer would be no but, if it was something in the terminal, you could hit your arrow up arrow and see what the command is and if it was an install or removing, then just replace it with the opposite.

---

### Post by tribaal on 2008-07-16
There is no specific command to reverse the effects of the previous command.

If the command is not data destructive, you can most certainly revert it using another command - What exactly did you type in?

- Trib'

---

### Post by nothingspecial on 2008-07-16
So if I`ve just moved a load of flac files into a directory that contains a load of flac files already using mv *flac, and I didn`t want them there, I`m going to have to look through what`s in there and mv them back 1 by 1?

---

### Post by markjensen on 2008-07-16
You can probably select the files by date and move them out that way.

Either by console/command or by GUI.

---

### Post by dracayr on 2008-07-16
well I guess you could do sth. with sed and ls -l because the moved flac files probably have a different timestamp (and they probably all have the same timestamp)

EDIT: whoa so. was faster^^

dracayr

---

### Post by nothingspecial on 2008-07-16
Thank the lord. That`s just saved me a few hours.
There`s always a way of doing it.
#-o:-k:oops::lol::lolflag:=D>

edit:and thankyou dracayr to whom, it seems, I cannot give thanks in the normal way.

---

### Post by elmoosecapitan on 2008-07-16
what can also be done is write a very short shell script that takes an array input such as ~/filepath/*.filetype

split/join functions on lists and strings work wonders for tedius tasks.

tcsh, perl, and python work well for that sort of thing.

---

### Post by jimv on 2008-07-16
Yes.

Go buy a dozen candles.
Place candles in a circle around your computer.
Light candles.
Sit cross legged on the floor in front of your computer.
Slowly start chanting these magical words:

"Undo, Undo, Undo, Undo."

Nothing will happen, but by the time you've done all this, the initial shock of your console command gone bad will have subsided.

---

