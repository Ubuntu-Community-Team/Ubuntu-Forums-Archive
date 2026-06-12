---
title: "Count individual tag occurrences"
date: 2007-06-01
forum: Programming Talk
---

### Post by Samjiman on 2007-06-01
Hi, guys.

I'm having a problem with a function I have defined to match every second occurrence of a tag - e.g. every second occurrence of <b>.

I have this JavaScript code:

```

// match closing tags - e.g. second <b> = </b>
re = new RegExp(rpStr, "g");
etag = msg.match(re);
if(etag != null)
{
   tag = etag;
   pos++;
   // output to Firebug log
   console.log("--------------------");
   console.log("All matches: " + tag);
   console.log("Array: " + tag.length);
   console.log("Second: " + tag[1]);
   console.log("Fourth: " + tag[3]);
   console.log("Test:"+ tag[pos] + " (" + pos + ")");
   //-
}
ctag++; // increment (outer) loop, 
//which changes which tag etag refers to

```

Problem is that I want to find each occurrence for an individual tag before progressing on to checking the next. What do I have to change here to do that? Any help is greatly appreciated. This has been bothering me for ages. Thanks. :D

BTW [here is a screenshot of the output I get in the Firebug console ]("http://img365.imageshack.us/my.php?image=vbcodedebugnq1.png").

---

### Post by pmasiar on 2007-06-01
Python and elementTree might simplify your task a lot - will parse your XML into something useful.

---

### Post by Samjiman on 2007-06-01
Appreciate the advice. But I am writing a [Firefox extension]("http://vbox.mozdev.org") and as such have to use a language supported by the Mozilla Framework - so far development with JavaScript has been smooth. I don't really want to switch language at this point. 

I'm sure its possible what I want to do with JS, just need some pointers. Thanks anyway. I'll learn Python while I wait for an answer.

---

### Post by Samjiman on 2007-06-02
I've fixed it. Turns out I just had to use a for loop, rather than a while.

---

