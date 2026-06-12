---
title: "Programming Challenge 3: BigNums"
date: 2008-03-05
forum: Programming Talk
---

### Post by aks44 on 2008-03-05
Hi everyone !

Your mission this week, if you accept it, will be to get rid of a *very* widespread bug: **integer overflows**. Most programmers tend to overlook that problem because of the wide range that integers can handle on modern architectures, but it may come and bite you when you expect it the least.

One workaround is to detect overflows (like I implemented in Lster's challenge), but it can only *prevent* them, not get rid of them.



The common solution is what is usually called [BigNums]("http://en.wikipedia.org/wiki/Bignum") (aka. arbitrary precision arithmetic).

Roughly, whenever a number is too wide to be represented by a single machine word, use as much words as necessary so that the number "fits in". This permits to represent infinitely large numbers (well, as far as the computer's memory allows).



You are expected to provide:
[LIST]
[*] A data structure for representing BigNums. BigNums are **integers** of arbitrary length, positive or negative. You are expected to represent them using sequences of typical machine words (eg. int32_t, int64_t is allowed too). That means that raw strings like "123456789123456789" are not allowed as a representation.
[*] Creation (from a normal integer) / copy / assignment (from either a BigNum or a normal integer) / deletion. Note the copy / assignment distinction (copy returns a new BigNum which is a copy of another, assignment modifies an existing BigNum).
[*] Addition and subtraction operations.
[*] A print routine (generic if possible, but stdout will do), base 10.
[/LIST]


Bonus points:
[LIST]
[*] Multiplication, division and modulo.
[*] "Trim" the BigNum so that it uses exactly the number of machine words that are needed to represent it. More points if every operation returns a "trimmed" number.
[*] Documentation & efficiency.
[*] Write a wrapper around BigNums so that it provides the same operations for arbitrary length decimal values. Hint: exponents.
[*] Surprise me. :)
[/LIST]


As usual, you have to code it from scratch.
You have until Wednesday 2008-03-12 19:00 GMT to submit your code.


"Que le meilleur gagne" ;)


**_EDIT:_** dammit, I didn't know that Python had built-in BigNum support... :oops:
Soooo...
**_Additional rule:_** anyone using a language that has built-in support for arbitrary length integers, has to consider that a valid signed integer is between -(2^31) and (2^31)-1, inclusive (ie. the 32-bit range). Valid unsigned integers would be from 0 to (2^32)-1, inclusive.

Sorry about that. :oops:

---

### Post by Lster on 2008-03-05
This is going to be tricky. I'm off to read up a little - I have a couple of ideas...

---

### Post by aks44 on 2008-03-05
> **Lster said:**
> This is going to be tricky. I'm off to read up a little - I have a couple of ideas...

Well, this is indeed an advanced topic.

TBH I don't expect anyone to implement such a library in a *complete* manner. This would involve too many tedious work, which is not the goal of these challenges. Just the "expected work" is way enough to keep you people busy.

So I went for the "educational" way, which you have grasped correctly: document yourselves, learn the issues, then do as much as you can.


If anyone manages to learn something from it (rather than just apply what she already knows) then I'll consider that this challenge fulfilled its goal. :D

---

