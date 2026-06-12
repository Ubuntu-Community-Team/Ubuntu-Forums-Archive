---
title: "digital filter implementation in C/C++"
date: 2008-03-25
forum: Programming Talk
---

### Post by cronholio on 2008-03-25
I need to implement a few basic low-pass, band-pass and notch filters for a project in C or C++. I have almost no experience with digital filters (hardly passed my signal processing classes at the university) and Google turns up thousands of pages of Matlab scripts which are of no use to me. Can anyone point me to some documentation describing how to implement digital filters in C/C++ or some existing library that can do the job for me?

Btw, I had a look at [this library]("http://ccrma.stanford.edu/software/stk/filtering.html") and it seems promising. Anyway the documentation assumes you are quite familiar with this kind of stuff, which I am not. For example, the tutorial builds a filter with some coefficients but doesn't explain how to obtain them in the first place.

Don't get me wrong, I'm not too lazy to learn something new, it's just that there is so much information out there and I think I really need to know only a small part of it to actually implement the filters.

It would be nice if anyone could point me in the right direction...

---

### Post by gnp421 on 2008-03-25
If you don't understand how digital filters work, then start with matlab then convert the matlab code to c/c++. Just doing the FFT and DFT will take you a while to understand. Alot of code goes into those alone and without them you can't implement any filter bandpass, low pass, high pass, band-stop etc.

As an engineer, I use matlab to get everything working right before I code it in another language. matlab gives you the tools needed to get everything working easily. What good is the c if it won't work in matlab?

---

### Post by cronholio on 2008-03-26
I wasn't aware that Matlab can output C/C++ code. I will get an evaluation copy and try that. Thanks.

---

### Post by cronholio on 2008-03-26
EDIT: never mind...

---

### Post by gnp421 on 2008-03-26
I use Matlab for C/C++ code all of the time. If you have any questions shoot me a pm, I'll try my best to help.

---

### Post by Kent Lobo on 2008-11-18
Hello, I joined Ubuntu specifically to ask you a question. I'm a senior in college. Electrical Engineering. My senior design project: I'm creating an effect pedal for electric guitar. You pick a key, and it filters out the wrong notes. I designed a band pass elliptical filter in Matlab, and took the normalized coefficients in to mathmatica. I have more experience with Mathmatica, so I used composite functions to scale the function allowing me to have a variable central frequency. 
Now H(s) -> H(s, Wc)
then I took the bilinear transform
s = 2 *Fs *(1-z^-1)/(1+z^-1), where Fs = sampling frequency

Factor, Expand, repeat. Now I have
H(z,Wc,Fs) theoretically allowing me to have a digital filter for whatever band pass I want, provided that Fs satisfies Nyquist and all that mess. 

PROBLEM: I'm using VB6 to implement it so I can work out the bugs before I put it in my DSP. I made a mock A/D sampler and every thing. The durn thing rails like nobody's business. Why???? I have vb make a list of the outputs, then I plot it in excel. I'm getting x10^150 size numbers. 

I've been working on this for months. Can anyone give me some advice?

---

### Post by jpkotta on 2008-11-22
> **Kent Lobo said:**
> Hello, I joined Ubuntu specifically to ask you a question. I'm a senior in college. Electrical Engineering. My senior design project: I'm creating an effect pedal for electric guitar. You pick a key, and it filters out the wrong notes. I designed a band pass elliptical filter in Matlab, and took the normalized coefficients in to mathmatica. I have more experience with Mathmatica, so I used composite functions to scale the function allowing me to have a variable central frequency. 
Now H(s) -> H(s, Wc)
then I took the bilinear transform
s = 2 *Fs *(1-z^-1)/(1+z^-1), where Fs = sampling frequency

Factor, Expand, repeat. Now I have
H(z,Wc,Fs) theoretically allowing me to have a digital filter for whatever band pass I want, provided that Fs satisfies Nyquist and all that mess. 

PROBLEM: I'm using VB6 to implement it so I can work out the bugs before I put it in my DSP. I made a mock A/D sampler and every thing. The durn thing rails like nobody's business. Why???? I have vb make a list of the outputs, then I plot it in excel. I'm getting x10^150 size numbers. 

I've been working on this for months. Can anyone give me some advice?

I'm guessing you have an IIR filter.  Your filter is probably unstable.  If you're sure that the coefficients are not completely wrong, you need to check that round off error isn't moving your poles.  Also check that intermediate results are not overflowing.  If it is more than 4th order, you should break it up into 2nd order sections and cascade them (Matlab has functions for doing this).

---

### Post by santosh160310 on 2012-03-05
How can i get the c program from existing matlab code??
does all the versions of matlab has that provision??

---

### Post by Zugzwang on 2012-03-06
> **santosh160310 said:**
> How can i get the c program from existing matlab code??
does all the versions of matlab has that provision??

First of all, since your question isn't really related to the rest of this thread, you would have been better off starting a new thread.

Second, most MATLAB versions come with a compiler "mcc" that has the option "-c" to produce C code - this is what a three minute googling session told me.

---

