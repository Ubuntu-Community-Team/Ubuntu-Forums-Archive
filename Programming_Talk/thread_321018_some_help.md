---
title: "some help"
date: 2006-12-18
forum: Programming Talk
---

### Post by ankakusu on 2006-12-18
the cpp code gives error. do you have any idea? I am trying to use template. can you help? thank you..

I have attached the codes. thank you again.

---

### Post by ankakusu on 2006-12-18
let me write the whole code explicitly:

I have a global function called AlgebraicExpression. I put the .h and .cpp codes. Then I have a Stack.h and Stack.cpp files. I will use them in the AlgebraicExpression files. I need a Stack object with type char and a Stack type object with type int. Therefore I decided to use template.

Question 1:
in Stack.h I write that:
friend class AlgebraicExpression;

but still I can not reach the private members of Stack from the global function Algebraic Expression. How can I solve this problem?

```


//AlgebraicExpression.h
#include <string>
using std::string;

#include "Stack.h"

string infix2postfix( const string);
int CheckTypeOfChar(const char);
int precedence(const char);
void toStack(const string );


Stack<char> operands;
Stack<int> operators; // end of AlgebraicExpression.h

```

```


//AlgebraicExpression.cpp

#include <iostream>
using std::cout;
using std::endl;

#include <string>
using std::string;

#include "AlgebraicExpression.h"

string infix2postfix( const string exp ){
   string postFix=" ";
   T tempc;
   T tempi;
   
   for(int index=0;index<exp.length();index++ ){
      int ch=CheckTypeOfChar(exp[index]);
      switch (ch)
      {
         case 1:
         (int) exp[index];
         operands.push(exp[index]);
         break;
         case 2:
            
            while (!operators.isEmpty()&&operators.topPtr->item!='('&& precedence(ch) <= precedence(operators.topPtr->item)){
               postFix += operators.topPtr->item;
               operators.pop(tempc);
            }
         operators.push(exp[index]);
         //postFix+=exp[index];
         break;
         case 3:
         operators.push(exp[index]);   
         break;
         case 4:
            while ( operators.topPtr -> item != '('){
                  postFix += operators.topPtr -> item;
                  operators.pop(T);
                  //cout<< "operators.topPtr->item" <<operators.topPtr->item<<endl;
               }
            operators.pop();
            //cout<< "operators.topPtr->item" <<operators.topPtr->item<<endl;
         operators.push(exp[index]);
         break;
      }
   }
   return postFix;
}

int CheckTypeOfChar(const char ch){
   if(ch =='1' || ch =='2'||ch =='3'||ch =='4'||ch =='5'||ch =='6'||ch =='7'||ch =='8'||ch =='9')
      return 1;
   else if (ch == '*' || ch =='/' || ch =='+' || ch =='-' )
      return 2;
   else if (ch == '(')
      return 3;
   else if ( ch ==')')
      return 4;
}

int precedence (const char ch1){
   char operatorTypes[]={'*','/','+','-','(',')'};
      if(ch1==operatorTypes[0] || ch1==operatorTypes[1] )
         return 2;
      else if (ch1==operatorTypes[2] || ch1==operatorTypes[3] )
         return 1;
   
}

void toStack(const string exp )
{
   for(int index=0;index<exp.length();index++ )
   {
      int ch=CheckTypeOfChar(exp[index]);
      switch (ch)
      {
         case 1:
         (int) exp[index];
         operands.push(exp[index]);
         break;
         case 2:
         operators.push(exp[index]);
         break;
         case 3:
         operators.push(exp[index]);   
         break;
         case 4:
         operators.push(exp[index]);
         break;
      }
   }
};//end of AlgebraicExpression.cpp  
```

```


//Stack.h
template < typename T>
class Stack
{
friend class AlgebraicExpression;

public:

Stack();
Stack(const Stack&);
~Stack();

bool isEmpty () const;
void push(T newItem);
void pop ();
void pop(T& stackTop);
void getTop(T& stackTop);

private:
struct StackNode
{
   T item;   
   StackNode *next;
};

StackNode *topPtr;
int size;
};//end of Stack.h


```

