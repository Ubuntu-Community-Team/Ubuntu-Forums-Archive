---
title: "Fooling around with continuations..."
date: 2008-04-09
forum: Programming Talk
---

### Post by CptPicard on 2008-04-09
The other night I was having a discussion with Wybiral and aks44 and lnostdal about continuations. I was trying to do my best to elucidate this somewhat difficult concept, but finally I was simply told to shut up and show the code ;) So... in order not to end up [looking all foolish]("http://www.hackles.org/cgi-bin/archives.pl?request=310"), I of course had to hack something up to demonstrate.

So, this is in Scheme, and what we're trying to do is to have two binary search trees that we want to merge and flatten so that we get the elements of the trees in ascending order. Of course, this can be performed by using two inorder traversals of the trees. The question remains how to interleave the processing. So what we've got to begin with is:

```


(define tree_a '(20 (10 5 12) (30 25 37)))
(define tree_b '(18 (9 8 16) (32 22 49)))


(define (inorder tree)
  (if (not (null? tree))
      (if (pair? tree)
	  (begin 
	    (inorder (cadr tree))
	    (inorder (car tree))
	    (inorder (caddr tree)))
	  (print tree))))  ; "print is a magic function that consumes item


```

Using Scheme's yield/force generator mechanism would of course work, but we'll just use two raw continuations here in a sort of coroutine arrangement. Think of threads, without threads.

I also want to keep our inorder traversal completely ignorant of what we're doing to its execution, so we need to hide some sort of a "traffic cop" into "print". Really cool (pure-functional) coroutines pass each others' continuations between each other as parameters (the call/cc evaluates to a value you pass the continuation as parameter when you call it, we don't do that here), juggling state like that, but I'm going to use side-effects here to just store a continuation in a variable from where it can be resumed at will, I think that illustrates a point better:

EDIT: This was just fixed, I removed the dependency on firing up the other tree from inside print, which was wrong. The explanation below refers to some old stuff that was since removed... I think this code is much more clear about what it does on its own.

```


(define the-other-continuation 'nil) ; The other continuation
(define bound 'nil) ; The value "the other continuation" waits to print



(define (print val)
  (if (or (eq? bound 'nil) (> val bound))
      (let ((old-cont the-other-continuation))
        (call/cc (lambda (cont)
                   (set! the-other-continuation cont)
                   (set! bound val)
                   (old-cont)))))
  (display val))

 

(define (run)  
  (call/cc (lambda (cont)
             (set! the-other-continuation cont)
             (inorder tree_a)))
  (inorder tree_b)
  (display bound)) ; ugly hack.. :(


```

The "store-and-call" bit is where we use call/cc to capture the current state of the computation into a variable that is passed as a parameter into the lambda, which in turn stores it in the variable, and does the same to the value we're trying to print (but are not allowed to print yet). Then we simply call into whatever is in the function parameter.

The "cond" is a gatekeeper that makes sure print suspends if the traversal calling print can't print yet -- there is a smaller value "queued up" by the waiting continuation. The first check simply makes sure that we don't go ahead without letting tree_b try first. It's the second one that does the actual comparison. Once we can be sure it's the other continuation that is waiting again, we are allowed to print!

Now, there's one issue with the code here and that is that when the first continuation to terminate does so, it just leaves the other one hanging -- the state is just discarded like any value as the program ends. So I need to actually explicitly print the last "bound"... my brain came to its limit for the time being when trying to avoid infinite loops with strategies to wake up the waiting continuation :)

Anyway, I'll try to think of other simple examples... would like to see others' too, as I'm trying to get "fluent" in continuation-passing-style :)

---

### Post by aks44 on 2008-04-09
Thanks for that. :)


I *think* I got how that example works, but TBH despite the ongoing IRC discussion I'm pretty sure I still don't get cc's. That's just too overwhelming ATM, but I'm working on it. ;)

---

