---
title: "c++ ios header"
date: 2007-07-21
forum: Programming Talk
---

### Post by zerobinary on 2007-07-21
c++ ios header i don't get what they mean by the deifnation of it defines streamsize
what is streamsize and what does ios header do

---

### Post by zerobinary on 2007-07-21
one more thing 
i don't understand this part of the script (from a book)
```

#include <iomanip>
#include <ios>
#include <iostream>
#include <string>
using std::cin;
using std::cout; sorry didn't indent
using std::endl;
using std::setprecision;
using std::string;
using std::streamsize;
int main ()
{ 
//ask for and read the student's name
cout<<"plz enter ur first name: ";
string name;
cin>>name;
cout<< "Hello, "<<name<<"!"<<endl;
//ask for and read the midterm and final grades
cout<<"plz enter ur mid team and final exam grades \: ";
double midteam, final; //how about it has to be in double can it be int
cin>>midterm>>final;
//ask for the homework grades
cout<<"enter all ur homework grades, "
"follow by end of file: ';
//the number5 and sums of grades read so far
int count= 0;
double sum = 0;
//variable into which to read
double x;
//invariant:
//we have read count grades so far, and 
// sum is the sum of the first count grades
while {cin>>x) //what is this mean {
++count;
sum +=x;
//write the result 
streamsize prec= cout.precision(); //what does that line mean
cout<<"ur final grade is"<< setprecision(3) //does that lines mean display the line to 3 decimal place
<<0.2*midterm=0.4*final =0.4*sum/count
<<setprecision(prec) // what does that mean<<endl;
return 0;
}

```

---

### Post by Paul820 on 2007-07-21
This is the section you should have read that explains what it does. Are you reading the book? > Our goal is to write the final grade with three significant digits, which we do by using  setprecision. Like endl, setprecision is a manipulator. It manipulates the stream by causing subsequent output on that stream to appear with the given number of significant  digits. By writing setprecision(3), we ask the implementation to write grades with three significant digits, generally two before the decimal point and one after. By using setprecision, we change the precision of any subsequent output that might appear on cout. Because this statement is at the end of the program, we know that there is no such output. Nevertheless, we believe that it is wise to reset cout's precision to what it was before we changed it. We do so by calling a member function of  cout named precision. This function tells us the precision that a stream uses for floating-point output. We use setprecision to set the precision to 3, write the final grade, and then set the precision back to the value that precision gave us.

---

### Post by slavik on 2007-07-22
formatted output ... this is why I like the C facilities (fprintf())

---

### Post by zerobinary on 2007-07-22
> digits. write grades with three significant digits
u mean like 10.324 or 
something like 72.8

---

### Post by Paul820 on 2007-07-22
Two digits before the decimal point and one after, so it's the bottom one, 72.8

---

### Post by zerobinary on 2007-07-22
and what is streamsize means

---

### Post by zerobinary on 2007-07-22
what is ios header do and what is streamsize

---

### Post by zerobinary on 2007-07-22
so if it is setprecison(5) 
then it will be something like 
2345.6
????
and what is streamsize and what does ios header do

---

