---
title: "Two pass gaussian filter"
date: 2012-10-11
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2012-10-11
Hi

I am trying to implement a two pass gaussian filter however I can't find any (easy to understand) explanation. Can anybody here explain me how to do this filter? I have already done single pass gaussian. Also I need to do this in plain C, I am representing the image as a array of struct which containt 3 unsigned char variables - RGB.

Thanks for any help

---

### Post by PaulM1985 on 2012-10-11
What are you trying to achieve with the image?  Why do you want to do a second pass?

Paul

---

### Post by Mr.Pytagoras on 2012-10-11
I'm trying to blur that image  and the two pass as I read is faster than the single pass gaussian filter

---

### Post by PaulM1985 on 2012-10-11
In that case you apply your blur that you used the first time round to your output from the first pass.

Paul

---

### Post by Mr.Pytagoras on 2012-10-11
> **PaulM1985 said:**
> In that case you apply your blur that you used the first time round to your output from the first pass.

Paul

I'm  not sure if we understand each other. If I would apply that second time then the image would be blured twice, however what I want is to use two passes to blur it one time. 

Hmm

I read that I need to do a vertical pass then a horizontal pass, the problem is that I don't know what to do in the vertical and then in the horizontal pass. I know that I need to blur it firs it vercital and then it horizontal direction, yes, yes, but how? 

In single pass you have the kernel, then pick a pixel, apply the kernel to its surrounding pixels, add everything together then divide it by a constant and then replace the pixel you original chose with the new pixel you have just calculated.

Two pass - no idea.

---

### Post by PaulM1985 on 2012-10-11
> **Mr.Pytagoras said:**
> 
I read that I need to do a vertical pass then a horizontal pass, the problem is that I don't know what to do in the vertical and then in the horizontal pass. I know that I need to blur it firs it vercital and then it horizontal direction, yes, yes, but how? 


Is the point in doing horizontal and vertical passes that you are only having a 1D kernel instead of a 2D kernel that you would use in a single pass.  I guess this would be quicker because you aren't having to take corner pixels of the blur kernel into account because you already blurred in one direction first time round.

Paul

---

### Post by PaulM1985 on 2012-10-11
By passing a gaussian filter with a smaller kernel size twice you may get faster processing with the same results.


If your image is m by n and you have a gaussian of diameter d, your for loops would be:

(m - d) * (n - d) * d * d

If you doubled the kernel size you have:

(m - 2d) * (n - 2d) * 2d * 2d

For m = 1000 and n = 1000 and d = 3 the two equations give:
8946081 iterations and 35569296 iterations respectively, so it is less than half the number of with a half size kernel.  Applying the half size kernel twice would be quicker than applying the full size kernel once.

Paul

---

### Post by Mr.Pytagoras on 2012-10-12
> **PaulM1985 said:**
> Is the point in doing horizontal and vertical passes that you are only having a 1D kernel instead of a 2D kernel that you would use in a single pass.  I guess this would be quicker because you aren't having to take corner pixels of the blur kernel into account because you already blurred in one direction first time round.

Paul

Well I really don't know, that why I have created this thread so that I learn something about how to do it.

> **PaulM1985 said:**
> 
By passing a gaussian filter with a smaller kernel size twice you may get faster processing with the same results.


If your image is m by n and you have a gaussian of diameter d, your for loops would be:

(m - d) * (n - d) * d * d

If you doubled the kernel size you have:

(m - 2d) * (n - 2d) * 2d * 2d

For m = 1000 and n = 1000 and d = 3 the two equations give:
8946081 iterations and 35569296 iterations respectively, so it is less  than half the number of with a half size kernel.  Applying the half size  kernel twice would be quicker than applying the full size kernel once.

Paul 	

Paul

That is interesting, however it isn't what I'm looking for, what I want is to learn how to do the two pasa gaussian filter, one pass in one direction and the other one in the other direction, so far I know only that I need to do this horizontal/vertical passes, but how I don't know, neither whether I should use 1D array instead of 2D or how to calculate the gaussian values for the kernel. Any help or reference to this subject would be great.

---

