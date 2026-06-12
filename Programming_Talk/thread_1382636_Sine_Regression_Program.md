---
title: "Sine Regression Program"
date: 2010-01-16
forum: Programming Talk
---

### Post by pokebirdd on 2010-01-16
I'm currently trying to write a program that does a sine regression analysis and generates a function in the form: y = a*sin[b*(x+c)]+d.

What I've tried so far is the obvious (and very dumb) method of cycling through a great deal of possible values for a, b, c, and d. Here's the simple code I have so far:
[PHP]float sq_calc(weekData *weeks, float a, float b, float c, float d, int set){
    float sum = 0;
    int i;
    for (i = 0; i < 52; i++){
        if (set)
            sum += fabs((a*sin(b*(i+1+c))+d) - weeks[i].avgset);
        else
            sum += fabs((a*sin(b*(i+1+c))+d) - weeks[i].avgrise);
    }
    //printf("%f\n", sum);
    return sum;
}

void sine_regress(weekData *weeks, float rangea, float rangeb, float rangec, float ranged,
float step, int set, float err){
    float a, b, c, d;
    float best = 2000000000, current;
    float besta, bestb, bestc, bestd;
    
    for (a = -rangea; a < rangea; a+=step){
        for (b = -rangeb; b < rangeb; b+=step){
            for (c = -rangec; c < rangec; c+=step){
                for (d = -ranged; d < ranged; d+=step){
                    current = sq_calc(weeks, a, b, c, d, set);
                    if (current < best){
                        best = current;
                        besta = a;
                        bestb = b;
                        bestc = c;
                        bestd = d;
                    }
                }
            }
        }
    }
    printf("%.5fsin[%.5f*(x+%.5f)]+%.5f", besta, bestb, bestc, bestd);
}[/PHP]Obviously, it's not optimized in any way and takes **forever** to produce a formula. But there's another problem. The formula it produces for me is basically a sine curve with a tiny period and a huge amplitude. I'm guessing that it **does **pass through every point that way, but it's not a really accurate model for the data. 

So anyways, I couldn't really find much information online about this or any algorithms so I was wondering if someone could point me in the right direction to writing a sine regression function?

Oh, by the way, I'm writing this for my math class. I don't feel like using the built in calculator regression function so I'm trying to write my own :P

---

### Post by MadCow108 on 2010-01-16
holy cow!
thats just terrible :)

you should first have a look at the mathematics of data model fitting.
e.g. your approach to determine the "goodness of fit" is not nice because its not differentiable which makes it very hard to determine in which direction you should optimize your parameters (its possible though, but rarely done)
But that does not concern your "algorithm" as you just brute force the parameters anyway ^^

And because you try to minimize that at all cost you end up with a "too good" fit, which is mostly a wrong result, especially when you have oscillating functions.

have a look at chi-square minimization and max-likelihood methods for the start.

---

### Post by pokebirdd on 2010-01-16
Yeah, unfortunately, I have no knowledge of statistics whatsoever. I guess I'll have to study up on this then. I'd really appreciate if you could give me some related links but for now, I'm just going to break out my statistics textbook :)

---

### Post by jpkotta on 2010-01-16
> **pokebirdd said:**
> But there's another problem. The formula it produces for me is basically a sine curve with a tiny period and a huge amplitude. I'm guessing that it **does **pass through every point that way, but it's not a really accurate model for the data. 

[http://en.wikipedia.org/wiki/Overfit](http://en.wikipedia.org/wiki/Overfit)

IIRC, there is no good general method for finding a sinusoidal curve fit.  Which method is best depends on how noisy the data is, how much data there is, how many periods there are, etc.  I'm reasonably sure that the most important parameter is the frequency; once you have a good estimate of that it becomes easier to estimate the other parameters.  If you have many periods, you can estimate the frequency with a periodogram or [more sophisticated techniques]("http://en.wikipedia.org/wiki/Frequency_estimation").  Once you have rough estimates of all parameters, you can use well known optimization algorithms to find a local minimum for your error.  Mean squared error is the most common error metric because it's easy to work with, but may not be the best for your application.  Read about minimal mean square error fitting here: [http://en.wikipedia.org/wiki/Non-linear_least_squares](http://en.wikipedia.org/wiki/Non-linear_least_squares).

---

