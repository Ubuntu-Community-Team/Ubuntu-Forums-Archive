---
title: "desperately need help in code in c++ and fitting functions in a frame"
date: 2010-05-01
forum: Programming Talk
---

### Post by crazzydevil on 2010-05-01
i am soryy my english is very bad but ill try my best to explain.i need help with my c++ assignemnt urgently.

i want to create a frame and fit in this histograph(ATTACHED PICTURE BELOW) which i made with the help of the container, where the x-axsis is the number from like eksempet 0-10 and the y-axis is telling me how many numbers there are from 0-10. But i cant seem to code it (given below). its in the number its gettin from a container where the container read it from a indata.txt file. the diagram created is just trying to make the x and y axis and put it in a frame. SO my question really is how to create and fit the function in the frame of my histogram(ATTACHED PICTURE BELOW) and how to code it. plzzz can someone help me!! :'(

ps: plz scroll down and check teh histograph picture i have attached






#include <iostream>
#include <algorithm>
#include <vector>
#include <string>
#include <fstream>
using namespace std;
void funk();
int getsum(vector<int> vec);
int getsize(vector<int> vec);
int getmax(vector<int> vec);
int getmin(vector<int> vec);
void getinterval(vector<int> vec);

void funk() {
vector<int> vec;
//int y;
ifstream in("Indata.txt");

int x, y, y2, y3, y4;
while (in>>x) {
vec.push_back(x);
}

y=vec.size();

y=getsum(vec);
y2=getsize(vec);
y3=getmax(vec);
y4=getmin(vec);
cout<<"\nsum = "<<y<<"\nsize = "<<y2<<"\nMax = "<<y3<<"\nmin = "<<y4;
getinterval(vec);
}

int getsum(vector<int> vec) {
int sum=0;
for (unsigned int i=0; i<vec.size(); i++) {

sum+=vec[i];
}

return sum;
}
int getsize(vector<int> vec) {

int sz;
sz=vec.size();

return sz;
}

int getmax(vector<int> vec) {
int max=0;

for (unsigned int i=0; i<vec.size(); i++) {
if (max<vec[i])
max=vec[i];
}

return max;
}

int getmin(vector<int> vec) {

int min=100000;

for (unsigned int i=0; i<vec.size(); i++) {
if (min>vec[i])
min=vec[i];
}

return min;
}

void getinterval(vector<int> vec) {
int count1=0, count2=0, count3=0, count4=0, count5=0, count6=0, count7=0,
count8=0, count9=0;

for (unsigned int i=0; i<vec.size(); i++) {

if (vec[i]>0 && vec[i]<=10) {
count1++;
} else if (vec[i]>10 && vec[i]<=20) {
count2++;
} else if (vec[i]>20 && vec[i]<=30) {
count3++;
} else if (vec[i]>30 && vec[i]<=40) {
count4++;
} else if (vec[i]>40 && vec[i]<=50) {
count5++;
} else if (vec[i]>60 && vec[i]<=70) {
count6++;
} else if (vec[i]>70 && vec[i]<=80) {
count7++;
} else if (vec[i]>80 && vec[i]<=90) {
count8++;
} else if (vec[i]>90 && vec[i]<=100) {
count9++;
}
}

int array[10]= { count1, count2, count3, count4, count5, count6, count7,
count8, count9 };
int max=0;
int y=10, t=10, t2=0,t3=10;
cout<<endl<<endl;
for (unsigned int i=0; i<9; i++) {
y-=1;

cout<<y<<endl;
if (max<array[i]) {
max=array[i];
}

}

cout<<endl<<endl;

for (unsigned int i=0; i<9; i++) {

for (; max>0; max--) {
unsigned int i;
for (i = 0; i < 9; i++)

if (array[i] >= max)
cout << "**** ";
else
cout << " ";
cout << endl;

}
}
cout<<endl;
for (unsigned int i=0; i<10; i++) {
cout<<t<<" ";
t+=10;
}
cout<<endl;

for (unsigned int i=0; i<10; i++) {

cout<<t2<<" ";
t2=t3+1;
t3+=10;
}

}

int main() {
vector<int> vec;
funk();

return 0;
}

---

### Post by dwhitney67 on 2010-05-01
Sorry, all I can say is good luck with your homework assignment.


Oh... and next time, please have the courtesy of posting your code within CODE tags.  It makes it easier to read.

---

