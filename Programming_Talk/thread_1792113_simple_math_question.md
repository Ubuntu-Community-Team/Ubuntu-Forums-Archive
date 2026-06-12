---
title: "simple math question"
date: 2011-06-27
forum: Programming Talk
---

### Post by t1497f35 on 2011-06-27
Hi,
I'm starting to learn math, have a look at the red underlined statement from screenshot of the book, to me that statement seems suspicious and hypocritical since same argument can be used to say "It therefore cannot be true. So it must be false" which would make that truth-table wrong. Don't you find so? Any comments/explanation?

---

### Post by doas777 on 2011-06-27
I **think** it means that since A implies B, if A is false it implies that B is false. but since A is false, B is not evaluated, it can't be the conclusion to the hypothsis. since B cannot be implied from A, it has to be true.  I believe its the implication that was eluding you. it took me 4 times through to come to that conclusion.

man, that is an awful book you have there.

---

### Post by t1497f35 on 2011-06-27
Thanks, can you suggest a math book for someone like me who only knows how to do +-*/ ?

---

### Post by doas777 on 2011-06-27
> **t1497f35 said:**
> Thanks, can you suggest a math book for someone like me who only knows how to do +-*/ ?
well, what kind of math are you trying to learn? that is more of a classical logic or discrete math topic. theory rather than arithmetic.

no I don;t know any good books on the topic, but I think if you look for somthing newer, it may help. textbooks have gotten much much better over the last 20 years.

---

### Post by t1497f35 on 2011-06-27
That's "Discrete mathematic demystified" (2009) by Steven Krantz.
I'm learning OpenGL and without a solid math brackground it goes really slow.
I started reading "Math for 3d game programming... 2nd ed" but already at page 13 the author starts using scary stuff/formula like on screenshot below, so I decided to start with something more basic and then come back to this book, this way I came across the discrete math book.

---

### Post by Pierrick584 on 2011-06-27
here's a book suggestion

