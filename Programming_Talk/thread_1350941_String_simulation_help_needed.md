---
title: "String simulation help needed"
date: 2009-12-09
forum: Programming Talk
---

### Post by Ultros88 on 2009-12-09
Hi, I've got some code written in an attempt to simulate a string and I've got an issue having to do with arrays, objects in those arrays, objects in the objects in the arrays, and functions which change those objects. Too complicated for me to figure out apparently, please help!

The code uses springs and nodes. Here are the headers:
```

class Node
{
private:
    Vector pos, vel, acc;
    float mass;

public:
    Node();
    Node(Vector p, Vector v, Vector a, float m);
    void setNode(Vector p, Vector v, Vector a, float m);
    void setPos(Vector p);
    void setVel(Vector v);
    void setAcc(Vector a);
    void setMass(float m);
    Vector getPos();
    Vector getVel();
    Vector getAcc();
    float getMass();
    void handle_input(SDL_Event event);
    void update(float dt);
};
```
```

class Spring
{
private:
    Node n1, n2;
    float springConst;
    float eqLen;
    float getEqLen();

public:
    Spring();
    Spring(Node nd1, Node nd2, float sC);
    void setSpring(Node nd1, Node nd2, float sC);
    void setNodes(Node nd1, Node nd2);
    void applyForce();
    void draw();
    Node getNode();
};
```

Basically the idea is to create an array of nodes, and with that array to create an array of springs that connect the nodes. Now loop having each spring object apply its force to the two nodes it is connected to by modifying the nodes' acceleration vector. Then update velocity and position and draw.

Here's a code snippet for that: Sp = spring, Nd = node
```

for(int i = 0; i < numSp; i++)
{
    Sp[i].applyForce();
}

for(int i = 0; i < numNd; i++)
{
    Nd[i].update(.01);
}

for(int i = 0; i < numSp; i++)
{
    Sp[i].draw();
}
```

It doesn't quite work. I've used the following test parameters right after the above code snippet in an attempt to weasel out what's gone wrong:

```
dy += 0.1;
p.setY(dy); //p is a Vector
Sp[5].getFirstNode().setPos(p);
cout << Sp[5].getFirstNode().getPos().getY();
```

Running with the above code tells me that the first node attached to spring 5 is not having its position vector updated. How can I get the functions of the objects in the arrays to successfully alter their internal values?

-Ultros

---

### Post by dwhitney67 on 2009-12-09
Can you please re-post again.  You left out too many details for me to comprehend what you are doing or require.

Where is Vector defined?
Where is Spring::getFirstNode() declared/defined?
Where do you declare your Springs array?

Plus try to explain what you are trying to accomplish.  Perhaps there is a better and/or more intuitive design that can be forged out of your code.

---

### Post by ve4cib on 2009-12-09
I'm also confused.  Are we talking about strings in the quantum mechanics sense?  Or was that a typo and you mean "springs" the whole time?  What are the mathematical formulae you're trying to model?  What do the functions you've listed actually do?  etc...?

Without more details I don't think there's much we can do.

---

### Post by Ultros88 on 2009-12-10
Okay, here's the whole shebang - it's meant to simulate something like a guitar string:

Vector.cpp
```
#include "vector.h"
#include <math.h>

Vector::Vector()
{}

Vector::Vector(float x1, float y1, float z1)
{
    setVector(x1,y1,z1);
}

void Vector::setVector(float x1, float y1, float z1)
{
    x = x1;
    y = y1;
    z = z1;
}

void Vector::setX(float x1)
{
    x = x1;
}

void Vector::setY(float y1)
{
    y = y1;
}

void Vector::setZ(float z1)
{
    z = z1;
}

float Vector::getX()
{
    return x;
}

float Vector::getY()
{
    return y;
}

float Vector::getZ()
{
    return z;
}

void Vector::equals(Vector v2)
{
    x = v2.x;
    y = v2.y;
    z = v2.z;
}

Vector Vector::add(Vector v2)
{
    Vector v(x+v2.x,y+v2.y,z+v2.z);
}

Vector Vector::scale(float s)
{
    Vector v(s*x,s*y,s*z);
}

Vector Vector::diff(Vector v2)
{
    Vector v(x-v2.x,y-v2.y,z-v2.z);
}

float Vector::norm()
{
    return sqrt(x*x + y*y + z*z);
}
```