### Post by Acglaphotis on 2008-03-05
This is waaay harder than the last one (and even that one i didn't finish on time).

---

### Post by hod139 on 2008-03-06
I noticed this thread was getting no love, so here is my quick hack of a solution
[php]
#include<string>
#include<sstream>
#include<deque>
#include<iostream>
#include<algorithm>
#include<iterator>

/**
 * BigNum representation for ints
 */
class BigInt{
public: 
  ///
  /// Default constructor, no value
  ///
  BigInt(){
     m_negative = false;
  }

  ///
  /// Constructor for a long, initializes value to val
  ///
  explicit BigInt(long val){
    (val < 0) ? m_negative = true : m_negative = false;
    val = abs(val);
    while (val) {
      m_bigNum.push_front(val % 10);
      val /= 10;
    }
  }
  
  ///
  /// Constructor for a string, initializes value to val
  ///
  explicit BigInt(const std::string &val){
     std::string::const_iterator itr = val.begin();
     if(*itr == '-')
     { // this is a negative number
        m_negative = true;
        ++itr;
     }
     else // positive number
       m_negative = false;

     int convertedVal = 0; // placeholder for converted chars 
     for ( ; itr != val.end(); ++itr) 
     { // for each character of this string
       std::string s2(1, *itr); // create a temp string from this char
       std::istringstream ss(s2); // now create an input stringstream of the temp string
       if (ss >> convertedVal){ // see if the string can be converted to an int 
          m_bigNum.push_back(convertedVal);
       }
       else{
         std::cerr << "Invalid string representation of an int\n"; 
         std::cerr << "  " << val << std::endl;
         assert(0); // lazy exception handling
       }      
    }
  }

 
  ///
  /// Assignment operator for long
  ///
  BigInt & operator = (long val)
  {
      BigInt newInt(val);
      m_bigNum = newInt.m_bigNum;
      m_negative = newInt.m_negative;
 
      return *this;
  }

  ///
  /// Assignment operator for string
  ///
  BigInt & operator = (const std::string &val)
  {
      BigInt newInt(val);
      m_bigNum = newInt.m_bigNum;
      m_negative = newInt.m_negative;
 
      return *this;
  }

  ///
  /// overload the - operator for subtraction
  ///
  BigInt operator-(const BigInt &rhs) const {
    BigInt returnVal;
    size_t carry = 0; 
    size_t diff = 0; 

    // (-a) - b == -(a+b)
    if(m_negative && !rhs.m_negative)
    {
      BigInt temp = *this;
      temp.m_negative = false;
      returnVal = (rhs + temp);
      returnVal.m_negative = true;
      return returnVal;
    }

    // (+-a) - (-b) == (+-a) + b
    if(rhs.m_negative)
    {
      BigInt temp = rhs;
      temp.m_negative = false;
      return (*this + temp);
    }
           
    // walk backwards through the deques
    std::deque<size_t>::const_reverse_iterator thisItr = m_bigNum.rbegin();
    std::deque<size_t>::const_reverse_iterator rhsItr = rhs.m_bigNum.rbegin();
 
    // as long as one of the two deques is not empty, subtract the values  
    for(; thisItr != m_bigNum.rend() && rhsItr != rhs.m_bigNum.rend(); ++thisItr, ++rhsItr ) 
    { 
      const size_t &integer1 = *thisItr; 
      const size_t &integer2 = *rhsItr;
      if(integer1 < integer2+carry)
      { // need to borrow
        diff = (integer1+10) - (integer2+carry);
        carry = 1;
      }
      else{
        diff = integer1 - (integer2+carry);
        carry = 0;         
      } 
      returnVal.m_bigNum.push_front(diff); 
    } 
         
    // one of the deque iterators may not be done 
    for ( ; thisItr != m_bigNum.rend(); ++thisItr ) 
    {  
      const size_t &integer1 = *thisItr;
      if(integer1 < carry)
      { // need to borrow
        diff = integer1+10 - carry;
        carry = 1;
      }
      else{
        diff = integer1 - carry;
        carry = 0;         
      } 
      returnVal.m_bigNum.push_front(diff); 
    }
  
    // OOPS, do it again, but switch the ordering of the subtraction
    // TODO: think of a better way, this is so wasteful
    if(carry == 1 || rhsItr != rhs.m_bigNum.rend())
    { 
       returnVal = rhs - *this;
       returnVal.m_negative = true;
    }

    returnVal.trim(); // trim away any leading zeros that might have showed up
    return returnVal;
  }

  ///
  /// overload the + operator for adding
  ///
  BigInt operator+(const BigInt &rhs) const{
    BigInt returnVal;
    size_t carry = 0; 
    size_t sum = 0; 

    // (-a) + b == b - a
    if(m_negative && !rhs.m_negative)
    {
      BigInt temp = *this;
      temp.m_negative = false;
      return (rhs - temp);
    }
    // a + (-b) == a - b
    if(!m_negative && rhs.m_negative)
    {
      BigInt temp = rhs;
      temp.m_negative = false;
      return (*this - temp);
    }
    // (-a) + (-b) == -(a + b)
    if(m_negative && rhs.m_negative)
      returnVal.m_negative = true; 
        
    // walk backwards through the deques
    std::deque<size_t>::const_reverse_iterator thisItr = m_bigNum.rbegin();
    std::deque<size_t>::const_reverse_iterator rhsItr = rhs.m_bigNum.rbegin();
 
    // as long as one of the two deques is not empty, add the values  
    for(; thisItr != m_bigNum.rend() && rhsItr != rhs.m_bigNum.rend(); ++thisItr, ++rhsItr ) 
    { 
      const size_t &integer1 = *thisItr; 
      const size_t &integer2 = *rhsItr; 
      sum = carry + integer1 + integer2; 
      carry = sum / 10; 
      sum = sum % 10; 
      returnVal.m_bigNum.push_front(sum); 
    } 
         
    // one of the deque iterators may not be done
    // only one of the following two for loops will be entered 
    for ( ; thisItr != m_bigNum.rend(); ++thisItr ) 
    {  
      const size_t &integer1 = *thisItr; 
      sum = carry + integer1; 
      carry = sum / 10; 
      sum = sum %10; 
      returnVal.m_bigNum.push_front(sum); 
    } 
    for ( ; rhsItr != rhs.m_bigNum.rend(); ++rhsItr ) 
    {  
      const size_t &integer2 = *rhsItr; 
      sum = carry + integer2; 
      carry = sum / 10; 
      sum = sum %10; 
      returnVal.m_bigNum.push_front(sum); 
    } 
         
    // There might still be a leftmost carry 1 not pushed  
    if (carry == 1) 
      returnVal.m_bigNum.push_front(1);

    return returnVal;
  }
  
  /// Let ostream's operator<<() be a friend
  friend std::ostream & operator<<(std::ostream &s, const BigInt &b);

private:

  ///
  /// remove any leading 0s
  ///
  void trim(){
    while(!m_bigNum.empty() && m_bigNum.front() == 0) m_bigNum.pop_front();
    if(m_bigNum.empty()) m_bigNum.push_back(0); // just in case the value is 0
  }

  std::deque<size_t> m_bigNum; //!< Use a deque representation of the bigNum
  bool m_negative; //!< flag to determine the sign of the number
};

///
/// Print the number
///
std::ostream &operator<<(std::ostream &s, const BigInt &b)
{
  if(b.m_negative) s << "-";
  std::copy(b.m_bigNum.begin(), b.m_bigNum.end(), std::ostream_iterator<int> (s, ""));
  return s;
  
}


/**
 * Entry point
 */
int main(void){

  BigInt a("1");
  BigInt b(2);
  std::cout << a+b << std::endl;
  std::cout << a-b << std::endl;

  a = -1;
  b = "2";
  std::cout << a+b << std::endl;
  std::cout << a-b << std::endl;

  a = 1;
  b = "-2";
  std::cout << a+b << std::endl;
  std::cout << a-b << std::endl;

  a = -1;
  b = "-2";
  std::cout << a+b << std::endl;
  std::cout << a-b << std::endl;

  a = 1;
  b = "123456789123456789123456789123456789123456789123456789";
  std::cout << a+b << std::endl;
  std::cout << a-b << std::endl;

  return 0;
}
[/php]and output
```

3
-1
1
-3
-1
3
-3
1
123456789123456789123456789123456789123456789123456790
-123456789123456789123456789123456789123456789123456788

```I didn't do too much error checking, so there could still be bugs.  I also didn't worry too much about efficiency (focusing on readability).  But it seems to be working for the few small test cases I did.

---

### Post by Siph0n on 2008-03-07
Not done yet, but I wanted to get this out there... Can someone tell me if I am on the right track, or if what I am doing is right? I was hoping to use a linked list instead of a list to be able to hold more digits (I think).... Thanks! I appreciated any constructive criticism...

```

import copy

def Sub(num1,num2):
    sum = []

    # Set the length
    if len(num1) >= len(num2):
        length = len(num1)
    else:
        length = len(num2)
        
    # Subtracting two numbers with different signs - Add
    if num1[0] != num2[0]:
        # Set the overall sign
        if num1[0] == '+': sign = '+'
        else: sign = '-'
                    
        # Reverse them so I can work left to right instead of right to left
        num1.reverse()
        num2.reverse()

        carryover = 0
        for i in range(0,length-1):
            if (len(num1) > len(num2)) and (i >= len(num2)): number2=0
            else: number2 = num2[i]
            if (len(num2) > len(num1)) and (i >= len(num1)): number1=0
            else: number1 = num1[i]
            if number1 == '-' or number1 == '+': number1 = 0
            if number2 == '-' or number2 == '+': number2 = 0
            result = int(number1) + int(number2) + carryover
            carryover = 0
        # Put the result of each column addition in result
            if result >= 10:
                carryover = result / 10
                result = result % 10
            sum.append(result)
        if carryover != 0: sum.append(carryover)
        
        sum.append(sign)

    # Subtracting two numbers with the same sign - Subtract
    else:
        reverse = False
        # Set the overall sign
        if len(num1) > len(num2):
            if num1[0] == '-': sign = '-'
            elif num1[0] == '+': sign = '+'
        else:
            if num1[0] == '-': sign = '+'
            elif num1[0] == '+': sign = '-'
            num1,num2 = num2,num1
            reverse = True
            
        # Set the sign
        if len(num1) == len(num2):
            for i in range(0,length-1):
                if num1[i] >= num2[i]:
                    if num1[0] == '-': sign = '-'
                    elif num1[0] == '+': sign = '+'
                    length = len(num1)
                else:
                    if num1[0] == '-': sign = '+'
                    elif num1[0] == '+': sign = '-'
                    num1,num2 = num2,num1
                    reverse = True
                    length = len(num2)

        # Reverse them so I can work left to right instead of right to left
        num1.reverse()
        num2.reverse()

        # Create copies of numbers because I need to change them, and I want to keep the originals
        numb1 = copy.copy(num1)
        numb2 = copy.copy(num2)
        
        for i in range(0,length-1):
            if (len(num1) > len(num2)) and (i >= len(num2)): number2=0
            else: number2 = numb2[i]
            if (len(num2) > len(num1)) and (i >= len(num1)): number1=0
            else: number1 = numb1[i]
            if number1 == '-' or number1 == '+': number1 = 0
            if number2 == '-' or number2 == '+': number2 = 0
            if number1 >= number2: result = int(number1) - int(number2)
            else:
                for ii in range(i+1,length-1):
                    if int(numb1[ii]) > 0:
                        numb1[ii] = int(numb1[ii]) - 1
                        numb1[i] = int(numb1[i]) + 10
                        break
                    else: numb1[ii] = 9
                result = int(numb1[i]) - int(numb2[i])
        # Put the result of each column addition in result
            sum.append(result)
        
        # If I reversed the numbers to get the subtraction to work, reverse them again
        if reverse: num1,num2 = num2,num1

        # Put the sign on the result
        sum.append(sign)
        
    # Reverse the numbers to make it forward
    sum.reverse()
    num1.reverse()
    num2.reverse()

    # Trim
    i = 1
    while i < len(sum)-1:
        if int(sum[i]) == 0:
            i += 1
        else: break
    del sum[1:i]

    # Print the results
    Print(num1,'-',num2,sum)
        
def Add(num1,num2):
    sum = []
    if num1[0] != num2[0]:
        # Get the max of the two numbers
        if len(num1) >= len(num2): length = len(num1)
        else:
            length = len(num2)
            num1,num2 = num2,num1
            
        # Make sure the greater number is num1
        if len(num1) == len(num2):
            for i in range(0,length-1):
                if num1[i] < num2[i]: num1,num2 = num2,num1

        if num1[0] == '-': sign = '-'
        else: sign = '+'

        # Reverse them so I can work left to right instead of right to left
        num1.reverse()
        num2.reverse()

        numb1 = copy.copy(num1)
        numb2 = copy.copy(num2)
        
        for i in range(0,length-1):
            if (len(num1) > len(num2)) and (i >= len(num2)): number2=0
            else: number2 = numb2[i]
            if (len(num2) > len(num1)) and (i >= len(num1)): number1=0
            else: number1 = numb1[i]
            if number1 == '-' or number1 == '+': number1 = 0
            if number2 == '-' or number2 == '+': number2 = 0
            if number1 >= number2: result = int(number1) - int(number2)
            else:
                for ii in range(i+1,length-1):
                    if int(numb1[ii]) > 0:
                        numb1[ii] = int(numb1[ii]) - 1
                        numb1[i] = int(numb1[i]) + 10
                        break
                    else: numb1[ii] = 9
                result = int(numb1[i]) - int(numb2[i])
        # Put the result of each column addition in result
            sum.append(result)
        
        sum.append(sign)

    else:
        # If adding two numbers and the signs are both negative, than over all sign is negative
        if num1[0] == '-': sign = '-'
        else: sign = '+'
        
        # Get the max of the two numbers
        if len(num1) >= len(num2): length = len(num1)
        else: length = len(num2)
        
        # Reverse them so I can work left to right instead of right to left
        num1.reverse()
        num2.reverse()

        carryover = 0
        for i in range(0,length-1):
            if (len(num1) > len(num2)) and (i >= len(num2)): number2=0
            else: number2 = num2[i]
            if (len(num2) > len(num1)) and (i >= len(num1)): number1=0
            else: number1 = num1[i]
            if number1 == '-' or number1 == '+': number1 = 0
            if number2 == '-' or number2 == '+': number2 = 0
            result = int(number1) + int(number2) + carryover
            carryover = 0
        # Put the result of each column addition in result
            if result >= 10:
                carryover = result / 10
                result = result % 10
            sum.append(result)
        if carryover != 0: sum.append(carryover)
        
        sum.append(sign)

    # Reverse the numbers to make it forward
    sum.reverse()
    num1.reverse()
    num2.reverse()

    # Trim
    i = 1
    while i < len(sum)-1:
        if int(sum[i]) == 0:
            i += 1
        else: break
    del sum[1:i]
        
    # Print the results
    Print(num1,'+',num2,sum)

def BigNum(a):
    num = []
    if a.isdigit():
        num.append('+')
        for i in range(0,len(a)):
            num.append(a[i])
        return num
    else:
        for i in range(0,len(a)):
            num.append(a[i])
        return num

def Print(num1,sign,num2,sum):
    print ' ',
    for i in num1:
#        print '\b'+str(i),
        print str(i),
    print
    print sign,
    for i in num2:
        print str(i),
    print
    if len(num1) >= len(num2): length = len(num1) + 1
    else: length = len(num2) + 1
    for i in range(0,length):
        print '-',
    print
    print ' ',
    for i in sum:
        print str(i),
    print
    print

# 2 New Big Numbers...
num1 = BigNum("-100000000000000000000000000000000")
num2 = BigNum("-1")
num3 = BigNum("1")
num4 = BigNum("100000000000000000000000000000000")
Add(num1,num2)
Add(num2,num1)
Add(num3,num4)
Add(num4,num1)
Sub(num1,num2)
Sub(num2,num1)
Sub(num3,num4)
Sub(num4,num1)

```

Output:
```

  - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
+ - 1
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1

  - 1
+ - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1

  + 1
+ + 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  + 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1

  - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
+ + 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  - 0

  - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - 1
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  - 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9

  - 1
- - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  + 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9

  + 1
- + 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  - 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9 9

  + 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
  + 2 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0

```

Had to change it up because the subtraction of two numbers that had the same sign was messed up...  Not the cleanest... But it works for addition and subtraction... :)

