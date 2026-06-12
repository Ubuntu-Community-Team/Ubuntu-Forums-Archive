---
title: "Use libraries or rewrite code?"
date: 2010-03-04
forum: Programming Talk
---

### Post by whackedspinach on 2010-03-04
I'm a beginning programmer, and I am trying to teach myself since my school doesn't offer any type of programming classes.  I'm learning python using online tutorials and Project Euler challenges.  So, here is my question:

What is more important for a programmer?  Adapting other people's code and fitting it into your code to make the entire program more streamlined and less dependent?  Or should you never rewrite code if you don't need to?
Whenever I import a module, I just wonder if I should be doing this instead of rewriting it into my script.

---

### Post by nmccrina on 2010-03-04
My software engineering professor would say to use libraries whenever possible. Why reinvent the wheel?

You want to understand the important algorithms and data structures, but that's different from writing them from scratch every time you use them. ;)

---

### Post by WitchCraft on 2010-03-05
> **whackedspinach said:**
> I'm a beginning programmer, and I am trying to teach myself since my school doesn't offer any type of programming classes.  I'm learning python using online tutorials and Project Euler challenges.  So, here is my question:

What is more important for a programmer?  Adapting other people's code and fitting it into your code to make the entire program more streamlined and less dependent?  Or should you never rewrite code if you don't need to?
Whenever I import a module, I just wonder if I should be doing this instead of rewriting it into my script.

Using other people's code is faster in the short run.
Not adding dependencies is better.
Time is money, but large junks of other people's code (most times completely undocumented) is most times unmaintainable.

In essence:
Don't use libraries when it's just as easy to write it yourself.
Use libraries when it would take too long to rewrite it yourself (graphics, cryptography, OperatingSystem).

It's common practice to use the fastest way. 
But common practice is not necessarely good practice, since it's also common to have untestable or unmaintainable code, parts of the code you don't understand, parts of code that you won't be able to migrate if you have to, errors that arise without warning, etc.

I guess it all boils down on how good you are in understanding other people's code.

---

### Post by leg on 2010-03-05
I would say for your project euler problems don't use libs and attempt the problem yourself as that is the point; to learn. If and when you become a jobbing programmer use them as much as possible to get the job done quickly.

---

### Post by lisati on 2010-03-05
There are advantages in using libraries, and advantages in not using libraries; some advantages of each have already been mentioned.

My $0.02: I'd suggest using libraries while you're finding your way around. Then as your confidence and experience grow, you'll be able to more easily work out when writing your own routines for common tasks will be a good idea.

---

### Post by Reiger on 2010-03-05
It really depends what it is. 

Consider: you need a fixed size list of values which rotates on a FIFO basis which will be used primarily in the context of &#8220;iterate over all these values and populate some UI controls with them&#8221;. Apart from that you also want to track the &#8220;cursor&#8221; of the list which is where the next addition/removal would occur.

That is probably not quite a standard data structure. But it is not that hard to hack it on top of an array... 

The real problem is that dependencies are fine from a purely theoretical perspective; but in practice they introduce a whole new class of problems beyond the &#8220;simple&#8221; compatibility.

---

### Post by Some Penguin on 2010-03-05
> **whackedspinach said:**
> I'm a beginning programmer, and I am trying to teach myself since my school doesn't offer any type of programming classes.  I'm learning python using online tutorials and Project Euler challenges.  So, here is my question:

What is more important for a programmer?  Adapting other people's code and fitting it into your code to make the entire program more streamlined and less dependent?  Or should you never rewrite code if you don't need to?
Whenever I import a module, I just wonder if I should be doing this instead of rewriting it into my script.

That's a false dichotomy.  What you should be focusing is developing the understanding to intelligently decide on a case-by-case basis, rather than looking for general guidelines that, in practice, tend to need frequent violation.  That includes understanding your own requirements and the capabilities and limitations of the options you're considering.

For instance, there isn't much reason to implement your own arbitrary-precision arithmetic library, since it's non-trivially difficult to do well -and- it's sufficiently important that multiple projects have already put in many, many, many man-hours doing it very well.  The probability that you would be able to replicate what they have done in a short time and to the same level of quality is rather low, so if they meet your requirements you are probably better off using what has already been written.

The same is true for, say, general-purpose compression algorithms.  bzip is extremely tried and true.  Now, if you wanted something different, like needing extremely fast on-the-fly compression of data streams and probably some error tolerance so a network glitch doesn't render the rest permanently incomprehensible, you might end up building your own if you can't find one that's good enough or has acceptable terms and functionality.  Google rolled its own compression algorithm, for instance, because widely-available ones didn't meet their needs.

On the other hand, you should probably be careful about e..g depending upon random projects...  Just because people think that they're contributing doesn't mean that they actually know how to do it well.  Even fairly well-known projects can have obvious design issues -- e..g the GATE framework, while a pretty serious attempt at providing a broad toolkit for research in natural language processing, has significant portions whose designs make it unnecessarily difficult and convoluted to support concurrency.  It was written by academics, not expert software engineers, and designing for throughput was likely not a major consideration.

---

### Post by ssam on 2010-03-05
python has a large standard library. this is guaranteed to be available in any python installation. it also has a good chance of already being loaded into memory as other programs will be using it. some of it is already optimised in C. there are projects to optimise some bits even more (unladen swallow).

also using the standard library makes you program a bit more predictable and easier to use. for example if you use getopt/optparse for command line arguments, then the syntax for the use will be the same as other programs. same with configparser/csv for reading files.

using obscure 3rd party libraries can be problematic, if the devs stop supporting/maintaining it, or if your users operating system does not handle dependencies. but its still probably less work than writing it your self.

---

### Post by nvteighen on 2010-03-05
I think it's a question easy to answer.

If you're doing serious programming (i.e. working on a project you intend to release), use libraries. Why? Well, because you should concentrate on your original code and original ideas instead of redoing what someone else already did in a fairly decent way. That's how science works: you use the good works of others to make your own good in its own.

If you're just learning and want to have some fun implementing an algorithm, do it. But don't do it if you're learning the basics of programming: do it when you've developed a sense of what a good library is and how it looks like and also, when you've learned to read basic algorithms and know basic programming structures.

---

