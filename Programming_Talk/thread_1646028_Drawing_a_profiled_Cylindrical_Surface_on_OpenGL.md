---
title: "Drawing a profiled Cylindrical Surface on OpenGL"
date: 2010-12-15
forum: Programming Talk
---

### Post by kaneomaniac on 2010-12-15
Hi all,

I am new to OpenGL and I would like to ask for all your kind assistance. I need to do this program for my school project.

Currently, I am stuck at the following problem:

I want to do a profiled cylindrical surface. In other words, I want to draw a cylindrical surface with an equation. Let's say y = x * x. So on a side view, the cylindrical surface would have a curve of y = x*x, on the front view, it will be a cylinder. 

Therefore, I came up with this part of the equation:

    while ( z < (a+b) )
    {
            y = 0.5*d; //This draws a cylinder for now
            glTranslatef(0,0,z);
            gluDisk(qobj, 0, y, 50, 50);
            z += 0.0001;
            
    }
    
    glPopMatrix();

Upon execution, nothing comes up on my runtime screen. Can anyone teach me why? Or do you have an easier way to do it? The constraints are that the y equation has to be dynamic and I can change it to anything I want in future. 

Pls help me out on this. Thank you in advance! :D

---

### Post by PaulM1985 on 2010-12-15
Interesting problem.  I am not great at opengl so I apologise if I go off track.  I am not sure that drawing lots of discs is what you need to be doing.  

Here is the sort of thing I would do.  Imagine an interpolated graph, so you only are interested with specific points on the graph, ie y = 1, 2, 3, 4, 5 etc.  Modeling this in 2d, you could draw a line from 1 to 2, 2 to 3, 3 to 4 and so on.

But from your description, it sounds like this line should be along the centre of a cylinder.

You could for each point on the line, find the cylinder around it (an interpolated cylinder).  Then match points from the cylinder at point 1 to points on the cylinder at point 2.  As an example, you would could make a quad out of:
point 1 angle 0
point 2 angle 0
point 2 angle 1
point 1 angle 1 

So all these little quads would make your cylinder.

For the curve to look nicely rounded you may want to take into acount the derivative of the curve at each point where you are creating the cylinder.

As for your original problem, you will probably want to post the whole thing.  You may have got something wrong on the original setup which someone on this forum might have a chance of spotting.

Hope this helps you sort your problem.

Paul

---

### Post by kaneomaniac on 2010-12-18
Thanks for your reply! :) 

Anyway what I meant was the line is on the face of the cylinder. In the 2D sense, it outlines the cylinder. Let say I want to make a cone. That will mean my line is y=x, something along that context. 

It is interesting with your interpolated suggestion, but I would like a 3D model. Yup, a could make a 2D outline of the shape I want with gl(points) and looping it over the entire range of x-axis. But it is impossible in the 3D sense.

Wow, I wouldn't dare show my messy code here cos its bits and pieces of various codes I extracted and commented, but I shall post it here for experts that are able to understand the junk I've written. :p

Pls advice on the new defined problem above. Thank you very very much! :)

#include <iostream>
#include <cstdlib>
#include <cmath>
#include <GL/glut.h>

using namespace std;

#define DEG_TO_RAD 0.017453
#define TRUE 1
#define FALSE 0

struct POINT
{
       int x;
       int y;
};

struct CAMERA
{
       GLfloat xeye;
       GLfloat yeye;
       GLfloat zeye;
};

struct POLAR
{
       float r;
       float alpha;
       float fy;
};

struct POLAR polar={3.0f, 60.0f, 45.0f};
struct CAMERA camera;
struct POINT oldpt={-1, -1};
int l_button_down=FALSE;

//Initializations
float x = 0, y, z=-1;
float zoom = 1.0f;
GLUquadricObj *qobj = gluNewQuadric();
float xeye = 0, yeye=0, zeye=-10;

//AUV parameters specifications
float a = 0.191, aoffset = 0.0165, n = 2,
      b = 0.654, c = 0.541, coffset = 0.0368,
      theta = 0.436, d = 0.191;

//Loop variables
int i=0, j=0;

void keyboard(unsigned char key, int x, int y)
{
    switch (key) 
    {
        case 27: //Escape key
            exit(0);
            
        case 'z':
            zoom += 0.2;
            glutPostRedisplay();
            break;
            
        case 'x':
            zoom -= 0.2;
            glutPostRedisplay();
            break;
    }
}

