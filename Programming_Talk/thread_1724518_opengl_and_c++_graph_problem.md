---
title: "opengl and c++ graph problem"
date: 2011-04-08
forum: Programming Talk
---

### Post by ackuang on 2011-04-08
1)Why the looping in sinegraph function cannot loop for many times?
2)Why it cannot stop when i click the letter other than Y or y?
3)How to let the user to key in x3 before the glutcreatewindow to execute?
4)Anything else need to improve in this coding?
 
Hopefully someone can help me solve it. Thanks^^
Below is the coding.
 
#include <iostream>
#include <cmath>
#include <gl\glut.h>
using namespace std;

#define SIZE 700
#define PI 3.14159265

void menu();
void sinegraph();
void cosinegraph();
void tangentgraph();
void drawline(float x1, float y1, float x2, float y2);
void selection();

int main(int argc, char ** argv)
{ 
        glutInit(argc, argv);
        glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_DEPTH);
        glutInitWindowSize(700,500);
        glutInitWindowPosition(650,100);
        
        menu();
        selection();

        glutMainLoop();

        return 0;
}
void menu()
{
        cout<<"******** Welcome to Trigonometric World ********"<<endl<<endl;
        cout<<"1. Sine Graph"<<endl;
        cout<<"2. Cosine Graph"<<endl;
        cout<<"3. Tangent Graph"<<endl;
        cout<<"4. Quit"<<endl<<endl;
        cout<<"************************************************"<<endl<<endl;

}
void sinegraph()
{ 
        float x1, x2, x3, y1, y2;
        char again;

        do
        {
        cout<<"Enter period(number of cycles) you want : ";
        cin>>x3;
        for (int i=-700;i<SIZE;i++)
        { 
                x1=((float)i/SIZE);
                x2=(((float)(i+1))/SIZE);
                y1=sin(x1*x3*PI);
                y2=sin(x2*x3*PI);
                drawline(x1,y1,x2,y2);
        }
        glutSwapBuffers();
        cout<<"Do you want to continue to draw? (Y/N) ";
        cin>>again;
        }while(again=='Y' & again=='y');
        
}
void cosinegraph()
{ 
        float x1, x2, y1, y2;
        for (int i=-700;i<SIZE;i++)
        { 
                x1=((float)i/SIZE);
                x2=(((float)(i+1))/SIZE);
                y1=cos(x1*2*PI);
                y2=cos(x2*2*PI);
                drawline(x1,y1,x2,y2);
        }
        glutSwapBuffers();
}
void tangentgraph()
{ 
        float x1, x2, y1, y2;
        for (int i=-700;i<SIZE;i++)
        { 
                x1=((float)i/SIZE);
                x2=(((float)(i+1))/SIZE);
                y1=tan(x1*2*PI);
                y2=tan(x2*2*PI);
                drawline(x1,y1,x2,y2);
        }
        glutSwapBuffers();
}
void drawline(float x1, float y1, float x2, float y2)
{ 
        //x-axis
        glBegin(GL_LINES);
        glColor3f(1.0, 0, 0);
        glVertex2f(-10.0f, 0.0f);
        glVertex2f(10.0f, 0.0f);
        glEnd();

        //y-axis
        glBegin(GL_LINES);
        glColor3f(1.0, 0, 0);
        glVertex2f(0.0f, -10.0f);
        glVertex2f(0.0f, 10.0f);
        glEnd();

        //curve
        glBegin(GL_LINE_STRIP);
        glColor3f(1.0,1.0,1.0);
        glVertex2f(x1,y1);
        glVertex2f(x2,y2);
        glEnd();
}
void selection()
{
        int choice;
        
        cout<<"Enter the type of graph you want(1,2,3 or 4) : ";
        cin>>choice;
        switch(choice)
        {
        case 1: glutCreateWindow(" Sine Graph ");
                        glutDisplayFunc(sinegraph);
                        break;
        case 2:        glutCreateWindow(" Cosine Graph ");
                        glutDisplayFunc(cosinegraph);
                        break;
        case 3:        glutCreateWindow(" Tangent Graph ");
                        glutDisplayFunc(tangentgraph);
                        break;
        default:exit(0);
        }
}

---

### Post by Arndt on 2011-04-08
> **ackuang said:**
> 1)Why the looping in sinegraph function cannot loop for many times?
2)Why it cannot stop when i click the letter other than Y or y?
3)How to let the user to key in x3 before the glutcreatewindow to execute?
4)Anything else need to improve in this coding?
 
