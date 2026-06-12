---
title: "C++ variable scope problem"
date: 2010-11-12
forum: Programming Talk
---

### Post by hanlin on 2010-11-12
I have a problem with variable being cleared unwantedly after a function call. Here's my scenario:

```

Mat *hist;
doSomething(hist);

void doSomething(Mat *hist) {
  hist=new Mat;
  ...
}

```

The problem is that after the function call, hist is being cleared out. I understand that the reason has to do with that memory location being cleared out after the function returns. If I initialize hist before the function call instead, it works fine:

```

Mat *hist=new Mat;
doSomething(hist);

```

So far, I've been doing this to get around this problem. However, I'm wondering how to do it properly, where hist gets initiated in the doSomething function.

---

### Post by dwhitney67 on 2010-11-12
Since your query pertains to C++, I will say this once... do NOT use global variables.

As far as the code you posted, the first part, albeit possibly syntactically correct, is not necessary.

Consider the following, perhaps even try to compile/run it:
```

class Mat
{
public:
   Mat() {}
};

void doSomething(Mat* hist);

int main()
{
   Mat* h = new Mat;

   doSomething(h);

   ...

   delete h;
}

void doSomething(Mat* hist)
{
   ...
}

```

---

### Post by Some Penguin on 2010-11-12
And if you're using global variables, shadowing them by using the same names for function parameters is a really, really bad idea.

---

### Post by hanlin on 2010-11-12
I guess I should be a little more clearer about what I need to do, as I do require changing of global variables.

So my Mat *hist is a global variable that is accessed by a bunch of functions. So the doSomething function does some manipulation on hist. In particular, it needs to initialize it with certain size paramters. I should have:

```

class foo{

public:
  Mat *hist;

int main() {
  doSomething;
}

void doSomething() {
  hist=new Mat(params);
  ...
}

```

dwhitney67:

I'm not sure how your code differs from what I have. Those first 2 lines are in main() (sorry for not being clear).

The reason I need to initialize my Mat object in the doSomething function is because I'm storing a matrix in Mat, and the size need to be determined first, which can't be done in main().

Also, what's wrong with using global variable?

---

### Post by matt_symes on 2010-11-12
Hi  

Global variables pollute the global namespace. Use singletons or monostatic patterns in C++. Either that or stick to C.

Kind regards

---

### Post by dwhitney67 on 2010-11-12
> **hanlin said:**
> 
Also, what's wrong with using global variable?
Nothing at all; I merely wrote my opinion.  Feel free to declare all of your variables as global.  Seriously, passing variables into functions is overrated.  Just declare everything global, and no matter which function you are in, voilà, they are available for use.  Never mind worrying about debugging your code, because you are the crème de la crème of programmers, that surely will design and develop perfect code.

---

### Post by worksofcraft on 2010-11-12
I saw this thread on subject of [global variables]("http://ubuntuforums.org/showthread.php?t=1611302") recently... IDK if the guy reached any conclusions.

---