Node.cpp
```
#include "node.h"
#include "vector.h"

Node::Node()
{}

Node::Node(Vector p, Vector v, Vector a, float m)
{
    setNode(p,v,a,m);
}

void Node::setNode(Vector p, Vector v, Vector a, float m)
{
    pos = p;
    vel = v;
    acc = a;
    mass = m;
}

void Node::setPos(Vector p)
{
    pos = p;
}

void Node::setVel(Vector v)
{
    vel = v;
}

void Node::setAcc(Vector a)
{
    acc = a;
}

void Node::setMass(float m)
{
    mass = m;
}

Vector Node::getPos()
{
    return pos;
}

Vector Node::getVel()
{
    return vel;
}

Vector Node::getAcc()
{
    return acc;
}

float Node::getMass()
{
    return mass;
}

void Node::handle_input(SDL_Event event)
{
    //If a key was pressed
    if( event.type == SDL_KEYDOWN )
    {
        //Adjust the velocity
        switch( event.key.keysym.sym )
        {
            case SDLK_UP: pos.setY(pos.getY() - .5); break;
            case SDLK_DOWN: pos.setY(pos.getY() + .5); break;
            case SDLK_LEFT: pos.setX(pos.getX() - .5); break;
            case SDLK_RIGHT: pos.setX(pos.getX() + .5); break;
        }
    }
}

void Node::update(float dt)
{
    vel.add(acc.scale(dt));
    pos.add(vel.scale(dt));
}
```

Spring.cpp
```
#include "spring.h"
#include "node.h"
#include <SDL/SDL_opengl.h>

Spring::Spring()
{}

Spring::Spring(Node nd1, Node nd2, float sC)
{
    setSpring(nd1,nd2,sC);
}

void Spring::setSpring(Node nd1, Node nd2, float sC)
{
    n1 = nd1;
    n2 = nd2;
    springConst = sC;
    eqLen = getEqLen();
}

void Spring::setNodes(Node nd1, Node nd2)
{
    n1 = nd1;
    n2 = nd2;
}

float Spring::getEqLen()
{
    return n1.getPos().diff(n2.getPos()).norm();
}

Node Spring::getNode()
{
    return n2;
}

void Spring::applyForce()
{
    n1.setAcc(n1.getAcc().add(n2.getPos().diff(n1.getPos()).scale(springConst/n1.getMass())));
    n2.setAcc(n2.getAcc().add(n1.getPos().diff(n1.getPos()).scale(springConst/n2.getMass())));
}

void Spring::draw()
{
    glBegin(GL_LINES);
    glVertex3f(n1.getPos().getX(),n1.getPos().getY(),n1.getPos().getZ());
    glVertex3f(n2.getPos().getX(),n2.getPos().getY(),n2.getPos().getZ());
    glEnd();
}
```

Timer.cpp
```
#include "timer.h"

Timer::Timer()
{
    //Initialize the variables
    startTicks = 0;
    pausedTicks = 0;
    paused = false;
    started = false;
}

void Timer::start()
{
    //Start the timer
    started = true;

    //Unpause the timer
    paused = false;

    //Get the current clock time
    startTicks = SDL_GetTicks();
}

void Timer::stop()
{
    //Stop the timer
    started = false;

    //Unpause the timer
    paused = false;
}

void Timer::pause()
{
    //If the timer is running and isn't already paused
    if( ( started == true ) && ( paused == false ) )
    {
        //Pause the timer
        paused = true;

        //Calculate the paused ticks
        pausedTicks = SDL_GetTicks() - startTicks;
    }
}

void Timer::unpause()
{
    //If the timer is paused
    if( paused == true )
    {
        //Unpause the timer
        paused = false;

        //Reset the starting ticks
        startTicks = SDL_GetTicks() - pausedTicks;

        //Reset the paused ticks
        pausedTicks = 0;
    }
}

int Timer::get_ticks()
{
    //If the timer is running
    if( started == true )
    {
        //If the timer is paused
        if( paused == true )
        {
            //Return the number of ticks when the timer was paused
            return pausedTicks;
        }
        else
        {
            //Return the current time minus the start time
            return SDL_GetTicks() - startTicks;
        }
    }

    //If the timer isn't running
    return 0;
}

bool Timer::is_started()
{
    return started;
}

bool Timer::is_paused()
{
    return paused;
}
```

