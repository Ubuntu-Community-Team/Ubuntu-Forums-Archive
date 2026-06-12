---
title: "what is the % before a character argument?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by alexebird on 2008-05-27
What does the %x argument to some program where x is some character?

For example, the command:

```
firefox %s
```

---

### Post by catanzag on 2008-05-27
It's a placeholder for the argument of that program. In your example, for instance, when run, firefox starts displaying the page/url you selected.

Hope this can help you

regards

---

### Post by alexebird on 2008-05-27
Thanks for the reply.

So then where do you select the URL?  I don't quite understand how its used.

---

### Post by lisati on 2008-05-27
> **alexebird said:**
> Thanks for the reply.

So then where do you select the URL?  I don't quite understand how its used.

If you saw the "%s" on one of the menus on your desktop, don't sweat it, the "%s" gets filled in by the GUI before starting up firefox. It's a bit like a "system variable". (I like the "placeholder" explanation given by catanzag)

I did see an explanation of "%s", "%e" and the like somewhere a few months back, but the thread title eludes me for the moment..firefox starting up on a strange place was the problem I was researching at the time.

---

### Post by Majorix on 2008-05-27
It has to do with programming. In programming, you use %s as a placeholder for a string, %d for integers, %f for floating point numbers and so on. In your case with Firefox I believe it might be the URL.

---

### Post by KingTermite on 2008-05-27
It's an argument to the program before it (Firefox in this case).

The %s probably stems from programming where many languages use terms like this for arguments and the letter determines the "type" of argument it is (%s is a string, %d is an integer number, etc...). 

Basically it just means there is an argument there and whatever you type next to the command replaces it and is taken as an argument to the program.

So when you type:
firefox [http://www.google.com](http://www.google.com)

You have replaced %s with [http://www.google.com](http://www.google.com), thus [http://www.google.com](http://www.google.com) is the argument.


It would have probably been more easy if they'd written it something like:
firefox <url>

---

### Post by wdaniels on 2008-05-27
> **Majorix said:**
> It has to do with programming. In programming, you use %s as a placeholder for a string, %d for integers, %f for floating point numbers and so on. In your case with Firefox I believe it might be the URL.

In that case, my FireFox is configured to open an unsigned integer :D But, yes it is the same general concept.

I don't think you should see any %s variables though, or at least not according to the [spec]("http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html").

---

