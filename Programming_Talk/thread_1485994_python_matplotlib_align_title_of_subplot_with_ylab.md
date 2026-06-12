---
title: "python matplotlib align title of subplot with ylabel"
date: 2010-05-17
forum: Programming Talk
---

### Post by capybara! on 2010-05-17
Dear all, 

I'm struggling with the following problem plotting my data: 

I have a figure with two panels next to each other, which I want to 
label 'A' and 'B'. I want to left-justify my panel labels, but not to 
the box that contains the plot, but to the y-axis label. I played around 
with 'text()' and 'title()', but did not find a good solution except for 
giving the coordinates manually to 'text()'. This would be very 
inconvenient though, because I have many different plots on different 
scales. 
Here is what I tried: 

```

import scipy 
import matplotlib.pyplot as plt 

fig = plt.figure() 
ax = fig.add_subplot(121) 
plt.plot(scipy.sin(scipy.arange(1,100, 0.001))) 
plt.xlabel('xlabel') 
plt.ylabel("ylabel") 
plt.text(0,1,"A", fontsize=14, transform=ax.transAxes)   

ax = fig.add_subplot(122) 
plt.plot(scipy.cos(scipy.arange(1,100, 0.001))) 
plt.text(0,1,"B", fontsize=14, transform=ax.transAxes) 
plt.xlabel('xlabel') 

``` 

So the texts 'A' and 'B' should be a little bit higher and more to the 
left. The 'A' I want to align with the y-axis label of the left plot, 
the 'B' with the values of the y-axis of the right plot. 

I hope my question is clear, I will appreciate any help! 

Thanks in advance!

---

