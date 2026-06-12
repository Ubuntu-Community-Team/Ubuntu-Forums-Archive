---
title: "[SOLVED] What am I doing wrong?"
date: 2008-08-28
forum: Programming Talk
---

### Post by Zeotronic on 2008-08-28
Python: For a while now I've had some problems with my program that I *cannot for the life of me figure out* I've figured most of it out, but its all boiled down to this one clip of code:
```
	item.faces=3
	item.face.append(face3d())
	item.face[0].vertex.append(3)
	item.face[0].vertex.append(2)
	item.face[0].vertex.append(1)
	item.face[0].vertex.append(0)
	item.face[0].vertecies=4
	
	item.face.append(face3d())
	item.face[1].vertex.append(0)
	item.face[1].vertex.append(1)
	item.face[1].vertex.append(5)
	item.face[1].vertex.append(4)
	item.face[1].vertecies=4
	
	item.face.append(face3d())
	item.face[2].vertex.append(5)
	item.face[2].vertex.append(1)
	item.face[2].vertex.append(6)
	item.face[2].vertex.append(7)
	item.face[2].vertecies=4
```
My tests (print) indicates that all of these faces have the same 4 vertex values as each other, and as far as what I'd like them to do, their not supposed to. I recently modified the code to be like that and in its present state all the faces have the same vertecies as the first face... before that they all had the same vertecies as the last face... I find it very confusing.

---

### Post by dwhitney67 on 2008-08-28
> **Zeotronic said:**
> ...
My tests (print) indicates that all of these faces have the same 4 vertex values as each other, and as far as what I'd like them to do, their not supposed to. I recently modified the code to be like that and in its present state all the faces have the same vertecies as the first face... before that they all had the same vertecies as the last face... I find it very confusing.
:confused:

---

### Post by Zeotronic on 2008-08-28
Your emoticon doesn't particularly help me in helping you help me.

Update:
> the faces have the same vertecies as the first face... before that they all had the same vertecies as the last face...
Now I see whats going on (sorta)... but I'm still not sure how to fix it.

---

### Post by WW on 2008-08-28
It might help if we could see the code for face3d().

---

### Post by pmasiar on 2008-08-28
What you are doing wrong?

For starters, title of your post suggest what you did not thought too long before posting.

Read "how to ask questions" (also in my sig) and learn ... how to ask questions :-) so it will be better use of our time, and also yours.

---

### Post by Zeotronic on 2008-08-28
> For starters, title of your post suggest what you did not thought too long before posting.
Yea... ok, I have to admit I could have probably been more specific, despite the fact that I was completely clueless what I did wrong (not sarcasm). However, you might want to take note that *you* probably ment "did not *think* too long" rather than "did not 'thought'" :) (you gotta catch these things man).

As for what I was actually doing wrong, it didn't occur to me that I should declare my vertex arrays as different arrays, so yes WW, it might have helped to see my face3d class, I'm going to have to make it a point include more code in the future... *I was in error to have thought that sufficient.*

All and all that was a bad post on my behalf.

---

### Post by pmasiar on 2008-08-28
> **Zeotronic said:**
> However, you might want to take note that *you* probably ment "did not *think* too long" rather than "did not 'thought'" :) (you gotta catch these things man).

OK. When you will be able to catch those in some foreign language (for you). English is my forth, man. From indo-european languages, try for fun Russian :-) Then we will talk

---

### Post by LaRoza on 2008-08-28
> **pmasiar said:**
> Then we will talk

In Russian?

@OP You can make a new thread if you want to reword it instead of trying to save this one.

---

### Post by pmasiar on 2008-08-28
> **LaRoza said:**
> In Russian?

Yeah why not, Russian is not my native language either.

Or try German for change: every noun has gender (and it's not "it"), article "the" has gender too, and 4 forms in singular, 4 in plural. Adjectives too.

---

### Post by dwhitney67 on 2008-08-28
> **Zeotronic said:**
> Your emoticon doesn't particularly help me in helping you help me.
...

Let's try writing in English!

---

### Post by LaRoza on 2008-08-28
> **pmasiar said:**
> Yeah why not, Russian is not my native language either.

Or try German for change: every noun has gender (and it's not "it"), article "the" has gender too, and 4 forms in singular, 4 in plural. Adjectives too.

I speak a little German (was pretty good, but am rusty now)

Or we could do Hindi. Every noun has gender (but it is simple, unlike many languages), has no word for "the" or "a", no prepositions, no verb for "have", and natively only has one punctuation mark ('|' in my title is it).

---