void initRendering() {
    glEnable(GL_DEPTH_TEST);
    glEnable(GL_LIGHTING);
    glEnable(GL_LIGHT0);
    glEnable(GL_NORMALIZE);
    glEnable(GL_COLOR_MATERIAL);
    glShadeModel(GL_SMOOTH);
    glClearColor(1.0f, 1.0f, 1.0f, 0.0f);
}

void reshape(int w, int h) {
    glViewport(0, 0, w, h);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluPerspective(45.0, (float)w / (float)h, 1.0, 200.0);
}

void display() {
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();

    gluLookAt(camera.xeye, camera.yeye, camera.zeye, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0);
    glScalef(zoom, zoom, zoom); //Using Z and X (zoom in and out)
    //glTranslatef(0.0,0.0,-10.0f);
    //glRotatef(angle,1.0,0.0,0.0);

    //Axis
    glPushMatrix();
    
    glColor3f(1,0,0); //Red X Axis
    glBegin(GL_LINES);
    glVertex3f(0,0,0);
    glVertex3f(5,0,0);
    glEnd();

    glColor3f(0,1,0); //Green Y Axis
    glBegin(GL_LINES);
    glVertex3f(0,0,0);
    glVertex3f(0,5,0);
    glEnd();

    glColor3f(0,0,1); //Blue Z Axis
    glBegin(GL_LINES);
    glVertex3f(0,0,0);
    glVertex3f(0,0,5);
    glEnd();
    
    glPopMatrix();
    
    //Initialize Default Color
    glColor3f(0,0,0);
    
    /* -> Cylinder
    GLUquadricObj *qobj = gluNewQuadric();
    gluCylinder(qobj, 0.8, 0.8, 5, 50, 50);
    */
    /*
    //Tail Section
    
    while ( x < a )
    {
            //float y_;
            float xsquare = pow(((x-a)/a),2);
            y = 0.5*d*pow(1-(xsquare),(1/n));
            //glVertex3f(x, y, z);
            //y_ = -y;
            //glVertex3f(x, y_, z);
            x += 0.0001;

    }
*/
    //Middle Section
    glPushMatrix();
    
    //y = 0.5*d;
    while ( x < (a+b) )
    {
            float y_;
            y = 0.5*d;
            glVertex3f(x, y, z);
            y_ = -y;
            glVertex3f(x, y_, z);
            glTranslatef(0,0,x);
            gluDisk(qobj, 0, 0.5*d, 50, 50);
            x += 0.001;
            
    }
    
    glPopMatrix();
    //y = 0.5*d;
    //gluDisk(qobj, x, y, 50, 50);
    /*
    
    //Head Section
    while ( x < (a+b+c) )
    {
            //float y_;
            float var1 = (3*d) / (2*c*c);
            float tan1 = tan(theta)/c;
            float pow1 = pow(x-a-b,2);
            float var2 = d / (c*c*c);
            float tan2 = tan(theta)/(c*c);
            float pow2 = pow(x-a-b,3);
            y = (0.5*d) - ((var1 - tan1)*pow1) + ((var2 - tan2)*pow2);
            //glVertex3f(x, y, z);
            //y_ = -y;
            //glVertex3f(x, y_, z);
            x += 0.0001;
    }
*/
    glutSwapBuffers();
}

void SetCamera(GLfloat x, GLfloat y)
{
       GLfloat alpha,fy;
       if((polar.fy+y)>5.0f && (polar.fy+y)<175.0f)
       {
              polar.alpha += x;
              polar.fy += y;
              if(polar.alpha>360.0f) polar.alpha-=360.0f;
              if(polar.alpha<0.0f) polar.alpha+=360.0f;
              alpha=polar.alpha*DEG_TO_RAD;
              fy=polar.fy*DEG_TO_RAD;
              camera.xeye = polar.r * sin(fy) * cos(alpha);
              camera.zeye = polar.r * sin(fy) * sin(alpha);
              camera.yeye = polar.r * cos(fy);
              display();
       }
}

void mouse(int button, int state, int x, int y)
{
   if(button == GLUT_LEFT_BUTTON && state == GLUT_DOWN)
   {
          l_button_down = TRUE;
          oldpt.x=x;
          oldpt.y=y;
   }

   if(button == GLUT_LEFT_BUTTON && state == GLUT_UP)
   {
          l_button_down = FALSE;
   }
}

void mousemove(int x, int y)
{
       if(l_button_down)
       {
             SetCamera((float)(x-oldpt.x),(float)(oldpt.y-y));
              oldpt.x=x;
              oldpt.y=y;
       }
}

void idle()
{
    glutPostRedisplay();
}

