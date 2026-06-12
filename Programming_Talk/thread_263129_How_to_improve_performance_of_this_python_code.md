---
title: "How to improve performance of this python code?"
date: 2006-09-22
forum: Programming Talk
---

### Post by MdaG on 2006-09-22
Hi!

I have a set of data representing positions relative time on the xy-plane. What I want to do is remove the positions reached with a high velocity (dx = x[t] - x[t - 1] > tol -> remove x[t-1]).
This is my attempt, but it's way too slow. Is there some way to speed it up without resorting to a C module?
samples is a list of 2-element lists with len = 64000 ([[x0,y0],[x1,y1],[x2,y2],[x3,y3]...]).
```
def remove_saccades(samples, tol):
	"""Remove data corresponding to saccades defined by tol"""
	remove_sample = samples.remove
	old_sample = samples[0]
	for sample in samples:
		dx = sample[0] - old_sample[0]
		dy = sample[1] - old_sample[1]
		old_sample = sample
		if abs(dx) > tol or abs(dy) > tol:
			remove_sample(sample)
```

I also want to remove duplicate samples that lies in sequence. How can I do that. I don't want to remove them all, but if we got four identical samples in a row like [2, 5], [2, 5], [2, 5], [2, 5], then I want to remove three of them. That is I'm only interested in removing those that lie in a row. It doesn't matter if we got 25 [2, 5] in there somewhere as long as they don't lie in sequence. 
This is my current attempt, but it doesn't work correctly:
```
def remove_duplicates(samples):
                old_sample = None
		remove_sample = samples.remove
		for sample in samples:
			if sample == old_sample:
				remove_sample(sample)
			old_sample = sample

```Any thoughts?

---

### Post by Jessehk on 2006-09-22
As a hobbyist who started on C, I don't have a problem with languages like Python. In fact, I quite like them. My general opinion however is that if you need performance, there are few substitutes for C or C++.

EDIT: Keep in mind that I say that without having looked at your code.

---

### Post by MdaG on 2006-09-22
Yes, I'm considering writing certain algorithms in C++ and then wrap them in Python. It's just that I'm not entirely sure how to do that. Oh well, the all knowing Google probably does ;)

---

### Post by Wolki on 2006-09-22
After looking at this for a bit, i think your problems are the remove operations. Each time you do one of these, you start searching the list for an entry with that value and take the first one. This leads to problems if the value is ok the first time, but not ok later; and can take really long, since you go through everything that already has passed the test with every iteration. 
Operate directly with the index numbers, or, if memory usage is not top priority, just leave the first list alone and copy the values that passed into a new list. Otherwise, there are probably some data structures that make operations like this easier.

---

### Post by ghostdog74 on 2006-09-22
> **MdaG said:**
> Hi!

I have a set of data representing positions relative time on the xy-plane. What I want to do is remove the positions reached with a high velocity (dx = x[t] - x[t - 1] > tol -> remove x[t-1]).
This is my attempt, but it's way too slow. Is there some way to speed it up without resorting to a C module?
samples is a list of 2-element lists with len = 64000 ([[x0,y0],[x1,y1],[x2,y2],[x3,y3]...]).
```
def remove_saccades(samples, tol):
	"""Remove data corresponding to saccades defined by tol"""
	remove_sample = samples.remove
	old_sample = samples[0]
	for sample in samples:
		dx = sample[0] - old_sample[0]
		dy = sample[1] - old_sample[1]
		old_sample = sample
		if abs(dx) > tol or abs(dy) > tol:
			remove_sample(sample)
```

I also want to remove duplicate samples that lies in sequence. How can I do that. I don't want to remove them all, but if we got four identical samples in a row like [2, 5], [2, 5], [2, 5], [2, 5], then I want to remove three of them. That is I'm only interested in removing those that lie in a row. It doesn't matter if we got 25 [2, 5] in there somewhere as long as they don't lie in sequence. 
This is my current attempt, but it doesn't work correctly:
```
def remove_duplicates(samples):
                old_sample = None
		remove_sample = samples.remove
		for sample in samples:
			if sample == old_sample:
				remove_sample(sample)
			old_sample = sample

```Any thoughts?

To remove duplicates, maybe you want to look at set
[http://docs.python.org/lib/types-set.html]("http://docs.python.org/lib/types-set.html")

---

### Post by MdaG on 2006-09-23
> **ghostdog74 said:**
> To remove duplicates, maybe you want to look at set
[http://docs.python.org/lib/types-set.html]("http://docs.python.org/lib/types-set.html")
Yes sets are great if you're only interested in removing all duplicates. This code works as well and is pretty fast:
```
                samples.sort()
		last = samples[-1]
		for i in range(len(samples)-2, -1, -1):
			if last==samples[i]: 
			   del samples[i]
			else: 
			   last=samples[i]
```
But I only want to remove sequential duplicates.
ex.)
[[1,5],[1,5],[1,5],[3,3],[1,5],[1,5],[3,3]]
should turn into
[[1,5],[3,3],[1,5],[3,3]]

I'm trying to rewrite the above code to do what I wish, but there are currently some bugs making it incorrect.

*edit*
Just made it work. Damn I'm stupid! :rolleyes:

---