---

### Post by Siph0n on 2008-03-08
Updated my code... It now does subtract and can take negative numbers... I still need to make it shorter/cleaner... Plus get rid of leading zeros...

---

### Post by aks44 on 2008-03-10
Hello,

I'm bumping this thread to remind you that you have until Wednesday 19:00 GMT (when I come home from work) to submit your solution. :)


The two entries so far are good.


To everyone else, I repeat: the goal of this challenge is not that you fulfil it completely, but that you learn about the issues of computer integer arithmetics, and how to work around them.
So don't worry, just do as much as you can... :)

---

### Post by Lster on 2008-03-10
I'll have a solution eventually but college is rather time consuming right now. I'm not put off by its difficulty! ;)

---

### Post by aks44 on 2008-03-12
Lster (and others) : about 6 hours left... ;)

---

### Post by Lster on 2008-03-12
It's coming... :) I should have it in two hours more.

---

### Post by Lster on 2008-03-12
Here is my very basic solution. It doesn't  even meet the minimum requirements but I might go on to expand it (obviously not for the competition) so I can use it generally.

[PHP]

/*
	Abitary Precision.c
	By Lster
	
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
*/


#include "stdlib.h"
#include "stdio.h"
#include "string.h"
#include "math.h"

// Notes: If an error is returned by a function, it should be assumed that the
// BigNum objects sent to the function are now destroyed. It performs very
// little error checking for speed.

