---
title: "Implementing Multi-layer Perceptron(Artificial Neural Network) in Python"
date: 2009-03-14
forum: Programming Talk
---

### Post by adamsnative on 2009-03-14
I have to write a code in python to implement Multi-Layer Perceptron (part of Artificial Neural Network,precisely a type of supervised learning in ANN). Its very hard to implement the whole thing at one go that too in python.[matlab has got pretty neat inbuilt functions for MLP,i dont know any such thing in python]

So it will be very helpful if you all can come up with something.

---

### Post by Wybiral on 2009-03-14
> **adamsnative said:**
> So it will be very helpful if you all can come up with something.

You mean do it for you? Hopefully not :)

What's your specific problem? Can you use an already written module, or is this homework?

---

### Post by monkeyking on 2009-03-14
Isn't the link [http://www.philbrierley.com/code.html](http://www.philbrierley.com/code.html)
given to you yesterday helpfull?

Couldn't you just do a intelligent copy paste from one of other languages.

---

### Post by adamsnative on 2009-03-14
the specific problem its hard to implement a multi layer perceptron thing into programming...have already implemented Self Organizing map[unsupervised learning]next on is this MLP.I need to put in atleast two layers of perceptron to make my system work...
Yup i can use a already written module and this is not any homework...

---

### Post by adamsnative on 2009-03-14
> **monkeyking said:**
> 
Couldn't you just do a intelligent copy paste from one of other languages.

I have the matlab code written by myself with me.Because i have implemented this in matlab.

But then too i cant write the whole thing in python becaue i am relatively new in python and dont know all its functions and methods.

In matlab there are inbuilt functions for nearly each complex step in ANN but do they have any such thing in Python???
I dont think so-and that means developing methods too from scratch.An 'intelligent copy paste' wont do justice here!

---

### Post by kjohansen on 2009-03-14
I recently did this in C++.

OOP is the best way to go for keeping track of layers and node.

You have a layer class which really only holds a list of nodes.  Each node will hold its weight and its output.

Then you can have a list of layers in order.

This makes the backpropogation algorithm easy to work with.  There are many books out there that have very good pseudocode for this.  Artificial Intelligence a Modern Approach by Russel and Norvig would be my choice.

---

### Post by gnusci on 2009-03-14
I also wrote one ANN in C++, basically a multi-layer perceptron using the back-propagation learning rule, you can find the code here:

[http://eetorres.googlepages.com/anna](http://eetorres.googlepages.com/anna)

However, I don't know Python at all, so I don't now if you can just translate the code though...

---

### Post by adamsnative on 2009-03-16
Thanx for all your help guys
But the thing is that i already have the ANN code in C,C++,C#,Java,Matlab...(nearly all languages) except python!!!!
And conversion of codes into python is not a easy thing,because different languages have different modules and functions!!!!
:(

Please help if u can-atleast in the conversion thing!!!

---

### Post by Wybiral on 2009-03-16
If you can use an existing module, use one. There's probably something you can use here: [http://pypi.python.org/pypi?:action=search&term=neural+network](http://pypi.python.org/pypi?:action=search&term=neural+network)

---

