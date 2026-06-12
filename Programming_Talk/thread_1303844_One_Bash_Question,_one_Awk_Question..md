---
title: "One Bash Question, one Awk Question."
date: 2009-10-28
forum: Programming Talk
---

### Post by rob86 on 2009-10-28
My first question is about awk. How do I get awk to round a number, or cut off some digits? I want a number like 0.55s but instead I'm getting something like 0.554354523s, too long!

My second question is about bash. How can I make a simple list/array of IP addresses/urls and then select an item from the array at random?

like, 

urls = [[www.websiteone.com,www.websitetwo.com,www.ubuntuforums.com]](www.websiteone.com,www.websitetwo.com,www.ubuntuforums.com])

and I'd use something like this to read it: $url[rand(0,len(urls)-1)] 

I know that's (probably) wrong syntax since I don't know much about bash, but that's the general idea of what I want to happen.

Thanks!

---

### Post by kaibob on 2009-10-28
> **rob86 said:**
> My first question is about awk. How do I get awk to round a number, or cut off some digits? I want a number like 0.55s but instead I'm getting something like 0.554354523s, too long!
I'm not all that knowledgeable with awk, but I believe you can use printf to round numbers. For example, the following does basic math calculation and rounds the result to 3 places:

```
awk 'BEGIN {printf "%.3f\n", 20/3 }'
```

There are some awk experts in this forum and hopefully they will be able to provide more information.

EDIT: I just noticed that this thread is marked solved, so perhaps the OP has resolved the issue on his own.

---

### Post by benj1 on 2009-10-28
> **kaibob said:**
> I'm not all that knowledgeable with awk, but I believe you can use printf to round numbers. For example, the following does basic math calculation and rounds the result to 3 places:

```
awk 'BEGIN {printf "%.3f\n", 20/3 }'
```

There are some awk experts in this forum and hopefully they will be able to provide more information.

EDIT: I just noticed that this thread is marked solved, so perhaps the OP has resolved the issue on his own.

yeah thats correct, its basically the same as C's printf.

@op 
re arrays if this is related to the awk question, you can use arrays in awk
```
array[0]="hello"
```
the arrays can even be named whatever so
```
array[hello]=0
```
i believe bash arrays use a simililar syntax although you can only index by number

---

### Post by ghostdog74 on 2009-10-28
> **benj1 said:**
> 
i believe bash arrays use a simililar syntax although you can only index by number
bash 4.0 now has associative arrays. FYI

---

### Post by rob86 on 2009-10-28
Thanks for the printf I was looking at printf but wasn't sure how to use it. I figured it out now though. I don't need help for the arrays now, I figured it'd be easier to just read a random line from a file.

---