// Signs, subtraction, multiplication and addition have been ommitted. I've just
// run out of time! Hope it's OK for a couple of hours work. :)

// The BigNum struct which represents a number, stored as binary of an abitary
// length. Properties include: N, the number of bits; and Binary a pointer
// to the bit string.
typedef struct _BigNum
{
	unsigned long N;
	char * Binary;
} BigNum;


// Gets a bit within a binary string.
long BigNum_GetBit ( char * Binary , long Bit )
{
	return ( Binary [ Bit / 8 ] >> ( Bit % 8 ) ) & 1;
}

// Sets a bit within a binary string.
void BigNum_SetBit ( char * Binary , long Bit , long Value )
{
	unsigned long K = 1 << ( Bit % 8 );
	if ( Value == 0 )
		Binary [ Bit / 8 ] &= ~K;
	else
		Binary [ Bit / 8 ] |= K;
}

// Allocates a new BigNum with the value Value.
BigNum * BigNum_Create ( unsigned long X , unsigned Size )
{
	BigNum * T = malloc ( sizeof ( BigNum ) );
	if ( T == 0 ) return 0;
	
	T -> N = Size;
	T -> Binary = malloc ( T -> N );
	if ( T -> Binary == 0 )
	{
		free ( T );
		return 0;
	}
	
	long I , J , K;
	for ( I = 0 ; I < Size ; I ++ )
		T -> Binary [ I ] = 0;
	
	for ( I = 0 ; I < Size ; I ++ )
	{
		J = BigNum_GetBit ( ( char * ) & X , I );
		BigNum_SetBit ( T -> Binary , I , J );
	}
	
	return T;
}

