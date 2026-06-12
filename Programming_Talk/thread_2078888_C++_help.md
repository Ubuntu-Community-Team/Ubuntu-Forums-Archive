---
title: "C++ help"
date: 2012-10-31
forum: Programming Talk
---

### Post by Jsegovia on 2012-10-31
im new to c++ and taking a course at a junior college. having trouble understanding nested loops anyways ill post my source code
 

#include<iostream>
#include<iomanip>
using namespace std;
int main ()
{
    int coin=0, creturn=0, slot=0;
    
    do
    {
        cout << "\t\t\tICE COLD COLA \n";
        cout <<        "\t\t\t\t.75 cents\n\n";
        cout << "Deposit -- dollar, quarters, dimes, or nickels:\n";
        cout << "\t     (1\t ,   .25   ,  .10   ,  .05)\n\n";
       
        do
        {
             cout << "[" << coin << "]";
             cin >> coin;
             
             if(coin == 1 || coin == .25 || coin == .10 || coin == .05)
                     slot += coin;
             else
                     creturn += coin;
            
         }while(slot < .75 || slot != -1);
         
         
         
         
         
                 
         
         
    }while(slot != -1);
}  
 
anyways .75 cents for a cola and -1 to turn off the machine. any help would be appreciated
 thanks

---

### Post by spillin_dylan on 2012-10-31
Three comments:

1) Looks like C++ to me. 
2) Is there a question in there somewhere? 
3) We aren't supposed to be helping you for school work on the forums, because you won't really learn C++ then!

Good luck!:KS

---

### Post by SuperCamel on 2012-11-01
What is it that you don't understand?

---

### Post by spjackson on 2012-11-01
> 
int coin=0, creturn=0, slot=0;

What sort of values are you dealing with? Are they really of type int?
> 
while(slot < .75 || slot != -1)

Are there any possible values of slot for which this expression is false? If not, the loop will never terminate.

---

