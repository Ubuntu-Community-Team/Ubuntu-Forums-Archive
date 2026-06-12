---
title: "grep and regex"
date: 2006-12-22
forum: Programming Talk
---

### Post by helphope on 2006-12-22
Hi evrybody.

Hope this is the right forum to post.

I'm trying to write down a grep string to find words which are near each other (not netx to each other) with few words among them. I found a regex but  it doesn't work

grep -E '\bword1\W+(?:\w+\W+){1,80}word2\b' input.txt>output.txt

:confused: :confused: 

Please, if someone has any hint, I would appreciate it a lot. Thanks

---

### Post by ghostdog74 on 2006-12-22
you might want to post an example of an input string and the expected output you want.

---

### Post by Arndt on 2006-12-22
> **helphope said:**
> Hi evrybody.

Hope this is the right forum to post.

I'm trying to write down a grep string to find words which are near each other (not netx to each other) with few words among them. I found a regex but  it doesn't work

grep -E '\bword1\W+(?:\w+\W+){1,80}word2\b' input.txt>output.txt

:confused: :confused: 

Please, if someone has any hint, I would appreciate it a lot. Thanks

I don't remember what (?:) means in Perl regexps, but apparently "grep -E" doesn't support them. Does the command below work?

```
grep -E '\bword1\W+(\w+\W+){1,80}word2\b' input.txt>output.txt
```

---

### Post by helphope on 2006-12-22
Thanks for replying
> **ghostdog74 said:**
> you might want to post an example of an input string and the expected output you want.

OK. Let's take Othello's end to see what I'm looking for

> Ah balmy breath, that dost almost persuade
Justice to break her sword! One more, one more.
Be thus when thou art dead, and I will kill thee,
And love thee after. One more, and this the last:
So sweet was ne'er so fatal. I must weep,
But they are cruel tears: this sorrow's heavenly;
It strikes where it doth love. She wakes.

Now let's say that I'd like to find a paragraph with the words "persuade" and "dead"; these two words cannot be separated by more than 20 words.  The outpt will be the quote I wrote up here (I mean all the paragraph, not just the sentence).

I got this 
grep 'persuade.*dead' shakspeare.txt>output.txt :-k 
but there is no limit for the words in bewteen the ones I specified.
I hope I made myself clear.

Thanks again

---

