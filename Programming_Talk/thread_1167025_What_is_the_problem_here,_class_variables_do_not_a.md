---
title: "What is the problem here, class variables do not appear"
date: 2009-05-22
forum: Programming Talk
---

### Post by colau on 2009-05-22
In vi editor the c++ auto complete is working.
But the custom class variables do no appear after the dot (.).
```

#include<stdio.h>
#include<vector>
#include<stack>
#include<iostream>
using namespace std;

class ownclass{
public:
        ownclass(){}
        int i;
        int j;
};

int main(){
        stack<int>st;
        vector<int>vv;
        st.push(45);
        ownclass obj;
        obj.
        std::cout<<"Hello world"<<endl;
        return 0;
}

-- Omni completion (^O^N^P) Pattern not found

```

---

### Post by monkeyking on 2009-05-22
I've never used it autocompletion.
But you might need to run ctags.
Not sure though

---

