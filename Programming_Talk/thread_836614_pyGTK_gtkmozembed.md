---
title: "pyGTK gtkmozembed"
date: 2008-06-21
forum: Programming Talk
---

### Post by Blice on 2008-06-21
Hi!

So, I've put a mozembed widget into my application, but I'd like to have it so that if a user clicks "submit" on the form in my HTML file, it does something within the python script.

it prints things like "** Message: GetValue variable 1" when I click on stuff- Is there a way to use that to do what I want?

Thanks!

---

### Post by id1337x on 2008-06-21
You should probably use JavaScript for HTML events, anything else will be really hard to implement.

---

### Post by Blice on 2008-06-21
> **id1337x said:**
> You should probably use JavaScript for HTML events, anything else will be really hard to implement.

Well, if anything, I would just have the 'Submit' point to a different .py script with those arguments. I would just rather it all be in the same place.

---