Main.cpp
```
#include <stdlib.h>
#include <iostream>
#include <SDL/SDL.h>
#include <SDL/SDL_opengl.h>

#include "node.h"
#include "spring.h"
#include "timer.h"
#include "vector.h"

/* screen width, height, and bit depth */
#define SCREEN_WIDTH  640
#define SCREEN_HEIGHT 480
#define SCREEN_BPP     16

/* Define our booleans */
#define TRUE  1
#define FALSE 0

using namespace std;

/* This is our SDL surface */
SDL_Surface *surface;

SDL_Event event;

/* function to release/destroy our resources and restoring the old desktop */
void Quit( int returnCode )
{
    /* clean up the window */
    SDL_Quit( );

    /* and exit appropriately */
    exit( returnCode );
}

/* function to reset our viewport after a window resize */
int resizeWindow( int width, int height )
{
    /* Height / width ration */
    GLfloat ratio;

    /* Protect against a divide by zero */
    if ( height == 0 )
	height = 1;

    ratio = ( GLfloat )width / ( GLfloat )height;

    /* Setup our viewport. */
    glViewport( 0, 0, ( GLsizei )width, ( GLsizei )height );

    /* change to the projection matrix and set our viewing volume. */
    glMatrixMode( GL_PROJECTION );
    glLoadIdentity( );

    /* Set our perspective */
    gluPerspective( 45.0f, ratio, 0.1f, 100.0f );

    /* Make sure we're chaning the model view and not the projection */
    glMatrixMode( GL_MODELVIEW );

    /* Reset The View */
    glLoadIdentity( );

    return( TRUE );
}

/* general OpenGL initialization function */
int initGL()
{

    /* Enable smooth shading */
    glShadeModel( GL_SMOOTH );

    /* Set the background black */
    glClearColor( 0.0f, 0.0f, 0.0f, 0.0f );

    /* Depth buffer setup */
    glClearDepth( 1.0f );

    /* Enables Depth Testing */
    glEnable( GL_DEPTH_TEST );

    /* The Type Of Depth Test To Do */
    glDepthFunc( GL_LEQUAL );

    /* Really Nice Perspective Calculations */
    glHint( GL_PERSPECTIVE_CORRECTION_HINT, GL_NICEST );

    return( TRUE );
}

int main(int argc, char** argv)
{
    float dy = 0;
    float mass = 2;
    float sC = .01;
    int numNd = 11;
    int numSp = numNd - 1;
    Vector initPos(-2,0,0);
    Vector initVel(0,0,0);
    Vector initAcc(0,0,0);
    Vector p(0,0,0);
    Spring *Sp = new Spring[numSp];
    Node *Nd = new Node[numNd];

    for(int i = 0; i < numNd; i++)
    {
        if(i == 0)
        {
            Nd[i] = Node(initPos,initVel,initAcc,mass);
        }
        else
        {
            initPos.setX(-2 + (float)i*numNd/30);
            Nd[i] = Node(initPos,initVel,initAcc,mass);
            if(i==5)
            {
                p.setX(-2+(float)i*numNd/30);
            }
        }
    }

    for(int i = 0; i < numSp-1; i++)
    {
        Sp[i] = Spring(Nd[i],Nd[i+1],sC);
    }

    /* Flags to pass to SDL_SetVideoMode */
    int videoFlags;
    /* main loop variable */
    int done = FALSE;
    /* used to collect events */
    SDL_Event event;
    /* this holds some info about our display */
    const SDL_VideoInfo *videoInfo;
    /* whether or not the window is active */
    int isActive = TRUE;

    /* initialize SDL */
    if ( SDL_Init( SDL_INIT_VIDEO ) < 0 )
    {
        fprintf( stderr, "Video initialization failed: %s\n",SDL_GetError( ) );
        Quit( 1 );
    }

    /* Fetch the video info */
    videoInfo = SDL_GetVideoInfo( );

    if ( !videoInfo )
    {
        fprintf( stderr, "Video query failed: %s\n",SDL_GetError( ) );
        Quit( 1 );
    }

    /* the flags to pass to SDL_SetVideoMode */
    videoFlags  = SDL_OPENGL;          /* Enable OpenGL in SDL */
    videoFlags |= SDL_GL_DOUBLEBUFFER; /* Enable double buffering */
    videoFlags |= SDL_HWPALETTE;       /* Store the palette in hardware */
    videoFlags |= SDL_RESIZABLE;       /* Enable window resizing */

    /* This checks to see if surfaces can be stored in memory */
    if ( videoInfo->hw_available )
	videoFlags |= SDL_HWSURFACE;
    else
	videoFlags |= SDL_SWSURFACE;

    /* This checks if hardware blits can be done */
    if ( videoInfo->blit_hw )
	videoFlags |= SDL_HWACCEL;

    /* Sets up OpenGL double buffering */
    SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, 1 );

    /* get a SDL surface */
    surface = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP,
				videoFlags );

    /* Verify there is a surface */
    if ( !surface )
	{
	    fprintf( stderr,  "Video mode set failed: %s\n", SDL_GetError( ) );
	    Quit( 1 );
	}

    /* initialize OpenGL */
    initGL();

    /* resize the initial window */
    resizeWindow( SCREEN_WIDTH, SCREEN_HEIGHT );

    /* wait for events */
    while ( !done )
    {
        /* handle the events in the queue */

	while ( SDL_PollEvent( &event ) )
        {
            switch( event.type )
            {
                case SDL_ACTIVEEVENT:
		/* Something's happend with our focus
		 * If we lost focus or we are iconified, we
		 * shouldn't draw the screen
		*/
                    if ( event.active.gain == 0 )
                        isActive = FALSE;
                    else
                        isActive = TRUE;
                    break;
		case SDL_VIDEORESIZE:
                    /* handle resize event */
                    surface = SDL_SetVideoMode( event.resize.w,event.resize.h,16,videoFlags );
		    if ( !surface )
                    {
                        fprintf( stderr, "Could not get a surface after resize: %s\n", SDL_GetError( ) );
			Quit( 1 );
                    }
		    resizeWindow( event.resize.w, event.resize.h );
		    break;
		case SDL_KEYDOWN:
		    /* handle key presses */
                    Nd[6].handle_input(event);
                    break;
		case SDL_QUIT:
		    /* handle quit requests */
		    done = TRUE;
		    break;
		default:
		    break;
            }
	}

	/* draw the scene */
	if (isActive)
        {
            /* Clear The Screen And The Depth Buffer */
            glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );

            /* Move Left 1.5 Units And Into The Screen 6.0 */
            glLoadIdentity( );
            glTranslatef( 0.0f, 0.0f, -6.0f );

            for(int i = 0; i < numSp; i++)
            {
                Sp[i].applyForce();
            }

            for(int i = 0; i < numNd; i++)
            {
                Nd[i].update(.01);
            }

            for(int i = 0; i < numSp; i++)
            {
                Sp[i].draw();
            }

            dy += 0.1;
            p.setY(dy);
            Sp[5].getNode().setPos(p);
            cout << Sp[5].getNode().getPos().getY();
            SDL_GL_SwapBuffers();
        }
    }

    /* clean ourselves up and exit */
    Quit( 0 );

    /* Should never get here */
    return( 0 );
}
```

