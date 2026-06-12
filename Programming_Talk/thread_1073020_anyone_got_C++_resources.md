---
title: "anyone got C++ resources?"
date: 2009-02-17
forum: Programming Talk
---

### Post by SonnHalter on 2009-02-17
I'm switching from c to C++ and need some good online resources.all i have is a book but its older and uses a lot of faux pahs that even i know not to use. 

all the google searchs seem to give me bad results or results that contradict each other. help please?

---

### Post by dwhitney67 on 2009-02-17
Here's one:  [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by SonnHalter on 2009-02-17
tried that, too hard to navigate cause everything is the same text size and color.

---

### Post by dwhitney67 on 2009-02-17
I'm not sure if I understand you.  Here's an example piece of code from that site:
[php]
// classes example
#include <iostream>
using namespace std;

class CRectangle {
    int x, y;
  public:
    void set_values (int,int);
    int area () {return (x*y);}
};

void CRectangle::set_values (int a, int b) {
  x = a;
  y = b;
}

int main () {
  CRectangle rect;
  rect.set_values (3,4);
  cout << "area: " << rect.area();
  return 0;
}
[/php]

---

### Post by Leo Dragonheart on 2009-02-18
This is the one I am currently using: [http://cprogramming.com/](http://cprogramming.com/)


**EDIT:** I have switched to [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) much better than cprogramming IMHO.....

---

### Post by ch42 on 2009-02-18
I also like [http://www.cppreference.com](http://www.cppreference.com)

---

### Post by rharriso on 2009-02-19
For sure you'll need this. 

[Standard Template Library]("http://www.sgi.com/tech/stl/")

---

### Post by SplinterOfChaos on 2009-02-19
The best references are forums and google.

Forums because, while I'd like to say people are best, people can be wrong. People in groups usually straighten things out and shut up the BS. And there's seriously a lot of BS out there. 

Like, for example, how to use the stream classes in C++. I think they're poorly designed and give way too much grief to beginning programmers. Because of this, I believe, many C++ programmers don't initially understand how exactly to deal with garbage input, or really the streams to begin with. You'll only get help of those problems from someone who has good experience with them and probably got told from someone else what to do.

And, google: When you have a reliable source, Google's not as needed, but I can usually get to the pages on [http://www.cplusplus.com/](http://www.cplusplus.com/) (their extensive std lib documentation, although it's incomplete) faster than I can get onto their site and hunt it down. It also opens me to new sources and sometime interesting articles and stuff.

---

### Post by krazyd on 2009-02-19
I really recommend getting a good book - I'm working through "[Accelerated C++]("http://www.acceleratedcpp.com/")" at the moment and it's great. Much better structure than online resources I found. Plus I find it easier to study flipping rather than clicking through pages..

---

### Post by Ng Oon-Ee on 2009-02-20
I've always liked [C++ FAQ Lite]("http://www.parashift.com/c++-faq-lite/index.html"), though its not as thorough as a book, assuming you have some knowledge to begin with it's quite brilliant at pointing out nuggets that you thought you knew, and covers more than just the language. I've learned a lot there.

Of course, in opposition to that is [C++ Frequently Questioned Answers]("http://yosefk.com/c++fqa/index.html") which tries to debunk everything written above.

---

