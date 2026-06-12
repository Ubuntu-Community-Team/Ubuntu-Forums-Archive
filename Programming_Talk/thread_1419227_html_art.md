---
title: "html art"
date: 2010-03-01
forum: Programming Talk
---

### Post by ebp on 2010-03-01
Hi

I'm experimenting with some html art like this:

[http://leetmachine.endoftheinternet.org/asciitoad/ascii1.html](http://leetmachine.endoftheinternet.org/asciitoad/ascii1.html)

I would like to make an animation of html art, but i don't know how to change the html at certain time inveral or if it even can be done.

Hope you can help. :)

---

### Post by Simon17 on 2010-03-01
You'd probably want to use javascript to change the innerhtml of the <pre>.

---

### Post by ebp on 2010-03-01
I'm now able to change the html:

[http://leetmachine.endoftheinternet.org/asciitoad/ascii2.html](http://leetmachine.endoftheinternet.org/asciitoad/ascii2.html)

but instead of changing to "new text" i would like to load html from another html file.

Also i would like to changed, the changed html. Let's say that the first file is called 1.html, then  i would like that one to change to 2.html and so on. How can that be done?

---

### Post by Simon17 on 2010-03-01
Do you want to load a new page for every "frame", or just store each image in a different file and load them onto the same page instance?

If the first, you can do a javascript redirect using location.replace().

For the 2nd route, you would need to open and read in the file, and do the innerhtml replace thing.

---

### Post by ebp on 2010-03-02
if i go for the second route, how to i load the content from another file?

---

### Post by myrtle1908 on 2010-03-02
> **ebp said:**
> if i go for the second route, how to i load the content from another file?

The JavaScript engine (hosted by your web browser) cannot access the local file system.  You would have to grab the file(s) via HTTP.  This is no good for animation as it will be too slow.

You would be better off storing your frames in local JavaScript Objects or Arrays.  Better still, create your frames on the fly (as they are just ASCII characters).

You can use the setInterval() JavaScript function to set your frame rate.

---

### Post by ebp on 2010-03-06
So it's not possible to change html fast enough?

---

### Post by Hellkeepa on 2010-03-06
HELLo!

Depends entirely upon how fast is "fast enough", and how you write the code. **myrtle1908** gave you at least one way to write the code, so that you can ensure it'll be near instantaneous. Using precaching with AJAX is another method, albeit more complex.

Happy codin'!

---

