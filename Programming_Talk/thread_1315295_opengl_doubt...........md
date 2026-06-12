---
title: "opengl doubt.........."
date: 2009-11-05
forum: Programming Talk
---

### Post by abhilashm86 on 2009-11-05
i've a simulated robot arm which does 5 operations, moves up,down, rotate, others...........
this i did using glutKeyboardFunc(), so user needs to press keys, which i need to change it automatically........

like without any user input/ event, robot arm should itself simulate, like rotate first, up, down, like that, 
what are my best options??
1) should i use glutTimerFunc(), an will it work
2) use for loop, delay??
3) use a external file input and make this............

---

### Post by abhilashm86 on 2009-11-05
code for above simulated robot is shown here, now though user key input like S,s,E,e,F,f.........
suggest how to implement with automatically without user input.........
like 4 seconds it should rotate then up and goes on............
```
#include<GL/glut.h>

#include<stdlib.h>

#include<math.h>

const float DEG2RAD = 3.14159/180;

static int shoulder = 0, elbow = 0,gripper=0,shldf=0;

//GLfloat position[]={0.0,0.0,5.0,1.0};

void init() 

{

   glClearColor (1.0, 1.0, 1.0, 0.0);

   glShadeModel (GL_SMOOTH);

   //glEnable(GL_LIGHTING);	

   //glEnable(GL_LIGHT0);

   //glLightfv(GL_LIGHT0,GL_POSITION,position);

   glEnable(GL_DEPTH_TEST);

}





void keyboard (unsigned char key, int x, int y)

{

   switch (key) 

   {

      case 's':

         shoulder = (shoulder + 2) % 360;		//Shoulder Motion

         glutPostRedisplay();

         break;

      case 'S':

         shoulder = (shoulder - 2) % 360;		//Shoulder Motion

         glutPostRedisplay();

         break;

      case 'e':

         elbow = (elbow + 2) % 90;				//Elbow Motion

         glutPostRedisplay();

         break;

      case 'E':

         elbow = (elbow - 2) % 90;				//Elbow Motion

         glutPostRedisplay();

         break;

	  case 'g':

		  gripper=(gripper+2)%360;				//Gripper Motion

		  glutPostRedisplay();

		  break;

	  case 'G':

		  gripper=(gripper-2)%360;				//Gripper Motion

		  glutPostRedisplay();

		  break;

	  case 'f':

		  shldf=(shldf+2)%45;					//Shoulder to-fro motion

		  glutPostRedisplay();

		  break;

	  case 'F':

		  shldf=(shldf-2)%75;					//Shoulder to-fro Motion

		  glutPostRedisplay();

		  break;

	  case 27:

         exit(0);

         break;

      default:

         break;

   }

}





void base_arm()

{

   glPushMatrix();



   glScalef (1.0,0.1,0.4);

   glColor3f(0.0,.0,0.0);

   glutSolidCube (1.0);   //Connecting cube

   glPopMatrix();

   glPushMatrix();


   glTranslatef(0.0,-0.6,0.0);

   glColor3f(0.0,.0,0.0);

   glScalef(1.0,0.1,0.4);

   glutSolidCube(1.0);	//Connecting Cube

   glPopMatrix();

   glPushMatrix();

   glTranslatef(0.0,0.6,0.0);

   glScalef(1.0,0.1,0.4);

   glColor3f(0.0,.0,0.0);

   glutSolidCube(1.0);	//Connecting Cube

   glPopMatrix();

   glPushMatrix();

   glTranslatef(-0.5,0.0,0.0);

   glScalef(0.4,2.0,0.4);

   glColor3f(0.4,.4,0.4);

   glutSolidCube(1.0);	//Side Long Cube

   glPopMatrix();

   glPushMatrix();

   glTranslatef(0.5,0.0,0.0);

   glScalef(0.4,2.0,0.4);

   glColor3f(0.4,.4,0.4);

   glutSolidCube(1.0);	//Side Long Cube

   glPopMatrix();

}



 

void drawCircle(float radius)			//Code to draw semi-circle; 360 limit in for loop draws circle,but i need filled one

{

   glBegin(GL_TRIANGLE_FAN);

   

   for (int i=0; i<360; i++)

   {

      float degInRad = i*DEG2RAD;

      glVertex2f(cos(degInRad)*radius,sin(degInRad)*radius);

   }

 

   glEnd();

}



void drawSemiCircle(float radius)			//Code to draw semi-circle; 360 limit in for loop draws circle,but i need filled one

{

   glBegin(GL_TRIANGLE_FAN);

   

   for (int i=0; i<180; i++)

   {

      float degInRad = i*DEG2RAD;

      glVertex2f(cos(degInRad)*radius,sin(degInRad)*radius);

   }

 

   glEnd();

}



void robotarm()

{

   glPushMatrix();

   glTranslatef(0.0,-1.4,0.0);

   glPushMatrix();

   glColor3f(0.0,.0,0.0);

   glRotatef(90.0,1.0,0.0,0.0);

   glTranslatef(0.0,0.0,-0.3);

   drawCircle(1.0);

   glPopMatrix();

   glColor3f(0.0,.0,0.0);

   glTranslatef(0.0,0.0,-0.5);

   glScalef(3.0,0.5,3.0);

   glutSolidCube(1.0);								//Fixed Base

   glTranslatef(0.0,-1.0,-0.5);

   glScalef(2.0,0.5,2.0);

   glColor3f(0.0,0.0,0.0);

   glutSolidCube(1.0);

   glPopMatrix();

   glPushMatrix();

   glColor3f(1.0,0.0,0.0);

   glRotatef((GLfloat) shoulder, 0.0, 1.0, 0.0);	//360deg motion; 

   glPushMatrix();

   glTranslatef(-0.7,-1.1,0.0);

   glRotatef(90.0,0.0,1.0,0.0);

   glColor3f(0.0,0.0,1.0);

   drawSemiCircle(0.3);

   glPopMatrix();

   glPushMatrix();

   glTranslatef(0.7,-1.1,0.0);

   glRotatef(90.0,0.0,1.0,0.0);

   glColor3f(0.0,0.0,1.0);

   drawSemiCircle(0.3);

   glPopMatrix();

   glPushMatrix();

   glTranslatef(0.0,-1.0,0.0);

   glRotatef(shldf,1.0,0.0,0.0);					//180deg frnt-bck motion

   glTranslatef(0.0,1.0,0.0);

   glPushMatrix();

   

   base_arm();										//Shoulder to elbow

   glPushMatrix();

   glTranslatef(-0.71,1.0,0.0);

   glRotatef(90.0,0.0,1.0,0.0);

   glColor3f(0.0,0.0,1.0);

   drawCircle(0.2);

   glPopMatrix();

   glPushMatrix();

   glTranslatef(0.71,1.0,0.0);

   glRotatef(90.0,0.0,1.0,0.0);

   glColor3f(0.0,0.0,1.0);

   drawCircle(0.2);

   glPopMatrix();

   glTranslatef(0.0,1.0,0.0);

   glRotatef(90.0,1.0,0.0,0.0);

   glTranslatef(0.0,1.0,0.0);

   glTranslatef(0.0,-1.0,0.0);

   glRotatef((GLfloat) elbow,1.0,0.0,0.0);			//Elbow rotation

   glTranslatef(0.0,1.0,0.0);

   base_arm();										//elbow to Gripper

   glPushMatrix();

   glColor3f(.7,0.7,.7);

   glTranslatef(0.0,1.2,0.0);

   glRotatef(90.0,1.0,0.0,0.0);

   glScalef(1.5,0.5,0.4);

   glRotatef(gripper,0.0,0.0,1.0);

   glutSolidCube(1.0);								//Gripper

   glPopMatrix();

   glPopMatrix();

   glPopMatrix();

   glPopMatrix();

}





void display(void)

{

   glClear (GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);

   glPushMatrix();

   glScalef(0.8,0.8,0.8);							//To Show entire robo arm within the window

   robotarm();

   glPopMatrix();

   glutSwapBuffers();

}



void reshape (int w, int h)

{

   GLint xc=100,yc=450,r=10;

   glViewport (0, 0, (GLsizei) w, (GLsizei) h); 

   glMatrixMode (GL_PROJECTION);

   glLoadIdentity ();

   gluPerspective(65.0, (GLfloat) w/(GLfloat) h,1.0, 20.0);

   glMatrixMode(GL_MODELVIEW);

   glLoadIdentity();

   glTranslatef (0.0, 0.0, -5.0);

}



int main(int argc, char** argv)

{

   glutInit(&argc, argv);

   glutInitDisplayMode (GLUT_DOUBLE | GLUT_RGB);

   glutInitWindowSize (600, 600); 

   glutInitWindowPosition (0,0);

   glutCreateWindow ("Robot Arm Simulation");

   init();

   glutDisplayFunc(display); 

   glutReshapeFunc(reshape);

   glutKeyboardFunc(keyboard);

   glutMainLoop();

   return 0;

}




```

---

### Post by grayrainbow on 2009-11-05
It seems you're on right way by your own. Just...what exactly you mean by "for loop, delay?" ? :O
Btw, you can also use simple algorithm to make arm moving, but then if you want to change the movements you should recompile(doesn't seem big problem).

P.S. You can show same general cod logic without posting functions like base_arm + _draw couse it is quite obvius what you do with it

---

### Post by abhilashm86 on 2009-11-05
now the program works by user input-> keyboard.......
i want it automatically to make trasitions, movement according to time, so i tried for loop and delay, but its really fast and i can't see the effect. 
So i thought of using glutTimerFunc(), it trigers any function called and in millie seconds.............
Is there any good better options??

---

