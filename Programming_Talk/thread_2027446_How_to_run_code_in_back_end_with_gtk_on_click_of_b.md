---
title: "How to run code in back end with gtk on click of button and display output on window?"
date: 2012-07-16
forum: Programming Talk
---

### Post by igitian on 2012-07-16
I have made several pages(5) with GtkAssistant(),each page is displaying something say,text. On 4th page i have a progress bar which completes in 5 seconds. Now i have a program coded in c++ . I want that after a click on button to run progress bar ,my code should start running, Ad on 5th page i want to display the o/p.my code is reading from a file ,so there are are no i/p to be given. I want to know how to implement this? I am new to GTK+.
basically i want to know how to connect gui with my algorithm

---

### Post by PaulM1985 on 2012-07-16
At stages in your algorithm you could call some PostProgress(Progress progress) type function on the thing that should be updating.

```

class Algorithm
{
ProgressListener *pListener;

void do()
{
   for (int i = 0; i < 5; i++) {
      pListener->postProcess(i);
   }
}
};

class ProgressListener
{
   virtual void postProgress(int i) = 0;
};

class MyWindow : public ProgressListener
{

   void postProgress(int i)
   {
      // update the window
   }

   virtual void runAlgorithm()
   {
      Algorithm alg;
      alg.pListener = this;
      alg.do();
   }
};


```

The above code is an example of how it might work.

Paul

---

### Post by igitian on 2012-07-17
can anybody ans it

---

### Post by igitian on 2012-07-17
this is my code
can anybody tell hoe to connect my algorithm to this
 i have implemented application of max. flow graph i.e."project selection problem" using F-F algorithm, so my i/ps are: total no. of projects , profit for each project and prerequisites for projects (prerequisites are other projects only) and o/p is :max.profit(integer value) and name of feasible projects that contribute to max. profit

---

### Post by PaulM1985 on 2012-07-17
If you put your code in [ code ] tags it is easier to read and people will be more likely to help you.

Paul

---

### Post by igitian on 2012-07-17
i want that on click of button 
g++ -o output maxflow.cpp should execute .

Can someone tell me function in gtk which does this thing.

I want to know how to implement this? I am new to GTK+.
:confused:

---