### Post by hod139 on 2007-07-23
streamsize represents the number of characters transferred in the cout operation (any io operation, but for this example is was a cout).  As for ios, here is the reference page: [http://www.cplusplus.com/reference/iostream/ios/](http://www.cplusplus.com/reference/iostream/ios/)

---

### Post by zerobinary on 2007-07-23
so if it is setprecison(5)
then it will be something like
2345.6
????

---

### Post by hod139 on 2007-07-23
[http://www.cplusplus.com/reference/iostream/manipulators/setprecision.html](http://www.cplusplus.com/reference/iostream/manipulators/setprecision.html)

---

### Post by zerobinary on 2007-07-27
how come this line
```
int count= 0;
double sum = 0;

```
from the previous script in page one 
that count is integer while sum is double 
how come count don't need to be double

---

### Post by zerobinary on 2007-07-28
```

#include <iomanip>
#include <ios>
#include <iostream>
#include <string>
using std::cin;
using std::cout; sorry didn't indent
using std::endl;
using std::setprecision;
using std::string;
using std::streamsize;
int main ()
{ 
//ask for and read the student's name
cout<<"plz enter ur first name: ";
string name;
cin>>name;
cout<< "Hello, "<<name<<"!"<<endl;
//ask for and read the midterm and final grades
cout<<"plz enter ur mid team and final exam grades \: ";
double midteam, final; //how about it has to be in double can it be int
cin>>midterm>>final;
//ask for the homework grades
cout<<"enter all ur homework grades, "
"follow by end of file: ';
//the number5 and sums of grades read so far
int count= 0;
double sum = 0;
//variable into which to read
double x;
//invariant:
//we have read count grades so far, and 
// sum is the sum of the first count grades
while {cin>>x) //what is this mean {
++count;
sum +=x;
//write the result 
streamsize prec= cout.precision(); //what does that line mean
cout<<"ur final grade is"<< setprecision(3) //does that lines mean display the line to 3 decimal place
<<0.2*midterm=0.4*final =0.4*sum/count
<<setprecision(prec) // what does that mean<<endl;
return 0;
}

```
how come this line
```

int count= 0;
double sum = 0;

```
from the previous script in page one
that count is integer while sum is double
how come count don't need to be double

---

### Post by Paul820 on 2007-07-28
Because in the book he says that there is no overhead in using double sum = 0 as the compiler will convert it to double at compile time. You can use sum = 0.0 but as he said it doesn't make any difference.

---

### Post by zerobinary on 2007-07-28
yeah but the question is why not overhead sum too and what is 0.0 means in the book that's the problem

---

### Post by Paul820 on 2007-07-28
0.0 represents values with decimal places like £1.50 or $1.99. count doesn't need to be 0.0 because count is an integer, they don't have decimal places. He is using count to keep a count of how many homework grades were entered so he can divide the sum by count at the end of the program to get the average grade. Sum is used to store the final result of all the homework grades added together.

---

### Post by zerobinary on 2007-07-28
o so becuase count will not be decimal so i t is integer on the other hand sum might be decimal so it is double ????

---

### Post by Paul820 on 2007-07-28
lol, now you are confusing me. Count is an integer, it does not have any decimal places, it's written as 1, 2, 3, therefore count = 0, he is using it as a counter. Sum on the other hand is a double, it won't be an integer, just double. He only wrote sum = 0 because the compiler will convert it to 0.0 when the program is compiled. The compiler knows it's a double because the type identifier says it is. Put it this way, he was being lazy, he couldn't be bothered to write 0.0 so he just wrote 0 and let the compiler convert it for him.

---

### Post by zerobinary on 2007-07-28
if i just put int sum=0 will it work

---

### Post by Paul820 on 2007-07-28
NO, sum has to be a double, the homework grades are being read as double, the final result will be a double. Why are you wanting to change it to an int? If you put a integer into a double the part after the decimal point is discarded, lost, gone, kaput. So if you enter 1.34 into an int you will get 1 when you print it out, the .34 is thrown away. That's why sum is a double, to keep the precision intact.

---

### Post by zerobinary on 2007-07-28
but can't integer have decimal 
or is it only double can have decimal

---

### Post by slavik on 2007-07-29
```
printf("%.2f",grade);
```

that is why C is easier. :)

---

### Post by the_unforgiven on 2007-07-29
> **zerobinary said:**
> but can't integer have decimal 
or is it only double can have decimal
I think you're confused about how the integers and real numbers are related.

The first number system man ever used was the [Natural Numbers]("http://en.wikipedia.org/wiki/Natural_numbers") (denoted in Maths by the set N). Then, the next extension to it was the set of integers (set Z, positive as well as negative integers). The next extension is [rational numbers]("http://en.wikipedia.org/wiki/Rational_numbers") (Q, fractions where both numerator and denominator belong to Z, with denom != 0), then comes real numbers (R, all possible numbers from -inf to +inf, excluding complex numbers, of course ;)).
More information on various number systems can be found in: [http://en.wikipedia.org/wiki/Number_system](http://en.wikipedia.org/wiki/Number_system)

Now, the way numbers are represented inside the computer is a bit complicated - integers don't have problem of precision, however, real numbers (both fixed point as well as floating point) cannot be represented with infinite precision. That's why, IEEE adopted a standard for representing real numbers inside computers - the IEEE 754.

Here is more info on fixed point arithmetic:
[http://en.wikipedia.org/wiki/Fixed-point_arithmetic](http://en.wikipedia.org/wiki/Fixed-point_arithmetic)
and here is info on floating point numbers:
[http://en.wikipedia.org/wiki/Floating_point](http://en.wikipedia.org/wiki/Floating_point)

So, I suppose, now it should be easy for you to answer why count is an integer while sum needs to be float (or double) and where does the problem of precision arise.

---

### Post by zerobinary on 2007-07-29
i kind of get it but not too sure 
i think because the mark u enter have decimal like 39.9mark times the percentage it worth +the same thing again
because it produce more bit than the operator then the decimal will be loss even before rounding 
using double will ensure the decimal won't loss before rounding right?????

if i am wrong plz correct me

---

### Post by escapee on 2007-07-30
I think this is what you need to see laid out:

**_[SIZE="3"]Integer:[/SIZE]_**
Example: -2, -1, 0, 1, 2

_Works:_
int i = 0;
int j = 4;
in k = 4242;

_Doesn't work:_
int x = 2.3;
int y = 73.45645;
int z = 0.0;



**_[SIZE="3"]Double:[/SIZE]_**
Example: -1.2, 0, 0.2, 0.4, 1

_Works:_
double i = 0;   
double j = 2;
double k = 4242;
double x = 2.3;
double y = 73.45645;
double z = 0.0;
____________________________

When you assign a double an integer value it works as shorthand, and as the others have said, the compiler will make it a double at compile time.

---

### Post by zerobinary on 2007-07-30
got it one explanation that save me thx

---

### Post by zerobinary on 2007-07-30
streamsize it is needed in this script because of this part 
```

streamsize prec= cout.precision(); //what does that line mean
cout<<"ur final grade is"<< setprecision(3) //does that lines mean display the line to 3 decimal place
<<0.2*midterm=0.4*final =0.4*sum/count
<<setprecision(prec) // what does that mean<<endl

```
because there is calculation in cout???????//
when u have calculation in cout u need to define a valuable with streamsize????/
is that right

---

### Post by zerobinary on 2007-07-30
come and help plz

---

### Post by Jessehk on 2007-07-30
There's always something like boost::format. :)

---

### Post by zerobinary on 2007-07-30
boost format ???????

---

### Post by Jessehk on 2007-07-30
> **zerobinary said:**
> boost format ???????

```

#include <iostream>

#include <boost/format.hpp>

// A silly example
class Coord {
    private:
        int x_, y_;
    public:
        Coord( int x, int y ) :
            x_( x ), y_( y ) {}
        
        int x() const { return x_; }
        int y() const { return y_; }
};

std::ostream &operator<<( std::ostream &os, const Coord &coord ) {
    os << boost::format( "(%d, %d)" ) % coord.x() % coord.y();
    
    return os;
}

int main() {
    Coord coord( 0, 3 );
    std::cout << coord << std::endl;
}

```

**OUTPUT**
```

(0, 3)

```

[http://www.boost.org/libs/format/doc/format.html](http://www.boost.org/libs/format/doc/format.html) :)

---

### Post by zerobinary on 2007-07-30
err is that even the code on the first page

---

### Post by zerobinary on 2007-07-30
streamsize it is needed in this script because of this part
```


streamsize prec= cout.precision(); //what does that line mean
cout<<"ur final grade is"<< setprecision(3) //does that lines mean display the line to 3 decimal place
<<0.2*midterm=0.4*final =0.4*sum/count
<<setprecision(prec) // what does that mean<<endl

```
because there is calculation in cout???????//
when u have calculation in cout u need to define a valuable with streamsize????/
is that right
the original whole code is that 
```

#include <iomanip>
#include <ios>
#include <iostream>
#include <string>
using std::cin;
using std::cout; sorry didn't indent
using std::endl;
using std::setprecision;
using std::string;
using std::streamsize;
int main ()
{ 
//ask for and read the student's name
cout<<"plz enter ur first name: ";
string name;
cin>>name;
cout<< "Hello, "<<name<<"!"<<endl;
//ask for and read the midterm and final grades
cout<<"plz enter ur mid team and final exam grades \: ";
double midteam, final; //how about it has to be in double can it be int
cin>>midterm>>final;
//ask for the homework grades
cout<<"enter all ur homework grades, "
"follow by end of file: ';
//the number5 and sums of grades read so far
int count= 0;
double sum = 0;
//variable into which to read
double x;
//invariant:
//we have read count grades so far, and 
// sum is the sum of the first count grades
while {cin>>x) //what is this mean {
++count;
sum +=x;
//write the result 
streamsize prec= cout.precision(); //what does that line mean
cout<<"ur final grade is"<< setprecision(3) //does that lines mean display the line to 3 decimal place
<<0.2*midterm=0.4*final =0.4*sum/count
<<setprecision(prec) // what does that mean<<endl;
return 0;
}

```

---

### Post by Paul820 on 2007-07-30
Quoted from the book again:

> Our goal is to write the final grade with three significant digits, which we do by using **setprecision**. Like endl, **setprecision** is a manipulator. It manipulates the stream by causing subsequent output on that stream to appear with the given number of significant digits. By writing **setprecision( 3 )**, we are asking the implementation to write grades with **three significant digits**, generally two before and one after.

By using  **setprecision**, we change the precision of any subsequent output that might appear on cout. Because this statement is at the end of the program, we know there is no such output. Nevertheless, we believe that it is wise to reset cout's precision to what it was before we changed it. We do so by calling a member function of cout named **precision**. **This function tells us the precision that a stream uses for floating-point output. We use setprecision to set the recision to 3, write the final grade, and then set the precision back to the value that precision gave us.**

In other words, he is going to store the default precision in the variable **prec**, then he modifies the stream with **setprecision(3)**, and then resets the stream back to the original value that is stored in **prec**. 

You must read the book carefully if you want to understand. Everything is explained. He wouldn't write the book without explaining it. I hope you understand now.

---

### Post by Jessehk on 2007-07-30
> **zerobinary said:**
> err is that even the code on the first page

No, but it was an example demonstrating its use. You're going to have to learn to be independent and read documentation. Things are rarely going to be handed to you on a silver platter.

---

### Post by PandaGoat on 2007-08-02
You are using std::iostream--cin and cout.  Each uses a stream. There is a stream of data going out to the user, output; and a stream of data coming from the user, input.  Pretend that the stream is a tube that has a set width depending on what is going through it.  Numbers are limited to a certain precision.  The default precision is 6 digits [or something, i dont feel like looking, so just assume it is]. 

```

cout << 1234567; // Result: 123456

```

To get the current precision value, you use precision().
```

int precision = cout.precision(); // 6 unless you have used setprecision()

```

His code may be easier to understand if it was written this way:
```

streamsize prec= cout.precision();
cout<<"ur final grade is";
cout.setprecision(3) // Start displaying 3 digits from now on
cout<<0.2*midterm=0.4*final =0.4*sum/count;
cout.setprecision(prec); // Reset the precision to before you used setprecision()

```

---

### Post by jdmrsx05 on 2007-08-02
instead of using 

> using std::cin;
using std::cout; sorry didn't indent
using std::endl;
using std::setprecision;
using std::string;
using std::streamsize;


why not just use 

using namespace std;

then he shouldn't have to worry about setprecision or any of that, right?
he should just be able to do something along the lines of:

cout << setprecision(2) << /*whatever double you're printing*/;

---

### Post by Paul820 on 2007-08-02
You should only declare the names you are going to use. Or just do what i do and precede all the name i am using 'with std::'

---

### Post by jdmrsx05 on 2007-08-02
so is a bad programming practice?

> 
#include <iostream> //and so on for libraries

using namespace std;


---

### Post by Paul820 on 2007-08-02
I wouldn't say bad. With small programs it's not too bad, but when you start writing bigger more complicated programs it's best to limit what can be seen. Here's an explanation, i'll let you decide: [http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5]("http://www.parashift.com/c++-faq-lite/coding-standards.html#faq-27.5")
By the way, i would bookmark that site, loads of info on there.

---

### Post by jdmrsx05 on 2007-08-02
hey, that's good stuff!  thanks a lot.

---

