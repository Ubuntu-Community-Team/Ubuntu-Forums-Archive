---
title: "[Curses][Python] getch() won't stop outputted text from whizzing by"
date: 2009-06-05
forum: Programming Talk
---

### Post by fiddler616 on 2009-06-05
Hello,
Since school just let out, I thought I'd make a larger-than-usual Python program, since I feel myself getting too Javafied (curse you, College Board).

I decided to make a terminal-based Twitter client, so I could also poke around with XML-based APIs (which I've worked with a little bit, but not enough to my liking), and curses.

A previous [discussion]("http://ubuntuforums.org/showthread.php?t=1088234") told me (and they were right, it worked at the time) that to make text displayed on the screen readable stay there, I had to call stdscr.getch(), and then curses.endwin() to restore the terminal to a usable state. However, that's not working out now. Since I'm using windows this time, I also tried calling getch from them (as opposed to stdscr), but I get the same problem.

I know the text is being properly added through judicious use of time.sleep(), but after it's done sleeping the text disappears and all I get is a blinking cursor (presumably getching).

How do I fix this?

Thanks.

---

### Post by nvteighen on 2009-06-05
Weird, really weird. Could you please post some code... if it's too long, try creating a smaller test unit that shows the same issue.

It should work, unless something else is interferring with curses's behaivor.

---

### Post by yaroto98 on 2009-06-05
Just pipe it through more or less.

j/k, post the code.

---

### Post by fiddler616 on 2009-06-05
[PHP]
import curses as c
stdscr = c.initscr()
#c.noecho() #This was so that the user doesn't have to press <Enter> when inputting things, but I commented it out in case it was affecting anything.
c.cbreak()
stdscr.keypad(1)

def getTweets():
    return "A whole bunch of tweets will go here.\nThey will span multiple lines and generally be awesome.\nWoo!!!!!"

def getInput():
    return "Input a tweet here."

def getReplies():
    return "Mr_spam: @timmymacdonald Hello World!\nMr_eggs: @timmymacdonald A rather long sentence here. Hopefully it word wraps. I wonder if I've exceeded the 160 character limit."

def displayPanel():
    return "Refresh | Account | Follow | Unfollow | Search"

tweets = c.newwin(22, 40, 1, 0)
input_box = c.newwin(6, 40, 1, 41)
replies = c.newwin(16, 40, 7, 41)
panel = c.newwin(1, 80, 24, 80)

tweets.addstr(getTweets())
input_box.addstr(getInput())
replies.addstr(getReplies())
panel.addstr(displayPanel())
tweets.refresh() #Originally I had a generic "refresh()" here: would that also work?
input_box.refresh()
replies.refresh()
panel.refresh()
import time as t; t.sleep(5)#Debugging

#Clean up terminal
stdscr.getch()
#When that didn't work, I added:
tweets.getch()
c.endwin()
[/PHP]
Obviously the functions will be a bit more involved, but I want to get curses working before I start with the Twitter API. And I'll also make more of an effort with docstrings, etc.

(Wow, that wasn't fun retyping (I'm coding on an old 300mHz Thinkpad that doesn't have an internet connection (so no copy and pasting))

---

### Post by nvteighen on 2009-06-06
The issue is **stdscr.getch()** :) Think about it: that window is there running at the background, so it makes no sense to try to make it get a character... You just need to use whatever window you're effectively using.

In C, you would use **int wgetch(WINDOW *)**, not **int getch(void)**, which is always referred to stdscr.

This worked for me:
```

import curses as c
stdscr = c.initscr()
# c.noecho() This was so that the user doesn't have to press <Enter> when
# inputting things, but I commented it out in case it was affecting anything.
c.cbreak()
stdscr.keypad(1)

def getTweets():
    return """A whole bunch of tweets will go here.\nThey will span multiple
    lines and generally be awesome.\nWoo!!!!!"""

def getInput():
    return "Input a tweet here."

def getReplies():
    return """Mr_spam: @timmymacdonald Hello World!\nMr_eggs: @timmymacdonald A
    rather long sentence here. Hopefully it word wraps. I wonder if I've
    exceeded the 160 character limit."""

def displayPanel():
    return "Refresh | Account | Follow | Unfollow | Search"

# Careful: avoid absolute values. I'm not sure how to do this in Python... in C,
# you'd use the globals COLS and LINES after initscr().
tweets = c.newwin(22, 40, 1, 0)
input_box = c.newwin(6, 40, 1, 41)
replies = c.newwin(16, 40, 7, 41)
panel = c.newwin(1, 80, 24, 80)

tweets.addstr(getTweets())
input_box.addstr(getInput())
replies.addstr(getReplies())
panel.addstr(displayPanel())
tweets.refresh() # Originally I had a generic "refresh()" here: would that also
                 # work?
input_box.refresh()
replies.refresh()
panel.refresh()

tweets.getch()
c.endwin()

```

---

### Post by fiddler616 on 2009-06-06
> **nvteighen said:**
> The issue is **stdscr.getch()** :) Think about it: that window is there running at the background, so it makes no sense to try to make it get a character... You just need to use whatever window you're effectively using.

In C, you would use **int wgetch(WINDOW *)**, not **int getch(void)**, which is always referred to stdscr.

Oh, that makes sense. Good call, thanks.
*Thanks nvteighen, then marks thread as solved* (I really miss those features) Dang.

And is [this]("http://www.amk.ca/python/howto/curses/curses.html#SECTION000600000000000000000") all I need to know for input? It seems kind of...short, but I guess there's not that much involved, and I should be happy.

---

