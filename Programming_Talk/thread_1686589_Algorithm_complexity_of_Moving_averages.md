---
title: "Algorithm complexity of Moving averages"
date: 2011-02-12
forum: Programming Talk
---

### Post by statty on 2011-02-12
Hi, 
I hope I am posting to the correct forum. It is with regard Algorithm complexity. I would like to know the complexity of moving averages in terms of O(x) where x might be 1, N, Log N etc. 
I am under the impression that Weighted Moving Averages have complexity O(N) and want to find an weighted averaging algorithm with lower complexity. Would I be right in thinking that the exponential weighted moving average has lower complexity i.e. O(1)? 
Any suggestions would be appreciated.

---

### Post by worksofcraft on 2011-02-12
> **statty said:**
> Hi, 
I hope I am posting to the correct forum. It is with regard Algorithm complexity. I would like to know the complexity of moving averages in terms of O(x) where x might be 1, N, Log N etc. 
I am under the impression that Weighted Moving Averages have complexity O(N) and want to find an weighted averaging algorithm with lower complexity. Would I be right in thinking that the exponential weighted moving average has lower complexity i.e. O(1)? 
Any suggestions would be appreciated.

If you just want to have a kind of smoothing filter to give rough current average of continuously varying input value then you can
do it as follows:

Multiply the current average by a constant, add the new value and divide by the constant+1. Depending on how large the value of said constant then dermines your degree of filtering.
It behaves similar to an [RC filter in electronics]("http://en.wikipedia.org/wiki/Low-pass_filter")

---

### Post by captnemo on 2011-02-12
> **worksofcraft said:**
> If you just want to have a kind of smoothing filter to give rough current average of continuously varying input value then you can
do it as follows:

Multiply the current average by a constant, add the new value and divide by the constant+1. Depending on how large the value of said constant then dermines your degree of filtering.
It behaves similar to an [RC filter in electronics]("http://en.wikipedia.org/wiki/Low-pass_filter")

That an excellent technique I've used many times both in signal processing and in econometric models(!).  An IIR filter configured as an integrator is extremely simple and fast.  As you "drive the filter through the data" it gives an exponential weighted average of the previous samples.

If you need a "double-ended" window, in other words a window with the peak in the middle and fading exponentially to either side of the peak, then take your array of data and drive one filter forwards and one backwards through the data and sum the outputs of the filters at each point.

---

### Post by CptPicard on 2011-02-12
Talking about moving averages I assume you're running a sliding window over a data set. In this case just put your window's values into a queue; then you get constant time updates: put new value into front of queue, remove from the end, add+subtract accordingly from sum you keep elsewhere, divide by number of values.

Otherwise, a moving average is linear-time in the size of the window.

---

### Post by captnemo on 2011-02-12
> **CptPicard said:**
> Talking about moving averages I assume you're running a sliding window over a data set. In this case just put your window's values into a queue; then you get constant time updates: put new value into front of queue, remove from the end, add+subtract accordingly from sum you keep elsewhere, divide by number of values.

Otherwise, a moving average is linear-time in the size of the window.

As you point out, the add-newest, subtract-oldest technique for moving averages runs very fast, requiring just one add, one subtract, and one divide (or multiply by a fraction) per sample.  But it only works on linear averages.  For exponentials or any other weighted "envelope" that you want to apply, you must recalculate the exponentials for all the samples in the window each time.  I think that's what the OP is trying to avoid and a method was proposed above.  (but it only works for exponential weighting, not other weighting methods)

---

### Post by CptPicard on 2011-02-12
> **captnemo said:**
> For exponentials or any other weighted "envelope" that you want to apply, you must recalculate the exponentials for all the samples in the window each time.  I think that's what the OP is trying to avoid and a method was proposed above.  (but it only works for exponential weighting, not other weighting methods)

Yes, true. An interesting approach. MAs/EMAs are staples in technical analysis of stock market signals and that's where I've been messing around with them... I'll have to look into that one a bit more deeply. :)

---

### Post by captnemo on 2011-02-12
> **CptPicard said:**
> Yes, true. An interesting approach. MAs/EMAs are staples in technical analysis of stock market signals and that's where I've been messing around with them... I'll have to look into that one a bit more deeply. :)

Nearly 30 years ago I was hired to develop some econometric models for the Federal Reserve and coming from recent DSP projects in the 70's I decided to try a new approach and build models entirely based on DSP type algorithms, and used the standard notation to draw them too.  IIR integrators, oscillators, delays, feedback, and it worked very well.  I have no idea if the bank did anything further with my "invention".  haha

---

### Post by statty on 2011-02-12
Thank you for your replies, I will investigate the suggested approaches and determine the one that best fits my data.
Thanks again!

---

### Post by statty on 2011-02-13
Having considered all of your options I am considering using the IIR/EMA approach. However, I would like your opinion in clarifying something. 
 
Originally using a weighted moving average (WMA) as follows: 
ave_x_i = sum (x_i*r_i)/ sum(r_i)
one division and at most N multiplications are required i.e. x_i*r_i is summed from i to N. 
 
If I replace the WMA with the following: 
ave_x_i = alpha*x_i + (1-alpha)*(prev_ave_x_i)
            = prev_ave_x_i + alpha (x_i -prev_ave_x_i)
 
Does this reduce the complexity of the algorithm? 
Do I still need at most N multiplications and if that is the case isnt the complexity still fairly high? 
Is there a way to measure this? Or am I incorrect in my thinking? 
 
Thank you again for any suggestions

---

### Post by Zugzwang on 2011-02-13
> **statty said:**
> Do I still need at most N multiplications and if that is the case isnt the complexity still fairly high? 
Is there a way to measure this? Or am I incorrect in my thinking? 


You can check this by answering the following question yourself:

Given a stream "x_1 x_2 ... x_n" of N values, for which the moving average (in this case, exponentially weighted) is to be computed, how many additions and multiplications have to be performed in order to compute the weighted averages of "x_1", "x_1 x_2", "x_1 x_2 x_3", ... in the given order?

So the trick is to consider not the computation time for obtaining *one* weighted average value, but rather to consider the time for the overall stream.

---

### Post by MadCow108 on 2011-02-13
a moving weighted average is nothing more than a convolution.
convolution in fourierspace is just a multiplication.
so depending on the size of your windows it may be be beneficial to fourier transform your data which can be done in O(N logN) and then simply multiply it

I hope this is not completely wrong its been a long time since I had a dsp lecture :/

---

### Post by statty on 2011-02-13
Thank you for your reply. For the exponentially weighted average I will still need at most N multiplications. I am trying to find a method that doesnt require as many multiplications. I will explore some of the other averaging methods outlined above. 
Thanks again.

---

### Post by CptPicard on 2011-02-13
Hmm, well, if your EMA constant is, say, c < 1, and you've got values in a queue, so your sum is t = v1 * c^0 + v2 * c^1 + .. + vn * c^(n-1), can't you do a step just by subtracting the last term (vn comes from the end of the queue, and you know how to compute the term), multiplying the remainder of t by c to "shift" and adding the new term?

---

