---
title: "C++ vector help"
date: 2009-04-27
forum: Programming Talk
---

### Post by abraxas334 on 2009-04-27
Hi,
this is probably a very silly question coming from an unexperience programmer.
so i have a class and within that class i have defined a vector like this:

[PHP]vector<int>Array;[/PHP]

now i want to init the vector in the constructor so it has a certain size and the entries are set to a certain value.

if i was doing this in main or any function if i define a vector i can do it like this:

[PHP]vector<int>Array(10,0) // has 10 entries with value zero[/PHP]

Is there a syntax like that for initing a vector if it has already been definied as a private variable in a class. Or is this the the only way of giving the vector a size of 10 with values 0 in the constructor of the class
[PHP]
for(int i =0; i<10; i++)
{
    Array.push_back(0);
}
[/PHP]
i mean this method works fine I was just wondering if there was an alternative.
Thanks a lot

---

### Post by Zugzwang on 2009-04-27
You can do so using assignment. Example:

[PHP]
#include <vector>
using namespace std;

int main() {
    vector<int> Array;
    Array = vector<int>(10,0);
}
[/PHP]

---

### Post by cabalas on 2009-04-27
You can run the constructors of member variables when the class constructor is run, you do this by calling the constructor immediately after the function declaration.  I'm not sure if that's the best way to explain but hopefully this example should clarify it.

Test.hh:
[PHP]
class Test {
    public:
        Test();
        Test(int);

    private:
        std::vector<int> my_vec;
        std::vector<int> my_vec2;
}
[/PHP]

Test.cc:
[PHP]
#include "Test.hh"

Test::Test() : my_vec(10, 0)
{
    // Do Stuff
}
[/PHP]

The ':' is needed so that the compiler knows that you are calling the classes member variables constructors.  If you have multiple members that you wish to run the constructors of just separate each with a comma like so:

[PHP]
Test::Test() : my_vec(10, 0), my_vec2(20, 1)
{
    // Do Stuff
}
[/PHP]

You can also use the parameters of the constructor as well like in the following:

[PHP]
Test::Test(int init_value) : m_vec(10, init_value)
{
    // Do some stuff
} 
[/PHP]

Hopefully that clears it up a bit for you.

---

### Post by abraxas334 on 2009-04-27
Thanks alot! Makes more sense now!

---