int main(int argc, char** argv) {
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB| GLUT_DEPTH);
    
    glutInitWindowSize(1020, 700);
    //glutInitWindowPosition(0, 0);

    glutCreateWindow("FYP");
    initRendering();
    
    glutDisplayFunc(display);
    glutKeyboardFunc(keyboard);
    glutMouseFunc(mouse);
    glutMotionFunc(mousemove);
    glutReshapeFunc(reshape);
    glutIdleFunc(idle);

    glutMainLoop();
    return 0;
}
 Here's my junk code. :p

---

### Post by kaneomaniac on 2010-12-18
Ok i did some modifications and managed to draw out a cylinder. However, i'm wondering why is my spacings between cylinders not equal?

    glPushMatrix();
    glRotatef(90.0f, 0.0f, 1.0f, 0.0f);
    y = 0.5 * d;
    for ( x = 0 ; x < a+b ; x += 0.01 )
    {
    gluCylinder(qobj, y, y, 0.01, 50, 50);
    glTranslatef(0, 0, x+0.01);
    }
    glPopMatrix();

This is the part that drew out the cylinders.

Thanks for your help! :)

---

### Post by PaulM1985 on 2010-12-18
I think it is because you are translating by x + 0.01.  So your translations are:
1 - 0.01
2 - 0.02
3 - 0.03

I think the translate is incremental, not absolute, so actual positions will probably be:

1 - 0.01
2 - 0.03
3 - 0.06

So you probably want to remove the x+0.01 from the translate and just use 0.01.

Also, from my original idea, this is how quite a lot of stuff is done.  Computer games usually use a mesh (see here [http://en.wikipedia.org/wiki/Polygon_mesh](http://en.wikipedia.org/wiki/Polygon_mesh)) to create 3d objects, rather than use primitives in opengl.  I work on 3d CAD modelling software and we use opengl for the rendering.  Everything we pass to opengl is a mesh.

The wikipedia article shows triangle-based meshes but I was suggesting rectangle-based because it would be easier for you to program.

If your code solves your problem you will be ok, I was just letting you know in case you weren't aware of the use of a polygon mesh.

Paul

PS:  When posting code please put it in ```
 
``` tags because it makes the formatting easier to read.

---

### Post by kaneomaniac on 2010-12-20
Hi Paul!

I managed to figure it out with the following code!

    //Tail Section
    glPushMatrix();
    glColor3f(1,0,0);
    glRotatef(90.0f, 0.0f, 1.0f, 0.0f);

    for ( x = 0 ; x <= a ; x += 0.001)
    {
        float xsquare = pow(((x-a)/a),2);
        y = 0.5*d*pow(1-(xsquare),(1/n));
        gluCylinder(qobj, y, y, 0.01, 50, 50);
        glTranslatef(0, 0, 0.001);
    }

    glPopMatrix();
    
    //Middle Section
    glPushMatrix();
    glColor3f(0,1,0);
    glRotatef(90.0f, 0.0f, 1.0f, 0.0f);
    glTranslatef(0, 0, a);
    for ( x = a ; x <= (a+b) ; x += 0.001)
    {
        y = 0.5 * d;
        gluCylinder(qobj, y, y, 0.01, 50, 50);
        glTranslatef(0, 0, 0.001);
    }

    glPopMatrix();
    
    //Head Section
    glPushMatrix();
    glColor3f(0,0,1);
    glRotatef(90.0f, 0.0f, 1.0f, 0.0f);
    glTranslatef(0, 0, (a+b));
    for ( x = (a+b) ; x <= (a+b+c) ; x += 0.001)
    {
        float var1 = (3*d) / (2*c*c);
        float tan1 = tan(theta)/c;
        float pow1 = pow(x-a-b,2);
        float var2 = d / (c*c*c);
        float tan2 = tan(theta)/(c*c);
        float pow2 = pow(x-a-b,3);
        y = (0.5*d) - ((var1 - tan1)*pow1) + ((var2 - tan2)*pow2);
        gluCylinder(qobj, y, y, 0.01, 50, 50);
        glTranslatef(0, 0, 0.001);
    }

    glPopMatrix();

It basically did what you mentioned about the translation!

However, I have another problem. The rendering is VERY VERY VERY slow. I mean, it makes sense cos of the numerous loops. Therefore, I should try looking into the Polygon Mesh you mentioned. :)

But I am unsure if there is a way to model a smooth cylinder with meshes like these from your wiki. I suck at visualizations, so could you teach me how to maybe model just a cylinder? :) Via a code will be great!

