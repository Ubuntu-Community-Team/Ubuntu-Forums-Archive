---
title: "C++ double linked list"
date: 2007-05-01
forum: Programming Talk
---

### Post by La Hechizera on 2007-05-01
hi there,

I have created a programm which uses a double linked list. when I enter a new element (that's char type) it places it in the end of the list. I also ...

---

### Post by amo-ej1 on 2007-05-01
Well you have two methods to follow, both differ a bit from architectural viewpoint. Starting with you current code, when you've finished reading (or before you do the print). You could call a sort() function which creates a new double linked list. The advantage is that this would fit in nicely into your existing code. The disadvantage is that this sorting will prove to be a pain in the a**. 

So the best approach is probably as follows. At the point you're reading your values you should insert you node sorted into you list, instead of at the back. Basicly using the following pseudo code:

```

node * tmp = head;
node * cur = readNode();
while(cur->val < tmp->val)
{
    tmp=tmp->next;
}

// Node should be inserted after tmp
tmp->next->prev=cur;
cur->next=tmp->next;
cur->prev=tmp;
tmp->prev=tmp;


```

But with proper end of list checking ...

---

### Post by La Hechizera on 2007-05-01
thanks amo-ej1..

---

### Post by La Hechizera on 2007-05-02
:neutral:

---

### Post by amo-ej1 on 2007-05-02
Well what have you tried ? What are you expecting and what isn't it doing ? Where do you expect your error lies ? Where is your proof of concept main() function clearly showing that things go wrong.

---

### Post by Jengu on 2007-05-02
Even though this reeks of a homework assignment, I'll give a little advice:

-If you're trying "hundreds of combinations" you're taking the wrong approach. Stop throwing lines around randomly wondering if *this* or *that* sequence of statements is correct for doing what you want, and actually spend some time thinking through the problem in your head and on paper, right down what the program should be doing, examine the code to see if it does that, etc. If you treat programming like alchemy you're likely to spin your tires in the mud.

-Try getting it to work on the smallest example possible, "ba". It should sort it to, "ab." Then see if you can get it working for "cba" -> "abc" and "bca" -> "abc". This process often helps and is a lot easier than dealing with complex inputs.

-Test the parts of your code apart to make sure they each work on their own. Have you tested that inserting/removing/swapping elements of the list works in general?

-It might be easier to first try to take a linked list of characters, and make a new linked list that has the same characters in alphabetical order, rather than trying to sort a linked list 'in place.' That way you don't have to worry about swapping things in the first list. Once you've solved that take a crack at the problem again.

-Editing the linked list so it's in alphabetical order, then printing it, might be easier to think about than trying to print it in alphabetical order without editing the list.

---

### Post by moma on 2007-05-02
For some time ago, I created a source package that contains good examples of some abstract data types. The data types are: A dynamic parray,  Doubly linked plist and Balanced ptree that uses the very effective black-red balancing algorithm ).  Study: [http://www.futuredesktop.org/adt/](http://www.futuredesktop.org/adt/)  The package name is "adt-0.1.tar.gz".

Read the "README" file. It says how to compile it and how to test all those data types.  
The "ptree_test" in /test directory creates some *.svg images that show how the tree is growing while nodes are inserted.  The "display" command is part of the Ubuntu's "imagemagick" package.

An idea: You could create a similar visual proof for your doubly linked list.  Then you can fix your code.

---

### Post by La Hechizera on 2007-05-02
to amo-ej1
main() wasn't there because there is no need in it, I mean there's only a switch of choices, so nothing that important.. the code I wrote works fine when printing as they go, the problem is in sorting the list.

Thanks Jengu.. and thanks moma, the link you've posted looks very useful! :)

---

