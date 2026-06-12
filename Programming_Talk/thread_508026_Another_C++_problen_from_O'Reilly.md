---
title: "Another C++ problen from O'Reilly"
date: 2007-07-23
forum: Programming Talk
---

### Post by sdmike on 2007-07-23
Just for the record I have done about 3 C++ problems since my last post with zero help.

But now I am stuck.
[COLOR="Red"]
The problem is to, write a program to perform date arithmetic, such as how many days there are between 6/1/90 and 8/3/92.
[/COLOR]

So I know that each month doesn't have the same numbers of days as the next. So I declared the number of days for each month but then I had to stop because I wasn't sure how to declare a number to a number of days. So then I got confused, then I started to think of other routes then I stopped.

So how should I be declaring numerical months to a number of days?

---

### Post by vambo on 2007-07-23
Have a look in C's time.h

---

### Post by sdmike on 2007-07-23
I shall check that out. The book hasn't gone over functions like those but I will still check it out.

Is your Avatar the British Dennis the Menes BTW?

---

### Post by lisati on 2007-07-23
You might want to look into the idea of "julian" dates, where a date is converted into the number of days from the start of the year.

---

### Post by vambo on 2007-07-23
> **sdmike said:**
> I shall check that out. The book hasn't gone over functions like those but I will still check it out.

Is your Avatar the British Dennis the Menes BTW?

Indeed it is

---

### Post by sdmike on 2007-07-23
I really appreciate your guys advice but I think those functions might be a bit too advanced for where I am at in this chapter.

So is there a more basic way to accomplish this?

---

### Post by sdmike on 2007-07-23
As you can see in my code. When I was done it hit me that people are going to be putting in numbers not letters. 
So I was thinking how I could convert these month initialize into numbers like 1 = Jan = 31 days.

```
#include <iostream>

int dateOne;
int dateTwo;
int difference;
int Jan;
int Feb;
int Mar;
int Apr;
int May;
int Jun;
int Jul;
int Aug;
int Sep;
int Oct;
int Nov;
int Dec;

int main()
{
Jan= 31;
Feb = 28;
Mar = 31;
Apr = 30;
May = 31;
Jun = 30;
Jul = 31;
Aug = 31;
Sep = 30;
Oct = 31;
Nov = 30;
Dec = 30;
 
std::cout <<  "Enter in the two dates.\n";
std::cin >> dateOne >> dateTwo;
std::cout << "The number of days between the two dates is "<< difference;
return (0);
}
```

---

### Post by vambo on 2007-07-23
Why not pit all these numbers into arrays, then manipulate them to suit?

---

### Post by sdmike on 2007-07-23
I haven't had much practice with arrays, but the book did go over arrays so far in the chapters that I have read. So I will read up on arrays again.

---

### Post by sdmike on 2007-07-23
So I've gotten this far just making things a bit more clear. I just got to figure out a simple algorithm for it now.

```
#include <iostream>
short m1, m2, d1, d2; // numerical number for days and months
int y1, y2; // numerical numbers for years

int main() {

 std::cout << "Please enter a start date (mm dd yyyy): ";
 std::cin >> m1 >> d1 >> y1;
 std::cout << "Please enter an end date (mm dd yyyy): ";
 std::cin >> m2 >> d2 >> y2;

 std::cout << "Difference in days: " << ".\n";
 return 0;
}
```

---

### Post by sdmike on 2007-07-23
Is there any way to tell the program to disregard negative numbers?
```

#include <iostream>
short m1, m2, d1, d2; // numerical number for days and months
int y1, y2; // numerical numbers for years
int days; //how many days there are total

int main() {

 std::cout << "Please enter a start date (mm dd yyyy): ";
 std::cin >> m1 >> d1 >> y1;
 std::cout << "Please enter an end date (mm dd yyyy): ";
 std::cin >> m2 >> d2 >> y2;

days = (((y1-y2)*360) - (d1-d2)) - ((m1-m2)*12);

 std::cout << "Difference in days: " << days << ".\n";
 return 0;
}
```

---

### Post by sdmike on 2007-07-24
I ended up with this. I know it's not accurate because of two things; Leap years and not every month has 31 days but here is what I have.

```
#include <iostream>
short m1, m2, m3, d1, d2, d3, d4, d5; // numerical number for days and months d4 and d5 are for the calculations to avoid a negative outcome
int y1, y2, y3; // numerical numbers for years
int days; //how many days there are total

int main() {
while (true){

 std::cout << "Please enter a start date (mm dd yyyy): ";
 std::cin >> m1 >> d1 >> y1;
 std::cout << "Please enter an end date (mm dd yyyy): ";
 std::cin >> m2 >> d2 >> y2;

if (m1||d1||y1 == 0)
    break;

else if (m2||d2||y2 == 0)
    break;

else if (m1 < m2)
y3 = -1*y3;

else if (d4 < 0)
d4 = -1*d4;

else if (d1 < 0)
d5 = -1*d5;

else if (d1 < d2)

d3 = -1*d3;

}
y3 = (y2 - y1);

d4 = d1 - 31;
d5 = d2 - 31;

d3 = ((d4) - (d5));
m3 = ((m1-m2)*31);

days = (((y3*360)-d3) - (m3));

 std::cout << "Difference in days: " << days << ".\n";

 return 0;
} 
```

---

### Post by hod139 on 2007-07-24
> **sdmike said:**
> Is there any way to tell the program to disregard negative numbers?

Yes.  Here is the example from the [C++ faq]("http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3")
```

while ((std::cout << "How old are you? ")
          && (!(std::cin >> age) || age < 1 || age > 200)) {
     std::cout << "That's not a number between 1 and 200; ";
     std::cin.clear();
     std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
   }

```
This will ignore all numbers not in the range 1 to 200, and loop until it gets valid input.

---

### Post by Note360 on 2007-07-24
an array for your usage

```

    int months[13];

    // the 0 here is purely so you can call January month 1 with a 1 instead of a zero and so on
    months = {0, 31, 28, 31, 30, 30, 31, 31, 30, 31, 30, 31};

    // After input divide the year that was inputed by 4 to see if it is a leap year then     change 28 to 29

```

---

