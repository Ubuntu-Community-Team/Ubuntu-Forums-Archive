---
title: "Neural nets and text patterns. Pointers?"
date: 2007-07-19
forum: Programming Talk
---

### Post by cunawarit on 2007-07-19
OK, this is a bit of a long shot. 

I know very little about neural nets, one thing I do know is that they can learn pattern recognition. 

I'm wondering if anyone here has a few pointers for neural nets, specifically for text patters. 

What I want to do is try to flag up potential fakes amongst personal details. For instance, it is safe to assume that all Mickey Mouses and Donald Ducks are fake, however, it is very difficult to try and work out more and more of these names by hand. Other fields I have other fields available, for instance email. 

In your opinion, is this easily achievable? Is it worth pursuing?

---

### Post by Wybiral on 2007-07-19
It's possible if there is some kind of pattern... Maybe it would be able to recognize an animal name in the text or something.

But it would have to have some kind of pattern, for instance Elmer Fudd probably wouldn't work because:

A. Someone could have that name for real
B. A name like "Richard Fudd" or "Elmer Jackson" would be normal.

But could a network recognize that an animal is within the text... Absolutely.

My tip: use a fast language... Training a net can take hours.

One more tip... Don't use a network for a database... It's a waste. If you just need it to recognize a list of names that you consider fake, just use a real database.

---

### Post by hod139 on 2007-07-19
Consider looking into Bayesian networks or support vector machines.

---

### Post by loell on 2007-07-19
yeah, just use regex and a database , though i would also like to see how neural net will work in this case.

---

### Post by vambo on 2007-07-19
Just as a first reaction - I don't find it obvious as to how you would train up an ANN to do this.

---

### Post by bread eyes on 2007-07-19
> **cunawarit said:**
> I know very little about neural nets, one thing I do know is that they can learn pattern recognition.

Pattern recognition can easily done without neural networks. IMO, you shouldn't assume that curtain names are fake.

---

### Post by Wybiral on 2007-07-19
> **vambo said:**
> Just as a first reaction - I don't find it obvious as to how you would train up an ANN to do this.

I've taught neural networks to return 0 or 1 if a certain phrase (or similar phrase) is found in a chunk of data.

The only issue here is that the author knows what kind of patterns they want, so a NN is probably overkill (when you can use a DB... Use a DB)

---

### Post by pmasiar on 2007-07-19
> **cunawarit said:**
> I'm wondering if anyone here has a few pointers for neural nets, specifically for text patters. 

What I want to do is try to flag up potential fakes amongst personal details.

Did you looked at wikipedia? [http://en.wikipedia.org/wiki/Neural_nets](http://en.wikipedia.org/wiki/Neural_nets), [http://en.wikipedia.org/wiki/Pattern_recognition](http://en.wikipedia.org/wiki/Pattern_recognition)

[pybayes](http://developer.berlios.de/projects/pybayes/) is different approach, using statistics instead of neural networks. 

If you want to fight off robots, [http://en.wikipedia.org/wiki/Captcha](http://en.wikipedia.org/wiki/Captcha) is another way.

---

### Post by kripkenstein on 2007-07-20
Neural networks are somewhat outdated. As already mentioned, look into Support Vector Machines (SVMs). There is a nice open-source library, with python bindings, called LibSVM, which I use.

You might want to simply google a little the topic of 'text categorization' or 'text classification'. Look for a good review. One example is this classical paper: [Joachim's work on SVMS for text categorization]("http://citeseer.ist.psu.edu/55854.html").

---