Hopefully someone can help me solve it. Thanks^^
Below is the coding.
 
#include <iostream>
#include <cmath>
#include <gl\glut.h>
using namespace std;

#define SIZE 700
#define PI 3.14159265

void menu();
void sinegraph();
void cosinegraph();
void tangentgraph();
void drawline(float x1, float y1, float x2, float y2);
void selection();

int main(int argc, char ** argv)
{ 
        glutInit(argc, argv);
        glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_DEPTH);
        glutInitWindowSize(700,500);
        glutInitWindowPosition(650,100);
        
        menu();
        selection();

        glutMainLoop();

        return 0;
}
void menu()
{
        cout<<"******** Welcome to Trigonometric World ********"<<endl<<endl;
        cout<<"1. Sine Graph"<<endl;
        cout<<"2. Cosine Graph"<<endl;
        cout<<"3. Tangent Graph"<<endl;
        cout<<"4. Quit"<<endl<<endl;
        cout<<"************************************************"<<endl<<endl;

}
void sinegraph()
{ 
        float x1, x2, x3, y1, y2;
        char again;

        do
        {
        cout<<"Enter period(number of cycles) you want : ";
        cin>>x3;
        for (int i=-700;i<SIZE;i++)
        { 
                x1=((float)i/SIZE);
                x2=(((float)(i+1))/SIZE);
                y1=sin(x1*x3*PI);
                y2=sin(x2*x3*PI);
                drawline(x1,y1,x2,y2);
        }
        glutSwapBuffers();
        cout<<"Do you want to continue to draw? (Y/N) ";
        cin>>again;
        }while(again=='Y' & again=='y');
        
}
void cosinegraph()
{ 
        float x1, x2, y1, y2;
        for (int i=-700;i<SIZE;i++)
        { 
                x1=((float)i/SIZE);
                x2=(((float)(i+1))/SIZE);
                y1=cos(x1*2*PI);
                y2=cos(x2*2*PI);
                drawline(x1,y1,x2,y2);
        }
        glutSwapBuffers();
}
void tangentgraph()
{ 
        float x1, x2, y1, y2;
        for (int i=-700;i<SIZE;i++)
        { 
                x1=((float)i/SIZE);
                x2=(((float)(i+1))/SIZE);
                y1=tan(x1*2*PI);
                y2=tan(x2*2*PI);
                drawline(x1,y1,x2,y2);
        }
        glutSwapBuffers();
}
void drawline(float x1, float y1, float x2, float y2)
{ 
        //x-axis
        glBegin(GL_LINES);
        glColor3f(1.0, 0, 0);
        glVertex2f(-10.0f, 0.0f);
        glVertex2f(10.0f, 0.0f);
        glEnd();

        //y-axis
        glBegin(GL_LINES);
        glColor3f(1.0, 0, 0);
        glVertex2f(0.0f, -10.0f);
        glVertex2f(0.0f, 10.0f);
        glEnd();

        //curve
        glBegin(GL_LINE_STRIP);
        glColor3f(1.0,1.0,1.0);
        glVertex2f(x1,y1);
        glVertex2f(x2,y2);
        glEnd();
}
void selection()
{
        int choice;
        
        cout<<"Enter the type of graph you want(1,2,3 or 4) : ";
        cin>>choice;
        switch(choice)
        {
        case 1: glutCreateWindow(" Sine Graph ");
                        glutDisplayFunc(sinegraph);
                        break;
        case 2:        glutCreateWindow(" Cosine Graph ");
                        glutDisplayFunc(cosinegraph);
                        break;
        case 3:        glutCreateWindow(" Tangent Graph ");
                        glutDisplayFunc(tangentgraph);
                        break;
        default:exit(0);
        }
}

It's best to use CODE tags, to keep the indentation of the code in the post. You can use the # symbol in the editing tool bar for that.

You use this test: again=='Y' & again=='y'

It has two problems. To start with, do you think it can ever be true? 'again' would have to have two different values at the same time.

The other problem is that & is not the operator you want; it's &&. The & operator may seem to work in the same way, but it is used for bit-wise AND of integers. It will not make the code behave differently here, but it may in your next program.

---

### Post by ackuang on 2011-04-08
actually I put put & twice already.Copy to here then become one only.
For your suggestion,how the coding should be like?

---

### Post by visitron on 2011-04-08
There are a few problems with your code.

I tried to fix  obvious ones and posted the revised code below.

