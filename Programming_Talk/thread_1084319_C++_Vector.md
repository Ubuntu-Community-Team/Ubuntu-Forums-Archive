---
title: "C++ Vector"
date: 2009-03-01
forum: Programming Talk
---

### Post by detorresrc on 2009-03-01
Hi anyone help me, my problem is i want to assign name to a variabe using vector and accept 20 char only, Here's my code . Tnx

#include<iostream>
#include<vector>

using namespace std;

int main(){
        const int max = 10;
        vector<float> weight(max);
        vector<char> name(max);
        int a=0;
        for(a=0; a<max; a++){
                cout << "Please enter your name[" << a <<  "]: " << endl;
                cin >> name.at(a);
                cout << "Please enter your age[" << a <<  "]: " << endl;
                cin >> weight.at(a);
        }
        return(0);
}

---

### Post by Queue29 on 2009-03-01
I'm confused.. how many names and weights are you trying to store? If it's just one, why do you have the cout prompts in the loop, and a vector to store the weight?

---

### Post by babyhuey on 2009-03-01
Wouldn't "vector<char>(max)" just create single character "arrays"?


My suggestion would be to make vectors of type string
[PHP]
#include<iostream>
#include<vector>
#include<string>

using namespace std;

int main(){
    const int max = 10;
    vector<float> weight(max);
    vector<string> name(max);
    int a=0;
    for(a=0; a<max; a++){
        cout << "Please enter your name[" << a << "]: " << endl;
        cin >> name.at(a);
        cout << "Please enter your age[" << a << "]: " << endl;
        cin >> weight.at(a);
    }
    return(0);
} 
[/PHP]
FYI, you can also index a vector with the [] operator just as you would an array.

---

### Post by rharriso on 2009-03-01
May you should try reading in the input as a String and then loop through that taking the first 20 char.

---

### Post by detorresrc on 2009-03-01
10 names and weights.

---

### Post by monkeyking on 2009-03-02
> **detorresrc said:**
> Hi anyone help me, my problem is i want to assign name to a variabe using vector and accept 20 char only, Here's my code . Tnx

#include<iostream>
#include<vector>

using namespace std;

int main(){
        const int max = 10;
        vector<float> weight(max);
        vector<char> name(max);
        int a=0;
        for(a=0; a<max; a++){
                cout << "Please enter your name[" << a <<  "]: " << endl;
                cin >> name.at(a);
                cout << "Please enter your age[" << a <<  "]: " << endl;
                cin >> weight.at(a);
        }
        return(0);
}
Is it not working and which errors do you get.?

---

### Post by babyhuey on 2009-03-02
> **monkeyking said:**
> Is it not working and which errors do you get.?

As his code is now it would put cin into a fail state if he entered more than one char at a time. Since the vector can only store 1 char at a given index the remaining characters would go to the weight variable which would cause the fail state.

If you wanted to stick with C style strings you might be able to use "vector<char*>(max)" but I haven't tried that personally.
Unless you have to stick with C style strings school or something of the like, I would definitely suggest the string class such as my example a couple posts up.

---

