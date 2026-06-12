---
title: "Question about program control in C"
date: 2011-12-21
forum: Programming Talk
---

### Post by ClientAlive on 2011-12-21
I was looking at some of the functions available in <math.h> and see that some of them involve more complicated math formulas (like trigonometric formulas like cos and tan, etc). What I'm wondering is if some of those more involved math formulas can come into play with program control? A simple comparisson that pops into mind is bubble sort. Bubble sort uses simple arithmatic to manipulate data and acheive the result. If there is a bubble sort and bubble sort uses math to do what it does - then is there other program control which uses more complicated math to do what it does?

Probably a pretty stupid question as I think I know what the answer is going to be - but I have to ask. It's either that or 'assume' and I don't think the latter is very healthy.

Thanks

---

### Post by nvteighen on 2011-12-21
> **ClientAlive said:**
> I was looking at some of the functions available in <math.h> and see that some of them involve more complicated math formulas (like trigonometric formulas like cos and tan, etc). What I'm wondering is if some of those more involved math formulas can come into play with program control? A simple comparisson that pops into mind is bubble sort. Bubble sort uses simple arithmatic to manipulate data and acheive the result. If there is a bubble sort and bubble sort uses math to do what it does - then is there other program control which uses more complicated math to do what it does?

Probably a pretty stupid question as I think I know what the answer is going to be - but I have to ask. It's either that or 'assume' and I don't think the latter is very healthy.

Thanks

One of the things I always insist on is that people should learn the technical terms of programming, not only programming languages, in order to make communication easier... What do you mean by "program control"?

---

### Post by ClientAlive on 2011-12-21
> **nvteighen said:**
> One of the things I always insist on is that people should learn the technical terms of programming, not only programming languages, in order to make communication easier... What do you mean by "program control"?


Ok, I'll do my best; but, I am just beginning to learn. Where I don't have a technical term to supply I'll try to explain how I'm thinking of it.

According to my understanding an algorithm is the solution to a problem. As I understand this term it would include not just the things that go on internally within the program to produce some result but...

You know? To be honest, no one has ever asked me that before and as I attempt to explain I'm thinking about it for the first time. Some very odd things are occurring to me as I do.

At any rate, I've thought of the term algorithm as meaning the entire solution - which would include user input, output from the program, calculations and data manipulation within the program and other things, to be sure. However, it seems to me this concept ought to include a more detailed breakdown of what goes on in a program. While I have not encounterd any such terms yet, it seems to me that each of those items in the list ought to have their own term (code to do with user input or taking user input, code to do with output from the program, code to do with data manipulation within the program, to do with calculations within the program, etc). While I wish I knew of these terms, I'm not sure it isn't a separate question and I'm gonna try not to hijack my own thread here.

Regarding my original question: I guess I was thinking about data manipulation within the program. I was certainly thinking about things that go on completely internal to the program - separate to any interaction with the user. Bubble sort would be a good example. In fact, it was when I first saw bubble sort that this question arose for me. I saw in it's code, that addition and subtraction were being used to move values stored in an array from one element to another, shuffling them around until the end result was acheived. More generally though it stood out to me (and I suppose I already knew it in the back of my mind) that it is math that is being used to manipulate those values. The way I pictured it was a connection between arithmetic and motion. This is key - *arithmetic and _motion_*

I've taken up to calculus level math. Though it has been a number of years, I do recall that the things you could do with calculus were pretty powerful (compared to say addition and subtraction). So it was at that moment (when I really grasped how bubble sort was working and 'what' it was doing to reach the goal) it was at that moment that I began to try to imagine code or a program that would employ much, much more complicated mathematics. Mathematics on the level of calculus, lets say. Or trigonometry.

Now I know that a person could include some calculation in their program that say, finds the flow rate of a liqud through a pipe and print the answer back to the user, but that's not what I meant. What I was thinking of is the part of the program entirely internal to that program. Examples might include things like data manipulation, possibly something like a compression algorithm (but I'm sure there are many other examples). The part of the program the user never sees.

So I guess it was more a fun natured question (at least to begin with). I was just wondering about a specific example where some really heavy duty math was employed to manipulate the internals of the program to acheive the result (not just addition and subtraction). When I saw the function calls for trig in the <math.h> library it reminded me of this question and kinda fired my imagination again.

I hope that makes sense. I'm sorry I can't do better by using actual, technical terms. I'm simply unaware of what they are. Sorry if this was too long winded - I was trying to be clear and explicit without having the ability to use technical terms.

---

