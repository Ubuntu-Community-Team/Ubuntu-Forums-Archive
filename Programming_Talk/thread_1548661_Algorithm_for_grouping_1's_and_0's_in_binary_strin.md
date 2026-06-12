---
title: "Algorithm for grouping 1's and 0's in binary string?"
date: 2010-08-08
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-08-08
I have a long binary string of 1's and 0's (which denote pass or fail).  I see that most of the time consecutive bits have the same value.  I want to partition the binary string into the largest passing (1's) and failing (0's) segments as possible.  There will be a tradeoff between size of segment and purity (% of bits in segment with same value).  In the 2D case, I know most people would use a self-organizing map algorithm to do this, but since I am dealing with only a 1D string, is there a simpler algorithm I can use?  

The first algorithm idea that came to mind would be:

1. Start new partition
2. Keep adding bits to partition until (#majority bits / #total bits) < 0.9.

But that would not pick ideal boundaries -- the rule would be too strict when the partition is small and not strict enough when array is large.

---

