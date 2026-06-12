---
title: "sed to replace spaces in quotation marks"
date: 2016-12-01
forum: Programming Talk
---

### Post by peter_brickles on 2016-12-01
I have a file containing a long passage of text as follows 
  an excerpt from the file is 

> Mother cooked eggs for them, and they ate their breakfast  hungrily. " It's lovely to be in the country! " said Jo,

How i would like to to read 

> Mother cooked eggs for them, and they ate their breakfast hungrily. "It's lovely to be in the country!" said Jo,

Is theres any way to achieve this using sed or any other cli tool ? 

any help would be appreciated

---

### Post by TheFu on 2016-12-01
"Any way?" Yes. That is very different from "a simple way."

Sure, you can perform pattern matching on almost anything. The hard part is making sure that it matches **only** the pattern you want and no others.  Basically, you need to build a grammar to make this a general solution, since the computer needs to know if 
> lovely to be in the country! " said Jo, 
should be 
> lovely to be in the country!" said Jo,
or
> lovely to be in the country! "said Jo,
It is a non-trivial problem in the general case.  With "said" in the line, you could make a mostly valid assumption that the " goes immediately after the last non-space character and probably be correct. What happens if "said" is on a different line? 
However,  >  hungrily. " It's lovely 
could be
>  hungrily." It's lovely 
or
>  hungrily. "It's lovely 
See?

I would probably begin by grouping all lines into paragraphs as a single line.  Then you could make smarter choices about the quoting by start/end points.  A tokenizer is needed for that.  [https://www.foo.be/docs/tpj/issues/vol5_3/tpj0503-0010.html](https://www.foo.be/docs/tpj/issues/vol5_3/tpj0503-0010.html) provides a little more reading.  If perl can do it, then python and ruby probably can too.  Java, C, C++ can as well, but those are usually used when the problem needs performance too.

Non-trivial problem.  You could create a script that prompts a human to modify the file with a {space}{quote} or a {quote}{space} based on a simple input by a human.  Probably a vim macro would be easiest? [https://github.com/tpope/vim-surround](https://github.com/tpope/vim-surround)  Yep, someone solved this already. ;)

---

