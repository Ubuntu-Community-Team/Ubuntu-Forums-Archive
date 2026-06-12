---
title: "Re: Lisp"
date: 2008-07-11
forum: Programming Talk
---

### Post by skeeterbug on 2008-07-11
Wow, I am almost speechless right now. I have been casually looking into LISP for months, and never really understood what the hype was about..

I had some free time at work today, and decided to write a simple test program that prints HTML. My goal was to use a macro, so I could finally understand them better. All I can say is WOW. This is stuff is amazing. My program that was going to have one macro, now how multiple macros (macros calling other macros). Here is what I was working on (it doesn't support attributes - yet):

```

(defmacro html (&body body)
  	`(tag "html" ,@body))

(defmacro body (&body body)
	`(tag "body" ,@body))

(defmacro p (text &body body)
	`(tag "p" ,text ,@body))

(defmacro tag (tagname &optional text &body body)
	`(progn
		(format t "<~A>" ,tagname)
	 	(if ,text (format t ,text))
	 	,@body
	 	(format t "</~A>" ,tagname)))

```

I can create HTML easily by going:
```

(html (body (p "This is a paragraph.")))

```

If a tag isn't supported, the tag macro can be called:
```

(html (body (tag "strong" "This is bold text!")))

```

Since the specific tag macro code repeats itself, I think it would be possible to save all known tags in a list, and loop through calling the tag macro for each item.

This definitely has me hooked. What should a newbie do next? CLOS?

---

