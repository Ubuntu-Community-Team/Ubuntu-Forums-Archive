---
title: "PHP Mysqli how to detect field too big?"
date: 2010-05-31
forum: Programming Talk
---

### Post by skkeeper on 2010-05-31
Is there a way to use Mysqli to detect if the data going into a field exceds its limits? Right now when I insert a data with (lets say) 25 characters into a VARCHAR(20) it just cuts the string out.

I'm extending the mysqli class so I can parse the errors into exceptions. This is really making my job kinda useless if i need to check the size of the fields by hand.

---

### Post by escapee on 2010-05-31
Well if you're extending it, upon update or insert check the length of the field vs the length of the input.  If your input is larger than the field, trigger an exception.  Since MySQL truncates by default, no warning or error is triggered.  For performance sake, I recommend caching the size of each field in an array upon connection and update on any table alteration.

I know it's not what you're looking for, but it isn't necessarily a bad solution.

---

### Post by skkeeper on 2010-06-01
Thanks that actually a good idea.

---

