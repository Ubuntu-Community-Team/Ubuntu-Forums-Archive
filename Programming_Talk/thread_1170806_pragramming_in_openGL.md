---
title: "pragramming in openGL"
date: 2009-05-26
forum: Programming Talk
---

### Post by garg89 on 2009-05-26
below is the partial code in opengl for displaying very large data sets >10^7 points and moving (rotating) them.
this i have created using the glui interface, instead of writing the application
myself. I have not been able to run this code on the LINUX machine with the
graphical accelerators.

please help me write a new code which can be implemented on a linux box.

the full code :
#include <GL/gl.h>
#include <GL/glui.h>
#include <GL/glut.h>
#include <GL/glu.h>
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <windows.h>

/* define a polygon with some structures for code readability */
typedef struct 
{ /* structure for a 3d point, height and 2 normal components */
float z;
float n1;
float n2;
float n3;
} POIN;

GLfloat light_diffuse_R[] = {1.0, 0.0, 0.0, 1.0};  /* Red  diffuse light. */
GLfloat light_diffuse_B[] = {0.0, 0.0, 1.0, 1.0};  /* Blue diffuse light. */

GLfloat light0_position[] = {1.0, 1.0, 1.0, 0.0};  /* Infinite light location. */
GLfloat light1_position[] = {-1.0, -1.0, -1.0, 0.0};


int type,nt,t,ii,jj; /* number of points */
float y, dy, /* position and increment along y axis */
      x, dx; /* position and increment along x axis */ 
float xa,ya,xb,yb,ylength,magn;
POIN q[4100][4100]; /* array of points */

float zoom=1;
float X=0, Y=0, Z=0; /* for translation*/
float angle=0;
float a,b,c; /* axis for rotation */

int inc;
int abc, pqr;

float obj_pos[] = { 0.0, 0.0, 0.0 };

float view_rotate[16] = { 1,0,0,0, 0,1,0,0, 0,0,1,0, 0,0,0,1 };

/*********************************************************/

void read_surface() 
{ 
int i,j; /* indices for x and y position */
float a1,a2,a3,b1,b2,b3,n1,n2,n3,nn; /* values for outer product */
float average, rdumx, rdumy, rdum;
FILE *fp;
char *fn = "d://sdas//opengl//P.dat";

printf("start make-surface\n");
/* read in values from file data file */

printf("\ngive filename  ");
//scanf("%s",fn);
printf("\ngive file-type 1=P, 2=H  ");
//scanf("%d",&type);

type = 1;
if (type==2)
  {
  printf("\ngive H magnification  ");
  scanf("%f",&magn);
  }
 
if ((fp=fopen(fn,"r"))==NULL) 
{ 
  printf(" \n INPUT-FILE NON-EXISTENT\n"); 
  exit(1);}
        
fscanf(fp,"%d %f %d %f\n",&ii,&dx,&jj,&dy);
fscanf(fp,"%f %f\n",&rdum,&rdum);
fscanf(fp,"%f %f\n",&xa,&ylength);
        
printf("ii=%d hx=%5.5e jj=%d hy=%5.5e\n",ii,dx,jj,dy);
ya=ylength;
xb=xa+(ii-1)*dx;
yb=ylength+(jj-1)*dy;
for (i =0; i <= ii; i++ )
  {
  for (j =0; j <= jj; j++ )
    {
        fscanf(fp,"%f %f %f",&rdumx,&rdumy,&rdum);
        /* printf("%4d %4d %f %f %f\n",i,j,rdumx,rdumy,rdum); */
        if (type==1) q[i][j].z=rdum; else q[i][j].z=1.0-magn*rdum; 
    }
  }
/* now compute polygon values */
for (i=0; i<=ii; i++) 
  {
  for (j=0; j<=jj; j++) 
    {
    /* calculate the normal of unit length */
        a1=dx ; a2=0.0; a3=q[i+1][j  ].z-q[i  ][j  ].z;
        b1=0.0; b2=dy ; b3=q[i  ][j+1].z-q[i  ][j  ].z;
        n1=a2*b3-a3*b2; n2=a3*b1-a1*b3; n3=a1*b2-a2*b1;
        nn=sqrt(n1*n1+n2*n2+n3*n3);
        q[i][j].n1 = n1/nn;
        q[i][j].n2 = n2/nn;
        q[i][j].n3 = n3/nn;
        }
  }
printf(" finished calculating normals\n");
printf("\noperation 1 : zoom in left click, zoom out right click, original figure middle click \n");

printf("\noperation 2 : x translate 't','y'; y translate 'g','h'; z translate 'b','n';  original position ' '\n  ");

printf("\noperation 3 : to rotate press 'u', and to get back to original position press 'i'\n\n");
}

