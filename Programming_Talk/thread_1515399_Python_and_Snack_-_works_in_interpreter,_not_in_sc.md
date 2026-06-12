---
title: "Python and Snack - works in interpreter, not in script. Bizzarre."
date: 2010-06-22
forum: Programming Talk
---

### Post by poetofcode on 2010-06-22
Install python-snack from the repositories (available in Lucid), and then give this quick tutorial a whirl: [http://www.speech.kth.se/snack/man/snack2.2/python-man.html](http://www.speech.kth.se/snack/man/snack2.2/python-man.html)

If the example script is entered into the Python interpreter, when I enter the mysound.play() statement, Python plays the requested file.

However, if I then enter the code into a python script, name it with a .py extension, add the executable bit on the file and run it with a #!/usr/bin/env python shbang at the top, it just runs and exits cleanly.

If I alter the code so to make it break (non-existent filename, mis-spelled function call), then it does break - which means there's nothing wrong with Python's ability to execute the script.

Bizarre, though. Any thoughts?

---

### Post by gmargo on 2010-06-22
How about providing your test code?

---

### Post by poetofcode on 2010-06-22
My test code is the example given on the website I posted to. It's copied verbatim. But, as you wish.

**Edit:** Added some of my own experimental code to the example.

```
#!/usr/bin/env python
from Tkinter import *
root = Tk() # At this point a Tk interface window appears, but only when running in the Interpreter. Running in script doesn't display anything. Worth noting, perhaps.

import tkSnack
tkSnack.initializeSnack(root)

mysound = tkSnack.Sound(load='/home/chris/sound.wav')
mysound.concatenate(mysound) # Will cat' a copy of sound.wav at the end of sound.wav.
mysound.write('/home/chris/newsound.wav') # Will save resulting cat as a file.

mysound.play() # When running in the interpreter, this plays the wav file given. When running in script, it doesn't. Nor does it give any error.
```

Note, the concatenation and consequent output to a file WORKS. So it's not like the statements are being ignored because Tk isn't being imported properly or anything. It just doesn't produce sound unless this code is run inside the Python interpreter.

---

### Post by poetofcode on 2010-06-22
I figured it out. It starts to play the sound with the .play() method, but as it plays in the background (asynchronous?) the program just quits as soon as the last line is executed - halting the playback.

Adding a wait loop of some sorts, or for this basic example, a simple raw_input() prompt allows the sound to finish playing.

Will work this into a GTK mainloop. :)

---

### Post by gmargo on 2010-06-22
According to the link you provided, you can add a 'blocking' option to the play() call to have it wait until the sound is finished.

---

