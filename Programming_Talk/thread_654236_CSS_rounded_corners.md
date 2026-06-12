---
title: "CSS rounded corners"
date: 2007-12-30
forum: Programming Talk
---

### Post by mrblue182 on 2007-12-30
Okay, I have searched all over, and I can't find a solution to my problem, and it is really annoying. I have recently started getting into CSS and web design, but rounded corners are killing me. I have used a LOT of different tutorials, but this one was the one the yielded the best results (that the person who made it got) [http://kalsey.com/2003/07/rounded_corners_in_css/](http://kalsey.com/2003/07/rounded_corners_in_css/) . But, the same thing happened with this one that happened to every other one. the background color over-rides the images, and they don't show up. I attached a picture of what happens (i changed the background-color to red to allow whats happening easily.)

i copied the source code for my page directly from the tutorial, all I did was change the path to the images.

---

### Post by LaRoza on 2007-12-31
There is a thread somewhere on this issue, but the best forum for CSS issues is: [http://cssforums.org](http://cssforums.org)

---

### Post by ThinkBuntu on 2007-12-31
In case you don't have time for my forum (but if you frequently wonder about these sort of things, you should definitely come by), use this link: It generates code instantly for different rounded corners: [http://www.spiffycorners.com/](http://www.spiffycorners.com/)

---

### Post by LaRoza on 2007-12-31
> **ThinkBuntu said:**
> In case you don't have time for my forum (but if you frequently wonder about these sort of things, you should definitely come by), use this link: It generates code instantly for different rounded corners: [http://www.spiffycorners.com/](http://www.spiffycorners.com/)

If the wiki were up....

---

### Post by MadMan2k on 2007-12-31
```
-moz-border-radius: 5px;
```

there is no commonly understood property yet...

---

### Post by LaRoza on 2007-12-31
> **MadMan2k said:**
> ```
-moz-border-radius: 5px;
```

there is no commonly understood property yet...

That is specific to one renderer. Stick with standards.

It is a shame SVG isn't supported well enough in browsers yet.

---

### Post by mrblue182 on 2007-12-31
Thanks for the quick response. I'm going to check out [cssforums.org](http://www.cssforums.org/index.php), and spiffy corners is great!

---

