---
title: "C++ Cafe !"
date: 2006-05-16
forum: Programming Talk
---

### Post by medya on 2006-05-16
Hey Guys I know it is shame to ask but ... please help me ,

I need help to write a program that
makes a sorted linked list that has ability of adding  and deleting as many nodes as user wants .


yes it is a project for my C++ class, 
i spend my hours on ubuntu , which supposed to be spent for c++ .
unfrotuatenly if I cant do this project I will fail ... plese a kind lovely c++ geek do this project to me... I am in pain  :( ... please . I hope a good guy will help me..

thanks again .
and sorry for asking such a shamefull request .

---

### Post by matthew on 2006-05-16
I am going to move this to Programming Talk. 

I am also going to suggest that you should open your books and do your own homework...I don't want someone programming flight systems on an aircraft that I fly on to have passed a class by soliciting help from an internet forum...see where I'm going? Learn it, learn it well, share what you learn with others. If someone helps you I hope it will be by steering you in the right direction rather than by giving you answers, etc.

---

### Post by BoyOfDestiny on 2006-05-16
[QUOTE=medya]Hey Guys I know it is shame to ask but ... please help me ,

I need help to write a program that
makes a sorted linked list that has ability of adding  and deleting as many nodes as user wants .


yes it is a project for my C++ class, 
i spend my hours on ubuntu , which supposed to be spent for c++ .
unfrotuatenly if I cant do this project I will fail ... plese a kind lovely c++ geek do this project to me... I am in pain  :( ... please . I hope a good guy will help me..

thanks again .
and sorry for asking such a shamefull request .[/QUOTE]

Sad.

Here is some example code.

[http://www.fortunecity.com/skyscraper/false/780/linklist.html](http://www.fortunecity.com/skyscraper/false/780/linklist.html)

As for it being sorted, do you mean it hold strings or what?

I don't think anyone here wants to help you cheat... Hopefully this tutorial helps enough that you can do it yourself...

---

### Post by Harleen on 2006-05-16
The quickst solutution would be using std::list. But that's probably too simple to pass the test?

```
#include <list>
#include <iostream>

using std::cout;
using std::endl;

int main(void)
{
    std::list<int> x;
    //add items
    x.push_back(3);
    x.push_back(1);
    x.push_back(2);
    // sort list
    x.sort();
    
    // print list
    cout << "List content:" << endl;
    for (std::list<int>::const_iterator it=x.begin(); it!=x.end(); ++it)
    {
        cout << *it << " ";
    }
    cout << endl;
    return 0;
}
```

---

### Post by medya on 2006-05-16
sorted  like numbers... it is for numbers.

---

### Post by Grey on 2006-05-16
Ah yes, I remember that assignment.  I wrote that in the school's computer labs, and at one point it was buggy enough that it took down a server running Solaris 8.  ;)  The rest of the time it just seg faulted.

I'm sorry though, I would help you out, but I've been up all night coding... for about 13 consecutive hours, and I am about spent.

EDIT:  I'm going to back up the others though.  I've often considered a linked list to be the "bar" in computer science, where if you manage to code one, then you are sufficiently advanced that you should be able to code anything.  So I am really going to suggest that you study hard, and try your best.  If you accomplish it on your own, then you will be that much better for it.  And believe me, I felt an enormous sense of accomplishment when I finished mine.  I felt like I could take on the world (and that summer, I wrote something that I am still proud of to this day).

---

### Post by Revert on 2006-05-16
[QUOTE=Grey](and that summer, I wrote something that I am still proud of to this day).[/QUOTE]

Out of curiosity, what did you write?

---

### Post by medya on 2006-05-16
grey I will study it hard, but I have just 2 days time to do this ... 

is the thing that harleen wrote correect ?

---

### Post by medya on 2006-05-16
how about this ..is this correct ? I think it needs an insertation sort function.. can somebody add it to this for me ... 

> #include <iostream>
#include <cstddef>
#include <string>
using namespace std;
struct Node
{
  string item;
  int count;
  Node * link;
};

typedef Node * NodePtr;
void remove( NodePtr & head , string target );
void head_insert(NodePtr & head, string an_item, int a_number);
void show_list(NodePtr  head);
NodePtr search(NodePtr head, string target);


int main()
{
   string target;
   NodePtr head = NULL;
   head_insert(head, "Tea", 2);
   head_insert(head, "Jam", 3);
   head_insert(head, "Rolls", 10);
   cout << "List contains:" << endl;
   show_list( head );


  cout << "Enter the item after which you want to delete \n";
  cin >> target;
   remove ( head , target );
   cout << endl;
   show_list ( head );

  return 0;
}

void remove( NodePtr & head , string target )
{

   if ( head ->item == target )
   {
       NodePtr temp = head;
       head = head -> link;
       delete temp;
       return;
   }

   NodePtr s = head;
   while ( s -> link )
   {
       if ( s -> link -> item == target )
       {
           NodePtr temp2 = s -> link;
           s -> link = s -> link -> link;
           delete temp2;
           return;


       }
       s = s -> link;
   }
}

void head_insert(NodePtr& head, string an_item, int a_number)
{
  NodePtr temp_ptr;
  temp_ptr = new Node;
  temp_ptr -> item = an_item;
  temp_ptr -> count = a_number;
  temp_ptr->link = head;
  head = temp_ptr;
}

void show_list(NodePtr  head)
{
  NodePtr temp = head;
  while ( temp  != NULL)
  {
        cout << temp -> item << "\t";
        cout << temp -> count << endl;
        temp  = temp ->link;
  }
}
NodePtr search(NodePtr head, string target)
{

  NodePtr temp = head;

  while ( temp )
  {
      if ( temp -> item == target )
          return temp;
  }


}

---

### Post by medya on 2006-05-17
the code above doenst have Insertation , would soembody please add it for me ...  I will be extremly gratefull.

---

### Post by supirman on 2006-05-17
[QUOTE=medya]the code above doenst have Insertation , would soembody please add it for me ...  I will be extremly gratefull.[/QUOTE]

I sure hope you're not in a CS program of any kind....  :rolleyes:

---

### Post by matthew on 2006-05-17
[QUOTE=medya]the code above doenst have Insertation , would soembody please add it for me ...  I will be extremly gratefull.[/QUOTE]

Let me repeat myself.

I  suggest that you open your books and do your own homework...I don't want someone programming important systems because they passed a class by soliciting help from an internet forum...see where I'm going? 

That's your lesson for today. Learn it, learn it well, share what you learn with others. 

To others: please only help by steering in the right direction rather than by giving answers, etc.

---

### Post by medya on 2006-05-17
why everybody on the forums is like that ?
I have my project tomorrow in 6 hours, and I cant learn the wholes stuff now 
but I will want to Learn these things and I will do that 
but I want to pass the project and nobody helpt me , so I will fail this course..

Thank you all.I go to sleep.

---

### Post by matthew on 2006-05-17
[quote=medya]why everybody on the forums is like that ?
I have my project tomorrow in 6 hours, and I cant learn the wholes stuff now 
but I will want to Learn these things and I will do that 
but I want to pass the project and nobody helpt me , so I will fail this course..

Thank you all.I go to sleep.[/quote]You had an entire term to learn the material. You will not fail because of anyone here. You may fail because you failed to work while you had the chance and then couldn't find anyone willing to help you cheat at the last minute.

---

### Post by Lord Illidan on 2006-05-17
My thoughts exactly.
There is the internet. There are your books. Research and look up a solution. Cheating will not work.

---

### Post by medya on 2006-05-17
u know what, I never learn things at class, I learn just when I feel like to learn, and I will learn C++ after my project, because I am not as busy more

I didnt say I will fail because of you, but it is a bit sad for me to see that somebody knows the code and doesnt give it to me ...  :(

never mind.. I will fail the exam .

---

### Post by JNowka on 2006-05-17
Im gonna try to say this in the nicest way possible.

I am taking Advanced Programming, I work hard at what I do, I am usually the first done, and have the highest grades.  There is a reason for that.  I do my work. I don't ask others for help unless absolutly neccisary, and definatly not if I was not working to get the grade.  I believe that the grade you earn is equivalent to how much you put into your work.  I hope that everyone here will not help you.  Linked lists are very simple, it should take no longer than 30 minutes to learn if you sit down and read the chapter.  Please learn it for yourself, because once you are in the real world there will be no second chances.  The boss man will see that you can't do your job and he will fire you.  Please do yourself a favor, and do your own work.

---

### Post by matthew on 2006-05-17
[quote=medya]it is a bit sad for me to see that somebody knows the code and doesnt give it to me ...  :([/quote]It's a bit sad for me to realize that in the time it has taken you to ask us repeatedly to just give it to you you could have learned it for yourself and even mastered it. We're doing you a favor. Truly.

---

### Post by LactosetheIntolerant on 2006-05-17
I learned my lesson about helping other people during my first year of CS in university.  Help one person with a little bit of code and the rest of the year them and their friends will be looking for debugging and programming assistance. This cut down on my time to work(I was usually done quickly, so it only really cut down on my spare time) and they ended up doing poorly on the exam because they didn't understand as well as they should.  If programming is something that you enjoy, take the course again and do your own work.  You'll be better off for it.

---

### Post by Lord Illidan on 2006-05-17
Think about it this way:

You pass by cheating. You coast through uni, copying and pasting your assignments.

You get a job. Manager asks you to do something.

You stand there speechless.

You're fired and made to look like a fool.

Best start getting good practices now rather than later.

---

### Post by unbuntu on 2006-05-17
You might have a better chance to just [www.rentacoder.com]("www.rentacoder.com"):D

Seriously, we know CS is hard, but if that's what you want to do, then suck it up.

---

### Post by Grey on 2006-05-18
Sorry, my Internet Access was killed for about a day, and I couldn't reply to anything.  So on the subject of the topic, anything I could say or do would probably be too late anyways.  Just think of it this way.  If you fail the class, just take it again.  Try harder next time, and you'll get through it.  There's no dishonour in failing a class in my books.  :)  Just think of it as a learning experience.

[QUOTE=Revert]Out of curiosity, what did you write?[/QUOTE]

I wrote most of a game engine for GBA.  Check out [my website](http://people.uleth.ca/~dave.brady/projects.php) for a binary/source.  Be warned that I wrote it many years ago though, and the code isn't exactly clean.  ;)

---

### Post by matthew on 2006-05-18
Really, there's no need for this thread to continue.

In the future, please refrain from asking others to do your homework/projects/etc for you.

---