/******************************************************/

void
drawBox(void)
{
 /* draw the surface by incrementing through ii and jj, with increments s */
int i,j,kk,ic,jc;
float normal1[3], normal2[3], normal3[3], normal4[3];
float vertex1[3], vertex2[3], vertex3[3], vertex4[3], vertex5[3];
char timestr[8];

/* ic, jc, central values */
ic=(ii)/2; jc=(jj)/2;

/* draw data onto screen */
printf("start draw-surface\n");

printf("%3d %3d %3d %3d \n",ii,jj,ic,jc);

for (i=0; i<ii; i +=inc) 
  {
  x= -4.5+i*dx;
  for (j=0; j<jj; j+=inc) 
    {
    y= -3.0+j*dy;
    if (x*x+y*y<2.0)
      {
        /* printf("%3d %3d %f %f %f %f\n",i,j,x,y,dx,dy); */
        vertex1[0]=vertex2[0]=x;  
        vertex3[0]=vertex4[0]=x+inc*dx;
        vertex1[1]=vertex4[1]=y;  
        vertex2[1]=vertex3[1]=y+inc*dy;
        vertex1[2]=q[i  ][j  ].z; 
        vertex2[2]=q[i  ][j+inc].z;
        vertex3[2]=q[i+inc][j+inc].z; 
        vertex4[2]=q[i+inc][j  ].z;
        normal1[0]=q[i  ][j  ].n1;
        normal1[1]=q[i  ][j  ].n2;
        normal1[2]=q[i  ][j  ].n3;
        /*normal2[0]=q[i  ][j+inc].n1;
        normal2[1]=q[i  ][j+inc].n2;
        normal2[2]=q[i  ][j+inc].n3;
        normal3[0]=q[i+inc][j+inc].n1;
        normal3[1]=q[i+inc][j+inc].n2;
        normal3[2]=q[i+inc][j+inc].n3;
        normal4[0]=q[i+inc][j  ].n1;
        normal4[1]=q[i+inc][j  ].n2;
        normal4[2]=q[i+inc][j  ].n3;*/
        
        

        glBegin(GL_POLYGON);
        glNormal3fv(normal1);
        glVertex3fv(vertex1);
        /* glNormal3fv(normal2); */
        glVertex3fv(vertex2);
        /* glNormal3fv(normal3); */
        glVertex3fv(vertex3);
        /* glNormal3fv(normal4); */
        glVertex3fv(vertex4);
        glEnd();
      }
    }
  }
}

/************************************************/



void display(void)
{
  
  glClearColor( .5f, .5f, .5f, 1.0f );
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
  
  glLoadIdentity();
  gluLookAt(0.0, 0.0, 10.0,  /* eye is at (0,0,10) */
    0.0, 0.0, 1.0,      /* center is at (0,0,1) */
    0.0, 1.0, 0.0);     /* up is in positive Z direction */
  
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  gluPerspective (25.0/zoom, 1, 1, 100);
  glMatrixMode(GL_MODELVIEW);
  
  
  glTranslatef(X,Y,Z);
  glRotatef(angle,a,b,c);
  
  glTranslatef( obj_pos[0], obj_pos[1], obj_pos[2] ); 
  
  glMultMatrixf( view_rotate );

  
  inc = 1;
  drawBox();
  glutSwapBuffers();
  
  glFlush(); 
}

/*************************************************/

void reshape(int w, int h)
{
  glViewport(0, 0, (GLsizei) w, (GLsizei) h);
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  gluPerspective (25.0/zoom, (int)w/(int)h, 4, 100);
  
  glMatrixMode(GL_MODELVIEW);
  //glLoadIdentity();

  glFlush ();
   
}

/*************************************************/

