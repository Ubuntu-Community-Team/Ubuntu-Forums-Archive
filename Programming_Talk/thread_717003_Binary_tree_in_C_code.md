---
title: "Binary tree in C code"
date: 2008-03-06
forum: Programming Talk
---

### Post by tjfrit01 on 2008-03-06
I need to take in an ASCII character input and convert in to a binary tree in array form and then have that array print out in preorder, postorder, and inorder.  However, I am not sure how to take the input and put it into an array in binary tree format while getting rid of duplicates.  Any help would be much appreciated!

Thanks in advance,
Tom

---

### Post by aks44 on 2008-03-06
I'm afraid your question is very vague and looks like [homework]("http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2")...


What is your (TECHNICAL) problem exactly?

---

### Post by LaRoza on 2008-03-06
If you "need" to do this, you must have a reason, either it is for personal use/fun, or it is homework.

You have a clearly defined problem, with interesting requirements, and that says "homework".

Thread Closed, if this is not homework, give the reason for it in a PM.

**edit:**

It is for fun (learning) not homework.

---

### Post by tjfrit01 on 2008-03-06
Ok for clarification, we are learning about binary trees in class and I wanted to create a program to put an input into an array in binary tree form.  However, I am not sure how to do this. I have read my input into an array and now I am trying to read that array into another one in binary tree format while removing duplicates.  I  know that the array is supposed to follow 2n for the left child and 2n+1 for the right child but I am not sure how to read one array into another like this.  That was the original question I had. Sorry for the confusion.

---

### Post by scourge on 2008-03-06
> **tjfrit01 said:**
> Ok for clarification, we are learning about binary trees in class and I wanted to create a program to put an input into an array in binary tree form.  However, I am not sure how to do this. I have read my input into an array and now I am trying to read that array into another one in binary tree format while removing duplicates.  I  know that the array is supposed to follow 2n for the left child and 2n+1 for the right child but I am not sure how to read one array into another like this.  That was the original question I had. Sorry for the confusion.

It's still a bit confusing. First of all, by "an array in binary tree form", do you mean that you want to use array indexes instead of pointers? And why not read the input straight into the binary tree? Can you show what you've got so far (if anything)?

---

### Post by WW on 2008-03-06
> **tjfrit01 said:**
>  I  know that the array is supposed to follow 2n for the left child and 2n+1 for the right child ...
This is a common technique for representing a binary tree in an array; see the [Wikipedia article about the Binary Heap](http://en.wikipedia.org/wiki/Binary_heap), especially the section **Heap implementation** near the end.

---

### Post by mike_g on 2008-03-06
Have you made a linked list yet?

If not that would be a good place to start.

Edit: if you are using an array then you would only need a binary search ;)

---

### Post by tjfrit01 on 2008-03-07
I think I have it figured out now.  I used a recursive function with three cases in order  to store the input as an array.  Thanks for the help!

---