[http://www.amazon.com/Everyday-Math-Dummies-Charles-Seiter/dp/1568842481](http://www.amazon.com/Everyday-Math-Dummies-Charles-Seiter/dp/1568842481)

---

### Post by EvilMarshmallow on 2011-06-27
Discrete math is very... erm, different... from "Math".  Discrete math is the distillation of logic to its basic principles.  Think of it as "how to prove things".

If you're looking to learn math for opengl programming, you'll likely want to cover some calculus, trigonometry, and linear algebra topics.  Those will teach you the foundations for the math that you'll use when you're calculating things for your programs.  

Don't count discrete out though!  It's a very handy skill, both within math/programming and in other fields.  I wish most of the people I work with knew more about logic than they do.

---

### Post by t1497f35 on 2011-06-27
Thanks anyone!

---

### Post by F.G. on 2011-06-27
hi,
regarding your query in the picture basically:

if any proposition or statement is either true or false (ie has a boolean value which can only be true or false, no where between)
if the statement S: 'if A then B' is true or false
if A is false then the value of B cannot effect the value of S
(as the outcome of S is true or false regardless of the value of B)
in this case S is evaluated as true, as S cannot be evaluated as false.

as far as I can tell this an arbitrary thing about logic, it makes no real sense. it is the same as saying that if the moon is made of green cheese the sun will be late rising tomorrow morning must be true as it cannot be false.  interestingly this would essentially evaluate all subjunctive conditional branches to be true, which in turn would mean that all un-taken branches must be evaluated to true, which is nicely coherent with the programming (ie that the logic of the un-taken branch is still true).

i may have got this wrong, i'm assuming that the parallel lines with the arrow mean implication, or the material conditional.  in which case i think this explanation is correct.

---

### Post by cyberslayer on 2011-06-27
> **doas777 said:**
> I **think** it means that since A implies B, if A is false it implies that B is false.
man, that is an awful book you have there.

Not quite.  The table is for if, not "if and only if".  You can think of "if A then B" as meaning "if A is true, so is B" as it says in the picture attached.  However, if A is false, this says nothing about B since then the statement does not apply.

---

### Post by doas777 on 2011-06-28
> **cyberslayer said:**
> Not quite.  The table is for if, not "if and only if".  You can think of "if A then B" as meaning "if A is true, so is B" as it says in the picture attached.  However, if A is false, this says nothing about B since then the statement does not apply.
I'm with you, but that does not quite lead us to why B cannot ever be false if A is. as I am reading it, the yeild sign => indicates an implication between hypothesis and conclusion. its a bit out of my depth however.

---

### Post by F.G. on 2011-06-28
> **cyberslayer said:**
> Not quite.  The table is for if, not "if and only if".  You can think of "if A then B" as meaning "if A is true, so is B" as it says in the picture attached.  However, if A is false, this says nothing about B since then the statement does not apply.
I agree with cyberslayer, if and only if is a very different logical statement, and i think is represented with a double ended arrow ie something like this <=>. if and only if means: 
if A then B is equivalent to if B then A, 
this is not the same as a normal conditional. i point you in the direction of alice in wonderland, and the mad hatters tea party:

[http://en.wikiquote.org/wiki/Alice's_Adventures_in_Wonderland#Ch._7_-_A_Mad_Tea-Party](http://en.wikiquote.org/wiki/Alice's_Adventures_in_Wonderland#Ch._7_-_A_Mad_Tea-Party)

to put it simply I see what I eat and I eat what I see do not mean the same thing.

---

### Post by doas777 on 2011-06-28
> **F.G. said:**
> I agree with cyberslayer, if and only if is a very different logical statement, and i think is represented with a double ended arrow ie something like this <=>. if and only if means: 
if A then B is equivalent to if B then A, 
this is not the same as a normal conditional. i point you in the direction of alice in wonderland, and the mad hatters tea party:

[http://en.wikiquote.org/wiki/Alice's_Adventures_in_Wonderland#Ch._7_-_A_Mad_Tea-Party]("http://en.wikiquote.org/wiki/Alice%27s_Adventures_in_Wonderland#Ch._7_-_A_Mad_Tea-Party")

to put it simply I see what I eat and I eat what I see do not mean the same thing.
I hear what you are saying, but if that is the case, then how does not seeing somthing imply that you can or can't eat it? that seems to be the critical question here. 
the book reference indicates that b always equals a unless a is false in which case b (which **should** be false; this is the point of contention the op asked about) cannot be false so must be true. if b is not always to be equal to a (unless b is undefined), then you could just as easily say that b **should** be true, but can't be true so must be false. 

there has to be a relation between A and B for anyone to assert that if A is false B should be false but cannot be, and thus is true.

---

### Post by beew on 2011-06-28
A -> B is a sentence built from A and B with the connective -> (imply),  its truth value is determined by the truth values of A and B by the truth table in the screen shot. So basically it is just a boolean function with A and B as arguments (1 = true, 0 = false)

 It kind of captures the intuitive meaning of "imply" but a bit more. In real life we don't make assertions (of truth or falsehood) with antecedents (A) known to be false, it is only in rhetorical "sentences" like "If pigs fly then I will pay you back". This is not really a true or false statement in ordinary speech, it basically is just a rhetorical way to say I will never pay you. 

But in formal logic we don't consider such subtleties, in particular, A and B don't have to have any semantical relationship. In sentential calculus we are just concerned with the way truth values are combined. So technically we will consider "if pigs fly then I will pay you back" to be "true" simply because 1) We have to assign a truth value to every 'sentence",--even in real life we don't and 2) it is not false, because *in a formal as well as intuitive sense* an assertion of implication can only be refuted if the antecedent turns out to be true but the conclusion does not hold up (A-> B is false if and only if A is true and B is false) 3) Since the sentence has a truth value (T or F) from 1) and it cannot be assigned F because of 2) so it has to be assigned T.

---

### Post by doas777 on 2011-06-28
> **beew said:**
> 
But in formal logic we don't consider such subtleties, in particular, A and B don't have to have any semantical relationship. In sentential calculus we are just concerned with the way truth values are combined. So technically we will consider "if pigs fly then I will pay you back" to be "true" simply because 1) We have to assign a truth value to every 'sentence",--even in real life we don't and 2) it is not false, because *in a formal as well as intuitive sense* an assertion of implication can only be refuted if the antecedent turns out to be true but the conclusion does not hold up (A-> B is false if and only if A is true and B is false) 3) Since the sentence has a truth value (T or F) from 1) and it cannot be assigned F because of 2) so it has to be assigned T.