void keyboard(unsigned char key, int x, int y) 
{
  switch (key) {
                 case 'r':
                   zoom = 1.0;
                   glutPostRedisplay();
                   printf ("zoom reset to 1.0\n");
                   break;
     
                 case 'z':
                   zoom = zoom + 0.5;
                   if (zoom >= 3.0)
                       zoom = 3.0;
                   glutPostRedisplay();  
                   printf ("zoom is now %4.1f\n", zoom);
                   break;
     
                 case 'Z':
                   zoom = zoom - 0.5;
                   if (zoom <= 0.5)
                       zoom = 0.5;
                   glutPostRedisplay();
                   printf ("zoom is now %4.1f\n", zoom);
                   break;


/***************/

                 case 't' :
                   X = X - 0.5;
                   glutPostRedisplay();
                   printf ("translated by %f in x axis\n", X);
                   break;

                 case 'y' :
                   X = X + 0.5;
                   glutPostRedisplay();
                   printf ("translated by %f in x axis\n", X);  
                   break;



                 case 'g' :
                   Y = Y - 0.5;
                   glutPostRedisplay();
                   printf ("translated by %f in y axis\n", Y);
                   break;
 
                 case 'h' :
                   Y = Y + 0.5;
                   glutPostRedisplay();
                   printf ("translated by %f in y axis\n", Y);
                   break;



 
                 case 'b' :
                 Z = Z - 0.5;
                   glutPostRedisplay();
                   printf ("translated by %f in z axis\n", Z);
                   break;

                 case 'n' :
                  Z = Z + 0.5;
                   glutPostRedisplay();
                   printf ("translated by %f in z axis\n", Z);
                   break;


  
                 case ' ' :
                  X=Y=Z=0;
                   glutPostRedisplay();
                   printf ("original position with no translation\n");
                   break;

/***********/

                 case 'u' :
                   printf("\n rotate command - enter angle, axis(x,y,z) of rotation\n");
                   scanf("%f %f %f %f", &angle,&a,&b,&c);
                   glutPostRedisplay();
                   printf ("rotated by angle %f, along axis (%f,%f,%f)\n", angle,a,b,c);
                   break;


                  case 'i' :
                   angle=a=b=c=0;
                    glutPostRedisplay();
                    printf ("original position\n");
                    break;


/***********/


                 case 27:
                   exit(0);
                   break;



                 default:
                   break;
                }
}


/*************************************************************/

void mouse(int button, int state, int x, int y)
{
  switch (button) {
    case GLUT_LEFT_BUTTON:
      if (state == GLUT_DOWN) 
      {zoom = zoom + 0.25;
       glutPostRedisplay();
       printf ("zoom is now %4.1f\n", zoom);
      }
      break;

    case GLUT_RIGHT_BUTTON:
      if (state == GLUT_DOWN)
      {zoom = zoom - 0.25;
       if (zoom<= 0.25)
        zoom=0.25;  
       glutPostRedisplay();
       printf ("zoom is now %4.1f\n", zoom);  
      }
      break;
     
    case GLUT_MIDDLE_BUTTON:
      if (state == GLUT_DOWN) 
      {zoom = 1.0;
       glutPostRedisplay();
       printf ("zoom reset to 1.0, original image (no zoom)\n");
      }
 

   /* mouse scroll button */
    /*  else if (state == GLUT_UP) 
      {
 
       if (button == GLUT_WHEEL_UP)
        {
          zoom = zoom + 0.5;
          glutPostRedisplay();
          printf ("zoom is now %4.1f\n", zoom); 
        }
        break; 

        if (button == GLUT_WHEEL_DOWN)
        {
          zoom = zoom - 0.5;
          glutPostRedisplay();
          printf ("zoom is now %4.1f\n", zoom); 
        }
        break;
       }
      */

    default:
      break;
    }
}



/***************************************** myGlutIdle() ***********/

void myGlutIdle( void )
{
  /* According to the GLUT specification, the current window is 
     undefined during an idle callback.  So we need to explicitly change
     it if necessary */
     
  if ( glutGetWindow() != abc )
     glutSetWindow(abc);
  
  
  
  inc = 1;
  drawBox();
  glutSwapBuffers();
  
  glFlush(); 
  
}


/***************************************************************/

