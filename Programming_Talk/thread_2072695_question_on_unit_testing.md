---
title: "question on unit testing"
date: 2012-10-18
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-18
Hello,
I have a couple of questions related to unit testing. I'm very sorry if this is not the right place to ask this, but I was not sure about where else to ask.
These are my questions.

1)Why does a unit testing framework(I'm using CUnit) need to have such a complex architecture of
1 Registry has multiple suites,
1 Suite has multiple tests.

Finally, it all comes down to the test functions, correct ? So, why can't we just have a simple architecture where test functions execute one after the other ?

**Someone asked me this question and I told him that it's so that multiple developers can work simultaneously, each one writing tests in a separate suite and collaborate. But he wasn't convinced and asked, even if that's the case, why have multiple registries ?**

2)Why do we need to have so many types of assertions. Please refer [http://cunit.sourceforge.net/doc/writing_tests.html#assertions]("http://cunit.sourceforge.net/doc/writing_tests.html#assertions"). Sorry again for asking a question about a particular framework, but my question is, can't ```
CU_ASSERT(int expression)
``` do the same job as all other assertions given the right "expression" ?

3)Because, I can't answer these questions, I often end up asking myself, why do I even need this framework ? It doesn't give me anything extra ; instead of assertions, I can just write my own if-else which decides if the test function passed or failed based on say, some return value
What are the advantages of using a framework for unit testing ?

**I asked someone this, and he gave me a very blunt answer , "Why don't you write your own Operating system?"**

Thanks.
Please advise.

---

### Post by XplosS on 2012-10-19
Hello there!

Actually, I guess that the problem is that you haven't really worked with TDD. TDD stands for test-driven development, where you first specify the kind of tests in which your code must succeed, and then you right the code with those tests in hand.

Therefore, the more complete the test set you write is, the more close to specifications your code will be, when you stop getting any kind of error from the set. Imagine a calculator (imagining that each operation is a complex programming task) - how many tests would you have to include before starting development?

- If you only include 4 operations (addition, subtraction, multiplication and division) the intuitive response would be "four".
- BUT, will it work with any combination of positive and negative numbers? "Ok, maybe we need 12 units".
- BUT, have you considered decimals? And special numbers, as infinity?

In conclusion, that set of questions required some knowledge of TDD. Google it! :)

PS: And good luck with your interviews!

---

### Post by IAMTubby on 2012-10-19
> **XplosS said:**
> Hello there!

Actually, I guess that the problem is that you haven't really worked with TDD. TDD stands for test-driven development, where you first specify the kind of tests in which your code must succeed, and then you right the code with those tests in hand.

Therefore, the more complete the test set you write is, the more close to specifications your code will be, when you stop getting any kind of error from the set. Imagine a calculator (imagining that each operation is a complex programming task) - how many tests would you have to include before starting development?

- If you only include 4 operations (addition, subtraction, multiplication and division) the intuitive response would be "four".
- BUT, will it work with any combination of positive and negative numbers? "Ok, maybe we need 12 units".
- BUT, have you considered decimals? And special numbers, as infinity?

In conclusion, that set of questions required some knowledge of TDD. Google it! :)

PS: And good luck with your interviews!
XplosS, thanks for the reply. Ok, I understand the part about units, but why suites and registries over it ?

No, it's not at all for an interview.

---

### Post by trent.josephsen on 2012-10-19
If you're proofreading a 1000 page book, do you re-read the whole thing every time you correct a mistake?

Think of the situation where you have dozens of developers working concurrently on a project with hundreds of thousands of lines of code. Surely you want to be able to subdivide your tests so that you can focus on different parts of the project without having to run a gazillion tests every time you fix a syntax error.

---

### Post by sapo on 2012-10-19
About having a test framework you actually don't really need it. Take a look at the Go language, they have a simple testing framework built in the language itself. Take a look at these Go tests for example:

[https://code.google.com/p/go/source/browse/test/args.go](https://code.google.com/p/go/source/browse/test/args.go)

Depending on what you are testing you don't really need a big framework, but a lot of things the framework will do for you, for example:

When you compare 2 float values, they can't really be the "equal", so you have to use a delta value to remove extra decimal digits, now imagine having to trunc ou round by hand every float value in every check that uses a floating point number, this would be a real a waste of time.

Uncle Bob Martin have some really great videos that can change what you think about unit testing, take a look at: [http://www.cleancoders.com/](http://www.cleancoders.com/) I highly recommend these videos if you wanna know the benefits of TDD (Test Driven Development).

---

