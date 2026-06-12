---
title: "[SOLVED] PHP: Warning: Unexpected character in input: ''' (ASCII=39)"
date: 2008-12-30
forum: Programming Talk
---

### Post by secondstage on 2008-12-30
The full error output is...
```
Warning: Unexpected character in input: ''' (ASCII=39) state=1 in /var/www/test.php on line 3

Parse error: syntax error, unexpected '<' in /var/www/test.php on line 4
```

The test.php code is a simple print '...'; command. With allot of escaped single quotes, and even more double quotes. Any idea on what it might be?

---

### Post by catchmeifyoutry on 2008-12-30
If the code is just
```

print '...';

```
why would you need to escape ' characters?

---

### Post by secondstage on 2008-12-30
The ... inside the quotes represented something that is continued, or something that is exempted to save space. That is the purpose of ellipses("..."). Sorry if I was misunderstood.

---

### Post by catchmeifyoutry on 2008-12-30
Maybe you could publish the complete code (or line + surrounding lines) here?
Please use the [CODE] or [PHP] tags to format the code in the forum.

---

### Post by secondstage on 2008-12-30
I am terribly sorry for this, but I managed to forget the end quote, and semi-colon. I am sorry to have wasted your time, and effort (along with this server's storage).

Sad thing is that now, I have to escape a whole bunch of "\'" (without the double quotes). I would use str_replace, but only some are meant to come out as \'. (JavaScript output ex. "<p onMouseOver="function(\'value\')">Word</p>" must be escaped in PHP)

---

### Post by catchmeifyoutry on 2008-12-31
> **secondstage said:**
> I am terribly sorry for this, but I managed to forget the end quote, and semi-colon. I am sorry to have wasted your time, and effort (along with this server's storage).

Don't worry about it ;) I'm replying out of, what appears to be, free will.

> **secondstage said:**
> 
Sad thing is that now, I have to escape a whole bunch of "\'" (without the double quotes). I would use str_replace, but only some are meant to come out as \'. (JavaScript output ex. "<p onMouseOver="function(\'value\')">Word</p>" must be escaped in PHP)

If your php quotes are ", then you can use mostly single ' quotes for the html tags, and only escape double quotes for javascript strings.
[PHP]
echo "<p onMouseOver=\"function('value')\">Word</p>";
echo "<p onMouseOver='function(\"value\")'>Word</p>";
[/PHP]

Probably you're already doing that, and your problem arises from javascript strings that must be escaped inside javascript.
In that case I would suggest to take a more maintainable approach to web programming, try "unobtrusive javascript":
[http://en.wikipedia.org/wiki/Unobtrusive_JavaScript](http://en.wikipedia.org/wiki/Unobtrusive_JavaScript)
[http://www.onlinetools.org/articles/unobtrusivejavascript/](http://www.onlinetools.org/articles/unobtrusivejavascript/)

Which becomes ridiculously easy with, for example, jQuery ([http://jquery.com/](http://jquery.com/)).

Just add an extra file containing all your javascript event handlers and remove the inline statements in the tags. For example:
[PHP]
/// site.js
$(document).ready(function(){

  $('.MyClick').hover(function () {
     funcFooBar('value with a \'string of " \'!!!');
  })
  ...
}
[/PHP]

Hope you get the idea.
And a happy new yea

---

### Post by secondstage on 2008-12-31
Good points. jQuery is something that I'll have to look into. I am only knee deep right now, because I just starting using JavaScript within the last week. (PHP for the last 3 months, HTML&CSS for 6).

---

