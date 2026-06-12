---
title: "How can one store an function that gives multiple returns? c++"
date: 2006-12-02
forum: Programming Talk
---

### Post by thenetduck on 2006-12-02
Hi, 
  I am building a simulation of a Binomial Distribution type thingy. The way it works is, I build a tree of nodes, drop 256 balls through it and then read the ball count and display it. The problem is with this function.

```

 /**************************************************************
      * Summary: This function takes in a number representing the 
      *  colum that it will look at to return the amount of balls there.
      *  It does this by going down the very right stran of nodes, getting
      *  that value, then going down the second stran of nodes until it works
      *  it's way back to the top. 
      * Process: 
      *          Check to see if we are at the 0th row.
      *          Go down the right nodes first
      *          Then start working the way down the left nodes.
      **************************************************************/
      int getBallCount(int colum)
      {
         if (colum !=0) // If you are not at the head node or first node.
         {
            rightNode->getBallCount(colum - 1);
         }
         
         if (leftNode == NULL) // If we are at the last node of that stran.
         {
cerr << balls << endl;
            return balls;
         }
         else
         {
            leftNode->getBallCount(0); // Just keep going down left. 
         }
      }

``` 

I have a function that calls the head of the node kind of like this. 

```

cout << "This outputed :" << head->getBallCount(8) << endl;

```

My tree is has 9 colums but I have 8 because it's from 0 - 8.  The code right there will output the last node returned. The getBallCount() function returns 9 different times. How can I store these answer?? Thanks,
 
The Net Duck

---

### Post by Tomosaur on 2006-12-02
You could enclose all of this:
```

         if (colum !=0) // If you are not at the head node or first node.
         {
            rightNode->getBallCount(colum - 1);
         }
         
         if (leftNode == NULL) // If we are at the last node of that stran.
         {
cerr << balls << endl;
            return balls;
         }
         else
         {
            leftNode->getBallCount(0); // Just keep going down left. 
         }

```
in a loop, and use the current count as the index of an array or vector, storing the result in said array/vector.

---

