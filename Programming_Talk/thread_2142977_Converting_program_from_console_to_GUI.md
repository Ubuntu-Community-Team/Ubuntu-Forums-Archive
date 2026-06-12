---
title: "Converting program from console to GUI"
date: 2013-05-07
forum: Programming Talk
---

### Post by Bresser on 2013-05-07
Ok I have this console program that what it does is converts a string into gibberish. I want to convert it from what it is right now to Qt(I have both just Qt and then also Netbeans with Qt). So what it is, is Two boxes, two radios, and a button. The first box is where you type the message in. The two radios are English and Fake. Then the button is a button that submits it to translate.

If there is a way to do it without having to press the Translate button that would be even better.
This is my code, I would like help converting it to use the features (button, radios, boxes)
```

#include <iostream>
#include <string>

using namespace std;

int main()
{
string str;

// The part below won't be necessary when it's on Qt. 
cout << "Enter A String. instead of spaces use a capital format such as: HelloWorld.\nIf you want to translate gibberish to english, type in the gibberish." << endl; 
// The problem with the below line is it stops at a space so you have to type it all as one word
cin >> str;
int x;
// This is because in my IF statement I had to have a condition. But in the Qt program. I want the If statement to be if engLang (the english radio) is selected then run the first part else run the second.
cout << "If you entered gibberish, type 1 to translate it back to english. \nIf you entered English press 0 to translate it to gibberish" << endl;
cin >> x; 
if (x==0) {
int index=0;
while(str[index])
{
str[index]=(str[index]+1)%256;
index++;
}
std::cout << str; 
}
// This part of the If statement would be if you pressed fakeLang(The fake language radio button) 
else {
int index = 0;
while(str[index++]) {}
for(int i=0;i<index;i++)
{
str[i]-=1
if(str[i]==-1)
{
str[i]=255;
}
}
std::cout << '\n' << str;
}
}

```

---

### Post by Chase993 on 2013-05-08
If you wish to build GUI applications on Ubuntu there are a few choices for you to choose from, and since you are using C++ I would suggest you use the QT Creator IDE. You can find it in the software center.

---

