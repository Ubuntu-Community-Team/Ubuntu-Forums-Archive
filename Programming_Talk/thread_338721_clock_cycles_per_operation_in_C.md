---
title: "clock cycles per operation in C"
date: 2007-01-14
forum: Programming Talk
---

### Post by Houman on 2007-01-14
Hi all,

I have to write a very time-critical function and I have come up with two different designs for this function but unfortunately I have no way of comparing their respective performance. Clocking them at runtime is not an option since I would like to compare the performance of the designs before I start coding. 

What I need is some sort of table that lists the clock cycles per operation in C (for ANDs, ORs, addition, multiplication...) , this way I can come up with a general idea which one will take more time. I was wondering if you know of such a table?


regards

Houman

---

### Post by Henry Rayker on 2007-01-14
This can vary widely due to different compilers, different compiler options...it can also depend widely based on the architecture the code will be running on. In order to get a reliable count, you're going to need to go down into either assembly, or you're going to have to run some tests on the operations (either break those down into assembly if your compiler allows it or just time those).

I'm sure there is probably a reasonable way to do it (without regards to reliability of the calculations). If you are going to need to just compare between two methods, you could always look at their efficiency. Addition and subtraction (whose time complexities should be exactly the same unless the hardware is very old) typically take far fewer cycles than multiplication, which takes far fewer than division (due to the way the operations are performed inside the machine). However, this can vary widely based on the machine's architecture depending on the functional units available and present.

---

### Post by Houman on 2007-01-14
hi there;

thank you for the informative comments. I think information regarding the "relative" efficiency of operations would also suffice. So multiplication as you say is less time consuming than division, but are there any exceptions? as far as i know it should always be faster.

Also if i am going to try the inline assembly route, how would I get the clock cycles per operation in my assembly code? for example how would I know whats the cost of a register shift versus a bitwise AND operations? Read the processor manual?

Also I should mention this code will run on an ARM chip.

regards

Houman

---

### Post by jblebrun on 2007-01-14
> **Houman said:**
> hi there;

thank you for the informative comments. I think information regarding the "relative" efficiency of operations would also suffice. So multiplication as you say is less time consuming than division, but are there any exceptions? as far as i know it should always be faster.

Also if i am going to try the inline assembly route, how would I get the clock cycles per operation in my assembly code? for example how would I know whats the cost of a register shift versus a bitwise AND operations? Read the processor manual?

Also I should mention this code will run on an ARM chip.

regards

Houman

Why not just write a unit test for the function in question?

---

### Post by Wybiral on 2007-01-14
Also, try compiling it with the flag "-S" which will dump it to assembly... Then you can manually optimize the time sensitive parts and assemble it. You'd be surprised what the compiler fails to optimize.

---

### Post by jblebrun on 2007-01-14
> **Wybiral said:**
> Also, try compiling it with the flag "-S" which will dump it to assembly... Then you can manually optimize the time sensitive parts and assemble it. You'd be surprised what the compiler fails to optimize.

Wybiral gives a good suggestion. It's easy to find the running time in the ARM documentation, like you already alluded. But I found this site, which may be helpful for you, as well:
[http://www.pinknoise.demon.co.uk/ARMinstrs/ARMinstrs.html](http://www.pinknoise.demon.co.uk/ARMinstrs/ARMinstrs.html)

---

### Post by Houman on 2007-01-14
thanks jblebrun for the link, I am reading it right now.

Also as for compiling it with the -s flag, I am not using gcc, (ARM comes with its own development suit provided by codewarrior).

But this compiler should have a similar option, However the function I am writing is not too big so i can do it all in assembly. 

regards and thanks for the links.


Houman

---

### Post by Henry Rayker on 2007-01-14
Multiplication will always be faster than division, save for some possible compiler optimizations. Imagine dividing by 2. If this is hard coded at the time of compiling, the compiler SHOULD see that this can be optimized by just bitwise shifting the number. If you shift to the right, this will be the same as dividing by two.

As far as the cycles required for each assembly instruction goes, you'll have to read the processor's documentation (or find a site with similar information); it's different for any architecture.

---

### Post by slavik on 2007-01-15
timing your algorithms is next to impossible with current CPUs.

Here's what you need:
1. CPU manual (I doubt Intel or AMD will give you their CPU spec for free).
2. Account for pipelining - not exactly simple.
3. If you are using Dual Core CPU, there are too many variables just from that.
4. Speed and latency of memmory if you are using it.

---

### Post by pmasiar on 2007-01-15
Summary - there is NO substitute for implementing both appraoches and measure the ACTUAL running time. If performance is critical, don't guess - measure.

---

### Post by Henry Rayker on 2007-01-15
He mentioned that this will be running on an ARM processor, so finding the timing shouldn't be too bad. I think you bring up a good point in that, depending on how the memory is managed and so on, there will be additional variables introduced. The key thing to remember is that, considering the speed of the processor, a couple missed cycles here and there won't break the bank.

As far as comparing the speed of different operations, anything operating on two bit-fields will typically have the same time complexity (AND, OR, XOR, addition, subtraction, and bit-wise shifts) but this could possibly depend on the size of the registers (I've never worked on an ARM platform, but some other platforms have different time complexity for 8-bit, 16-bit and 32-bit operations). Other things will take more cycles due to the fact that they have to perform more actions (and take up more cycles) due to complexity. Multiplication, depending on the method used to perform the multiply at the machine level, will take longer, Division even longer than that.

---

### Post by slavik on 2007-01-15
> **Henry Rayker said:**
> He mentioned that this will be running on an ARM processor, so finding the timing shouldn't be too bad. I think you bring up a good point in that, depending on how the memory is managed and so on, there will be additional variables introduced. The key thing to remember is that, considering the speed of the processor, a couple missed cycles here and there won't break the bank.

As far as comparing the speed of different operations, anything operating on two bit-fields will typically have the same time complexity (AND, OR, XOR, addition, subtraction, and bit-wise shifts) but this could possibly depend on the size of the registers (I've never worked on an ARM platform, but some other platforms have different time complexity for 8-bit, 16-bit and 32-bit operations). Other things will take more cycles due to the fact that they have to perform more actions (and take up more cycles) due to complexity. Multiplication, depending on the method used to perform the multiply at the machine level, will take longer, Division even longer than that.

I guess I missed the ARM mention. I guess then it should be easy to time as long as you get the assembly code for your program and a table of how many cycles each operation takes. Then you would have to cross-reference the two. IMO, Perl is the best tool for this job.

---

### Post by jblebrun on 2007-01-15
> **slavik said:**
> timing your algorithms is next to impossible with current CPUs.

Here's what you need:
1. CPU manual (I doubt Intel or AMD will give you their CPU spec for free).


You can get datasheets for almost any processor quite easily. For example, here's a link to a page easily found on Intel's website that provides you data sheets for processors, design guides, application notes, and technical documents:

[http://www.intel.com/design/core2duo/documentation.htm#manuals](http://www.intel.com/design/core2duo/documentation.htm#manuals)

---