---

### Post by dwhitney67 on 2009-12-10
It looks like you have great ambition to develop this application into something interesting, however I see that your development experience is not very extensive.

A few of things I would recommend:

1.  Avoid using arrays; use the STL vector, or STL array.
2.  Avoid using the operator 'new' unless absolutely essential; in your program, for the arrays, it is not.
3.  Avoid passing objects by value; pass by reference, and when warranted, pass these as const objects.  When you pass by value, you are passing a copy of the object (and gobbling CPU time and RAM to make these copies).
4.  Decide if you want to store copies of objects in your classes, or if you want to store references or pointers to allocated objects.

Syntactically, it appears that your code is ok, however when you manipulate the vector 'p', this is *not* the same vector that you stored earlier in the Spring object.  Refer to suggestion #3 above to figure out why.

---

### Post by Ultros88 on 2009-12-11
Hey, thanks for the help. I'll try and implement your suggestions. When I get it working - fingers crossed - I'll post everything here. Thanks again, Ultros

Okay, I've looked up how to pass by reference and changed most of my functions to the form:

type class::function(type& a, ...);

But when those functions are called via something like - function(a); - the compiler tells me:

spring.cpp:29: error: no matching function for call to &#8216;Vector::diff(Vector)&#8217;
vector.h:31: note: candidates are: Vector Vector::diff(Vector&)