// Deallocates a BigNum object.
void BigNum_Delete ( BigNum * X )
{
	free ( X -> Binary );
	free ( X );
}

// Allocates and returns a new, identical BigNum from another.
BigNum * BigNum_Copy ( BigNum * X )
{
	BigNum * R = malloc ( sizeof ( BigNum ) );
	if ( R == 0 ) return 0;
	R -> N = X -> N;
	
	R -> Binary = malloc ( R -> N );
	if ( R -> Binary == 0 )
	{
		free ( R );
		return 0;
	}
	
	memcpy ( R -> Binary , X -> Binary , X -> N );
	return R;
}

// Copies X's properties into Y. X and Y must have been already allocated.
void BigNum_Set ( BigNum * Y , BigNum * X )
{
	Y -> N = X -> N;
	memcpy ( Y -> Binary , X -> Binary , X -> N );
}

// Prints a unsigned long as binary. This is primarily used by BigNum_Print but
// may also serve other uses.
long BigNum_PrintLong ( unsigned long X , long Write )
{
	long I;
	unsigned long K = 1 << 7;
	
	for ( I = 0 ; I < 8 ; I ++ )
	{
		if ( X & K )
		{
			printf ( "1" );
			Write = 1;
		}
		else if ( Write )
		{
			printf ( "0" );
		}
		
		K >>= 1;
	}
	
	return Write;
}

