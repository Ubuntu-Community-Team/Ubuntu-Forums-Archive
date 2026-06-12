---
title: "Iterating elements in Python"
date: 2010-04-02
forum: Programming Talk
---

### Post by cdiem on 2010-04-02
I have a long list of pixels, represented as RGB as:

[PHP]
[(123, 32, 43), (123, 54, 87), (213, 98, 78), (88, 99, 101), (95, 11, 243), (222, 111, 98), (55, 66, 89) ...]
[/PHP]

In Python, how do I iterate 3 tuples at a time? Basically I want to inspect every 9 RGB values at a time; the result should be something like:
[php]
a = [(123, 32, 43), (123, 54, 87), (213, 98, 78)]
a = [(88, 99, 101), (95, 11, 243), (222, 111, 98)]
...
[/php]

EDIT: I think I have found some workaround here: [http://code.activestate.com/recipes/496958-group-iterator-into-n-tuples-with-none-padding/](http://code.activestate.com/recipes/496958-group-iterator-into-n-tuples-with-none-padding/) for grouping them 3 by 3

---

### Post by LKjell on 2010-04-03
Something like this? ```

r = [(123, 32, 43), (123, 54, 87), (213, 98, 78), (88, 99, 101), (95, 11, 243), (222,
	111, 98)]

a = []

for i in range(len(r)):
	if i % 3 == 0:
		a.append(r[i])
		a.append(r[i+1])
		a.append(r[i+2])
		print a
		a = []


```

I know it is not flexible and not pythonic but it works

---

### Post by cdiem on 2010-04-04
Thank you; actually I ended up making a generator with very similar to your code:

```

"""
>>> all_pixels = [(110, 103, 145), (109, 103, 147), (104, 101, 144), (109, 104, 145), (107, 102, 143), (106, 103, 146)]
>>> info_generator = info_gen(all_pixels)
>>> info_generator.next()
[(110, 103, 145), (109, 103, 147), (104, 101, 144)]
>>> info_generator.next()
[(109, 104, 145), (107, 102, 143), (106, 103, 146)]
"""
def info_gen(pixels):
	count = 0
	info_pixels = []
	for pix_tuple in pixels:
		count += 1
		info_pixels.append(pix_tuple)
		if count % 3 == 0:
			last_three_pixels = info_pixels[-3:]
			yield last_three_pixels

```

---

### Post by Can+~ on 2010-04-04
[PHP]def slice_generator(pixels, step):
	for c in range(0, len(pixels), step):
		yield pixels[c:c+3][/PHP]

A shorter version of yours, also using a generator (Prefer xrange if working with python2.x). Example of using it:

[PHP]for pixel in slice_generator(all_pixels, 3):
	print(pixel)[/PHP]

Alternative with lambda, and generator expression (basically the same, but one-lined):

[PHP]slice_generator = lambda pixels, step: [pixels[c:c+step] for c in range(0, len(pixels), step)][/PHP]

---

