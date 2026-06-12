---
title: "Question about optimized out"
date: 2012-04-17
forum: Programming Talk
---

### Post by forsubhi on 2012-04-17
what is the meaning of optimized out  in eclipse cdt when I am debugging code contains k variable for example , this is snapshot describing this .

I cannot know the real value of variable 


[IMG]http://img6.imagebanana.com/img/ktyjmejo/Tooltip_052.png[/IMG]

---

### Post by lisati on 2012-04-17
Here is a translation as I understand the situation:

> I am unable to show you anything about variable k right now because the details I need aren't there because of code optimization

You might want to take a look at what optimization options you have in effect, and see if disabling any of them allows the information you need to be displayed.

---

### Post by Simian Man on 2012-04-17
It means that compiler optimizations have removed the usage of that variable.  For example, if it was a constant, the compiler could have simply replaced the variable with a constant value.  If you post the code concerning k, I will try to figure out the situation.

---

### Post by forsubhi on 2012-04-17
this is the entire code 

```
feat_array_alloc(feat_t * fcb, int32 nfr)
{
    int32 i, j, k;
    mfcc_t *data, *d, ***feat;

    assert(fcb);
    assert(nfr > 0);
    assert(feat_dimension(fcb) > 0);

    /* Make sure to use the dimensionality of the features *before*
       LDA and subvector projection. */
    k = 0;
    for (i = 0; i < fcb->n_stream; ++i)
        k += fcb->stream_len[i];
    assert(k >= feat_dimension(fcb));
    assert(k >= fcb->sv_dim);

    feat =
        (mfcc_t ***) ckd_calloc_2d(nfr, feat_dimension1(fcb), sizeof(mfcc_t *));
    data = (mfcc_t *) ckd_calloc(nfr * k, sizeof(mfcc_t));

    for (i = 0; i < nfr; i++) {
        d = data + i * k;
        for (j = 0; j < feat_dimension1(fcb); j++) {
            feat[i][j] = d;
            d += feat_dimension2(fcb, j);
        }
    }

    return feat;
}
```
I use flag CXXFAG -g -O0 and CFLAG -O0 in makefile 
do I have to make additional step in eclipse to stop optimisation 

I make my project using new --> make file project with existing resource 
and this is my project properties 
[IMG]http://img6.imagebanana.com/img/9kq0jy5d/PropertiesforSphinxTrain_053.png[/IMG]

I don't see optimisation option , why ?

---

### Post by forsubhi on 2012-04-17
I have also problem that my debugger goes up and down 
like this video 
[http://www.4shared.com/video/yD-OtYIq/error-1.html](http://www.4shared.com/video/yD-OtYIq/error-1.html)

---