// Prints a BigNum.
void BigNum_Print ( BigNum * X , long NewLine )
{
	long I , L = X -> N / 8;
	long Write = 0;
	
	for ( I = L - 1 ; I >= 0 ; I -- )
	{
		unsigned char T = X -> Binary [ I ];
		Write = BigNum_PrintLong ( T , Write );
	}
	if ( NewLine ) printf ( "\n" );
}

// Adds Y to X, modifying X.
long BigNum_Add ( BigNum * X , BigNum * Y )
{
	long Last = 0;
	long I , T;
	
	for ( I = 0 ; I < X -> N ; I ++ )
	{
		Last += BigNum_GetBit ( X -> Binary , I ) + BigNum_GetBit ( Y -> Binary , I );
		T = Last >= 2;
		
		BigNum_SetBit ( X -> Binary , I , Last % 2 );
		
		if ( T )	Last = 1;
		else		Last = 0;
	}
	
	return 1;
}


// Test it!
int main ( void )
{
	BigNum * A = BigNum_Create ( 16383 , 16 ); //18446744073709551615
	BigNum * B = BigNum_Create ( 9 , 16 );
	
	printf ( "\n" );
	
	BigNum_Print ( A , 1 );
	BigNum_Print ( B , 1 );
	
	BigNum_Add ( A , B );
	BigNum_Print ( A , 1 );
	
	BigNum_Delete ( A );
	BigNum_Delete ( B );
	
	printf ( "\n" );
	
	return 0;
}

