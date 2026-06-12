---
title: "CSS Apparent width? Or something like that..."
date: 2008-06-03
forum: Programming Talk
---

### Post by Verminox on 2008-06-03
Is there any way to change the 'apparent width' of an element. What I mean is, even though the element should have a real width of say X pixels, it should actually not take up that much spacing for the next element.

Ok, I know I sound confusing, so let's take an example.

```
<span id="one">Hello</span> <span id="two">World</span>
```

This looks like:
```
Hello World
```

However, I want 'World' to be written over 'Hello'. That is, after 'Hello' is printed on the screen, I don't want the browser's 'cursor' to be located at the end of the word, but instead I don't want the 'cursor' to be moved at all. I want the next element to be placed exactly where the previous one was.

I can achieve this by setting a negative margin to #two...

```
#two { margin-left: -40px; }
```

But then the value of negative margin varies as the width of the previous element. I want a solution where I can do this without knowing the width of the previous element. So I want something that can style #one so that it prints normally but doesnt actually move the browser's 'cursor' ahead.

Possible?

---

### Post by odyniec on 2008-06-03
One possible solution is:
```
#one { position: absolute; }
```

You might also experiment with width/float/overflow:
```
#one { float: left; width: 0px; overflow: visible; }
```

---