It seems you were trying to use & as a logical operator when you meant to use ||

|| means 'or'


The proper way to call glutinit;

glutInit(&argc, argv);



Also the way you structured the code it asks you what type of function you want and then the window pops up without first asking for the period.

My version fixed those problems  but there are others.

Notice that when you enter 'y' for yes you wish to continue it seems as if nothing happens, that's because it's just doing the same thing again so it seems as nothing changes.

if you say 'n' to mean wanting to quit the program you just get blank lines but the window doesn't close.

You are trying to use GLUT in a way it's not meant to be used.

The trouble  is that glutMainLoop() is a function that never returns, in other words it's meant to be used in an event driven program.

You should be using the GLUT keyboard and input functions, not your own.

What I would recommend is not using GLUT at all, it really will limit what you can do, it's more trouble than it's worth.

```

#include <iostream>
#include <cmath> 
#include <GL/glut.h>


using namespace std;


#define SIZE 700
#define PI 3.14159265

void menu();
void sinegraph();
void cosinegraph();
void tangentgraph();
void drawline(float x1, float y1, float x2, float y2);
void selection();


float x3;

int main(int argc, char ** argv)
{
glutInit(&argc, argv);
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_DEPTH);
glutInitWindowSize(700,500);
glutInitWindowPosition(650,100);

menu();
selection();

glutMainLoop();

return 0;
}
void menu()
{
cout<<"******** Welcome to Trigonometric World ********"<<endl<<endl;
cout<<"1. Sine Graph"<<endl;
cout<<"2. Cosine Graph"<<endl;
cout<<"3. Tangent Graph"<<endl;
cout<<"4. Quit"<<endl<<endl;
cout<<"******************************************* *****"<<endl<<endl;

}
void sinegraph()
{
float x1, x2, y1, y2;
char again;

do
{



for (int i=-700;i<SIZE;i++)
{
x1=((float)i/SIZE);
x2=(((float)(i+1))/SIZE);
y1=sin(x1*x3*PI);
y2=sin(x2*x3*PI);
drawline(x1,y1,x2,y2);
}



glutSwapBuffers();
cout<<"Do you want to continue to draw? (Y/N) ";
cin>>again;
}while(   (again=='Y') ||  (again=='y')   );

}
void cosinegraph()
{
float x1, x2, y1, y2;
for (int i=-700;i<SIZE;i++)
{
x1=((float)i/SIZE);
x2=(((float)(i+1))/SIZE);
y1=cos(x1*2*PI);
y2=cos(x2*2*PI);
drawline(x1,y1,x2,y2);
}
glutSwapBuffers();
}
void tangentgraph()
{
float x1, x2, y1, y2;
for (int i=-700;i<SIZE;i++)
{
x1=((float)i/SIZE);
x2=(((float)(i+1))/SIZE);
y1=tan(x1*2*PI);
y2=tan(x2*2*PI);
drawline(x1,y1,x2,y2);
}
glutSwapBuffers();
}
void drawline(float x1, float y1, float x2, float y2)
{
//x-axis
glBegin(GL_LINES);
glColor3f(1.0, 0, 0);
glVertex2f(-10.0f, 0.0f);
glVertex2f(10.0f, 0.0f);
glEnd();

//y-axis
glBegin(GL_LINES);
glColor3f(1.0, 0, 0);
glVertex2f(0.0f, -10.0f);
glVertex2f(0.0f, 10.0f);
glEnd();

//curve
glBegin(GL_LINE_STRIP);
glColor3f(1.0,1.0,1.0);
glVertex2f(x1,y1);
glVertex2f(x2,y2);
glEnd();

//glutSwapBuffers();

}
void selection()
{
int choice;

cout<<"Enter the type of graph you want(1,2,3 or 4) : ";
cin>>choice;
switch(choice)
{
case 1: 
cout<<"Enter period(number of cycles) you want : ";
cin>>x3;


glutCreateWindow(" Sine Graph ");
glutDisplayFunc(sinegraph);
break;
case 2: glutCreateWindow(" Cosine Graph ");
glutDisplayFunc(cosinegraph);
break;
case 3: glutCreateWindow(" Tangent Graph ");
glutDisplayFunc(tangentgraph);
break;
//default:exit(0);
}
}




```

---

### Post by ackuang on 2011-04-09
Thanks for your help.
Unfortunately,I really need to use GLUT instead of others.
Anyway,thanks again,I try to figure out the solutions^^

---

