---
title: "how to get performance counters using c#"
date: 2012-04-11
forum: Programming Talk
---

### Post by ghouse1982 on 2012-04-11
Hi,

I am using mono on ubuntu in c#, I am trying to get performance counters like total bytes received, total memory like shown below:

var pc = new PerformanceCounter (Mono Memory, Total Physical emory);

pc.NextValue() or pc.RawValue always gives me 0.

Please help.

---

### Post by muteXe on 2012-04-11
what do you actually pass into the constructor?

---

### Post by muteXe on 2012-04-11
I found this comment on msdn (not mono sorry but it might be relevant):

> 
If the calculated value of a counter depends on two counter reads, the first read operation returns 0.0. Resetting the performance counter properties to specify a different counter is equivalent to creating a new performance counter, and the first read operation using the new properties returns 0.0. The recommended delay time between calls to the NextValue method is one second, to allow the counter to perform the next incremental read.


---

### Post by ghouse1982 on 2012-04-12
Ya it works in windows. I put Thread.sleep(1000) between two reads but still i get result as 0.

var pc = new PerformanceCounter ("Mono Memory","Total Physical emory");

pc.NextValue();

Thread.sleep(1000)

pc.NextValue();

---

### Post by Zugzwang on 2012-04-12
> **ghouse1982 said:**
> var pc = new PerformanceCounter ("Mono Memory","Total Physical emory");


Does the problem persist if you fix you spelling of "Memory"? You forgot an "M".

---

### Post by ghouse1982 on 2012-04-13
ya that was my typing mistake in the forum it is not in the main code though

---

