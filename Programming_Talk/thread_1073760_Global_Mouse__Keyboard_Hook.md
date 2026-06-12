---
title: "Global Mouse / Keyboard Hook"
date: 2009-02-18
forum: Programming Talk
---

### Post by joc85 on 2009-02-18
Is there a way using C, C++ java python or any other language to get a hook on the mouse and keyboard event under linux GNOME or KDE where I can detect if thre hasn't been any motion or keys pressend in a while? Even if my application doesn't have the focus?


Thanks

---

### Post by SusurAce on 2010-02-18
Wow, sorry to piggyback your thread but I was about to ask exactly the same question.  Any ideas would be gratefully recieved

---

### Post by SusurAce on 2010-02-19
This is a bit rough and quick, but here is a basic python-xlib script I came up to show my most successful attempt to date.

It picks up a single button click and tells you its x, y coordinates .



from Xlib import X, display
    
trip = False

while trip == False:
    d = display.Display().screen().root.query_pointer()._data

    #In my case Left down = 256, right down = 1024 and no press = 0
    if d["mask"] == 256:
        print "Left Down"
        print "xpos: " + str(d["root_x"]) + " | ypos: " + str(d["root_y"])
        trip = True
    elif d["mask"] == 1024:
        print "Right Down"
        print "xpos: " + str(d["root_x"]) + " | ypos: " + str(d["root_y"])
        trip = True

---

### Post by spupy on 2010-02-19
You could take a look at the **unclutter** program. It hides the mouse cursor when it is unmoved for some time.

---

