---
title: "Linux command to replace strings in a line of text?"
date: 2007-01-12
forum: Programming Talk
---

### Post by Trickyphillips on 2007-01-12
I need to be able to replace certain strings in a line of text, and echo it back out to the screen, for a shell script that I'm working on.

Basically, I need something similar to PHP's str_replace(); something that will give this type of effect:```
ubuntu:~$[command name] --replace "Hello, this is a line of text." "Hello" "Goodbye"
Goodbye, this is a line of text.
```

Any simple way to do this? :)

---

### Post by capitalistpiglet on 2007-01-12
What you want to use is sed, [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html) this tutorial should show you what you need.
To change hello to goodbye it would look something like
```
sed 's/hello/goodbye/g'
```

---

### Post by gborzi on 2007-01-12
I'm not sure I have correctly understood what you need, but in case I understood correctly, here is a possible solution > echo "Hello, this is a line of text."|sed -e 's/Hello/Goodbye/'
Goodbye, this is a line of text.
Hope this helps.

---

