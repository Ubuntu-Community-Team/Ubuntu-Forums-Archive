---
title: "OpenGL Lighting getting translated with object"
date: 2008-03-30
forum: Programming Talk
---

### Post by mikeym on 2008-03-30
Hi,

I'm trying to write a little program for displaying mathematical shapes (nothing fancy just hard coded to display a certain shape). I can create my shapes in 3d with surfaces but I'm trying to light them. All I want is a fairly ambient light pointing at them from roughly the camera's direction so as to best get a sense of their shape.

For some reason when I rotate the object the light seems to rotate around with it. I can't figure how or why it's happening.

Anyway here's my code:

```

#include <stdlib.h>
#include <GL/gl.h>
#include <GL/glu.h>
#include <SDL/SDL.h>
#include "svl/SVL.h"
#include "svl/SVLgl.h"
#include "math.h"

#define PI 3.1415926535897932384626433832795 
#define SEGS 20
#define WIREFRAME 0

using namespace std;
 
// Width & Height of window
#define width  640
#define height 480

/* Ambient Light Values ( NEW ) */
GLfloat LightAmbient[]  = { 0.5f, 0.5f, 0.5f, 1.0f };
/* Diffuse Light Values ( NEW ) */
GLfloat LightDiffuse[]  = { 1.0f, 1.0f, 1.0f, 1.0f };
/* Light Position ( NEW ) */
GLfloat LightPosition[] = { 0.0f, 0.0f, 2.0f, 1.0f };

// Variable storing degree of rotation
float Angle = 0.0;
float x, y, z;
#define mMAXX SEGS
#define mMAXY SEGS
Vec3 vmatrix[mMAXX][mMAXY];
int mx, my;
 
// Kill program
void endProgram(int code) {SDL_Quit();    exit(code);}
 
// Handle SDL keypresses
void handleKeys(SDL_keysym* keysym, bool state) {
    switch(keysym->sym) {
        case SDLK_ESCAPE:    endProgram(0); break;
    }
}
 
// Process SDL events
void processEvents() {
    SDL_Event event;
    while(SDL_PollEvent(&event)) {
        switch(event.type) {
            case SDL_KEYDOWN:    handleKeys(&event.key.keysym, true ); break;
            case SDL_KEYUP  : handleKeys(&event.key.keysym, false);    break;
            case SDL_QUIT   : endProgram(0); break;
        }
    }
}

void CreateHyperbolic(double a, double b) {
	for(int i=0;i<mMAXY;i++) {
		y = 2*(float)i/mMAXY-1;
		for(int j=0;j<mMAXX;j++) {
			x = 2*(float)j/mMAXX-1;
			z = x*x/(a*a)-y*y/(b*b);
			vmatrix[j][i]= Vec3(x,y,z);
			printf("V%i%i(%f,%f,%f)\n", j, i, x, y, z);
		}
	}
}

void DrawHyperbolic() {
	//glPushMatrix();
    	glTranslatef(0, 0, -10);
	glRotatef(Angle, 1, 0, 1);

	for(int i=0;i<mMAXY;i++) {
		for(int j=0;j<mMAXX;j++) {
			if(WIREFRAME) {
				glBegin(GL_LINES);
				glColor3f(0,0,1);
				my = i + 1;
				//Only do the bottom line if we're more than one index from the end
				if (my < mMAXY ) {
					glVertex(vmatrix[j][i]);
					glVertex(vmatrix[j][my]);
				} 
				mx = j + 1;
				//Shape is a cloed shape so draw a line from the furthest right back to the start
				if (mx < mMAXX) {
					glVertex(vmatrix[j][i]);
					glVertex(vmatrix[mx][i]);
				} 
				glEnd();
			} else {
				glBegin(GL_QUADS);
				glColor3f(0,0,1);
				my = i + 1;
				mx = j + 1;
				//Only do the bottom line if we're more than one index from the end
				if (my < mMAXY && mx < mMAXX ) {
					glVertex(vmatrix[j][i]);
					glVertex(vmatrix[j][my]);
					glVertex(vmatrix[mx][my]);
					glVertex(vmatrix[mx][i]);
				} 
				glEnd();
			}
			/*glBegin(GL_POINTS);
			glColor3f(0,1,0);
			glVertex(vmatrix[j][i]);
			glEnd();*/
		}
	}
	//glPopMatrix();
}
 
void mainLoop() {
    while(true) {
	processEvents();
 
        glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT); // Clear color and depth buffer
        glLoadIdentity(); // Reset orientation
	
        // Graphical commands go here
	DrawHyperbolic();
 
        SDL_GL_SwapBuffers(); // Update screen
 
        // Increase degree of rotation to spin QUAD
        Angle+=0.5;
	SDL_Delay(1000/60);
    }
}
 
// Setup OpenGL perspective
void setupOpengl() {
	glViewport(0, 0, width, height);
	glMatrixMode(GL_PROJECTION);
	glEnable(GL_DEPTH_TEST);
	gluPerspective(45, (float)width/height, .1, 100);
	glMatrixMode(GL_MODELVIEW);
	glEnable ( GL_LIGHTING );

	/* Setup The Ambient Light */
	glLightfv( GL_LIGHT1, GL_AMBIENT, LightAmbient );

	/* Setup The Diffuse Light */
	glLightfv( GL_LIGHT1, GL_DIFFUSE, LightDiffuse );

	/* Position The Light */
	glLightfv( GL_LIGHT1, GL_POSITION, LightPosition );

	/* Enable Light One */
	glEnable( GL_LIGHT1 );
}
 
// Init everything
int main(int argc, char* argv[]) {
	CreateHyperbolic(1,1);
	SDL_Init(SDL_INIT_VIDEO);
	SDL_SetVideoMode(width, height, 24, SDL_OPENGL | SDL_GL_DOUBLEBUFFER);
	setupOpengl();
	mainLoop();
	return 0;
}

```

