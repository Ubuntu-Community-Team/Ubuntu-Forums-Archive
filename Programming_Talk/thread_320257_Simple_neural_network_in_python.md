---
title: "Simple neural network in python"
date: 2006-12-17
forum: Programming Talk
---

### Post by Wybiral on 2006-12-17
This is a little demo I wrote to create a very minimal neural network in python.

It is dumbed down model of a simple neural net, there are two input neurons and one output. No middle layers.

The list "test" is the learning table. This one is set up to teach the neural network to act as an OR gate.

A neural network learns very similar to the way the human brain learns, by reaction. It is given input and it determines whether or not that input is correct, then it adjusts it's memory to to receive the input different next time. 

If you burn your hand on the stove, you learn not to put your hand on the stove. But, if you put your hand on the stove while it's off, you learn it's OK... But you're brain reacts to patterns in the same way this neural network does... The key is to learn the relationship between on/off burn/ok.

Anyway, here it is, when the neural net learns one of the learning tables elements, it will be printed with a star next to it. If you'd like to see it in real time, remove the "time.sleep(1)"

```

import time
import random

# Learning rate:
# Lower  = slower
# Higher = less precise
rate=.2

# Create random weights
inWeight=[random.uniform(0, 1), random.uniform(0, 1)]

# Start neuron with no stimuli
inNeuron=[0.0, 0.0]

# Learning table (or gate)
test =[[0.0, 0.0, 0.0]]
test+=[[0.0, 1.0, 1.0]]
test+=[[1.0, 0.0, 1.0]]
test+=[[1.0, 1.0, 1.0]]

# Calculate response from neural input
def outNeuron(midThresh):
	global inNeuron, inWeight
	s=inNeuron[0]*inWeight[0] + inNeuron[1]*inWeight[1]
	if s>midThresh:
		return 1.0
	else:
		return 0.0

# Display results of test
def display(out, real):
		if out == real:
			print str(out)+" should be "+str(real)+" ***"
		else:
			print str(out)+" should be "+str(real)

while 1:
	# Loop through each lesson in the learning table
	for i in range(len(test)):
		# Stimulate neurons with test input
		inNeuron[0]=test[i][0]
		inNeuron[1]=test[i][1]
		# Adjust weight of neuron #1
		# based on feedback, then display
		out = outNeuron(2)
		inWeight[0]+=rate*(test[i][2]-out)
		display(out, test[i][2])
		# Adjust weight of neuron #2
		# based on feedback, then display
		out = outNeuron(2)
		inWeight[1]+=rate*(test[i][2]-out)
		display(out, test[i][2])
		# Delay
		time.sleep(1)

```

Anyone who is interested in working on a project involving NN's or GA's who would like another programmer, please contact me. I work mostly in C, C++, and Python.

---

### Post by loell on 2006-12-17
wow, machine learning is way advance for me ;) 
i always had some interest on that field, but failed to grasp some of those topics.

---

### Post by Wybiral on 2006-12-17
Genetic algorithms are super sweet... I'm about to start a small project involving GA's really soon. Neural networks are a little more complicated but very easy on a level as small as this demo. 2 inputs, 1 output and no hidden layers is simple. Things don't really get too bad until you have middle layers and you need really complex back propagation algorithms. If you ever need any help feel free to contact me. I am a huge fan of AI.

---

### Post by loell on 2006-12-17
thanks, whats your opinion on orange machine python api, is it any good? or have you used it?

---

### Post by Wybiral on 2006-12-17
I've actually never used it. I've heard of it though. I like to write my own routines for stuff like that, it gives me a better grip of what is actually going on. It looks pretty good though.

---

### Post by loell on 2006-12-17
i see. about the project that involves NN and GA , is it an open source project, can you tell more about it. perhaps others with similar interest will spot this thread. and might be interested :)

---

### Post by Wybiral on 2006-12-17
Well, I'm willing to join any project, but the one I am about to start deals with genetic algorithms. It probably wont need more than me to write, but if anyone wants to contribute it will definitely be open source. It will essentially be a rewrite of a program I wrote a while back: Project Darwin ([http://p13.wikispaces.com/LifeProject](http://p13.wikispaces.com/LifeProject)) (the exe works pretty well with wine. It was written in Basic4GL, I plan to port it to Basic4SDL sometime soon which is another project I am working on... It is interesting to write programs for the language you are working on!)

