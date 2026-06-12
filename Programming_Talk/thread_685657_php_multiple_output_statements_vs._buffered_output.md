---
title: "php: multiple output statements vs. buffered output"
date: 2008-02-02
forum: Programming Talk
---

### Post by RocketRanger on 2008-02-02
Hi

Which is more efficient, buffering all html output in a variable and echoing the variable at the end of the php file or using a single output statement for each line of output? Or maybe using the output buffering function build into php.

---

### Post by anbumanij on 2008-02-06
Use array for buffering and to output the file. by

echo "<pre>";
print_r (array);
echo "</pre>";

---

### Post by deuce868 on 2008-02-07
output buffering is shown to have some speed improvements. It can sometimes complicate things. If everything is in a buffer and an exception is thrown, do you catch the exception and dump the buffer? If not, then you might never see any output and think the script is doing nothing. 

I use output buffering nearly all the time, but you have to be aware of the side effects.

---

### Post by DrMega on 2008-02-07
Output buffering is good, but beware of the following:

1. If your page is going take a while to render (lots of DB activity for example), then there is a an increased risk that the client browser will timeout before you page has set off.

2. Related to 1, your user won't see anything until you flush the buffer.

---

### Post by michaelzap on 2008-02-07
Speed-wise I don't think that buffering your output versus outputting as you generate it makes any difference to the user (PHP scripts should usually be executed in a second or less, and then the page is sent to the client's browser). In terms of program flow, I think that it's better to have only one exit point per function or script, so I always buffer and output at the end. If I need to debug a script, then I'll add echo code along the way.

There are probably benchmarks out there comparing these two methods, so you could search for them if you're really interested, but I imagine that they'd vary depending upon the amount of code that you're buffering and your system resources.

Caching pages or parts of pages that don't need to be dynamically generated every time and compressing the files that you send to browsers definitely makes a difference, however.

---

### Post by deuce868 on 2008-02-07
Link with some speed differences
[http://planetozh.com/blog/2006/05/speeding-things-with-php-output-buffer/](http://planetozh.com/blog/2006/05/speeding-things-with-php-output-buffer/)

Most show a 5-15% difference using ob. In the end, ob gets you more flexibility than anything though. 

One of the things we use a lot is to buffer the output and if a horrible error is thrown we can change to a nice pretty error page and there's no messy output we're in the middle of dumping to the page.

---

### Post by RocketRanger on 2008-02-07
So what I'm getting from this is that ob is a better solution with regards to speed and implementation at the cost of a bit more planning in the design and build phase.

---

### Post by aks44 on 2008-02-07
In addition to what has been said: the main problem with OB is that it requires more memory (so it is way less scalable on servers that have to handle heavy load).

---