[/PHP]

It does very little error checking, and should be reasonably fast. I could do a _lot_ of things to improve performance - but there is no time now! :)

---

### Post by Siph0n on 2008-03-12
I don't know if its too late, but I added trim in mine... to get rid of leading 0's

---

### Post by aks44 on 2008-03-12
Ok, here are my comments...


Lster: very good work, quite close "in spirit" to what I had in mind (ie. bit/binary manipulations rather than decimal arithmetic) but unfortunately the implementation is not as complete as the others'. Better luck next time. ;)


hod139 & Siph0n : both your submissions are quite close, so I had hard time choosing between the two.


[SIZE="3"]**Siph0n**[/SIZE], your code could use some factorization, but (from what I can tell) your substraction algorithm is not victim of leftover carries like hod139's algorithm is (his "OOPS" part) as you do more work upfront to avoid that. This detail makes you the **winner** of this challenge... Congratulations. :)



Oh well, this was not an easy one, all I hope is that you people learned something along the way... I'm eagerly waiting for the next challenge. :-D

---

### Post by Siph0n on 2008-03-12
Thanks! :) Yea my code could use a lot of work! :) I will think of the new challenge when I get home today, and have it up by tonight! :)

---

### Post by Lster on 2008-03-12
Congratulations, Siph0n! :) I'm looking forwards to the next challenge.

[QUOTE=aks44]Lster: very good work, quite close "in spirit" to what I had in mind (ie. bit/binary manipulations rather than decimal arithmetic) but unfortunately the implementation is not as complete as the others'. Better luck next time.[/QUOTE]

This topic has intrigued me, so I doubt I'll stop with just positive numbers and addition. I'll be coding up the other functions in m spare time - but I don't have a lot of it! :)

---

### Post by ruy_lopez on 2008-03-12
Well done Siph0n.

Now it's over, I can post this [link]("http://en.literateprograms.org/Special:Downloadcode/Arbitrary-precision_integer_arithmetic_%28C%29").

---

### Post by aks44 on 2008-03-12
> **Lster said:**
> This topic has intrigued me

A real-world implementation would use all bits (like you did) but in a more efficient manner (ie. using the processor's ability to handle 32 or 64 bits in a row).

The most efficient way to handle this would be in ASM, using the Overflow (or Carry? can't remember right now) flag to propagate the carry. Another (less efficient way) would be to use the same kind of overflow detection I implemented in Lster's previous challenge.


The only really tricky part is displaying the whole BigNum in base 10, which the "double dabble" algorithm addresses... ;)

---