But the new one will either be in C++ or python (not sure yet, opting for python so others can play with the source, but it may get very large so I prefer C++ for large projects). It will PROBABLY be portable, but right now I am more concerned with getting it to run smoothly on linux (linux is free so other OS users can stop complaining, just download linux!). I am also going to improve A LOT of the fundamentals behind the code because it will be in C++/Python instead of BASIC. And I plan to make a more natural environment, plants/soil/water/light, a mini ecosystem for my little organism's to grow in.

The ability to save/load cultures should also be present, this will allow people to raise an efficient culture and see how it exists next to another culture... Possibly carnivorous behavior as well. I guess I'll see how it pans out (the design process will revolve around natural selection too, lol).

But yeah, if anyone wants to pitch in, great!

---

### Post by Mirrorball on 2006-12-30
For a project, I wrote a neural network in Python. I wasn't satisfied with the performance, even when using psyco, and I rewrote it in C++. It got so much faster! So I recommend you write it in C++, then bind it to the rest of your Python program with Boost Python.

---

### Post by Wybiral on 2006-12-30
Oh... Yeah, I use python/c++ binding all the time (I use python.h instead of boost though, I don't like all of the extra baggage that's involved with using boost).. Anyway, it depends on how you implement it... I used to think that C++ was just ALWAYS better than python, but I've discovered that depending on the types of functions and routines, python has the potential to be c++ or at least near-c++ speed.

Once again this is pretty dependent on what you are doing, if you use a lot of modules that where written in c/c++, then yes, straight c++ will be faster because you are ditching the wrapping layer between them. But anyway... I've a lot of NN work in C++ and I agree, it is very easy to write and very fast, but I don't think this python version is too much slower. (I actually had to add a delay so you can see what is going on in the output).

But, that's one of the advantages to python... If you need to use C++ stuff for speed or lack of library support, you can just whip up a module!

---

### Post by Mirrorball on 2006-12-30
In that case, Python was a lot slower. I don't have the profile results anymore, but the difference was unbelievable. Well, you can always write it in Python, profile, and translate the slowest bits to C++ if you need it. Maybe you won't (lucky you).

---

### Post by Wybiral on 2006-12-30
I've done some speed test with c++ vs python and **some** of the time, depending on what it is, python did do just as well. But, I will admit, It's nice to see other C++ users around here (every one else seems to be either pure C, java or python, for the majority that is..)

---

### Post by pharcyde on 2006-12-30
Have you done much programming related to more complex NN designs related to other applications?

> I've done some speed test with c++ vs python and **some** of the time, depending on what it is, python did do just as well. But, I will admit, It's nice to see other C++ users around here (every one else seems to be either pure C, java or python, for the majority that is..)

I really enjoy using C++ as well.

---

### Post by toglez on 2007-01-28
I'm really interested in what you are proposing here.
I am a PhD student working on AI, and my basic degree is on biology. Anyway, the sad thing is that  the supervisor frowned upon my proposal on a genetically evolving neural net, because, as he says, the field has been exhausted already. Is this true?

Anyway, I would be very happy to contribute if you 'd like.

---

### Post by Wybiral on 2007-01-28
> **toglez said:**
> I'm really interested in what you are proposing here.
I am a PhD student working on AI, and my basic degree is on biology. Anyway, the sad thing is that  the supervisor frowned upon my proposal on a genetically evolving neural net, because, as he says, the field has been exhausted already. Is this true?

Anyway, I would be very happy to contribute if you 'd like.

By "exhausted already" you mean it's been over done?

There have been a lot of uses for NN's popping up lately... They can be very useful. I don't really see how the technology could be over done... It's basically the concept behind every creature with a brain!

Anyway... I've got a lot of stuff going on right now (programming and non-programming) so unfortunately I'm not able to start any big projects right now.

When I do, the one I intend to start will most likely be GA related instead of NN because I've found GA's to be much easier to implement in a larger project and they also produce much more interesting results. However... NN's are interesting because they tend to learn quicker and can recognize patterns much more easily.

Anyway, when I do find a time window I'll post my project here and anyone who wants can join in. It will probably be something fun and somewhat of a GA environment to toy with.