### Post by mssever on 2008-04-09
I haven't learned any functional programming languages yet, so I don't fully understand your code, but I think that this is the way Ruby does all the time. Ruby calls such constructions blocks. For example, instead of a for loop, Rubyists would write ```
some_iterable_object.each do |item|
  # This is the body of a block, which is executed in the
  # scope in which it's defined, not the scope of the
  # each method.
end
```It also enables cool stuff like auto-closing files:```
File.open('some/file') do |file|
  file.each_line do |line|
    puts line
  end
end
```No need to explicitly close the file. I'm not sure how File.open is implemented, but this is equivalent (sans error checking):
```
class File
  def File.open(*args, &block)
    file = File.new *args
    begin
      yield file # file is passed to the block as an argument, and the block is executed in the scope in which it was defined; not this scope
    ensure
      file.close
    end
  end
end
```EDIT: I should add that blocks are one of my favorite Ruby features.

---

### Post by CptPicard on 2008-04-09
Ruby blocks are closures, which are sort of encapsulated frames. Continuations encapsulate an entire "stack" if you will :) And btw, Ruby does have call/cc. Try it :)

Btw, my code above is wrong as well, I need to remove the (inorder tree_b) call from inside the print function... working on it. :) (EDIT: Just corrected it)

---

### Post by Lau_of_DK on 2008-04-26
Picard,

Looking at your continuation example I feel like the worst programmer alive. Do you have some more documentation, some tutorials, some line/by/line guidance, something that would enable me to grasp this concept a lil more?


/Lau

---

### Post by CptPicard on 2008-04-26
Don't worry, I felt exactly the same way the first time I met them as well... and if you're unfamiliar with Lisp(s), reading is an additional issue although personally I find the Lispish syntax very clear (the format is always nested lists of essentially (function_name parameter parameter...))...

Aks44 "got it" when I explained to him in low-level programming (and implementation) terms that what call/cc does is that it captures your "state in the program" as far as stack goes and hands it over as a parameter to a function call. You can save that state in a variable, like I am doing in the example. Real Men don't do that but instead write their entire programs so that *every* function takes one extra parameter that contains the stack where-to the value from calling the continuation must be returned to.

Actually, a simple "return" statement in programming languages is a sort of degenerate implicit stupid version of continuation... when you call a function, it gets passed an "implicit parameter" (in CPUs this is the stack frame pointer). Then when you "call" the continuation, you call "return (value)" which magically appears in the place of the function call you made, just like happens in "normal" programming languages.

Exceptions are one step further -- they are so called escape continuations. This time, the continuation doesn't return to the one stack frame immediately preceding your function call, but it returns several stack frames back, unwinding the stack.

You should keep in mind here that in Lisps you shouldn't *really* think in terms of stack... but in terms of bindings. But for people used to thinking in terms of the CPU, the analogy is helpful, and in implementations, we are of course in practice playing with the stack.

Now, we've just talked of the everyday stuff you see in run of the mill languages that are corner cases of continuations. The trick with full continuations is that now the "where you return to" can be *anywhere* in your program where you have called call/cc, provided you still have the continuation object at hand. Also, you can call the continuation many times, materializing that other state at will as many times as you want. An important issue to remember though is that side-effects "outside of the stack" are not remembered, so "complete" program state is not preserved. But of course as you know, at least in theory everything can be written in pure functional style (and Haskellers do)!

In our stack-view of things, this is where things get really really interesting! Now you no longer have a single stack where you are able to jump backwards in... you actually have multiple tops of stacks where you can go back to, so your stack becomes a tree with each leaf being a continuation that you can "call" -- or if you discard the continuation, that branch of the tree gets abandoned altogether. Thus continuations actually give you a very concise and abstract way to implement something like pruning searches that do backtracking. Backtracking to last known good value, or jumping to some "current best value" we knew at some other branch is just an issue of calling the associated continuation.

Taking a more formal functional-programming point of view, CS professors tell you that a continuation is the "future" of the computation, but don't listen to them, it's more like the past.. it is, anyway, everything packaged into a single object that is needed to take the computation to its desired end, with some given parameter that is returned via "call" of the continuation. That kind of philosophy never helped me understand what it is though...

In the pure-functional formalism though, you can just simply look at how you're simplifying your expression by rewriting it by evaluating your functions, and whenever you do a call/cc, you just simply get a value that, when you call it, gets you back to that state of rewriting the expression. It really is not more difficult than that.