Thanks Paul! :)
To others, pls help us out if you can! much help will be appreciated. thank you! :)

---

### Post by PaulM1985 on 2010-12-20
This is very clearly a school project and I am not going to do it for you.  That is why I have been giving descriptions and ideas with my posts.

If I understand your problem currently, you are looking to take an equation, as an example y = x, for x >= 0 and rotate this around the y axis, so that the line y = x is on the face to the rotated object.


I will explain how I would solve this problem using interpolation and assume that the equation is y = x.
I will use points x = {1, 2, 3, 4, 5}.

So we have {1, 1, 0}, {2, 2, 0}, {3, 3, 0}, {4, 4, 0}, {5, 5, 0}.

So we have an interpolated line in y and x.  We now want to obtain a series of rotated points around the y axis.

You may know the relationship between polar and cartesian co-ordinates.  On our y=x line we can say the angle is zero, so the x value is equal to the radius.  Based on this, you can work out z and x values to rotate round the y-axis.  (The smaller the angle, the more round it will look.  Try 60 degrees at first so you don't have may points and then maybe try more angles).

Now you should have a series of coordinates in x, y, z which act as lines going round the axis.  Iterate over these creating quads like:
```

corner1 = row1[i];
corner2 = row1[i+1];
corner3 = row2[i+1];
corner4 = row2[i];

```
Then you will have plotted a mesh.

If it is really slow you can have a look at display lists in opengl.  This stores the information you want to draw on your graphics card.  However, I would get something working first before looking at display lists.  I have never used them so I don't know how difficult they are to implement, I just know of them.

Paul

---

### Post by PaulM1985 on 2010-12-20
Following from my above post, if you have done what you need for your project (not using a mesh), I would save a copy of what you have and look at the display list stuff.  It probably doesn't matter if it is slow if it works.  The reason it is slow is because it keeps telling the graphics card things to draw, rather than loading to it once and then telling it to draw the thing it already knows.  If you add "NeHe" when you search google, you will probably find some good tutorials on opengl.

Paul

---

### Post by kaneomaniac on 2010-12-21
Hi Paul,

I think I am fine with the cylinders since my model is a missile shape look-a-like. :) However, It is very slow when rendering and I am supposed to come up with a graphics user interface using OpenGL to control this missile in runtime. Therefore, I need the speed as well. I looked up on displaylists and implemented it. However, I can't get the shape out anymore. Quite puzzling why. :( any takes on this? my code is as follows.

static void initialize(void)
{
    //Display List
    listName = glGenLists (1);
    glNewList (listName, GL_COMPILE_AND_EXECUTE);
           gluDisk(qobj, 0, y, 50, 50);
        gluCylinder(qobj, y, y, 0.001, 50, 50);
        glTranslatef(0, 0, 0.001);
    glEndList ();
    
    //Enabling OpenGL variables
    glEnable(GL_DEPTH_TEST);
    glEnable(GL_LIGHTING);
    glEnable(GL_LIGHT0);
    glEnable(GL_NORMALIZE);
    glEnable(GL_COLOR_MATERIAL);
    glShadeModel(GL_SMOOTH);
    glClearColor(1.0f, 1.0f, 1.0f, 0.0f);
    

}

//Inside display:
    //Tail Section
    glPushMatrix();
    glColor3f(1,0,0);
    glRotatef(90.0f, 0.0f, 1.0f, 0.0f);

    for ( x = 0 ; x <= a ; x += 0.001)
    {
        float xsquare = pow(((x-a)/a),2);
        y = 0.5*d*pow(1-(xsquare),(1/n)); //Equation of Tail Section
        glCallList (listName);
    }

    glPopMatrix();

Nothing comes out from this. :( Pls advice. Thank you!

Kane

---

### Post by PaulM1985 on 2010-12-21
Display lists take things that you have already drawn and re-draw them for you.

In your initialisation part, you have:
```

listName = glGenLists (1);
glNewList (listName, GL_COMPILE_AND_EXECUTE);
gluDisk(qobj, 0, y, 50, 50);
gluCylinder(qobj, y, y, 0.001, 50, 50);
glTranslatef(0, 0, 0.001);
glEndList ();

```

What is y here?

Take a good look at each line of your code and think about what it is doing.

Similarly:
```

float xsquare = pow(((x-a)/a),2);
y = 0.5*d*pow(1-(xsquare),(1/n)); //Equation of Tail Section
glCallList (listName);

```

What does y do here?  Anything?

Paul

---

