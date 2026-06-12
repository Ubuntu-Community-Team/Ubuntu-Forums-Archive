---
title: "Efficient way to code using data from offline data"
date: 2011-10-28
forum: Programming Talk
---

### Post by alfa_80 on 2011-10-28
I would like to know how to code in efficient way to read from a dataset(300*10000 for example), store it in an array(in vector is better) and then further process it. Of course, if we store it that huge amount of data, it is not so computationally cheap. I have heard from someone that instead of storing it, we don't do that. We should simply open the logfile to be read and straightaway process it. Even, I got a little bit the idea, but it is still unclear to me. Anyway, I'm writing in C++. It would be nice if somebody can guide me how to realize this in more detail or point me to some good  resources/references.

---

### Post by 11jmb on 2011-10-28
I'm afraid I don't quite understand what you are asking.

Do you have a text file representing a large dataset that you would like to process in some way? If that is the case, I have always liked using Perl for parsing text. What kind of processing do you need to do?

---

### Post by alfa_80 on 2011-10-28
> **11jmb said:**
> I'm afraid I don't quite understand what you are asking.

Do you have a text file representing a large dataset that you would like to process in some way? If that is the case, I have always liked using Perl for parsing text. What kind of processing do you need to do?

The dataset contains both integer and double values. It is laser scanner data processing stuff involving a lot of operation like multiplication etc..

Thanks anyway.

---

### Post by 11jmb on 2011-10-28
I am just trying to understand your problem better so that I don't lead you down any wrong paths.

Is this data stored in a text file? If it is just formatted as integers and doubles, you should have no problem using C++ to process it.

---

### Post by alfa_80 on 2011-10-28
> **11jmb said:**
> I am just trying to understand your problem better so that I don't lead you down any wrong paths.

Is this data stored in a text file? If it is just formatted as integers and doubles, you should have no problem using C++ to process it.

Exactly, the offline data stored in a text file..yes, I'll have no problem in processing it but it is a matter of efficiency.

---

### Post by gsmanners on 2011-10-28
I think efficiency of data manipulation depends on how well you divide it into groups. Organize your data efficiently, and you'll be able to process it efficiently.

---

### Post by karlson on 2011-10-28
> **alfa_80 said:**
> I would like to know how to code in efficient way to read from a dataset(300*10000 for example), store it in an array(in vector is better) and then further process it. Of course, if we store it that huge amount of data, it is not so computationally cheap. I have heard from someone that instead of storing it, we don't do that. We should simply open the logfile to be read and straightaway process it. Even, I got a little bit the idea, but it is still unclear to me. Anyway, I'm writing in C++. It would be nice if somebody can guide me how to realize this in more detail or point me to some good  resources/references.

If you are doing statistical analysis use R.  You can actually call R from C++ if you want to.

---

### Post by 11jmb on 2011-10-28
I understand. C or C++ will probably be the most efficient. The biggest performance gain you will get is from selecting the proper algorithms, though. There are a few other tricks to keep in mind. perhaps I can be of more help if you tell me specifically what kind of processing you want to do.

---

