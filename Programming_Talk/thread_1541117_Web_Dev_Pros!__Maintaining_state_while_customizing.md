---
title: "Web Dev Pros!  Maintaining state while customizing a product!"
date: 2010-07-28
forum: Programming Talk
---

### Post by era86 on 2010-07-28
I'm having an hard time figuring out how to do this.  Pardon my inexperience!

What I want to do is maintain some sort of product configuration throughout the steps of ordering the product.  Each page is an individual page load, meaning it isn't done via fancy AJAX or anything on one page.  There is a new request and a page refresh for each step.

I have solutions in mind, but I want to know if anyone has had similar experience (professional or hobby) doing something like this.  Here is an example of the behavior:

Widget A has specs Tire, Color, Body, Material.
Each spec has the following options:
    Tire - Smooth, Spiked
    Color - Green, Red, Blue
    Body - Small, Large
    Material - Iron, Steel, Aluminum

On page 1, you select a Tire.  On page 2, you select a Color.  Blah blah.  Now on the last page, you see a summary of your selections.  How is that "configuration" maintained throughout the first couple of pages up until the end?

I can A) store the configuration in the session or B) propagate the configuration through in the URL via GET variables.

If anyone else has any other ideas, or likes one of the solutions above, please let me know.

Thank you so much in advance.
:popcorn:

---

### Post by myrtle1908 on 2010-07-28
> **era86 said:**
> 
I can A) store the configuration in the session or B) propagate the configuration through in the URL via GET variables.


Either method is fine however with option B you can more easily create a link direct to a certain product combination.

That said, full page loads for something so trivial are an annoyance for the user so you should investigate going the single-page route using AJAX etc.

---

### Post by shadylookin on 2010-07-28
you could use cookies that expire quickly.

---

### Post by worseisworser on 2010-07-29
> **era86 said:**
> I'm having an hard time figuring out how to do this.  Pardon my inexperience!

What I want to do is maintain some sort of product configuration throughout the steps of ordering the product.  Each page is an individual page load, meaning it isn't done via fancy AJAX or anything on one page.  There is a new request and a page refresh for each step.

I have solutions in mind, but I want to know if anyone has had similar experience (professional or hobby) doing something like this.  Here is an example of the behavior:

Widget A has specs Tire, Color, Body, Material.
Each spec has the following options:
    Tire - Smooth, Spiked
    Color - Green, Red, Blue
    Body - Small, Large
    Material - Iron, Steel, Aluminum

On page 1, you select a Tire.  On page 2, you select a Color.  Blah blah.  Now on the last page, you see a summary of your selections.  How is that "configuration" maintained throughout the first couple of pages up until the end?

I can A) store the configuration in the session or B) propagate the configuration through in the URL via GET variables.

If anyone else has any other ideas, or likes one of the solutions above, please let me know.

Thank you so much in advance.
:popcorn:

I'm pretty sure using both methods is needed in almost all cases regardless of whether AJAX or "plain old Web 1.0" is used. At least if your goal is to be able to link to some state; if not, then just using method A is enough. 

If using AJAX, the "hash-part" of the URL can be used to store data just as the query-string part of the URL usually is in the "Web 1.0" case.

There's always some data which is more relevant to the *current session*, and less interesting for when one want to link to some particular state.

---

### Post by Some Penguin on 2010-07-29
You can also write servlets which handle a request, modify its parameters (including setting objects) and forward to a JSP.

---

### Post by era86 on 2010-07-29
Thank you all for the replies.  I'd really like to completely redesign the site to avoid the "Web 1.0" style, however, I am not in a position to argue with the designer...

Though, I have a question about session passing.  When I insert a key/value in the session, does it propagate throughout the page?  For example, if I store the config for Widget A in the session and decide to start over by navigating away (or to the first page), is there an elegant way to clear the session?  Should I store the page of each step in the session?  Do I wipe out the session from the server for every page but the config steps?  Is this elegant enough or more trouble than its worth?

Also, passing the variables in GET variables might not work since I'd like to hide the details of the config from the URL (SEO crap that really doesn't make sense if your customizing a product, but whatever).

I guess these are very vague questions which will warrant very vague answers.  I just don't want to expose too much of the actual problem because it is information sensitive.  I can't seem to find any good examples for the "Web 1.0" style of product configuration that I'm trying to implement.

I did however find a solution that might work:

C) Propagate the configuration as a string through a hidden form and POST method.  This would allow me to hide the configuration from the user by passing it via POST.  It would also wipe the state should the user navigate away.  I wouldn't want Widget B configuration information when I go to Widget A's page.

Meh... Thanks again for all the suggestions/affirmations!

---

