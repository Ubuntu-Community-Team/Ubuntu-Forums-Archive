---
title: "Machine Learning - how to begin?"
date: 2010-11-21
forum: Programming Talk
---

### Post by Tapas Bose, India on 2010-11-21
Hello everybody.
I am studying Masters in Computer Application and my course is going to end. In the mean time I joined a software company as a trainee. Our COO is intended to do some work on machine learning and he appointed me for this purpose. But I don't know anything about machine learning. He told me take your time, study the subject and inform me about your progress. But I don't know how to start, where to start, which books should I read. He wants me to do some programming on this topic using JAVA. I googled and found some API like WEKA, JAVA-ML etc. If anybody suggest anything regarding these matter, where to start, which book should read to start working on machine learning it will be very helpful to me. I am a beginner.
I will wait for your responses.
Thank you.

---

### Post by worksofcraft on 2010-11-21
> **Tapas Bose, India said:**
>  Our COO is intended to do some work on machine learning.

The most up-to-date machine learning I have worked on is called "neural networks". It is a simulation of how organic brains work and it is used in applications like image and speech recognition.

---

### Post by Tapas Bose, India on 2010-11-21
> **worksofcraft said:**
> The most up-to-date machine learning I have worked on is called "neural networks". It is a simulation of how organic brains work and it is used in applications like image and speech recognition.

Thank you. Can you please tell me which book should I read to learn machine learning?

---

### Post by worksofcraft on 2010-11-21
> **Tapas Bose, India said:**
> Thank you. Can you please tell me which book should I read to learn machine learning?
I was a hardware test engineer and I learnt programming as a hobby. I picked things up from people I worked with so I only have practical experience.

You can start [exploring neural networks right here on the www]("http://en.wikipedia.org/wiki/Neural_network") :)

---

### Post by lisati on 2010-11-21
> **Tapas Bose, India said:**
> Thank you. Can you please tell me which book should I read to learn machine learning?

I don't think there's any one book that can cover everything: it's a very rich subject. You might want to look [here]("http://en.wikipedia.org/wiki/Machine_learning") for a broad outline - neural networks (which some people have suggested) are mentioned.

---

### Post by Tapas Bose, India on 2010-11-21
> **worksofcraft said:**
> I was a hardware test engineer and I learnt programming as a hobby. I picked things up from people I worked with so I only have practical experience.

You can start [exploring neural networks right here on the www]("http://en.wikipedia.org/wiki/Neural_network") :)

:) 
Thank you. 
In our office I am the only person working on machine learning. So I have to start from scratch. I have semester in December and after that I will start working and learning machine learning. 
Anyway take care. I will be in contact here.
:)

---

### Post by Tapas Bose, India on 2010-11-21
> **lisati said:**
> I don't think there's any one book that can cover everything: it's a very rich subject. You might want to look [here]("http://en.wikipedia.org/wiki/Machine_learning") for a broad outline - neural networks (which some people have suggested) are mentioned.

Thank you lisati.
Yes, you are right.
I found a book [Machine Learning by Tom M. Mitchell]("http://www.amazon.com/Machine-Learning-Tom-M-Mitchell/dp/0070428077"). Is this book fine to start for a beginners to learn Machine Learning?

---

### Post by CptPicard on 2010-11-21
Machine learning is probably the most mathematically intense and demanding of all the application fields within CS. As one of my professors once said, everything that hasn't been solved yet can put under artificial intelligence...

Neural networks are a bit old these days; the hot stuff is in Bayesian statistics and inference. Bayesian belief networks, for example. Also look into support vector machines and neural network-ish structures such as Kohonen maps, Hopfield networks...

But if I were you I had work on my math first if it's not top notch.

---

### Post by Tapas Bose, India on 2010-11-21
> **CptPicard said:**
> Machine learning is probably the most mathematically intense and demanding of all the application fields within CS. As one of my professors once said, everything that hasn't been solved yet can put under artificial intelligence...

Neural networks are a bit old these days; the hot stuff is in Bayesian statistics and inference. Bayesian belief networks, for example. Also look into support vector machines and neural network-ish structures such as Kohonen maps, Hopfield networks...

