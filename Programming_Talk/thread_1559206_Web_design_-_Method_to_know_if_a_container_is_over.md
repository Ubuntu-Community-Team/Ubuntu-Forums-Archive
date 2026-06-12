---
title: "Web design - Method to know if a container is overflown"
date: 2010-08-23
forum: Programming Talk
---

### Post by mickeelm on 2010-08-23
I am designing a Wordpress blog and would like the posts on my main page only to show if there is enough space for it, without overflowing.

I have the property *overflow:hidden* set in my CSS. So, the posts won't show when they come down to the set height of the container, but it gets "cut off" and I'd rather have that last post not showing at all.

So what I would like is

[LIST]
[*]A method in PHP (or JavaScript) that is something like isOverflow() or something, I could then "test" if my post can show without overflowing the page and then choose not to load it if it would "cause overflow".
[*]A method that calculates the height of a container in pixels. Then I could compare this to the total height and only show if if would not cause overflow.
[/LIST]

Any of those would solve my problem.

Any other ideas greatly appreciated as well!

---

### Post by simeon87 on 2010-08-23
This is possible using the jQuery library: [height]("http://api.jquery.com/height/") which is JavaScript.

---

### Post by mickeelm on 2010-08-23
Oh that is awesome, thank you! JavaScript works fine, although if I could get in i PHP that'd be even sweeter. So if you or anyone else knows something for this in PHP, please let me know :)

Anyway, thanks!

---

### Post by soapytheclown on 2010-08-23
dont think so in php cause the dimensions of the users screen wont be known untill the page reaches the users browser, JS would be my best bet for this sort of problem too!

---

### Post by mickeelm on 2010-08-24
With that info - which is also what I've got from all the googling and IRC:ing the past day I'll mark the thread as solved, I did get a javascript solution even if I had wished for php :)

---

