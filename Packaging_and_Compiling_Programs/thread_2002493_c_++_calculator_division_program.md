---
title: "c ++ calculator division program"
date: 2012-06-12
forum: Packaging and Compiling Programs
---

### Post by zayid on 2012-06-12
Hello guys, pls im supposed to create a c++ program to calculate two input numbers. I'm also expected to add error handling but it keeps giving me errors. i have commented on it so you can have an idea what i'm trying to do. If i run the program straight it works, but if i'm to use an alphabet for either numerator or denominator it fails. thanks
```
//division calculator with error handling
#include <iostream> 
 
using namespace std; 
int main(int argc, char* argv[]) 
{ 
      int returnvalue; 
      float numerator = 0; 
      float denominator = 0; 
      float divresult = 0; 
       
       
      cout <<"Please enter the numerator:"; //the numerator is put in
      cin >>numerator;  
      if(cin.fail()) //if the value put in is not a number (0-9), it fails 
       
       { 
                   cerr<<"Invalid Input\nNumbers required!"<<endl;//information regarding the error and advising for input change 
                   cin.clear(); 
                   char discardit[3]; 
                   cin>>discardit; 
                   char exitchar; 
                   cout <<"please enter the numerator:"; 
                cin >>numerator; 
                              
        } 
                         
      else// but if the numerator is correct (0-9), it moves here 
      { 
               cout<<"Please enter the denominator:"; 
               cin>>denominator; 
            }
           if(cin.fail()) //if the denominator is not a number(0-9), it fails        
                         { 
                          cerr<<"Invalid Input\nNumbers required!"<<endl;//information regarding the error and advising for input change 
                          cin.clear(); 
                        char discardit[3]; 
                          cin>>discardit; 
                        char exitchar; 
                          cout<<"Please enter the denominator:"; 
                       cin>>denominator;

                          } 
                     else// but if the denominator is correct then... 
 
                if(denominator==0)//...it tests to make sure the input is not zero 
                    { 
                    cout<<"Cannot divide by zero"<<endl; 
                              cout<<"please enter the denominator:"; 
                           cin>>denominator; 
                         } 
                       else // but if it isn't zero, it moves here and does the division 
                    divresult = (numerator/denominator); 
                            cout<<divresult<<endl; 
                           return returnvalue;// returns the result.                
                         
}//end of program 

```

---

### Post by MadCow108 on 2012-06-12
your if else logic is wrong
if you put in a non digit it never sets the denominator, so its always zero
you are better off putting the input parsing in a function which loops until it gets the correct input (or an abort)
it makes your code more readable and avoids bugs.

also clearing a errornous stream should be done like this:
```
cin.clear()
cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n')
```

your variant will try to read a pointer type value, so again a digit.
also string won't work as cin white space separated by default.

---

### Post by zayid on 2012-06-13
pls you should first understand that i started learning programming about 2 months ago so i'm very much a newbie lol, also, i do get what you're saying - sort of but it is insisted i follow this format. i have refined it a bit but i'm having problem if i use an alphabet as numerator, then it'll be blank but the compiler is waiting for the denominator, how do i get that info to show? also if at the first instance i use an alphabet in the denominator, even if it does the division, the answer will be zero(that means it has reset my numerator to 0) thanks
```
//division calculator with error handling 
#include <iostream> 
 
using namespace std; 
int main(int argc, char* argv[]) 
{ 
      int returnvalue; 
      float numerator = 0; 
      float denominator = 0; 
      float divresult = 0; 
       
       
      cout <<"Please enter the numerator:"; //the numerator is put in 
      cin >>numerator;  
      if(cin.fail()) //if the value put in is not a number (0-9), it fails 
       
       { 
                   cerr<<"Invalid Input\nUse only Numbers"<<endl;//information regarding the error and advising for input change 
                   cin.clear(); 
                   char discardit[3]; 
                   cin>>discardit; 
                   char exitchar; 
                   cout <<"Please enter the numerator:"; 
                cin >>numerator;                           
        } 
                         
      else// but if the numerator is correct (0-9), it moves here 
       
               cout<<"Please enter the denominator:"; 
               cin>>denominator; 
             
           if(cin.fail()) //if the denominator is not a number(0-9), it fails        
                         { 
                          cerr<<"Invalid Input\nUse only Numbers"<<endl;//information regarding the error and advising for input change 
                          cin.clear(); 
                        char discardit[3]; 
                          cin>>discardit; 
                        char exitchar; 
                          cout<<"Please enter the denominator:"; 
                       cin>>denominator; 
                 
                          } 
                     // but if the denominator is correct then... 
                 
                else if(denominator==0)//...it tests to make sure the input is not zero 
                    { 
                    cout<<"Cannot divide by zero"<<endl; 
                              cout<<"please enter the denominator:"; 
                           cin>>denominator; 
                         } 
                       else // but if it isn't zero, it moves here and does the division 
                    divresult = (numerator/denominator); 
                            cout<<divresult<<endl;
                                
            returnvalue = 0; 
                           return returnvalue;// returns the result.                
                         
}//end of program 

```

---