Huh? Everything I've read about passing by reference so far seems to suggest that what I'm doing should work. So... what's up?

---

### Post by dwhitney67 on 2009-12-11
Here's a sample of what declarations/implementations should look like; adjust your code to model these suggestions.

Vector.h:
```

#include <iostream>

class Vector
{
public:
   Vector(int x = 0, int y = 0, int z = 0);
   Vector(const Vector& other);

   ~Vector() {}

   inline int getX() const { return _x; }
   inline int getY() const { return _y; }
   inline int getZ() const { return _z; }

   Vector operator+(const Vector& other) const;
   Vector operator-(const Vector& other) const;
   Vector operator=(const Vector& other) const;
   bool   operator==(const Vector& other) const;

   Vector& operator+=(const Vector& other);
   Vector& operator-=(const Vector& other);

   friend std::ostream& operator<<(std::ostream& os, const Vector& v);

private:
   int _x, _y, _z;
};

```
Vector.cpp:
```

#include "Vector.h"

Vector::Vector(int x, int y, int z)
  : _x(x),
    _y(y),
    _z(z)
{
}

Vector::Vector(const Vector& other)
   : _x(other._x),
     _y(other._y),
     _z(other._z)
{
}

Vector
Vector::operator+(const Vector& other) const
{
   return Vector(_x + other._x, _y + other._y, _z + other._z);
}

Vector
Vector::operator-(const Vector& other) const
{
   return Vector(_x - other._x, _y - other._y, _z - other._z);
}

Vector
Vector::operator=(const Vector& other) const
{
   return Vector(other._x, other._y, other._z);
}

bool
Vector::operator==(const Vector& other) const
{
   if (this == &other) return true;

   return _x == other._x && _y == other._y && _z == other._z;
}

Vector&
Vector::operator+=(const Vector& other)
{
   _x += other._x;
   _y += other._y;
   _z += other._z;

   return *this;
}

Vector&
Vector::operator-=(const Vector& other)
{
   _x -= other._x;
   _y -= other._y;
   _z -= other._z;

   return *this;
}

std::ostream&
operator<<(std::ostream& os, const Vector& v)
{
   os << "( " << v._x << ", " << v._y << ", " << v._z << " )";
   return os;
}

```
TestMain.cpp:
```

#include "Vector.h"
#include <iostream>

int main()
{
   Vector v1(5,6,7);
   Vector v2(1,2,3);

   Vector v3 = v1 - v2;
   Vector v4 = v2 + v3;

   std::cout << "v1 = " << v1 << std::endl;
   std::cout << "v2 = " << v2 << std::endl;
   std::cout << "v3 = " << v3 << std::endl;
   std::cout << "v4 = " << v4 << std::endl;
   std::cout << "v1 == v4? " << (v1 == v4 ? "true" : "false") << std::endl;
   std::cout << "v2 == v3? " << (v2 == v3 ? "true" : "false") << std::endl;

   Vector v5 = (v1 += v2);

   std::cout << "v1 = " << v1 << std::endl;
   std::cout << "v5 = " << v5 << std::endl;
   std::cout << "v1 == v5? " << (v1 == v5 ? "true" : "false") << std::endl;
}

```

---