somthing is starting to tickle at the back of my head regard 2), but lets start with 3)

> 3) Since the sentence has a truth value (T or F) from 1) and it cannot be assigned F because of 2) so it has to be assigned T.

why woudl you try to assign it F at all? couldn't you just as easily try to assign it true? additionally the table does show that S(F=>F) = T.  is it just because an S( A->B ) can only be false if A is false and B is true?

---

### Post by F.G. on 2011-06-28
i guess the main point is to consider all of the truth values independently, and then it becomes a bit clearer.  consider a statement S, it can be true or false. S states that 'if A then B'. if A is false, and B is false S can still be true.

ie 'if it is raining then i'll get wet' can be true.
even if 'it is raining' is false, ie it's not raining.
and 'i'll get wet' is false (ie i'm not wet).

if the first part a conditional is false it is difficult to intuitively decide if the statement as a whole is true or false, the convention in logic and programming is to consider the statement as true.  

if the first part is true and the second part is false then the statement as a whole must be false (obviously), in all other circumstances it is evaluated as true.

in all of these circumstances it is possible for A and B to be completely unrelated and yet for S to appear true, i think this is where alot of superstition comes from, ie taking inductive reasoning and inferring deductive beliefs from it.

---

### Post by beew on 2011-06-28
> **doas777 said:**
> somthing is starting to tickle at the back of my head regard 2), but lets start with 3)



why woudl you try to assign it F at all? couldn't you just as easily try to assign it true? additionally the table does show that S(F=>F) = T.  is it just because an S( A->B ) can only be false if A is false and B is true?

So it is assigned true, that is what I said.

---

### Post by ve4cib on 2011-06-28
Just to toss in another example, since examples tend to make things more clear (or they do to me anyway)...

**A --> B**
If an animal is a bird then it has wings.

We can rephrase this to be "Being a bird implies that you have wings," if you want.  Same meaning, but a slightly different way of wording it.  Alternatively "Bird --> Wings" could get the point across too.

(And for the duration of this example we are looking at the species in its natural state; no birds that have been subject to wing amputation, birth defects, or similar mishaps.)

So, if A is true (whatever animal we are looking at), B *must* be true, since being a bird implies that wings must be present.

If B is false then A must likewise be false.  If the animal in question does not have wings it cannot be a bird, since birds must have wings.

However, if B is true is *possible* that A is true or false.  All we know is that the animal is some winged creature.  It could be a bird (A is true), or it could be a pegasus (A is false).  Simply knowing that B is true gives us no information about the state of A.

Similarly, if A is false, we have no information about B.  The animal is not a bird, but that does not mean it cannot have wings.  The animal could be any non-bird.  e.g. insect (B is true) or a beaver (B is false).


As for the truth table of A --> B, this simply indicates whether or not the implication contains a contradiction:

T --> T is true (a bird with wings)
F --> F is true (a non-bird without wings, e.g. bear)
F --> T is true (a non-bird with wings, e.g. insect)
T --> F is false: a bird without wings cannot exist, and therefore we have a contradiction


Hopefully this makes things a little bit clearer for anyone who's still confused.

---

### Post by beew on 2011-06-28
> **F.G. said:**
> 
in all of these circumstances it is possible for A and B to be completely unrelated and yet for S to appear true, i think this is where alot of superstition comes from, ie taking inductive reasoning and inferring deductive beliefs from it.

I think most people are a bit unclear about the role of mathematical/symbolic logic. That include many philosophers who write textbooks on the subject. The point of symbolic logic is not so much to teach you "how to think logically" in everyday situations through formal thinking, but rather formal logic is a model or caricature of certain way of reasoning, namely  the kind of reasoning typical in mathematics (hence also computer science. Theoretical computer science is a branch of math). Once we have such a model we would be able to analyse mathematical reasoning, explore its strength and limitations using mathematics itself!  So, as Yuri Manin ( the great Russian mathematician) said mathematical logic as a quality of introspection to it. The philosophers confuse the issue by peppering their textbooks with poorly contrived and convoluted examples of applying these stuffs to real life, which is not the point at all.

