---
title: "HTML embedded sounds"
date: 2008-06-11
forum: Programming Talk
---

### Post by phenest on 2008-06-11
How do I embed a sound into a web page that does not play until requested? That is, I want to use a sound as a sound effect when an object receives a mouse over event. I can get all this to work, except, when the page loads, the sound is played. I have hidden=true and autostart=false, but it still plays. If I remove hidden=true, it no longer plays on page load, but then I get a playback object appear on the page.

Suggestions please?

N.B. I don't get this problem with IE in Windows, but only with browsers in Ubuntu.

---

### Post by LaRoza on 2008-06-11
Is the code valid and the markup standard?

---

### Post by phenest on 2008-06-12
Even though I can answer 'yes' to both questions, my code may not be the issue.

Through research, I am guessing this is an issue with the Quicktime plugin for Linux. I cannot test it with Firefox in Windows as there appears to be a problem with downloading the Quicktime plugin at the moment.

---

### Post by phenest on 2008-06-12
To elaborate on this: I want to embed a sound that has no visible elements on the web page and does not auto start on page load. It is given an id so I can start and stop it from Javascript. Using the attributes hidden=true and autostart=false inside the embed tag, I can accomplish this. But... only in Windows. In Ubuntu, the sound will autostart if the element is not visible.

The only way I can do this in Ubuntu, is to have the element visible but setting its position to absolute and its width and height to 1 pixel via a style sheet (it's also placed where there is already a png or jpg to ensure it's hidden).

---

### Post by xlinuks on 2008-06-12
I guess the only way to do this so that it works 100% is to use Flash (or Java), if the user has the plugin of course.

---

