---
title: "jQuery post function"
date: 2009-11-24
forum: Programming Talk
---

### Post by sdlynx on 2009-11-24
If any of you guys have experience with this, I'm having quite a predicament at the moment.  I have a file that uses PHP to dynamically determine how many rows of a certain template to display (determined by MySQL query), and I have jQuery that I want to execute on each template/row.  I want to make all of the jQuery relative (no need for IDs), so that I can implement it in another area.  So far it has been going good but now I have come to a problem:

```
$('.click').click( function() {
$.post("page.php", {data: 'data'}, function(data) {
$(this).slideUp();
});
});
```

The problem is, the "this" on line 3 is not being identified.  Apparently the "this" will not pass through the post function.  How can I solve this, keeping the code relative?

This is the page I am working with: [http://mylifeisnerdy.co.cc/personal2.php](http://mylifeisnerdy.co.cc/personal2.php)
The part of the code that I'm trying to get to work is when you click the submit button I want the .expandComments div to show once data is returned.

Feel free to browse the site if you like ^_^.

---

### Post by korvirlol on 2009-11-25
nevermind... it is 2 am here and i read that wrong ~.~

---

### Post by sdlynx on 2009-11-25
anyway, I figured it out actually

I could just store "this" in a variable right at the beginning of the function;

```

$('.whatever').click( function() {
var theThis = this;
$.post("nothing.php",{}, function(data) {
$(theThis).slideUp('fast');
});
});

```

---