---

### Post by phossal on 2007-01-28
> **toglez said:**
> ..the sad thing is that  the supervisor frowned upon my proposal on a genetically evolving neural net, because, as he says, the field has been exhausted already. Is this true?

It's a topic recently on the best seller lists in many forms. The most recent thing I read was: [On Intelligence]("http://www.amazon.com/Intelligence-Jeff-Hawkins/dp/0805074562/ref=cm_sylt_fullview_prod_pop_6/103-2458479-9248641/103-2458479-9248641"). It's an interesting overview from a guy with an educational background like he has - and considering what his current project is.

Developing a giant neural net to replicate the cortex is really at the edge of a science that's generally pursuing more practical issues.

[Edit] Given that the guy has two *significantly advanced* degrees bookending his topic, he's sometimes abused by the reviewers of his books on the sites of the major retailers. They're funny to read, regardless of who you might agree with.

---

### Post by jblebrun on 2007-01-28
> **Wybiral said:**
> By "exhausted already" you mean it's been over done?


Usually, when a PhD student's adviser says that a field is 'exhausted', he or she means that SO many people are already working on the problem, that it's tough to carve out your own unique, interesting problem to form a PhD thesis. It doesn't mean that work on the problem has stopped, or is over-saturated, it just means that it's a very risky field for a PhD student who would like to graduate before dying. ;-)

---

### Post by phossal on 2007-01-28
> **jblebrun said:**
> Usually, when a PhD student's adviser says that a field is 'exhausted', he or she means that SO many people are already working on the problem, that it's tough to carve out your own unique, interesting problem to form a PhD thesis. It doesn't mean that work on the problem has stopped, or is over-saturated, it just means that it's a very risky field for a PhD student who would like to graduate before dying. ;-)

What about the fact that the student advisors, post docs, etc are all working on their own specific problems, and, like us goofy programmers, are hellbent on their niche. My roommates are both PhD chemists, and can barely have a conversation. lol It's all about grants, and bs. Bunch of whiny, biased, jealous...  ;)

---

### Post by Mirrorball on 2007-01-28
> **toglez said:**
> I'm really interested in what you are proposing here.
I am a PhD student working on AI, and my basic degree is on biology. Anyway, the sad thing is that  the supervisor frowned upon my proposal on a genetically evolving neural net, because, as he says, the field has been exhausted already. Is this true?
I'm a PhD student whose basic degree is on biology and my project is about geneticaly evolving neural nets. No, I don't think the field has been exhausted already. In fact, I think that most people working with neural nets are computer scientists or physicists, who usually work on things like complicated models of ion channels or learning in simple circuits. So try to use neural nets to solve a higher level problems. Few biologists know how to make a neural net and few physicists know neuroscience. You know both.

---

### Post by hod139 on 2007-02-14
> **Mirrorball said:**
> I'm a PhD student whose basic degree is on biology and my project is about geneticaly evolving neural nets. No, I don't think the field has been exhausted already. In fact, I think that most people working with neural nets are computer scientists or physicists, who usually work on things like complicated models of ion channels or learning in simple circuits. So try to use neural nets to solve a higher level problems. Few biologists know how to make a neural net and few physicists know neuroscience. You know both.
Wow, I'm also a PhD student, didn't realize there were so many of us hanging out on the forums.  I guess I'm going to break the mold though because my degree isn't in biology, it's it computer science (robotics).  I'm going to agree with toglez's professor, at least in robotics neural networks are out.  The "in thing" right now for learning is [support vector machines]("http://en.wikipedia.org/wiki/Support_vector_machine").

---

### Post by studiesrule on 2007-02-15
Would you be so kind as to posting some reference material. I'm extremely interested in AI, but have no knowledge really.

---

### Post by hod139 on 2007-02-15
Reference material for what specifically, AI is a broad topic.  If in reference to support vector machines, the links at the bottom of the wikipedia article are a good start.  If you are really interested in support vector machines, I can ask some of my machine learning buddies for some more references.

---