void init(void)
{

glShadeModel(GL_FLAT);

GLfloat mat_specular[] = {1.0, 1.0, 1.0, 1.0};
GLfloat mat_shininess[] = {100.0};

glEnable(GL_LIGHTING);
//glEnable( GL_NORMALIZE );

  /* Enable a single OpenGL light. */
  if (type==1) 
  { glLightfv(GL_LIGHT0, GL_DIFFUSE, light_diffuse_R);
    glLightfv(GL_LIGHT0, GL_POSITION, light0_position);
    glEnable(GL_LIGHT0);
  
    glLightfv(GL_LIGHT1, GL_DIFFUSE, light_diffuse_R);
    glLightfv(GL_LIGHT1, GL_POSITION, light1_position);
    glEnable(GL_LIGHT1);
  }
  
  else 
  
   {glLightfv(GL_LIGHT0, GL_DIFFUSE, light_diffuse_B);
    glLightfv(GL_LIGHT0, GL_POSITION, light0_position);
    glEnable(GL_LIGHT0);
  
    glLightfv(GL_LIGHT1, GL_DIFFUSE, light_diffuse_B);
    glLightfv(GL_LIGHT1, GL_POSITION, light1_position);
    glEnable(GL_LIGHT1);
   
  }
  
    
  glMaterialfv(GL_FRONT_AND_BACK, GL_SPECULAR,  mat_specular );
  glMaterialfv(GL_FRONT_AND_BACK, GL_SHININESS, mat_shininess);

  /* Use depth buffering for hidden surface elimination. */
  glEnable(GL_DEPTH_TEST);

  /* Setup the view of the cube. */

  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  gluPerspective( /* field of view in degree */ 25.0,
    /* aspect ratio */ 1.0,
    /* Z near */ 1.0, /* Z far */ 100);
  glMatrixMode(GL_MODELVIEW);
    
}

/*******************************************************/

int
main(int argc, char **argv)
{
  read_surface();
  glutInit(&argc, argv);
  glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB | GLUT_DEPTH);
  
  glutInitWindowSize(800,800);
  glutInitWindowPosition(20,20);
  abc = glutCreateWindow("red Pressure disribution");
  init(); 
  glutDisplayFunc(display);
  glutReshapeFunc(reshape); 
  glutKeyboardFunc(keyboard);
  glutMouseFunc(mouse);
  
  /* GLUI CODE */
  //GLUI *glui = GLUI_Master.create_glui("GLUI TOOLBAR", 0, 400, 50);
  
  GLUI *glui = GLUI_Master.create_glui_subwindow(abc, GLUI_SUBWINDOW_RIGHT );
  
  glui->add_statictext( "     TOOLBAR" );
  glui->add_separator();
  /**********/  
  GLUI_Panel *obj_panel = glui->add_panel ( "Operation 1" );
  
  GLUI_Rotation *view_rot = glui->add_rotation_to_panel( obj_panel, "ROTATION", view_rotate);
  view_rot->set_spin( 0.0);
  glui->add_separator_to_panel(obj_panel);
  
  /*************/
  
  GLUI_Panel *obj_panel1 = glui->add_panel ( "Operation 2" );
  
    
  GLUI_Translation *trans_xy = 
    glui->add_translation_to_panel( obj_panel1, "XY translation", GLUI_TRANSLATION_XY, obj_pos );
  trans_xy->set_speed( .05);
   glui->add_separator_to_panel(obj_panel1);
  /*************/
      
  GLUI_Translation *trans_x = 
    glui->add_translation_to_panel( obj_panel1, "X translation", GLUI_TRANSLATION_X, obj_pos );
  trans_x->set_speed( .05);
   glui->add_separator_to_panel(obj_panel1);
  /*************/
      
  GLUI_Translation *trans_y = 
    glui->add_translation_to_panel( obj_panel1, "Y translation", GLUI_TRANSLATION_Y, &obj_pos[1] );
  trans_y->set_speed( .05); 
  glui->add_separator_to_panel(obj_panel1);
  
  /****************/
  
  GLUI_Translation *trans_z = 
    glui->add_translation_to_panel( obj_panel1, "Z translation", GLUI_TRANSLATION_Z, &obj_pos[2] );
  trans_z->set_speed( .05); 
  
  
  glui->set_main_gfx_window( abc );

  /* We register the idle callback with GLUI, *not* with GLUT */
  GLUI_Master.set_glutIdleFunc( myGlutIdle );   
    
  glutMainLoop();
  
  return 0;             /* ANSI C requires main to return int. */
}

---

### Post by HavocXphere on 2009-05-26
[Google OpenGL Tutorial Ubuntu]("http://www.google.co.za/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=X8P&q=site%3Aubuntuforums.org+opengl+tutorial&btnG=Search&meta=") (<-link ;))

900+ hits on that...and thats only from this specific forum alone.:popcorn:

