---
title: "signal ordering with gtk"
date: 2008-12-07
forum: Programming Talk
---

### Post by Tony Flury on 2008-12-07
Is there a documented description of the order in which signals are triggered when one widget looses focus and another one gains focus (or in fact is clicked).

I have a text entry widget and and a toolbar button, and i need to process the information in the text entry widget before executing the button press. I thought i could use the focus-out-event to trap when the user moves away from the text entry to the button, but it seems that the focus-out event on the loosing widget fires after the "clicked" on the button and not before, so that wont work.

I know i could process the entry field in the button clicked event, but I would prefer to handle the entry in a discrete event associated with the entry field.

Is there another signal I could use on the entry field.

---