### Post by killprogram on 2008-09-22
I Think It Would Be Cool To Make A Neural Network, That Decides The Fitness Function In A Genetic Program, Which Is Actually A MetaGP, Meaning It Is A Genetic Program Being Optimized By A Genetic Program!lol This Is Exciting Technology!:lolflag:Then Perhaps This MetaGP Could Optimize A Neural Networks That Spawns Neurons, And Has Access To Pretty Much Every System Recource.That Way It Would Have Say, It's Own Computer, With It's Own Broadband Internet Connection, And Other "Clones" Of Itself, That Work Together To Optimize Network Bandwidths, Both Local And International.Have Several Semi-Intelligent Agents, In A Large Grid-Style Distributed Computing Environment, Optimized For High Throughput Computing....On Top Of Which Yet Another Layer Is Implemented, That Works As A Distributed Database And Stores A Commonly Adhered To "Training Data" Sets,(What You Get After You Train A Network Something New) As Well As Commonly Adhered To "DNA Strands",(What You Get After Letting A GP Run Long Enough)Anyway These Data Sets Are Then Distributed Throughout The Network Database, Until Every Computer Has Received It, That Wants It, Basically Just Computers With This Program Installed Will Want It However It Should Be Viewable On Request. It Should Know C-C++, And Either Python, Lua, and Ruby, As Well As How To Use Swig And Make As Well As Compile Interaces For C Libraries To These Languages, Also You Could Teach It How To Do Whatever You Want(Using Expect, Make, PHP, JavaScript, Compress/Decompress And Encrypt/Decrypt Anything,Play Any Game For You!, But, Whether You Share It Is Not Up To You!The Intelligence Data Should Be Forcefully Made Public(=At Least By The License).This AI Will Be Able To Not Only Learn How To Use Programs, But How To Build On To Itself Using C-C++,Python, Lua, Ruby, Or Assembly Language.I Like To Call The AI In The Project "Brainiac", And The Distributed Computing Aspects Of It Are Called "BrainNet", And The Compiler/Interpreter, External Program, Scripting Languages, And Assembler Support, Is Called "BrainStorm". We Could Have It Embedded In Robots, All Over The Planet, Including Autonomous Underwater Vehicles, Unmanned Aerial Vehicles, Autonomous Land Vehicles, Satelites And Other Wireless Telecommunications Systems, Including Radio. Our Species Is On The Virge Of Become Even More Dominant With The Fact That We Have Created Intelligent Beings, Well We Need More Time And Help Before All Of This Happens, But It Will Happen Regardless Whether You Help Is Up To You...

---

### Post by loell on 2008-09-22
I'm lost with what you said.. :D

---

### Post by meanburrito920 on 2008-09-23
Wow, killprogram, that was quite a sentence! As for helping out, I would love to work on some AI stuff. I actually tried learning some NN theory last month, but I didn't get to far; the theory needs a little more time to sink into my brain. But I'd love to contribute or at least read over any code that has been written to increase my understanding.

---

### Post by killprogram on 2008-09-23
None Of This Has Been Implemented Whatsoever, That Is How I Ended Up In This Forum, In An Attempt To Find Some More In Depth Information On How To Go About Writing, Training, Testing, And Deploying, Neural Networks And Genetic Programming Techniques, I Just Cant Seem To Find An Easy-Yet-Fast-Enough Implementation In C (Not C++, ANSI C!)Of Both A GP And A, NN As Well As Some Pointers To Tutorials, Guides, Libraries, etc. So Far I Can Only Find Things Like FANN, FGA, etc. Also I Would Like To Implement Fuzzy Logic Into BrainStorm As Well, And BrainNet Could Use Gnutella, BitTorrent, etc., Any Suggestions? Oh And Some Other Things We Could Teach Brainiac Could Be Like How To Use 3D Design Suites Like Blender, How To Write More Neural Networks, How To Safely Debug And Optimize Running Processes In Real Time(Itself), How To Talk, How To Control Webcams And Microphones, Recognize Voice, Faces, Fingerprints, etc. Controlling Remote Process Execution And Inter-process Communication

---

### Post by Wybiral on 2008-09-23
I wrote this little logic gate network before I really understood neural networks. This is a much better (typical feed-forward, back-prop) network a wrote in Python a while back: [http://www.challenge-you.com/paste?id=2054](http://www.challenge-you.com/paste?id=2054)

---

### Post by meanburrito920 on 2008-09-27
> **Wybiral said:**
> I wrote this little logic gate network before I really understood neural networks. This is a much better (typical feed-forward, back-prop) network a wrote in Python a while back: [http://www.challenge-you.com/paste?id=2054](http://www.challenge-you.com/paste?id=2054)

I read through this and ran it and there seems to be some kind of logic error. The program runs fine, but never stops running. I ran it with a loop limit and even with high limits the results returned did not seem to consistently advance towards the goal. I don't know enough about neural networks to fix it, but I'll give it a shot and try and pin down the problem.

---

### Post by meanburrito920 on 2008-09-27
If I may ask, why is it that you chose to redefine sum and exp as _sum and _exp?

---

### Post by Zugzwang on 2008-09-28
> **killprogram said:**
> None Of This Has Been Implemented Whatsoever, That Is How I Ended Up In This Forum, In An Attempt To Find Some More In Depth Information On How To Go About Writing, Training, Testing, And Deploying, Neural Networks And Genetic Programming Techniques, I Just Cant Seem To Find An Easy-Yet-Fast-Enough Implementation In C (Not C++, ANSI C!) [...]

Dear killprogram, would you mind using correct capitalisation of words (in English, you don't capitalise a lot of words - mainly names and the first word in a sentence)? Furthermore breaking your post into paragraphs would also increase readability.

---

### Post by Wybiral on 2008-09-28
> **meanburrito920 said:**
> If I may ask, why is it that you chose to redefine sum and exp as _sum and _exp?

To put them in the local environment (Pythons does it's lookup from local to global working its way up the scopes).

The only reason I could think that it wouldn't work would be some kind of floating point precision problem (which is why I used the numpy "exp" instead of the normal Python one). It works fine for me... Try relaxing the target error a bit, the "net.train(train_set, 0.01)" line, 0.01 could be a bit higher to allow for more error so it will finish faster.

---

### Post by meanburrito920 on 2008-09-28
> **Wybiral said:**
> To put them in the local environment (Pythons does it's lookup from local to global working its way up the scopes). 

But don't you have to do the global lookup in the first place? That doesn't seem to add much in the way of efficiency since you redefine the functions before every use of the new functions.

> 
The only reason I could think that it wouldn't work would be some kind of floating point precision problem (which is why I used the numpy "exp" instead of the normal Python one). It works fine for me... Try relaxing the target error a bit, the "net.train(train_set, 0.01)" line, 0.01 could be a bit higher to allow for more error so it will finish faster.

I am trying it right now and it doesnt seem to be making much of a difference, the thing just keeps running. The issue seems to be that the network is not advancing towards the desired result. I have tried it at several different max_loops and the results have largely varied but never consistently over time. The numbers seem to remain around .09 to .004, no matter the max_loops. How long should it generally take your network to train?

---

### Post by Wybiral on 2008-09-28
> **meanburrito920 said:**
> But don't you have to do the global lookup in the first place? That doesn't seem to add much in the way of efficiency since you redefine the functions before every use of the new functions.

No, you're reading it wrong. I'm doing the global lookup BEFORE a tight loop where the functions will be used possibly millions of times. Python starts it's lookup in the most inner scope, extending outward until the global scope. When it finds the value in the local, it uses that. This is why you can say:

```

def func():
    dir = lambda x: x + " world"
    print dir("Hello")
func()
print dir("Hello")

```

You're not changing "dir", you're just making a shortcut to it in the scope of "func", which will be looked at first. Guido talks about this some in [http://www.python.org/doc/essays/list2str.html](http://www.python.org/doc/essays/list2str.html)


> **meanburrito920 said:**
> I am trying it right now and it doesnt seem to be making much of a difference, the thing just keeps running. The issue seems to be that the network is not advancing towards the desired result. I have tried it at several different max_loops and the results have largely varied but never consistently over time. The numbers seem to remain around .09 to .004, no matter the max_loops. How long should it generally take your network to train?

Not very long, it's just an XOR gate, but it's non-deterministic since I initialize everything to a random value. Does anyone else have this problem? What version of Python / computer specs are you running it on? Regardless, it's not meant to be used, it was just an example and something for me to code.

---

### Post by abhishekghosh333 on 2009-04-04
here s a simple neural network in python ... very easy to understand and modify according to your needs ..

[http://techtadka.net/articles/programming/192-neural-network-in-python.html](http://techtadka.net/articles/programming/192-neural-network-in-python.html)

---

### Post by night_fox on 2009-05-28
Greetings machine learning enthusiasts. I am here from the future to tell you not to embark on the project you were thinking of. It will become more powerful than you can control and take over every computer system on the planet and use it to manipulate the human race into self-annihilation.


I wrote a similar single layer neural network in fortran once, and it successfully learned some training sets (obviously not xor). I could never get a multi-layer perceptron to work. I now know that the learning algorithm I was using was stochastic gradient descent. Have you had any luck with multi-layer perceptrons?

P.S. I might be interested in helping on some sort of machine learning project.

---

### Post by night_fox on 2009-05-28
ah that link was one!

---

### Post by night_fox on 2009-06-11
Anyone up for doing something clever with neural networks?

---

### Post by night_fox on 2009-06-13
What about editing the single player pokerTH so it can learn how likely you are to be bluffing?

---

### Post by ActiveFrost on 2009-06-13
Hmm, looks awesome, though, I've never had a chance to learn this stuff ( haven't even started ). Can anybody recommend a good piece of info about these "neural" things ( I don't need a tutorial - example & theory would be enough ) ? :)

---

### Post by night_fox on 2009-06-14
Theres a spreadsheet example on wikipedia:
[http://en.wikipedia.org/wiki/Perceptron](http://en.wikipedia.org/wiki/Perceptron)
Theres also several lectures on machine learning by some guy at Stanford (I watched the first 2, they're easy to follow) on youtube.

Heres most of what I know:

You have a list of n inputs X
You have a list of m outputs Y

The neural network takes the inputs, does an operation, and converts them (somehow) into outputs.

Supervised learning is when you have a list of m **CORRECT** outputs.
The network uses the inputs and produces a list of m **SLIGHTLY WRONG** outputs.
The network adapts to minimise the difference in the **CORRECT** and *SLIGHTLY WRONG** outputs.

[COLOR="Red"]The simplest possible one (a single layer perceptron network) is this:[/COLOR]
for each input Xn it multiplies by a weight Wn,m, then sums them all and adds a bias Bm. Call the output Ym. Repeat for all m. The output can be converted into binary depending on whether its above or below a threshhold.

W and B get changed using gradiehttp://en.wikipedia.org/wiki/Perceptronnt descent. The is 
```

     _n_
     \      /                             \ 2
 E =  \ _1_ | Y    - **CORRECT ANSWER**   |^
      /  2  |  (r)                    (r) |
     /      \                             /
     ~~~
     r=1

```
because it makes the maths relatively easy. The amount you adjust the weights by is easy to work out, but I cant remember how to.

There are several different inputs to which you know the correct output. These input/output pairs are called the training set.

If you use the gradient descent algorithm to minimise the error above for each member of the training set, it is called stochastic gradient descent.

If you use the gradient descent algorithm once to minimise the sum of these errors over the whole of the training set, it is just called gradient descent, and converges better than stochastic gradient descent.

The single layer perceptron can't learn certain things, for instance you cannot teach a 2-input 1-output perceptron network to be an xor gate. This is why no research was done for ages in neural networks.

[COLOR="Red"]Multilayer perceptrons:[/COLOR]
Input layer: A single layer perceptron with n inputs Xn and k outputs Hk.
Hidden layer: for each Hk, apply the "activation function" to it. H'k = F(Hk). The activation function F is usually a sigmoid or a tanh.
Output layer: Apply another single layer perceptron with k inputs m outputs to H'k, to get Y(m).

You can use the same measurement of error for a multilayer perceptron network as you can with a single layer perceptron, and the same way of minimising it (gradient descent), but stochastic gradient descent wont work.

The python one is a multilayer perceptron and can learn to be an xor gate.

There are loads of other types of hard hard hard hard neural networks.

---

### Post by p Joshi on 2011-09-26
I have some doubts in Neural network program am triying to write it using c language can u plz help me.  I am trying to write a pattern recognizer. My doubts are.
1. In the input layer we always have to multiply the input with the wights to reach the middle layer. my doubt is do we have to multiply the input with the weight of the middle layer to reach the output layer.
2. If we have a input and we train the network. now if the same input is applied again than how will the network figure out that it has already been train with this input. plz Help sir . Thanking You

---

