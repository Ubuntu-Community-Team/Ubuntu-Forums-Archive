---
title: "Try Ruby Online! web app broken"
date: 2008-04-21
forum: Programming Talk
---

### Post by danbuter on 2008-04-21
I tried the Ruby Online! thing listed in LaRozza's sig for the heck of it. I was kinda disappointed when I found it was broken. In book 2, after changing toast to honeydew, the poem sticks at toast and will not let me continue the tutorial. There are no Ruby forums that I can find, so I figured I'd post it here and hopefully the message will get back to the maintainer of the site. It's a really neat little program, and this is unfortunate.

---

### Post by mssever on 2008-04-21
If you do a ```
sudo aptitude install ruby irb
```you'll have a full Ruby available from your terminal just by typing irb.

If you show your code, then I can probably help you figure out what's wrong.

---

### Post by danbuter on 2008-04-21
This is a web browser contained tutorial. Ruby is not required to be installed to use it. It's more of a way to introduce curious people to the language easily. I think it's a really neat idea, and would just like for the person who made it to be notified so it can be fixed. There is no contact info on that site, or I would have done it.

---

### Post by a9bejo on 2008-04-21
"Try Ruby" was made by the great [http://en.wikipedia.org/wiki/Why_the_lucky_stiff](http://en.wikipedia.org/wiki/Why_the_lucky_stiff) , a hacker who  wrote a lot of great software for Ruby (for example  [Shoes](http://code.whytheluckystiff.net/shoes/), [Hpricot](http://code.whytheluckystiff.net/hpricot/), [Camping](http://code.whytheluckystiff.net/camping/) or [RedCloth](http://whytheluckystiff.net/ruby/redcloth/)). The one problem with _why is that he seems to lose sight of his past projects a bit once he moved on to something new.

You can try to  contact him at  [ why AT whytheluckystiff DOT net ].

Btw: You will find the various ways to get in touch with the Ruby Community at [http://www.ruby-lang.org/en/community/](http://www.ruby-lang.org/en/community/) .

---

### Post by shroomcmn on 2008-11-14
Maybe has to do with caching.  I was able to workaround it by using different syntax for the second print statment.  (I added parentheses)
```
print(poem)
```

---

