---
title: "Java change GUI when button clicked"
date: 2011-04-19
forum: Programming Talk
---

### Post by dominatorv8 on 2011-04-19
Hi guys, I was wondering if someone could help me out with this. For a bit of a project im building a calculator using Java basically I want to be able to change the GUI and action listeners when a button is clicked. The same way if you want to switch between basic and scientific modes. How would i go about doing this, should i have the layouts of the calculator under differnet methods or is that even possible. 

P.s I dont want any code as i want to do this on my own just a nudge in the right direction

Thanks 
Paddy

---

### Post by r-senior on 2011-04-22
Do you need to change the listeners? I would have thought the listener would be the same for a '+' key or a '%' key regardless of mode?

I'd be thinking of laying out the controls on multiple panels and hiding/showing those panels, probably using a CardLayout?

---

### Post by dominatorv8 on 2011-04-24
Thanks for your reply, I was thinking of having multiple frames and hiding them and making them reappear when a button was clicked though I found a easier way in my opinion. 
     I removed everything from the container, then I had to invalidate the container, re-draw the new layout then validate the container and it worked :)

but I think ill have a look into CardLayout anyway thanks

---

