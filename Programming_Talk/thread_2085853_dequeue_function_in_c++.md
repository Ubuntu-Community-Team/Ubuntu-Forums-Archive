---
title: "dequeue function in c++"
date: 2012-11-19
forum: Programming Talk
---

### Post by hatsoff on 2012-11-19
i am writing code for queue which uses linked list data structure for its implementation, in which node class has two data member(for instance node has name and number in its private section) , i am having problem to write function for get() in dequeue(delete node having two data members and move front pointer ahead) as there are two data members,

---

### Post by lisati on 2012-11-19
*Thread moved to **Programming Talk**.*

---

### Post by dwhitney67 on 2012-11-19
> **hatsoff said:**
> 
both are not working ,i need some advise.
(clarification will be provided if needed)

Could you please explain what is not working?  Your first example (attempt) seems pretty straightforward, and I cannot see why it would fail.

If might be helpful if you provided more code to show how you are initializing the list, how you are populating it, etc.

Also, are you "re-inventing" the list/queue classes, or are you using the standard C++ classes that bear the same name?

---

### Post by hatsoff on 2012-11-19
here it class

---

### Post by dwhitney67 on 2012-11-19
It appears that you are missing a constructor for your node class.  This would be helpful to initialize the member data, specifically the nextnode member, to 0.  This way you can be assured that when a node is created, that it's nextnode member does not contain a bogus pointer.

If this does not resolve the issue with your application, then more information will be needed (ie. example usage of how you are employing the node class).

Also, in the future, please post your code within CODE tags so as to preserve the formatting of your original code.  You can manually do this, or you can highlight your posted code and then select the # icon in the tool-set above the edit box.

Anyhow, back on topic, here's what I suggest with respect to the constructor:
```

class node
{
public:
    node() : name(), age(0), nextnode(0), size(0)
    {
    }

    ...
};

```

---

### Post by dwhitney67 on 2012-11-19
> 
here is my full code


Please don't send me a PM (Private Message) seeking help.  You should seek help on the forum so that everyone, who wishes to, can assist you.

Now, it's obvious that you are working on a school project (ie homework), so I will not resolve your program's issues for you, but I can assist in getting you to think about what may be causing your application to fail.

For starters, here's your code, in its entirety.  Note that I have made changes to make it compile/run under Linux and added a few changes:
```

#include <string>
#include <iostream>
//NOT SUPPORTED FOR LINUX #include <conio.h>
#include <cstdlib>

using namespace std;

class node
{
private:
    string name;
    int age;
    node* nextnode;
    int size;
public:
    //string getname()
    string getname() const
    {
        return name;
    }
    //int set(string x, int y)
    void set(const string& name, const int age)
    {
        this->name = name;
        this->age = age;
    }
    //int setnext(node* nextnode)
    void setnext(node* nextnode)
    {
        this->nextnode = nextnode;
    }
    //int getage()
    int getage() const
    {
        return age;
    }
    //node* getnext()
    node* getnext() const
    {
        return nextnode;
    }
};

//class queue
class queue
{
private:
    node* rear;
    node* front;
    int size;

public:
    //void enqueue(string y, int x)
    void enqueue(const string& name, const int age)
    {
        node* newnode = new node(); //pointer has the adreess where node is exist
        //newnode->set(y, x);
        newnode->set(name, age);
        newnode->setnext(NULL);
        rear->setnext(newnode);
        rear = newnode;
        size++;
    }

    //int dequeue()
    string dequeue()
    {
        //int x = front->getname();
        //node* w = front->getage();

        string name = front->getname();
        //int age = front->getage();

        node* p = front;

        front = front->getnext();

        delete p;
        //delete w;

        size--;

        //return x;
        return name;
    }

    int frontof()
    {
        //WHAT IS get()??
        //return front->get();
        return 0;
    }

    //int isempty()
    bool isempty()
    {
        return (front == NULL);
    }

    //void display_Q()
    void display_Q() const
    {
        while (front == NULL)
        {
            cout << front->getname() << "\t" << front->getage();
            cout << "---------------------------------------";
        }
    }

    //int Qsize()
    int Qsize() const
    {
        return size;
    }
};

int main()
{
    queue queue1;
    int choice, ageofcustomer, input;
    string nameofcustomer;

    do
    {
        cout << "1.Press 1 for adding" << endl;
        cout << "2- for remove/serve a customer " << endl;
        cout << "3- to show customer at front " << endl;
        cout << "4- for display all customer in Queue " << endl;
        cout << "5- for show size of queue " << endl;
        cout << "6- for Quit " << endl;
        cin >> choice;
        switch (choice)
        {
        case 1:
            do
            {
                //NOT APPLICABLE FOR LINUX system("cls");
                cout << "Enter the name of customer " << endl;
                getline(cin, nameofcustomer);
                cout << "Enter the age " << endl;
                cin >> ageofcustomer;
                queue1.enqueue(nameofcustomer, ageofcustomer);
                cout << "do you want to add more : (y/n)";
                cin >> input;
            } while (input == 'y' || 'Y');
        case 2:
            if (!queue1.isempty())
            {
                queue1.dequeue();
                cout << "removed/served";
            }
            else
                cout << "queue is empty";
            break;
        case 3:
            if (!queue1.isempty())
                queue1.frontof();
            else
                cout << "queue is empty ";
            break;
        case 4:
            if (!queue1.isempty())
                queue1.display_Q();
            else
                cout << "queue is empty ";
            break;
        case 5:
            cout << "size is" << queue1.Qsize();
            break;
        case 6:
            cout << " quiting ";
            break;
        default:
            cout << "please enter a numeric from list ";
        }
    } while (choice != 6);
    //NOT APPLICABLE FOR LINUX system("PAUSE");
}

```
The code was beautified using "uncrustify".  I hope it resembles the original formatting of your code to some degree.

Areas of the code that appear to be error prone:

1.  Acquiring raw input from the command line. Don't assume cin will flush input stream of newline characters (ie <Enter> key) that you input.  Using getline() is a good choice.

2.  Don't assume user will start adding nodes.  Check the validity of your queue's pointers before attempting to access them.

There's probably other issues, but since you are far from completing the basics of the application, I'll let you discover them.

---

### Post by Elfy on 2012-11-19
Given that the OP has both edited their posts to be empty and they reported the thread as an assignment - I'm closing it.

---