---

### Post by doas777 on 2011-06-28
> **beew said:**
> So it is assigned true, that is what I said.
my point was that by attempting to assign B = true, it can't be, because B is unevaluated so B must be False? seems as reasonable as attempting to set b = F, but because B is unevaluated B must be True as is stated in the text. I'm saying that the assumption that B must be F when A is, seems completely arbitrary, and you could just as easlily turn it around.

saying that any boolean value becomes its opposite whenever it is unevaluated seems unsupportable, but that seems to be what I am seeing/hearing. in order for B to flip from false to true, it had to be false first. that means that since the value is unevaluated, it must have a value before it can have a value. chicken egg.

---

### Post by Maheriano on 2011-06-28
After completing a computer science degree, I can say the image is correct. Though I don't know why you would choose discrete and combinational mathematics as your first choice of math to learn on your own.

---

### Post by F.G. on 2011-06-28
> **beew said:**
> I think most people are a bit unclear about the role of mathematical/symbolic logic. That include many philosophers who write textbooks on the subject. The point of symbolic logic is not so much to teach you "how to think logically" in everyday situations through formal thinking, but rather formal logic is a model or caricature of certain way of reasoning, namely  the kind of reasoning typical in mathematics (hence also computer science. Theoretical computer science is a branch of math). Once we have such a model we would be able to analyse mathematical reasoning, explore its strength and limitations using mathematics itself!  So, as Yuri Manin ( the great Russian mathematician) said mathematical logic as a quality of introspection to it. The philosophers confuse the issue by peppering their textbooks with poorly contrived and convoluted examples of applying these stuffs to real life, which is not the point at all.
hmmm...  not applicable to real life? it is certainly true that this kind of logic is only applicable to boolean systems.  then again there are probabalistic equivalencies which can be applied to non-boolean systems.  i suppose arguably you still need to have fairly complete set of data to apply  them.  i don't really know enough about this.  people certainly misuse logic in real-life arguments.

---

### Post by beew on 2011-06-29
> **doas777 said:**
> my point was that by attempting to assign B = true, it can't be, because B is unevaluated so B must be False? seems as reasonable as attempting to set b = F, but because B is unevaluated B must be True as is stated in the text. I'm saying that the assumption that B must be F when A is, seems completely arbitrary, and you could just as easlily turn it around.

saying that any boolean value becomes its opposite whenever it is unevaluated seems unsupportable, but that seems to be what I am seeing/hearing. in order for B to flip from false to true, it had to be false first. that means that since the value is unevaluated, it must have a value before it can have a value. chicken egg.

You are too hung up of the semantic meaning of "->" , think of it as an abstract function which assigns a value (T/F) to each ordered pair of T or F (1 or 0)  The assignment is given by the table in OP's screenshot. Now for the assignment (1, 0) --> 0 ; (1, 1) --> 1  you can obviously interpret it as "imply" in ordinary language (actually not quite, but will come to that later) so the controversy is what to make of the cases (0, 1) --> 1 and (0,0)--> 1 , well if you think about it, these can be incorporated within the same interpretation as a kind of convention if you argue the way I did before. It is not a proof, but a plausible argument that such an interpretation would be **consistent** with the usage of "imply" in mathematical reasoning, though in truth no one would try to prove something with a false antecedent (since you can prove anything with a false antecedent in this scheme) 

If this bothers you just think of it as not ordinary "imply", but an **extension** to it.

Also, as hinted at before even the cases (1, 0) and (1,1) don't capture exactly "imply" in natural language, because in the latter to say A implies B would usually subsume that there is some relationship between A and B, but here the actually meaning of A and B is irrelevant, only the combination of truth value. In real life you would not say something like "1+1 = 2 implies your mother is a woman" though it is a true statement logically.

Man this brings back memory, I taught a course on discrete mathematics a few years ago and that was the kind of discussions we had on the first week. :)

---