### Post by Tony Flury on 2011-12-21
Of course there are algorithms that use more complex maths (maybe not sorts etc), but if for instance you need to start thinking about trajectories, rotations, 3D projects, then you quickly get to use trig functions and others.
Some compression functions use complex maths concepts too, like fractals etc (but how they are exactly implemented I don't know).

You are right that the entire solution could be viewed as an Algorithm (i.e. a process that takes inputs and generates outputs in some form), but remember that whole solution is made up of a lot of smaller algorithms (input of data from a keyboard and storing into memory is an algorithm, sorting data in memory, drawing onto the screen), and the art of a good s/w engineer is knowing how to stitich those smaller blocks together to make the whole.

Don't get too hung up on the seeming difference between the internal and visible functions of a piece of code, if you need to output data in a sorted form - or you need to sort the data so that you can process it later in some priority order, they are all critical parts of your algorithm, and ultimately effect what your user sees. There should be nothing that your program does that the user ultimately does not see (in some form).

For your benefit - the term program control normally refers to constructs likes loops (for, while), branchs (switch, if), and other similar constructs which allow your programm to repeat itself or make "choices" as to what piece of code to execute.

There are some basic building blocks in many programs - sort algorithms, data input/output etc - the key to these is to make them as quick as possible. It would be technically possible I guess to develop a sort algorithm that used trigonomety to accomplish the sort, but it would be almost certianly much slower than non-trig sorts since the trig functions themselves are probably pretty complex and therefore comparably slow to execute.

---

### Post by Arndt on 2011-12-21
> **Tony Flury said:**
> Of course there are algorithms that use more complex maths (maybe not sorts etc), but if for instance you need to start thinking about trajectories, rotations, 3D projects, then you quickly get to use trig functions and others.
Some compression functions use complex maths concepts too, like fractals etc (but how they are exactly implemented I don't know).

You are right that the entire solution could be viewed as an Algorithm (i.e. a process that takes inputs and generates outputs in some form), but remember that whole solution is made up of a lot of smaller algorithms (input of data from a keyboard and storing into memory is an algorithm, sorting data in memory, drawing onto the screen), and the art of a good s/w engineer is knowing how to stitich those smaller blocks together to make the whole.

Don't get too hung up on the seeming difference between the internal and visible functions of a piece of code, if you need to output data in a sorted form - or you need to sort the data so that you can process it later in some priority order, they are all critical parts of your algorithm, and ultimately effect what your user sees. There should be nothing that your program does that the user ultimately does not see (in some form).

For your benefit - the term program control normally refers to constructs likes loops (for, while), branchs (switch, if), and other similar constructs which allow your programm to repeat itself or make "choices" as to what piece of code to execute.

There are some basic building blocks in many programs - sort algorithms, data input/output etc - the key to these is to make them as quick as possible. It would be technically possible I guess to develop a sort algorithm that used trigonomety to accomplish the sort, but it would be almost certianly much slower than non-trig sorts since the trig functions themselves are probably pretty complex and therefore comparably slow to execute.

One example of a field where very much more advanced math can be used than is visible to the user is primality testing. To the user, it all only seems to be about divisibility by integer numbers, but among the best algorithms there are those that use elliptic functions (which are not even in libm).

---

### Post by 3Miro on 2011-12-21
Computer Science started as a branch of Mathematics and then it split off from there. CS today is mostly math, especially at the level of making algorithms. For example, the compiler class that I took as an undergrad was one of the hardest undergrad math classes.

What you have in <math.h> are just some very basic functions, sin() cos() exp() sqrt() log() ... Those are not going to help you sort an array and are useful only in special cases.

Bubble sort is also the weakest algorithm for sorting things. You want to look at Quicksort. This one uses a lot more advanced math, although it is not the math that you are used to form Calculus. Quicksort relies on Discrete Math, that works with graphs and trees. In fact, all programming languages are build around the mathematical concept of graphs.

Also, using addition and subtraction to swap values is a good demonstration of a concept and a good exercise, but you don't ever want to do that in practice.

---

### Post by ClientAlive on 2011-12-21
Wow. Right on!

I plan to take discreet math in the summer semester (maybe 4 mos from now). I'm really excited about it. It looks very different from the kind of math most people are used to and I hope to really get a lot out of it.

I never thought about there being a compiler class but that sounds neat. I'm not sure we offer that where I go to school but I'll have to take another look now.

Sure is neat to hear about these things going on in computer science you guys. It inspires me. Gives me something to dream about while I drudge through these boring, first baby steps of programming  :)

Thanks

---

### Post by Bachstelze on 2011-12-22
Care to explain how exactly Quicksort "relies" on graphs and trees? If anything, they are representations, and you use them to illustate visually how it works. That's all. the algorithm itself does not need any graph or tree data structure (as opposed to e.g. heap sort or topological sort).

---

