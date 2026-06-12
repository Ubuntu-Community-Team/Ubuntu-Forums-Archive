---
title: "Help with Python strings"
date: 2010-10-19
forum: Programming Talk
---

### Post by Yes on 2010-10-19
I don't have any experience at all in Python, so please excuse me if I'm going about this the totally wrong way, but what I need to do is find the current volume of Alsa's master channel.  Here's what I have so far:

```
 f = os.popen ("amixer -c 0 set Master 0dB+")

    counter = 0
    
    for i in f.readlines ():
        counter += 1
        if counter == 5:
          vol_line = i
    
    start_s = vol_line.find ("[", 0, 50)
    end_s = vol_line.find ("%", 0, 50)
    
    start_i = int (start_s)
    end_i = int (end_s)
    real_vol = vol_line [start_i, end_i]
    print real_vol
```

And I get the error

```
File "vol.py", line 117, in main
    real_vol = vol_line [start_i, end_i]
TypeError: string indices must be integers, not tuple
```

So I have no idea what I'm doing wrong... as far as I can see, I convert the tuple start_s and end_s into an int with the int () function, but I guess that's not happening?

If you can please help, thanks!

---

### Post by wmcbrine on 2010-10-19
The tuple is the new one you created, right there in that line that's quoted in the error message. Assuming you're going for a substring there, the correct syntax would use a colon, not a comma:

real_vol = vol_line [start_i:end_i]

Also, your int() lines are unneeded -- start_s and end_s are already ints.

---

### Post by Yes on 2010-10-19
Oh, that makes way more sense.  I thought it was odd find () didn't just give me an int, thanks very much!

---