---

### Post by soltanis on 2009-05-26
Use [code] tags for formatting code so that we can read it easier, thanks.

---

### Post by garg89 on 2009-05-27
```

#include <GL/gl.h>
#include <GL/glui.h>
#include <GL/glut.h>
#include <GL/glu.h>
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <windows.h>

/* define a polygon with some structures for code readability */
typedef struct 
{ /* structure for a 3d point, height and 2 normal components */
float z;
float n1;
float n2;
float n3;
} POIN;

GLfloat light_diffuse_R[] = {1.0, 0.0, 0.0, 1.0}; /* Red diffuse light. */
GLfloat light_diffuse_B[] = {0.0, 0.0, 1.0, 1.0}; /* Blue diffuse light. */

GLfloat light0_position[] = {1.0, 1.0, 1.0, 0.0}; /* Infinite light location. */
GLfloat light1_position[] = {-1.0, -1.0, -1.0, 0.0};


int type,nt,t,ii,jj; /* number of points */
float y, dy, /* position and increment along y axis */
x, dx; /* position and increment along x axis */ 
float xa,ya,xb,yb,ylength,magn;
POIN q[4100][4100]; /* array of points */

float zoom=1;
float X=0, Y=0, Z=0; /* for translation*/
float angle=0;
float a,b,c; /* axis for rotation */

int inc;
int abc, pqr;

float obj_pos[] = { 0.0, 0.0, 0.0 };

float view_rotate[16] = { 1,0,0,0, 0,1,0,0, 0,0,1,0, 0,0,0,1 };

/************************************************** *******/

void read_surface() 
{ 
int i,j; /* indices for x and y position */
float a1,a2,a3,b1,b2,b3,n1,n2,n3,nn; /* values for outer product */
float average, rdumx, rdumy, rdum;
FILE *fp;
char *fn = "d://sdas//opengl//P.dat";

printf("start make-surface\n");
/* read in values from file data file */

printf("\ngive filename ");
//scanf("%s",fn);
printf("\ngive file-type 1=P, 2=H ");
//scanf("%d",&type);

type = 1;
if (type==2)
{
printf("\ngive H magnification ");
scanf("%f",&magn);
}

if ((fp=fopen(fn,"r"))==NULL) 
{ 
printf(" \n INPUT-FILE NON-EXISTENT\n"); 
exit(1);}

fscanf(fp,"%d %f %d %f\n",&ii,&dx,&jj,&dy);
fscanf(fp,"%f %f\n",&rdum,&rdum);
fscanf(fp,"%f %f\n",&xa,&ylength);

printf("ii=%d hx=%5.5e jj=%d hy=%5.5e\n",ii,dx,jj,dy);
ya=ylength;
xb=xa+(ii-1)*dx;
yb=ylength+(jj-1)*dy;
for (i =0; i <= ii; i++ )
{
for (j =0; j <= jj; j++ )
{
fscanf(fp,"%f %f %f",&rdumx,&rdumy,&rdum);
/* printf("%4d %4d %f %f %f\n",i,j,rdumx,rdumy,rdum); */
if (type==1) q[i][j].z=rdum; else q[i][j].z=1.0-magn*rdum; 
}
}
/* now compute polygon values */
for (i=0; i<=ii; i++) 
{
for (j=0; j<=jj; j++) 
{
/* calculate the normal of unit length */
a1=dx ; a2=0.0; a3=q[i+1][j ].z-q[i ][j ].z;
b1=0.0; b2=dy ; b3=q[i ][j+1].z-q[i ][j ].z;
n1=a2*b3-a3*b2; n2=a3*b1-a1*b3; n3=a1*b2-a2*b1;
nn=sqrt(n1*n1+n2*n2+n3*n3);
q[i][j].n1 = n1/nn;
q[i][j].n2 = n2/nn;
q[i][j].n3 = n3/nn;
}
}
printf(" finished calculating normals\n");
printf("\noperation 1 : zoom in left click, zoom out right click, original figure middle click \n");

printf("\noperation 2 : x translate 't','y'; y translate 'g','h'; z translate 'b','n'; original position ' '\n ");

printf("\noperation 3 : to rotate press 'u', and to get back to original position press 'i'\n\n");
}

/************************************************** ****/

void
drawBox(void)
{
/* draw the surface by incrementing through ii and jj, with increments s */
int i,j,kk,ic,jc;
float normal1[3], normal2[3], normal3[3], normal4[3];
float vertex1[3], vertex2[3], vertex3[3], vertex4[3], vertex5[3];
char timestr[8];

/* ic, jc, central values */
ic=(ii)/2; jc=(jj)/2;

/* draw data onto screen */
printf("start draw-surface\n");

printf("%3d %3d %3d %3d \n",ii,jj,ic,jc);

for (i=0; i<ii; i +=inc) 
{
x= -4.5+i*dx;
for (j=0; j<jj; j+=inc) 
{
y= -3.0+j*dy;
if (x*x+y*y<2.0)
{
/* printf("%3d %3d %f %f %f %f\n",i,j,x,y,dx,dy); */
vertex1[0]=vertex2[0]=x; 
vertex3[0]=vertex4[0]=x+inc*dx;
vertex1[1]=vertex4[1]=y; 
vertex2[1]=vertex3[1]=y+inc*dy;
vertex1[2]=q[i ][j ].z; 
vertex2[2]=q[i ][j+inc].z;
vertex3[2]=q[i+inc][j+inc].z; 
vertex4[2]=q[i+inc][j ].z;
normal1[0]=q[i ][j ].n1;
normal1[1]=q[i ][j ].n2;
normal1[2]=q[i ][j ].n3;
/*normal2[0]=q[i ][j+inc].n1;
normal2[1]=q[i ][j+inc].n2;
normal2[2]=q[i ][j+inc].n3;
normal3[0]=q[i+inc][j+inc].n1;
normal3[1]=q[i+inc][j+inc].n2;
normal3[2]=q[i+inc][j+inc].n3;
normal4[0]=q[i+inc][j ].n1;
normal4[1]=q[i+inc][j ].n2;
normal4[2]=q[i+inc][j ].n3;*/



glBegin(GL_POLYGON);
glNormal3fv(normal1);
glVertex3fv(vertex1);
/* glNormal3fv(normal2); */
glVertex3fv(vertex2);
/* glNormal3fv(normal3); */
glVertex3fv(vertex3);
/* glNormal3fv(normal4); */
glVertex3fv(vertex4);
glEnd();
}
}
}
}

/************************************************/



void display(void)
{

glClearColor( .5f, .5f, .5f, 1.0f );
glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

glLoadIdentity();
gluLookAt(0.0, 0.0, 10.0, /* eye is at (0,0,10) */
0.0, 0.0, 1.0, /* center is at (0,0,1) */
0.0, 1.0, 0.0); /* up is in positive Z direction */

glMatrixMode(GL_PROJECTION);
glLoadIdentity();
gluPerspective (25.0/zoom, 1, 1, 100);
glMatrixMode(GL_MODELVIEW);


glTranslatef(X,Y,Z);
glRotatef(angle,a,b,c);

glTranslatef( obj_pos[0], obj_pos[1], obj_pos[2] ); 

glMultMatrixf( view_rotate );


inc = 1;
drawBox();
glutSwapBuffers();

glFlush(); 
}

/*************************************************/

void reshape(int w, int h)
{
glViewport(0, 0, (GLsizei) w, (GLsizei) h);
glMatrixMode(GL_PROJECTION);
glLoadIdentity();
gluPerspective (25.0/zoom, (int)w/(int)h, 4, 100);

glMatrixMode(GL_MODELVIEW);
//glLoadIdentity();

glFlush ();

}

/*************************************************/

void keyboard(unsigned char key, int x, int y) 
{
switch (key) {
case 'r':
zoom = 1.0;
glutPostRedisplay();
printf ("zoom reset to 1.0\n");
break;

case 'z':
zoom = zoom + 0.5;
if (zoom >= 3.0)
zoom = 3.0;
glutPostRedisplay(); 
printf ("zoom is now %4.1f\n", zoom);
break;

case 'Z':
zoom = zoom - 0.5;
if (zoom <= 0.5)
zoom = 0.5;
glutPostRedisplay();
printf ("zoom is now %4.1f\n", zoom);
break;


/***************/

case 't' :
X = X - 0.5;
glutPostRedisplay();
printf ("translated by %f in x axis\n", X);
break;

case 'y' :
X = X + 0.5;
glutPostRedisplay();
printf ("translated by %f in x axis\n", X); 
break;



case 'g' :
Y = Y - 0.5;
glutPostRedisplay();
printf ("translated by %f in y axis\n", Y);
break;

case 'h' :
Y = Y + 0.5;
glutPostRedisplay();
printf ("translated by %f in y axis\n", Y);
break;




case 'b' :
Z = Z - 0.5;
glutPostRedisplay();
printf ("translated by %f in z axis\n", Z);
break;

case 'n' :
Z = Z + 0.5;
glutPostRedisplay();
printf ("translated by %f in z axis\n", Z);
break;



case ' ' :
X=Y=Z=0;
glutPostRedisplay();
printf ("original position with no translation\n");
break;

/***********/

case 'u' :
printf("\n rotate command - enter angle, axis(x,y,z) of rotation\n");
scanf("%f %f %f %f", &angle,&a,&b,&c);
glutPostRedisplay();
printf ("rotated by angle %f, along axis (%f,%f,%f)\n", angle,a,b,c);
break;


case 'i' :
angle=a=b=c=0;
glutPostRedisplay();
printf ("original position\n");
break;


/***********/


case 27:
exit(0);
break;



default:
break;
}
}


/************************************************** ***********/

void mouse(int button, int state, int x, int y)
{
switch (button) {
case GLUT_LEFT_BUTTON:
if (state == GLUT_DOWN) 
{zoom = zoom + 0.25;
glutPostRedisplay();
printf ("zoom is now %4.1f\n", zoom);
}
break;

case GLUT_RIGHT_BUTTON:
if (state == GLUT_DOWN)
{zoom = zoom - 0.25;
if (zoom<= 0.25)
zoom=0.25; 
glutPostRedisplay();
printf ("zoom is now %4.1f\n", zoom); 
}
break;

case GLUT_MIDDLE_BUTTON:
if (state == GLUT_DOWN) 
{zoom = 1.0;
glutPostRedisplay();
printf ("zoom reset to 1.0, original image (no zoom)\n");
}


/* mouse scroll button */
/* else if (state == GLUT_UP) 
{

if (button == GLUT_WHEEL_UP)
{
zoom = zoom + 0.5;
glutPostRedisplay();
printf ("zoom is now %4.1f\n", zoom); 
}
break; 

if (button == GLUT_WHEEL_DOWN)
{
zoom = zoom - 0.5;
glutPostRedisplay();
printf ("zoom is now %4.1f\n", zoom); 
}
break;
}
*/

default:
break;
}
}



/***************************************** myGlutIdle() ***********/

void myGlutIdle( void )
{
/* According to the GLUT specification, the current window is 
undefined during an idle callback. So we need to explicitly change
it if necessary */

if ( glutGetWindow() != abc )
glutSetWindow(abc);



inc = 1;
drawBox();
glutSwapBuffers();

glFlush(); 

}


/************************************************** *************/

void init(void)
{

glShadeModel(GL_FLAT);

GLfloat mat_specular[] = {1.0, 1.0, 1.0, 1.0};
GLfloat mat_shininess[] = {100.0};

glEnable(GL_LIGHTING);
//glEnable( GL_NORMALIZE );

/* Enable a single OpenGL light. */
if (type==1) 
{ glLightfv(GL_LIGHT0, GL_DIFFUSE, light_diffuse_R);
glLightfv(GL_LIGHT0, GL_POSITION, light0_position);
glEnable(GL_LIGHT0);

glLightfv(GL_LIGHT1, GL_DIFFUSE, light_diffuse_R);
glLightfv(GL_LIGHT1, GL_POSITION, light1_position);
glEnable(GL_LIGHT1);
}

else 

{glLightfv(GL_LIGHT0, GL_DIFFUSE, light_diffuse_B);
glLightfv(GL_LIGHT0, GL_POSITION, light0_position);
glEnable(GL_LIGHT0);

glLightfv(GL_LIGHT1, GL_DIFFUSE, light_diffuse_B);
glLightfv(GL_LIGHT1, GL_POSITION, light1_position);
glEnable(GL_LIGHT1);

}


glMaterialfv(GL_FRONT_AND_BACK, GL_SPECULAR, mat_specular );
glMaterialfv(GL_FRONT_AND_BACK, GL_SHININESS, mat_shininess);

/* Use depth buffering for hidden surface elimination. */
glEnable(GL_DEPTH_TEST);

/* Setup the view of the cube. */

glMatrixMode(GL_PROJECTION);
glLoadIdentity();
gluPerspective( /* field of view in degree */ 25.0,
/* aspect ratio */ 1.0,
/* Z near */ 1.0, /* Z far */ 100);
glMatrixMode(GL_MODELVIEW);

}

/************************************************** *****/

int
main(int argc, char **argv)
{
read_surface();
glutInit(&argc, argv);
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB | GLUT_DEPTH);

glutInitWindowSize(800,800);
glutInitWindowPosition(20,20);
abc = glutCreateWindow("red Pressure disribution");
init(); 
glutDisplayFunc(display);
glutReshapeFunc(reshape); 
glutKeyboardFunc(keyboard);
glutMouseFunc(mouse);

/* GLUI CODE */
//GLUI *glui = GLUI_Master.create_glui("GLUI TOOLBAR", 0, 400, 50);

GLUI *glui = GLUI_Master.create_glui_subwindow(abc, GLUI_SUBWINDOW_RIGHT );

glui->add_statictext( " TOOLBAR" );
glui->add_separator();
/**********/ 
GLUI_Panel *obj_panel = glui->add_panel ( "Operation 1" );

GLUI_Rotation *view_rot = glui->add_rotation_to_panel( obj_panel, "ROTATION", view_rotate);
view_rot->set_spin( 0.0);
glui->add_separator_to_panel(obj_panel);

/*************/

GLUI_Panel *obj_panel1 = glui->add_panel ( "Operation 2" );


GLUI_Translation *trans_xy = 
glui->add_translation_to_panel( obj_panel1, "XY translation", GLUI_TRANSLATION_XY, obj_pos );
trans_xy->set_speed( .05);
glui->add_separator_to_panel(obj_panel1);
/*************/

GLUI_Translation *trans_x = 
glui->add_translation_to_panel( obj_panel1, "X translation", GLUI_TRANSLATION_X, obj_pos );
trans_x->set_speed( .05);
glui->add_separator_to_panel(obj_panel1);
/*************/

GLUI_Translation *trans_y = 
glui->add_translation_to_panel( obj_panel1, "Y translation", GLUI_TRANSLATION_Y, &obj_pos[1] );
trans_y->set_speed( .05); 
glui->add_separator_to_panel(obj_panel1);

/****************/

GLUI_Translation *trans_z = 
glui->add_translation_to_panel( obj_panel1, "Z translation", GLUI_TRANSLATION_Z, &obj_pos[2] );
trans_z->set_speed( .05); 


glui->set_main_gfx_window( abc );

/* We register the idle callback with GLUI, *not* with GLUT */
GLUI_Master.set_glutIdleFunc( myGlutIdle ); 

glutMainLoop();

return 0; /* ANSI C requires main to return int. */
}

```