```

//Stack.cpp
#include <cstddef>

#include "Stack.h"

template < typename T>
Stack<T>::Stack() : topPtr(NULL)
{
}
template < typename T>
Stack<T>::Stack(const Stack& aStack)
{
   if (aStack.topPtr == NULL)
      topPtr = NULL;  // original list is empty

   else
   {  // copy first node
   
      topPtr = new StackNode;
      topPtr->item = aStack.topPtr->item;

      // copy rest of list
      StackNode *newPtr = topPtr;    // new list pointer

      for (StackNode *origPtr = aStack.topPtr->next;origPtr != NULL; origPtr = origPtr->next)
      {  newPtr->next = new StackNode;
         newPtr = newPtr->next;
         newPtr->item = origPtr->item;
      }  // end for
      newPtr->next = NULL;
   }  // end if
}  // end copy constructor

template <class T>
Stack<T>::~Stack()
{
   // pop until stack is empty
   while (!isEmpty())
      pop();
   // Assertion: topPtr == NUL
}  // end destructor

template <class T>
bool Stack<T>::isEmpty() const
{
   return topPtr == NULL;
}  // end isEmpty

template < typename T>
void Stack<T>::push(T newItem)
{
   // create a new node
   StackNode *newPtr = new StackNode;

   // set data portion  of new node
   newPtr->item = newItem;
   // insert the new node
   newPtr->next = topPtr;
   topPtr = newPtr;
}  // end push

template <class T>
void Stack<T>::pop() //throw(StackException)
{
   if (isEmpty());
      //throw StackException("StackException: stack empty on pop");

   else
   {  // stack is not empty; delete top
      StackNode *temp = topPtr;
      topPtr = topPtr->next;
      // return deleted node to system
      temp->next = NULL;  // safeguard
      delete temp;
   }  // end if
}  // end pop

template < typename T>
void Stack< T >::pop(T& stackTop) // throw(StackException)
{
   if (isEmpty());
//      throw StackException("StackException: stack empty on pop");

   else
   {  // stack is not empty; retrieve and delete top
      stackTop = topPtr->item;
      StackNode *temp = topPtr;
      topPtr = topPtr->next;

      // return deleted node to system
      temp->next = NULL;  // safeguard
      delete temp;
   }  // end if
}  // end pop

template < typename T>
void Stack<T>::getTop(T& stackTop) //const //throw(StackException)
{
   if (isEmpty());
//      throw StackException("StackException: stack empty on getTop");

   else
      // stack is not empty; retrieve top
      stackTop = topPtr->item;
}  // end getTop
// End of implementation file. end of Stack.cpp

```

```

//driver.cpp
#include <iostream>
using std::cin;
using std::cout;
using std::endl;

#include <exception>
using std::exception;

#include <string>
using std::string;
using std::strncat;

#include <cstddef>

#include "AlgebraicExpression.h"

int main(){
   cout<<infix2postfix("3+4+5");
   return 0;
};//end of driver.cpp

```

Error:
```

AlgebraicExpression.cpp: In function 'std::string infix2postfix(std::string)':
AlgebraicExpression.cpp:12: error: 'T' was not declared in this scope
AlgebraicExpression.cpp:12: error: expected `;' before 'tempc'
AlgebraicExpression.cpp:13: error: expected `;' before 'tempi'
Stack.h:25: hata: 'Stack<int>::StackNode* Stack<int>::topPtr' is private
AlgebraicExpression.cpp:25: error: bu baglamda
Stack.h:25: hata: 'Stack<int>::StackNode* Stack<int>::topPtr'is private
AlgebraicExpression.cpp:25: error: bu baglamda
Stack.h:25: hata: 'Stack<int>::StackNode* Stack<int>::topPtr' is private
AlgebraicExpression.cpp:26: error: bu baglamda
AlgebraicExpression.cpp:27: error: 'tempc' was not declared in this scope
Stack.h:25: hata: 'Stack<int>::StackNode* Stack<int>::topPtr' is private
AlgebraicExpression.cpp:36: error: bu baglamda
Stack.h:25: hata: 'Stack<int>::StackNode* Stack<int>::topPtr' is private
AlgebraicExpression.cpp:37: error: bu baglamda

```

---

### Post by po0f on 2006-12-18
ankakusu,

IIRC, template definitions have to reside in the header file they are declared in, not a separate source file.  Something about the compiler has to know at compile time what a template looks like, not link time.

And when declaring variables for use with templates, don't declare them as "T".  The whole point of templates is to write one "template" function that works on different types.  The "typename T" is just a placeholder for any type, an int, a float, whatever.

---

### Post by ankakusu on 2006-12-18
But I've already declared in the header file (Stack.h)  but I must also make declarations in Stack.cpp you say that I should not declare it in the .cpp file? do you mean that?

can you explain the reasoning that I can not declare the template variable as T?

---

