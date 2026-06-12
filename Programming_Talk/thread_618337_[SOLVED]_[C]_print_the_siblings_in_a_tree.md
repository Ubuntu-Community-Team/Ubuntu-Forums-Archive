---
title: "[SOLVED] [C] print the siblings in a tree"
date: 2007-11-20
forum: Programming Talk
---

### Post by DesertRose on 2007-11-20
.

---

### Post by smartbei on 2007-11-20
I had a hard time understanding what you meant exactly, but look at this:
```

void print(FILE *f, tree *elem)
{
	if (elem) 
	{
		int value1, value2;
		value1 = elem->getLeftChild()->getId();
		value2 = elem->getRightChild()->getId();
		if (value1 != 0 && value2 != 0)
		{
			fprintf(f, " %u\n" , value1);
			fprintf(f, " %u\n" , value2);
		}else if (value1 == 0 && value2 != 0)
		{
			//...
		}else if (value1 != 0 && value2 == 0)
		{
			//...
		}else
		{
			//both are 0
		}
	}
	else
		fprintf(f, "error!!!!!\n");
}

```
Now just fill in what you want done in each case. Why is the complicated decision tree necessary? It doesn't save LOCs (lines of code) or make the program any easier on the programmer to read.

If nothing works, you may want to check the output of your getId() - that seems to be the major change (other than a bunch of [if/else]s) in the code.

Lastly, please be consistent in your use of tabs/spaces, at the least so that the code looks good in these forums.

---

### Post by DesertRose on 2007-11-20
.

---

### Post by smartbei on 2007-11-20
Well, considering the fact that I have no idea what getId() looks like internally - ...ummm... :D.

Could you post getID and the class elem so that I/<anyone else on this forum> could take a look at them?

It might be a problem of type conversion, but I can't tell for sure without seeing the source.

---

### Post by DesertRose on 2007-11-20
.

---

### Post by DesertRose on 2007-11-20
.

---

### Post by iharrold on 2007-11-20
Shouldn't you be checking that the left and right children exist and are not null, prior to getting their id?  Ie, I am assuming you null terminate them, that if the element has a left, but not a right and you access the right->getID() you are actually accessing nothing.

---

### Post by smartbei on 2007-11-20
Here we go.
```

void print(TreeElement *elem)
{
	if (elem) 
	{
		int value1 = 0, value2 = 0;
		TreeElement *leftC = 0, *rightC = 0, *parent = 0;
		leftC = elem->getLeftChild();
		rightC = elem->getRightChild();
		if (leftC != 0)
			value1 = leftC->getId();
		if (rightC != 0)
			value2 = rightC->getId();
		
		if (leftC != 0 || rightC != 0) 
		{ //Note that I check the pointers, not the values - the values might really be 0 in the tree!
			printf(" Left:%u Right:%u\n" , value1, value2);
		}else
		{
			parent = elem->getParent();
			if (parent == 0)
				printf(" This node has no children or parents");
			else
			{
				if (elem->getParent()->getLeftChild() == elem)
					printf(" Left:%u Right:%u\n", 0, elem->getParent()->getId());
				else if (elem->getParent()->getRightChild() == elem)
					printf(" Left:%u Right:%u\n", elem->getParent()->getId(), 0);
				else
					printf(" Something is wrong - this node is not linked to by its parent!");
			}
		}
	}
	else
		printf("error!!!!!\n");
}
int main ()
{
 	TreeElement t1(1);
	t1.createLeftChild(2);
	t1.createRightChild(3);
	
	print(&t1);
	print(t1.getRightChild());
	
	return 0;
}

```

Note the changes I made to print. I changed its parameters a bit for my conveniance - should be no problem for you.

Currently, this is able to do the following:
[list]
[*]If the given node has two children, print them.
[*]If the given nodehas only one child, print it and 0 for the other, in the correct order.
[*]I this node has no children, print the parents id or 0, in order, depending on if it is left or right.
[/list]

You may need to add some granularity (some additional simple options), but this should serve as a good example so extending it will be simple.

The problem was that you can't do [object]->[method] if [object] is null, which happens in cases where the node does not have a child/parent.

Hope that solves your problem :)!

---

### Post by Wybiral on 2007-11-20
As a friendly suggestion, you should choose either C or C++. Currently your code is a strange mix of both. C (as the title suggests) doesn't have methods in it's structures (and it doesn't have classes at all). And if it's C++ then you shouldn't be using the old C IO library.

---

### Post by smartbei on 2007-11-20
You're right Wybiral, though the mix really isn't that strange - we are just using the cstdio library.

I used printf in my example code because it was apparent that the OP was using that anyway (from fprintf).

---

### Post by DesertRose on 2007-11-20
Oh, ** smartbei**, it works!!!!!!!!! oh my God!!!!!!!!!! THANK YOU!!!!!!!!!! :D:D:D:D:D:D

---

### Post by smartbei on 2007-11-20
Glad I could help.

BTW - what was this for? Or should I say...Homework for what class? :D

Oh - please mark this thread as solved.

---

### Post by DesertRose on 2007-11-20
.

---

