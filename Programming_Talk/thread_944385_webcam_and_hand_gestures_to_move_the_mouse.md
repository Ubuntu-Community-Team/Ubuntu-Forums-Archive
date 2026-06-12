---
title: "webcam and hand gestures to move the mouse"
date: 2008-10-11
forum: Programming Talk
---

### Post by mcai8sh4 on 2008-10-11
Here's what I'm doing.... look down for my problem.

I'm using handvu to track the movment of my hand and recognise gestures... all works well, I'm certainly not a programming guru so I want to do a simple bash move the mouse pointer from the output of handvu.
Here's the plan... Handvu sets us a telnet server displaying usefull information. I want to grab that info, monkey around with it (sed awk whatever) then use that information to move the mouse cursor around (using xte or somthing similar). The main point is I want to use the telnet info to then do somthing.

For this to work I need a way to grab each line from the telnet server and store it as a var.

As I mentioned, my plan (purely as a POC) is to script this in bash.

If I use ```
nc localhost 7045
```
Then it just keeps streaming all the data - I just want one line.

I've tried ```
data=$(nc localhost 7045 &)
```
but then the $data doesn't seem to alter.

Is there a way to just grab the current line OR have a variable constantly update to the current output of the telnet server?

Any thoughts would be appreciated.

Best regards,

Steve

---

### Post by lswb on 2008-10-11
That seems like a neat project. Have you considered redirecting the output from netcat to a file or perhaps to tail ?

---

### Post by mcai8sh4 on 2008-10-11
I've thought of nc localhost 7045 & > file but I'd rather just have a variable constantly update, then I could pass the coords to xte to move the mouse.

I've tried a number of things - even if I could get the output to update a variable about twice a second would work for a simple demo.

I'm sure it's easy to do, I should try and alter the output of the program so it doesn't go through telnet, but I'm just trying to work with what I've already got.


OOOOHHHHHHHH you might have somthing there!!!!!!
```
 data=$(nc localhost 7045 | head -1) 
```

will just pull the current output!!

Thanks for the thought, it's been driving me mad.
I'll see how well that works.

Thanks again

---

### Post by mcai8sh4 on 2008-10-11
all seems to work!!

It's of no use at all, and difficult to control, but I can move my mouse just using my hand floating around in the air!

If I could get it smoother and more accurate then I suppose it could have a use, but I think thats out of the relms of using a bash script to add functionality to an amazing program.

Anyone wanting to play, have a look at handvu!!! And if you can do a decent little app (mainly to show off) please let me know.

-Steve

---

### Post by Rich78 on 2008-10-11
Handvu site isn't rendering, do you have a direct link to the source etc?

---

### Post by mcai8sh4 on 2008-10-11
try this - I had difficulties this morning getting the source

[http://www.movesinstitute.org/~kolsch/HandVu/HandVu.html](http://www.movesinstitute.org/~kolsch/HandVu/HandVu.html)

---

### Post by Rich78 on 2008-10-11
Thanks, that site wasn't coming up before but it seems fine for the moment.  I'm guessing it's just a little popular at the mo.

---

### Post by mcai8sh4 on 2008-10-11
no problem! I hope it does get busy - I want to try some of the things that people who know what they're doing have achieved. 

:)

---

### Post by Mister.Vash on 2008-10-13
That handvu like an interesting program - I see the last update on their page from back in 2006 - is it still being developed?  Anyone know of any other hand gesture programs?  Not trying to threadcap, just was wondering if the author or anyone has checked any other ones out.

---

### Post by tomchuk on 2008-10-13
This is an alternative to what you have, as the command you have is reading the entire buffer and throwing away all but the first line. This is assuming that what you're doing with each line can keep up with how many lines are being sent. If it can't your way is probably best, as the mouse won't be lagging behind handvu.

```

#!/bin/sh

nc localhost 7045 | while read $data # read into data one line at a time
do
  #something with $data
  echo $data
done

```

---

### Post by mcai8sh4 on 2008-10-13
Mister.Vash : This is the only program I've seen where the you can download/try/use/improve. I just stumbled across it and thought I'd have a play around. I would like to find more projects like this.

Tomchuk : I like the thinking, thats one method I have not tried. My problem was netcat/telnet etc continued running. The 'head' method solved this. There is no way I can keep up with the amount of data (at least no on this laptop - old). 

My script (albeit very badly written) does work, but it is slow. I expected that, as mentioned earlier, this is not the best way of achieving my goal - but it's the only way I know how.

Thanks - Steve

---