But if I were you I had work on my math first if it's not top notch.

Yes in machine learning I saw a lots of statistics, I love that. What I need is to begin learning this extraordinarily interesting subject. I posted a link of a book in my previous post. This book is also can be found in the reference section of wiki article on Machine Learning. Is this book is the best for beginners?

---

### Post by Some Penguin on 2010-11-22
Off-hand:

the Mitchell book you've mentioned.
Russell & Norvig's "Artificial Intelligence" is pretty elementary and a decent overview.

And you should already be sharp on data structures and algorithms if you want to work on reasonably-sized problems and have runs finish within a decent time.

But to actually *do* much you'd want to look at more specific books.  Volumes have been written just individual approaches for handling high-dimensionality spaces, for instance.  Or for classifying text documents. Or on regularization.  Or for selecting kernels for SVM.  Or processing words to simplify subsequent NLP work.  It's not really a field that rewards dilettantes, and it also frequently is a massive help to actually inject human effort and understanding rather than expecting 'AI' to solve it all.  

Regarding WEKA, last I checked, their code was nominally functional and 'correct', but horribly suboptimal in terms of performance.  For instance, I recall seeing code which would e.g. instead of treating an array as a circular buffer and moving indices, would instead shift the entire contents within the array every iteration.  Gah.  This is not entirely uncommon for academic frameworks where working on multi-GB datasets might be somewhat rare.

---

### Post by ziekfiguur on 2010-11-22
> **Tapas Bose, India said:**
> Thank you lisati.
Yes, you are right.
I found a book [Machine Learning by Tom M. Mitchell]("http://www.amazon.com/Machine-Learning-Tom-M-Mitchell/dp/0070428077"). Is this book fine to start for a beginners to learn Machine Learning?

That's a pretty good book, It was recommended to me by my professor when i did my bachelors thesis (Artificial Intelligence).

The book Some Penguin mentioned is actually called `Artificial Intelligence, A Modern Approach' (usually shorted to AIMA) you can find more info about it here: [http://aima.cs.berkeley.edu/](http://aima.cs.berkeley.edu/) It covers pretty much everything that has anything to do with AI or Machine Learning, highly recommended.

---

### Post by DanielWaterworth on 2010-11-22
I started to learn about unsupervised machine learning as a hobby. It was after I saw [http://www.youtube.com/watch?v=AyzOUbkUf3M](http://www.youtube.com/watch?v=AyzOUbkUf3M) that I started to make interesting things. Learn about hopfield nets, boltzmann machines and restricted boltzmann machines and you'll have a pretty good start in up to date technology. There are lots of scientific papers on the subject, many of them are freely available.

---

### Post by Tapas Bose, India on 2010-11-22
Thank you everybody. I really appreciate your kind help. I will going to start my study. And love to see more suggestions if possible. Thank you again all of you.

---

### Post by kvorion on 2010-12-03
Hi Tapas,

If all you are interested in, is using this stuff in applications, then don't spend too much time learning the theory. I know it sounds counterintuitive and shortsighted, but ML as a subject is very deep and involved, and if you want to get things done, you should explore the resources available to you in terms of tools and APIs. I am a comp sci PhD student. I love the R&N AI textbook, and Tom Mitchell's book is also excellent, but these teach you the very core of the subject, and you won't really learn anything about how to use these in real life from these books.

Weka in my opinion is an excellent tool for starters, and you should spend most of your time learning to use weka and its Java API, because I am quite certain that this is what you will end up using for most of your experiments.

I think the most important thing here is to limit your scope. What exactly is it that you want to accomplish? What kind of applications do you want to build? Without answers to these questions, you will be lost in an ocean of information. The most important thing that you can learn is to understand which algorithm to apply for a particular application. I would suggest you take a look at this book:

Data Mining: Practical Machine Learning Tools and Techniques with Java Implementations (Ian H. Witten, and Eibe Frank)

---

### Post by Tapas Bose, India on 2010-12-04
Hello kvorion.
I will keep your advice in mind. in future if I face any problem I will ask here.
Thank you for cooperating me. :)

---