An interesting point is btw that in really formal approaches, continuation passing style where "return" is never implicit but all functions take a continuation where they pass their return value to, is useful in writing compilers. For example the Haskell compiler always first transforms everything into explicitly using continuations, because that is a more general form that all sorts of nice optimizations can be applied to.

---

### Post by Lau_of_DK on 2008-04-26
Thank you for that - It goes straight to the scrap book!

Now, let me see if I misunderstood everything: The way youre working with continuations is that at every pass of your program (when new functions are invoked) you save the entire memory-space of your program in an object. By memory-space Im thinking that when your executable it loaded into memory, you make sort of a raw copy of that data and pass that around in variables. Every new pass is a new branch in this virtual stack tree, where we can rewind to any given point at any given time. The new spawns occur with every call/cc. 

Is thats whats going on?

If Im even remotely close - could you try to add a few comments to your Scheme code, as its near-russian to me right now.

---

### Post by evymetal on 2008-04-26
Are you basically saying that this takes a copy of the stack above the point where it entered the local scope (where there's a reference to the instruction to return to), and puts that into the heap, then when you call it it moves the data back from the heap into the stack above the new calling instruction's return address - and continues processing from the top of the stack?

(sorry for not knowing the correct terms, I never had any formal training in CS so I never had to memorise all the correct names for any reason)

---

### Post by CptPicard on 2008-04-26
> **Lau_of_DK said:**
> Thank you for that - It goes straight to the scrap book!

Cool. There is the little star medal symbol at the bottom of each post you can use to show your appreciation -- I'm trying to keep my thanks/posts ratio around 10% --- every 10th post should be something else than bs ;)

> 
Now, let me see if I misunderstood everything

You are sort of very close really... not quite, but remarkably so. We can work from here.

> The way youre working with continuations is that at every pass of your program (when new functions are invoked) you save the entire memory-space of your program in an object.

Not the entire memory space (I thought this initially too a few years back). Continuations only hold your program state as far as your "call stack" goes, which is equivalent to the pure-functional evaluation state -- side effects are somewhere outside the scope of your current stack of binding (stack) frames. And there are no "every passes of program", whatever you mean by that... there is a single pass of program going on all the time. But that's picking nits.

> By memory-space Im thinking that when your executable it loaded into memory, you make sort of a raw copy of that data and pass that around in variables.

Don't think that low level... just think stack. You're passing "a version of stack" in a variable.  Interestingly, one version of stack plus code plus some value to return to that waiting stack frame equals everything you need to complete the computation, so therefore, continuations are called the "futures" of the program, because they *hold everything you need to go the end of the program*. To me it was a bit unintuitive the first I was told that, but it does make sense if you think of it. Call/cc makes a "hole" in your program, and stores your whole program minus that hole in a variable. When you call the continuation, you fill in that hole (but the analogy sort of fails in the sense that you don't get the result of the "entire computation" as the result of the "call" -- the current continuation is just abandoned). 

If the above confused you, ignore it and just think of stack, I can't help going off on a tangent...

But you ARE of course correct in the sense that if your program is pure-functional, the continuation DOES hold the entire memory space...


> Every new pass is a new branch in this virtual stack tree, where we can rewind to any given point at any given time. The new spawns occur with every call/cc.

Yeah, sort of. The key idea is that we have a variable that holds the "state of the pass through the other tree", and whenever we find that there is a smaller value coming up in the other tree than we have, we need to pass control, so we simply save our *own* state in the "waiting continuation" variable and invoke the waiting continuation, magically getting to the "other state" that had to "hold" before!

If I had wanted to be really really fancy about it, I would not even have used a global variable. This can be implemented so that the continuations just pass each other to each other, like.. "I need to wait for you, here *I* am, come back to me when you can, and pass yourself back for me to do the same". But using a variable is clearer... and I just wanted to hack up a simple example.

Damnit I really hope that all those "OMG C is the most fundamental language and it's all you need!!" folks read this thread... :p

---

### Post by CptPicard on 2008-04-26
> **evymetal said:**
> Are you basically saying that this takes a copy of the stack above the point ...

Yeah. That's it, esp. in implementation terms.

EDIT: Damn, that was a very excellent explanation now that I think of it :) Too bad I can only give you one star :(

EDIT2: Actually, now that I return to this and reread it, you're a bit off in the 

> 
then when you call it it moves the data back from the heap into the stack above the new calling instruction's return address - and continues processing from the top of the stack

part. Calling a continuation simply replaces your current stack, it does not put anything on top of the current stack.

---

### Post by Lau_of_DK on 2008-04-26
Captain,

I understand now! The 'versions of stack' and the simulated conversation between the 2 threads really brought it home for me. And yes, you have most definately earned your star!

ps: That last comment about C cracked me up, but this time im laughing WITH you !! :lolflag:

---

### Post by CptPicard on 2008-04-26
> **Lau_of_DK said:**
> the simulated conversation between the 2 threads really brought it home for me.

And let's remember that this is all single-threaded... it's one of the strengths of continuations -- if you can model your code in terms of continuation passing which is a form of co-operative multitasking -- you don't need to worry about thread synchronization because there is always just one thread. Of course if the co-operation is buggy then it just all fails. These kinds of co-operative "threads" can be very efficient btw in certain applications. 

Personally I feel that synchronizing threads is much more of a problem than managing your continuations once you understand them... I like knowing that I am the only thread of execution while I'm at it, unless I specifically swap execution states. And as I tried to show in my example, continuation swapping can, with the use of external state "on the heap" (figuratively), be used to "multithread" code that you don't need to actually alter much. The "inorder" function knows nothing of what is going on!

---

### Post by Lau_of_DK on 2008-04-26
> **CptPicard said:**
> And let's remember that this is all single-threaded... it's one of the strengths of continuations -- if you can model your code in terms of continuation passing which is a form of co-operative multitasking -- you don't need to worry about thread synchronization because there is always just one thread. Of course if the co-operation is buggy then it just all fails. These kinds of co-operative "threads" can be very efficient btw in certain applications.

Apropos - Have you got some links to examples of Lisp being used in actual programs. I imagine it would be simple to write a mean webserver that was much more capable of handling high pressure than what we have today...?

---

### Post by CptPicard on 2008-04-26
If you want a Lisp webserver, ask lsnostdal. Your current seeing of the light will have made him much more receptive to helping you I'm sure :)

---

### Post by Lau_of_DK on 2008-04-26
> **CptPicard said:**
> If you want a Lisp webserver, ask lsnostdal. Your current seeing of the light will have made him much more receptive to helping you I'm sure :)

No Im not looking for a Lisp webserver - I just remember reading some theories on how to profile peaks using some form of AI, which helped webservers deal with heavy loads better than before. Then I thought, thats a job for Lisp.

Anyway - 
import off_topic from CptPicard.

My question is this: Do you have some simple examples, tutorials, links or docs of actual programs written in Lisp (to get me started) ?

---

### Post by CptPicard on 2008-04-26
Google Is Your Friend... Lisp is under-appreciated for some reason, but there is stuff written in it. For example, the wonderful, all-encompassing Emacs editor was originally all in Lisp, running on a Lisp machine... nowadays it's an Emacs-Lisp interpreter written in C, with most of the parts of the editor written in Emacs-Lisp. That's why it is so extensible...

I really wish there was a kind of best of both worlds version of Lisp. Common Lisp is very practical and *can* be used to do pretty much anything any other language can... Scheme on the other hand is nicely minimalistic and has a few key primitives built in that CL does not have (yield and call/cc). I suppose currently CL is closer though.

---

### Post by evymetal on 2008-04-26
> **CptPicard said:**
> Too bad I can only give you one star :(

Thanks, it's amusing that my first "thanks" is for a post on a thread I was reading to learn something new from - my ratio is now somewhere around 1 percent. Thanks returned for posting the thread!

Come to think of it, I think I remember one of my parents mentioning something like this to me when I was a kid (they were programmers back in the days when you coded in hex/binary on paper and got a secretary to type it up onto punch cards - A friend of mine currently has the job of upgrading one of the systems they helped write, which is still in use in a large international bank!)

I'll have to look into Scheme - I had a go at common lisp a few years ago but never wrote much in it.

---