---

### Post by bmeyer on 2008-03-30
Why do you have glPushMatrix(); and glPopMatrix(); commented out?  Could be the reason -- pushing on the new matrix prior to rotating and translating is necessary...

---

### Post by WW on 2008-03-30
Looks like it will be a pretty cool program.  I can't help you with the OpenGL question--I did wonder about glPushMatrix and glPopMatrix, but I don't know enough about OpenGL to know if that is your problem. I'm just going to point out that math.h defines the the constant **M_PI** for you, so you don't have define PI yourself.

---

### Post by mikeym on 2008-03-30
Thanks again for your replies. I put the glPushMatrix and glPopMatrix in myself to try to find a way around this problem but they didn't make any difference so I commented tehm out.

---

### Post by DougB1958 on 2008-03-30
Several thoughts, I hope some help...

To your immediate question about the light source rotating: when you position a light source, it is transformed by the modelview matrix. Sometimes I find the implications of this rule totally incomprehensible, and other times totally obvious, depending on how recently I've written lighting code in OpenGL. Right now it's been a while, so I'm probably in "incomprehensible" mode -- be forewarned :) But in general, if you want a light source to appear to be in a fixed place in your scene, I think you want to position the light source after putting your viewing transformation into the modelview matrix, but before putting in any modeling transformations. In other words, after doing those glTranslate/glRotate/glScale calls that you think of as positioning the whole scene relative to the viewer, but before the calls that you think of as positioning individual objects within the scene. In your case, the glTranslatef in drawHyperbolic looks like it's there for viewing purposes, and the glRotatef might be (depending on whether you think of the geometric object turning in front of a fixed viewer, or of a viewer orbiting around the geometric object). My guess is that whether you position your light source before or after this glRotatef is the crucial thing in whether you get the effect you expect or not.

However, there's a second thing that puzzles me about your program: to get lighting effects in OpenGL, you need to associate reflection coefficients with vertices by calling one of the glMaterial functions. This replaces glColor. You also need to call a glNormal function to define a normal to each vertex. Since you aren't doing any of these things, I wouldn't expect your other lighting operations to have much effect (or at least not the effects you intend).

---

### Post by Wybiral on 2008-03-30
I haven't ran the code, but I'm willing to bet DougB1958 is correct. You need to position the light AFTER the transformations. Think of it as placing the light in the scene where it belongs (like a vertex), you want those transformations so that it doesn't appear to be "moving" with the scene.

---