---

### Post by hod139 on 2009-05-27
Here's what I did to get your code to compile on my laptop (running hardy)
```

sudo apt-get install libglui-dev

```Then I had to change your headers.  For some reason ubuntu puts glui.h in /usr/include, not in /usr/include/GL.  There is no window.h in linux.
```

#include <GL/gl.h>
//#include <GL/glui.h>
#include <glui.h>
#include <GL/glut.h>
#include <GL/glu.h>
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
//#include <windows.h>

```Then I compiled it (I had to use g++ instead of gcc, otherwise glui.h was giving compile errors.  I don't know why and didn't investigate),
```

g++ -Wall temp.cpp -lglut -lglui

```I can't run it since you didn't provide an input file, and there are some warnings you should take a look at:

```

temp.c: In function &#8216;void read_surface()&#8217;:
temp.c:53: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:51: warning: unused variable &#8216;average&#8217;
temp.c: In function &#8216;void drawBox()&#8217;:
temp.c:121: warning: unused variable &#8216;kk&#8217;
temp.c:122: warning: unused variable &#8216;normal2&#8217;
temp.c:122: warning: unused variable &#8216;normal3&#8217;
temp.c:122: warning: unused variable &#8216;normal4&#8217;
temp.c:123: warning: unused variable &#8216;vertex5&#8217;
temp.c:124: warning: unused variable &#8216;timestr&#8217;
temp.c: In function &#8216;int main(int, char**)&#8217;:
temp.c:503: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:506: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:508: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:514: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:518: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:524: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:530: warning: deprecated conversion from string constant to &#8216;char*&#8217;
temp.c:537: warning: deprecated conversion from string constant to &#8216;char*&#8217;

```

---

