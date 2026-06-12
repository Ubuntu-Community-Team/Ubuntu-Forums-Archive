---
title: "python's wave.readframes()"
date: 2008-06-25
forum: Programming Talk
---

### Post by &amp;)ky#)^ on 2008-06-25
I've been playing around with the wave library in python.  If anyone has any experience with it, could you tell me what in the heck the readframes function returns?  I know it's a string of bytes, but what do those bytes mean?

---

### Post by stuaxo on 2009-10-18
Hi,
  Did you ever find out, also would like to know.

S++

---

### Post by TehBeege on 2009-12-04
Found at [http://coding.derkeiler.com/Archive/Python/comp.lang.python/2004-09/4727.html](http://coding.derkeiler.com/Archive/Python/comp.lang.python/2004-09/4727.html)


Date: Sat, 25 Sep 2004 23:31:10 -0700

 andrea valle <andrea.valle@unito.it> wrote: 
*> *
*>I'm using wave module with success. I'm writing data to wave file.  *
*>Typically I create a list of values (data) and pass it to  *
*>.writeframes(data) methods. *
*> *
*>a = wave.open("/test.wav", "w") *
*>a.writeframes([32000, 0]) *

What version of Python are you using??  On my Win32 Python 2.3, writeframes 
accepts only strings, and only after you have set the frame rate, sample 
size, and number of channels. 

*>But when I use the .readframes() method I don't know exactly what   *
*>values I extract from the open wave. *
*> *
*> >>> a = wave.open("/test.wav", "r") *
*> >>> a.readframes(1) *
*>'\x00\x00' *
*>What does it mean? (hexa?) *
*>How do I convert it to an integer? I'd like to have it like 32000 or 0,  *
*>so to make some maths on it. *

You get back a buffer of bytes.  You can use the array() module to convert 
it to a list of integers. 

-- 
- Tim Roberts, [EMAIL="timr@probo.com"]timr@probo.com[/EMAIL]
  Providenza & Boekelheide, Inc.



I'll edit in a moment to confirm success.

EDIT:: Appears to have worked... 

```

sampleData = array.array('h') #creates an array of ints
# later on...
self.sampleData = file.readframes(file.getnframes())

```

Pretty simple. For some reason, my debugging prints aren't showing up to doubly confirm success. I'll edit again if I get those to work.

---

