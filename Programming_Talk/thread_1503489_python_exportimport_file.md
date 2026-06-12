---
title: "python export/import file"
date: 2010-06-06
forum: Programming Talk
---

### Post by werecatomega on 2010-06-06
Hey guys,
lets say i wanted to make a game that uses a save file (i.e. exports save to "save.txt" and imports it again). How would i do that?

---

### Post by Axos on 2010-06-07
The most basic way to read and write files is introduced in the tutorial. Click the link corresponding to the version of Python you are using.

2.x: [http://docs.python.org/tutorial/inputoutput.html](http://docs.python.org/tutorial/inputoutput.html)
3.x: [http://docs.python.org/py3k/tutorial/inputoutput.html](http://docs.python.org/py3k/tutorial/inputoutput.html)

---

### Post by Tony Flury on 2010-06-07
Since the data is unlikely to be just strings, and to save yourself the trouble of having to parse the data etc, look at using pickle.

---

### Post by DanielWaterworth on 2010-06-07
Well, there are a number of things to think about; foremost, what do you want to save? Is it acceptable to be saved in plain-text? Lastly, what format will you use, will you use a standard library like Pickle or json, or will you design your own?

Honestly though, seeing as your asking this question, it's likely that the project that your dreaming of is too difficult for you at this moment in time. Think simpler, make pong and have fun [=

---

