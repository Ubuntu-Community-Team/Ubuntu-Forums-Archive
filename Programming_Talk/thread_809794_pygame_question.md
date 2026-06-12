---
title: "pygame question"
date: 2008-05-27
forum: Programming Talk
---

### Post by lapubell on 2008-05-27
I have this rad little game that I am using to teach myself some pygame stuff and have a quick question.  I have been working with a guy that is pretty busy (but very helpful) and wanted to get a quick explanation.  Attached is a tar.gz with the files for the project, and I'm wondering if anyone can help me out.

If you take a look at my code, you will see that I have gone through some tutorials and learned some good stuff for foundational pygame stuff.  The only issues I can't wrap my head around is the keyboard input.  In the main loop I have a check for each button that could be pressed, but this makes me push the button for every move.  I want the player to be able to hold down the direction key and the sprite to keep moving, not wait until the key is pressed again.

If anyone is interested, I have the vision to recreate Donald Duck's Playground (an old dos game) once I get the basics down.

---

### Post by days_of_ruin on 2008-05-27
add this to the top of the main loop```
pressed_keys = pygame.key.get_pressed()
```
replace ```
 if (event.type == KEYDOWN and event.key == K_UP):
```
with ```
if pressed_keys[K_UP]:
```

And do the same with all the keys.:guitar:

---

### Post by days_of_ruin on 2008-05-27
One more thing.Move all that stuff so its NOT nested in the ```
for event in pygame.event.get()
```
It won't work until you do that.

---

### Post by days_of_ruin on 2008-05-27
Actually you don't have to do the part I mentioned in my first post but its
a lot cleaner and might be faster:D

The reason your code wasn't working was because it was nested in the for
loop.So it only executed when a new event happened.

---

### Post by lapubell on 2008-05-27
so I did what you said, and now I know that I am missing just one crucial thing, I just can't figure out the syntax for it...

I liked your list for keys, but please help me out here.  I'm still waiting for that lightbulb to click in my head...

What do I need to call in the for event in pygame.event.get() for it to grab the keys?  Not even the escape key quits anymore...

note: new code attached...

---

### Post by days_of_ruin on 2008-05-27
> **lapubell said:**
> so I did what you said, and now I know that I am missing just one crucial thing, I just can't figure out the syntax for it...

I liked your list for keys, but please help me out here.  I'm still waiting for that lightbulb to click in my head...

What do I need to call in the for event in pygame.event.get() for it to grab the keys?  Not even the escape key quits anymore...

note: new code attached...
You need to call the movement stuff INSIDE the loop.
So it gets refreshed every frame.

---

### Post by lapubell on 2008-05-28
I finally got it!!!

Thanks a million.

---

### Post by Hwoarang on 2008-07-13
> **lapubell said:**
> I finally got it!!!

Thanks a million.

Can you post the final .py cause I am having the same problem?Thanks :)

---

