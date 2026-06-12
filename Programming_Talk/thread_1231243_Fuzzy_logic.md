---
title: "Fuzzy logic"
date: 2009-08-04
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-04
Has any one used fuzzy logic?In which language is it implemented?I know there is a toolbox in Matlab,which i wish to avoid.I have been advised by someone to do some programs which i otherwise did conventionally ,using Fuzzy logic.Any ideas?

---

### Post by MindSz on 2009-08-04
I believe you can implement fuzzy logic in any language. It's just a different way of looking at the results.

So for a given action, instead of having a YES/NO (binary) answer, you get a range of possible answers.

It's like when you have a set of if/elseif/else blocks that determine what your program is going to do next.

For example, let's say you need to control the speed of a car. Instead of just having the usual GO/STOP of toy cars, you need to have ranges of speed depending the pressure on the gas pedal. So you might say something like:

```
if(pressure<=0) STOP();
else if(pressure>0 && pressure<50) MEDSPEED();
else FULLSPEED(); // 50<=pressure<=100
```

At least that's how I look at it.

---

### Post by nipunreddevil on 2009-08-04
OK,That was a good explanation,but how to use it in stuff where it is not used.

---

### Post by MindSz on 2009-08-04
I'm not sure I understand what you mean. Could you give an example?

---

### Post by nipunreddevil on 2009-08-04
Like we do database management or design software or do searching.
guess people dont use fuzzy logic here.Is it applicable in such areas as well.
Someone told me about solving differential equations using fuzzy logic

---

### Post by y-lee on 2009-08-04
> **nipunreddevil said:**
> Has any one used fuzzy logic?In which language is it implemented?I know there is a toolbox in Matlab,which i wish to avoid.I have been advised by someone to do some programs which i otherwise did conventionally ,using Fuzzy logic.Any ideas?

As far as I know one can implement any of the fuzzy logics in any turing complete language. You may however wish to use a library as opposed to "reinventing the wheel", see [Fuzzy-Logic]("http://en.wikipedia.org/wiki/Fuzzy_logic#External_links") for a small list of fuzzy logic libraries and google for more if those do not suite your purposes.

---

### Post by CptPicard on 2009-08-04
Besides you are going about things completely backwards... why not learn the concept first so you will be able to know when and where it is applicable, instead of just deciding to apply it as some kind of matter of principle?

---

### Post by MadCow108 on 2009-08-04
> **nipunreddevil said:**
> Like we do database management or design software or do searching.
guess people dont use fuzzy logic here.Is it applicable in such areas as well.
Someone told me about solving differential equations using fuzzy logic

its not about solving differential equations its about avoiding to solve the complicated equations which arise from traditional control theory.

a good application is user interaction with devices like cameras, washing machines etc as you have parameters that are very easy to understand like slow, hot, heavy etc.
its not useful when you need exact results as for example controlling a nuclear plant.

---

### Post by ahmatti on 2009-08-04
CptPicard is absolutely right! First learn the concept then see if it is useful for you. Its too often that I see scientific papers using fuzzy logic (or something else) that is not well suited for the problem, but the authors are predetermined to use it.

Fuzzy logic is also good if you wan't to make a model based on expert opinions, but I find that if yiu work with data there are usually better options. 

Once you know what you want to accomplish you can easily program it in any language. The wikipedia article that y-lee posted gives you a good start. 

I think fuzzy control was more fashionable a few years back and you can also use it for precise control like autopilot of a helicopter, but then again also a lot of other MPCs can do it.

---

