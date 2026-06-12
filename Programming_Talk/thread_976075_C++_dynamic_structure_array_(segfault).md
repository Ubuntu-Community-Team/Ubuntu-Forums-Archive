---
title: "C++ dynamic structure array (segfault)"
date: 2008-11-09
forum: Programming Talk
---

### Post by Nergar on 2008-11-09
I'm having problems with a dynamic structure array, it is in a function and it works fine the first time I call the function but the second time it gives a segmentation fault. I really don't know whats wrong, i'm very new at this c++ thingy.

[PHP]
void addClient () {
    clients = new clientsStruct [1];
	//NUM_CLIENTS is global and contains how many clients you
        currently have
    cout << "ID: " << NUM_CLIENTS << endl;
    cout << "Name: "; cin >> clients[NUM_CLIENTS].name;
    cout << "Email :"; cin >> clients[NUM_CLIENTS].email;
    cout << "Balance :"; cin >> clients[NUM_CLIENTS].balance;
    system("clear");
    cout << "Confirmation:" << endl;
    cout << "ID:\t" <<clients[NUM_CLIENTS].id << endl;
    cout << "Name:\t" <<  clients[NUM_CLIENTS].name << endl;
    cout << "email:\t" << clients[NUM_CLIENTS].email << endl;
    cout << "Balance:\t$" << clients[NUM_CLIENTS].balance << endl;
    NUM_CLIENTS++;
}
[/PHP]

What I want is to save the info to the array and create new elements every time i call the function to store new data in.

---

### Post by samjh on 2008-11-09
You are getting segfault because the function declares "clients" with ONE element, but if you call the function a second time, the function tries to access a SECOND element of "clients" that don't exist.

Without knowing anything more about your program, I can only suggest that you declare clients as a global vector (not a normal array), and that addClient() should add an element to client when you call it.

In other words:
```
vector<clientsStruct> clients;
int NUM_CLIENTS = 0;

// ...blah blah blah...

void addClient () {
    clientsStruct aclient;
    cout << "ID: " << NUM_CLIENTS << endl;
    cout << "Name: "; cin >> aclient.name;
    cout << "Email :"; cin >> aclient.email;
    cout << "Balance :"; cin >> aclient.balance;
    system("clear");
    cout << "Confirmation:" << endl;
    cout << "ID:\t" <<c aclient.id << endl;
    cout << "Name:\t" <<  aclient.name << endl;
    cout << "email:\t" << aclient.email << endl;
    cout << "Balance:\t$" << aclient.balance << endl;
    clients.push_back(aclient);
    NUM_CLIENTS++;
}
```You need to #include <vector> to be able to use vectors.

Two important things:
1. My code example is bad, so you should not consider it as authoritative.  I'm not going to clean up your code.  Use it only as a guide.
2. You have not assigned the id field of your client element anywhere in that function (you must do so before attempting to cout the value).

More on vectors: [http://en.wikipedia.org/wiki/Vector_(STL)](http://en.wikipedia.org/wiki/Vector_(STL))

---

### Post by Nergar on 2008-11-10
So this won't work:
[PHP]
int * nums;
nums = new int [1];
nums [0] = 1;
nums = new int [1];
nums [1] = 2;
nums = new int [1];
nums [2] = 3;
cout << nums [0];
cout << nums [1];
cout << nums [2];
[/PHP]

You can only create "new" elementes once? but with vectors you can?

Thanks a lot for your help, my teacher isn't the best one out there :(

---

### Post by dribeas on 2008-11-10
> **Nergar said:**
> So this won't work:
[PHP]
int * nums;
nums = new int [1];
nums [0] = 1;
nums = new int [1];
nums [1] = 2;
nums = new int [1];
nums [2] = 3;
cout << nums [0];
cout << nums [1];
cout << nums [2];
[/PHP]

You can only create "new" elementes once? but with vectors you can?

Thanks a lot for your help, my teacher isn't the best one out there :(

Implementation of std::vector goes in the line of creating a new array of a big enough size and then copying elements from one array to the other.

Some simplified code could go in the line of:
```

class ElementStorage
{
public:
   void addElement( element e )
   {
      element * tmp = new element[ this->size + 1 ];
      std::copy( this->data, this->data+size, tmp ); // copy old elements to new position

      std::swap( this->data, tmp );
      ++this->size;
   }
private:
   element* data;
   int size;
}

```

Note that the real code inside vector is more complicated, and that the code above is not exception safe (if the copy of one of the elements fail -exception thrown in copy constructor of element) it will leak memory.

---

### Post by Bichromat on 2008-11-10
> **Nergar said:**
> So this won't work:
[PHP]
int * nums;
nums = new int [1];
nums [0] = 1;
nums = new int [1];
nums [1] = 2;
nums = new int [1];
nums [2] = 3;
cout << nums [0];
cout << nums [1];
cout << nums [2];
[/PHP]

You can only create "new" elements once? but with vectors you can?

'new int[1]' does not create a new element, it creates a new array of size 1.

---

### Post by samjh on 2008-11-10
> **Nergar said:**
> So this won't work:
[PHP]
int * nums;
nums = new int [1];
nums [0] = 1;
nums = new int [1];
nums [1] = 2;
nums = new int [1];
nums [2] = 3;
cout << nums [0];
cout << nums [1];
cout << nums [2];
[/PHP]

You can only create "new" elementes once? but with vectors you can?

Thanks a lot for your help, my teacher isn't the best one out there :(
An array can only hold a fixed number of elements, which is declared when you create the array.

So...
```
nums = new int [1];
```...creates an array with just one element.

A vector is basically an array which allows you to dynamically increase or decrease its number of elements, by adding or removing elements as necessary.

In pseudocode, vectors work something like this behind the scenes (if you create a vector named "MyVector" with no size...):
```
Create Array of size 0.
Give Array the name "MyVector".
If Add_Element:
    Create New Array with one more element.
    Copy values from Array to New Array.
    Delete Array.
    Give New Array the name "MyVector".
If Remove_Element:
    Create New Array of one less element.
    Copy values from Array to New Array.
    Delete Array.
    Give New Array the name "MyVector".
```

---

### Post by Nergar on 2008-11-10
Thanks a lot!!! Now i get it!

Now i have to study vectors, where did you all learn all of this?

---

### Post by samjh on 2008-11-10
> **Nergar said:**
> Thanks a lot!!! Now i get it!

Now i have to study vectors, where did you all learn all of this?

Crash course on vectors: [http://www.cprogramming.com/tutorial/stl/vector.html](http://www.cprogramming.com/tutorial/stl/vector.html)

Learning C++ on the web: [http://www.cplusplus.com/](http://www.cplusplus.com/)

Learning C++ from a book: [http://www.amazon.com/Accelerated-Practical-Programming-Example-Depth/dp/020170353X](http://www.amazon.com/Accelerated-Practical-Programming-Example-Depth/dp/020170353X)

---

