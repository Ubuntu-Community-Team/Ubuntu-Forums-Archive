---
title: "while"
date: 2011-01-11
forum: Programming Talk
---

### Post by Dorian Mayorquin on 2011-01-11
Hello, i'm having trouble with this c++ code:



// average.cpp
// Computing the average of numbers
#include <iostream>
using namespace std;
int main()


{
int x = 0;
int count = 0;
float sum = 0.0;

cout << "Please enter some integers:\n"
"(Break with any letter)"<< endl;

while( cin >> x )
{
 sum = sum + x;
++count;
}
cout << "The average of the numbers: "<< endl;
cout << sum / count << endl;
return 0;
}



Why does the variable "x", stores more than one value and with cin >> x; only stores one value?

When you input 9 10 12a, when does 9+10+12 occur if it only says sum = sum +x; or sum += x; i mean 0.0 + 9 10 12 ?

Why does ++count; stores how many numbers there are and not only one number that would be 91012?


Thanks everybody!

---

### Post by dwhitney67 on 2011-01-11
91012 is not the same as 9 10 12

cin attempts to fulfill the request you have asked of it, and that's to read an int value from the input stream.  Since you have a while loop, it will continue doing that until it is unable to.  Thus when cin encounters a letter, it cannot plug that into an int, and thus the stream reports that an error occurred.

There is an operator bool() function associated with cin, thus that function is called when necessary to fulfill the need for a conditional value within the while () statement.

Hopefully with this knowledge, you will experience some enlightenment and understand the purpose of the while loop, and furthermore that for each iteration that it performs, the value of sum is incremented by the value of x, and that the count variable is incremented by one.

Btw, it is customary to write "sum = sum + x" as "sum += x".

---

### Post by Lootbox on 2011-01-11
> Why does the variable "x", stores more than one value and with cin >> x; only stores one value?
Could you clarify what you mean?

```

while (cin >> x) {
    sum = sum + x;
    ++count;
}

```
Basically, x is a single variable of type int, declared above. Calling cin >> x will wait for the user to input an integer; when the user does (and hits <enter>), that integer will be written to x. Then, in the body of the loop, that value x is added to sum, and count is incremented by 1.

One tricky thing to note: the while loop will only exit when cin >> x returns a value that converts to false. If all you enter are numbers and whitespace characters, the loop will keep going. It will only stop when the extraction from cin fails, which is when you type in a character that can't be converted to an integer (like 'a' in your example). At that point, cin >> x evaluates to false, so the average (sum divided by number of integers input) is computed and printed.

> When you input 9 10 12a, when does 9+10+12 occur if it only says sum = sum +x; or sum += x; i mean 0.0 + 9 10 12 ?
If on a single line, you input multiple numbers separated by whitespace ("2 3 4"), cin >> x consumes them one at a time; however, each subsequent extraction happens immediately without waiting for further user input. So typing in "9 10 12a" and then hitting <enter> will do the following:

- cin >> x will extract the value 9 and store it in x. The cin stream is currently positioned after the "9" in "9 10 12a". cin >> x was successful, so it evaluates to true.

- The while loop's body executes; 9 is added to sum, and count increases by 1.

- Back to the while loop's condition. This time, cin >> x will extract the value 10 and store it in x. The cin stream is currently positioned after the "10" in "9 10 12a", and the while condition is true.

- The while loop's body executes; 10 is added to sum, and count increases by 1.

- Same thing happens with 12 (sorry, I'm lazy).

- Now, the cin stream is positioned right before the 'a'. cin >> x expects to extract an integer and store it in x. This is not possible, so the cin stream is put in a failed state and cin >> x evaluates to false. The while loop is finished.

- sum has the value of 31 (9 + 10 + 12), and count is 3.

Unintuitive behavior like this with unexpected input is why using cin with the >> operator has limited utility; you're probably better off using a combination of getline and a stringstream object.

---

