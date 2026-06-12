---
title: "[JAVA] my circular linked list implementation"
date: 2008-12-20
forum: Programming Talk
---

### Post by babacan on 2008-12-20
Greetings,
I am trying to implement the circular single linked list algorithm to Java and I have done the most of the core part, just wondering if this would be an acceptable way of doing it?

```

class SingleLinkedNode{
int value;
SingleLinkedNode next;

SingleLinkedNode(int a){
value=a;
next=null;
}

}

class SingleLinkedUnsortedCircularList{
SingleLinkedNode head;
SingleLinkedNode tail;

SingleLinkedUnsortedCircularList(){
head=null;
tail=null;
}

void addElement(SingleLinkedNode input){
if (head==null){
head=input;
}
if(tail != null){
tail.next=input;
}

tail=input;
}

}

class SingleLinkedUnsortedCircularListTest{

public static void main(String[] args){

SingleLinkedUnsortedCircularList TestList = new SingleLinkedUnsortedCircularList();

SingleLinkedNode a = new SingleLinkedNode(1);
SingleLinkedNode b = new SingleLinkedNode(2);
SingleLinkedNode c = new SingleLinkedNode(3);
SingleLinkedNode d = new SingleLinkedNode(4);
SingleLinkedNode e = new SingleLinkedNode(5);
SingleLinkedNode f = new SingleLinkedNode(6);
TestList.addElement(a);
TestList.addElement(b);
TestList.addElement(c);
System.out.println("After inserting 1, 2, 3 to the testlist:");
System.out.println("head:" + (TestList.head).value );
System.out.println("tail:" + (TestList.tail).value );
TestList.addElement(d);
TestList.addElement(e);
TestList.addElement(f);
System.out.println("After inserting 1, 2, 3, 4, 5, 6 to the testlist:");
System.out.println("head:" + (TestList.head).value );
System.out.println("tail:" + (TestList.tail).value );
}
}

```

secondly, what exactly is a "sorted" linked list is about? While adding new elements will the adding function also checking the sorting of the list and putting them in a correct order?

Cheers

---

### Post by monkeyking on 2008-12-21
I've never really heard the excact phrase "sorted linked list"...

My best guess is that, if you want to insert a element in your list,
then you should place it in some special(non-random) place given by some specific ordering.

suppose you have a node, consisting of a key and data, and the ordering is strict ascending.

Then you would input your node such that all elements,their keys, before is smaller and after is heigher.

If the key isn't a numeric, then I would hash it to some numeric value.

good luck

---

### Post by dwhitney67 on 2008-12-21
The thread title is misleading, or perhaps the OP is not sure what he wants.  Is it s sorted linked list or is it a circular linked list??  It is obvious from the code that neither has been implemented.

What the OP has provided in a simple linked list, where a new new node is inserted at the tail.  No sorting has been done yet.  If sorting is required, then the insertion-sort algorithm should be considered.

If a circular list is required, then limits need to be specified as to what size the list will be.  Essentially the easiest way to create a circular list is not to use a linked-list, but to define a buffer (i.e. an array) of size N.

---

