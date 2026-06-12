---
title: "There must be an easy(ier) way..."
date: 2009-01-02
forum: Programming Talk
---

### Post by eckertd on 2009-01-02
Greetings all.

I've been wokring on a DIY data acquisition project for my 1967 Mustang. Using a [[color="red"]USB BitWhacker[/color]]("http://www.sparkfun.com/commerce/product_info.php?products_id=762") and a simple binary counter circuit (with reset), I'm counting "pulses" from an MSD-6AL ignition module's tach output port. Knowing that there are 4 spark events (pulses at the tach output) per revolution, RPM between 250ms polls is determined and logged to CSV file.  I plan on adding other sensor data (exhaust gas temp, driveshaft RPM, AFR, etc) eventually, but sticking with engine RPM for now.

To make things a bit "spiffier" I'd like to animate a tachometer on the screen. This is my first foray into OpenGL/SDL programming, and I've hit a bit of a snag.  I'm able to create a surface from a BMP file of the tach face, and plot points from 0 to 9000 rpm.  However, this isn't "real" animation. I'd really like to have a pointer/triangle rotate back & forth with vertex at the points I'm computing without altering the tach face image itself.

I've been playing a bit with GLUT, though my C++ skills are worse than my C, and most of the GL/SDL stuff is from online tutorials.

Any hints/tips/suggestions on how to proceed?  Thanks!

--Doug

Source is below and the tach BMP file is here:

[COLOR="Red"]http://mysite (dot) verizon (dot) net/dougeckert/files/tach.bmp[/COLOR]

tach.c (compile with -lGL -lSDL)

```

#include <stdlib.h>
#include <stdio.h>
#include <math.h>	// math libraries needed for sin & cos
#include <SDL/SDL.h>	// SLD library
#include <GL/gl.h>  	// OpenGL library
#include <GL/glu.h> 	// OpenGL Utilities (GLU)
#include <GL/glut.h> 	// OpenGL Utilities (GLUT)

#define ZERO_RPM	(208)
#define NINEK_RPM	(293)
#define TACHX		(160)
#define TACHY		(160)
#define NEEDLE		(100)

struct gridxy{
	int grid_x;
	int grid_y;
};

struct gridxy getpos(int);

//-----------------------------------------------------------------------

void ShowBMP(SDL_Surface *image,SDL_Surface *screen, int x, int y)
{
    SDL_Rect dest;

    /* Blit onto the screen surface.
       The surfaces should not be locked at this point.
     */
    dest.x = x;
    dest.y = y;
    dest.w = image->w;
    dest.h = image->h;
    SDL_BlitSurface(image, NULL, screen, &dest);

    /* Update the changed portion of the screen */
    SDL_UpdateRects(screen, 1, &dest);
}

//-----------------------------------------------------------------------

struct gridxy getpos(int rpm) {

  struct gridxy	position;
  float		d_deg, new_x, new_y, new_deg, rads;
  float		deg_per_rpm = 32.73;
  float		c28=28.0,
		c118=118.0,
		c208=208.0,
		c275=275.0;

  d_deg = (rpm/deg_per_rpm);

  if ( *(int*)&d_deg < *(int*)&c28 ) {
    new_deg = ZERO_RPM - d_deg - 180;
    rads = M_PI*new_deg/180;
    new_x = (160-(NEEDLE*cos(rads)));
    new_y = (160+(NEEDLE*sin(rads)));
  }
  else if ( *(int*)&d_deg == *(int*)&c28 ) {
    new_x = 160-NEEDLE;
    new_y = 0;
  }
  else if ( *(int*)&d_deg < *(int*)&c118 ) {
    new_deg = 180 - (ZERO_RPM - d_deg);
    rads = M_PI*new_deg/180;
    new_x = (160-(NEEDLE*cos(rads)));
    new_y = (160-(NEEDLE*sin(rads)));
  }
  else if ( *(int*)&d_deg == *(int*)&c118 ) {
    new_x = 0;
    new_y = 160-NEEDLE;
  }
  else if ( *(int*)&d_deg < *(int*)&c208 ) {
    new_deg = ZERO_RPM - d_deg;
    rads = M_PI*new_deg/180;
    new_x = (160+(NEEDLE*cos(rads)));
    new_y = (160-(NEEDLE*sin(rads)));
  }
  else if ( *(int*)&d_deg == *(int*)&c208 ) {
    new_x = 160+NEEDLE;
    new_y = 0;
  }
  else if ( *(int*)&d_deg < *(int*)&c275 ) {
    new_deg = d_deg - ZERO_RPM;
    rads = M_PI*new_deg/180;
    new_x = (160+(NEEDLE*cos(rads)));
    new_y = (160+(NEEDLE*sin(rads)));
  }
  else {
    new_x=0;
    new_y=0;
  }
  position.grid_x=roundf(new_x);
  position.grid_y=roundf(new_y);
  return(position);
    
}

//-----------------------------------------------------------------------

void setpixel(SDL_Surface *screen, int x, int y, Uint8 r, Uint8 g, Uint8 b)
{
    Uint32 *pixmem32;
    Uint32 colour;  
 
    colour = SDL_MapRGB( screen->format, r, g, b );
  
    pixmem32 = (Uint32*) screen->pixels  + y + x;
    *pixmem32 = colour;
}

//-----------------------------------------------------------------------

int main(void) {
  
  int rpm;
  int x=0, y=0;
  struct gridxy	position;
  int options = ( SDL_ANYFORMAT | SDL_SWSURFACE );
  SDL_Surface *image = NULL;
  SDL_Surface *screen = NULL;

  // Initialize SDL Video
  if ( SDL_Init(SDL_INIT_VIDEO) < 0 ) {
    fprintf(stderr, "Unable to init SDL: %s\n", SDL_GetError());
    exit(1);
  }

  // Define a surface/screen to draw on
  screen = SDL_SetVideoMode(320, 320, 32, options);
  if (NULL == screen) {
    printf("Can't set video mode");
    exit(1);
  }

  // Load the bitmap file
  image = SDL_LoadBMP("tach.bmp");
  if ( image == NULL ) {
      fprintf(stderr, "Couldn't load image: %s\n", SDL_GetError());
      return;
  }

  // Load the Bitmap image to the surface
  ShowBMP(image,screen,0,0);

  // Get needle tip coordinates for RPM 0 to 9000 in 10 RPM increments
  rpm = 0;

  while(rpm <= 9000) {
    position = getpos(rpm);
    printf("%d\t%d\n",position.grid_x,position.grid_y);
    setpixel(screen,position.grid_x,(position.grid_y*320),0,0,255);
    rpm = rpm + 10;
    if(SDL_MUSTLOCK(screen)) {
          if(SDL_LockSurface(screen) < 0) return;
    }
    if(SDL_MUSTLOCK(screen)) SDL_UnlockSurface(screen);
    SDL_Flip(screen);
//    ShowBMP(image,screen,0,0);
  }  /* end while */

  // printf("160\t160\n");  

  //atexit(SDL_Quit);
  sleep(30);
  SDL_Quit();

}

```

---

### Post by catchmeifyoutry on 2009-01-03
Well, start coding with OpenGL! Only thing to look up is how to combine SDL with OpenGL (I have no experience with SDL so I don't know).

Procedure should be simple, when refreshing the screen:
1) draw background image
2) calculate x,y location of meter
3) draw line from image center to x,y using OpenGL
4) swap buffer (== show result)

Alternatively, you could replace step 2+3 by letting OpenGL solve the rotation:
2) push a rotation matrix with appropriate rotation on the OpenGL modelview stack
3) draw a line, OR a more complicated polygon (will be rotated by modelview matrix, pop modelview stack afterwards to return original state).

OpenGL tutorials on basic transformations and primitive drawing are available on the web. [http://nehe.gamedev.net/](http://nehe.gamedev.net/) comes to mind, most tutorials are also available with code using SDL I believe.
If this is not what you wanted to hear, can you be a bit more specific on what your problem is?

---

### Post by eckertd on 2009-02-12
I've found some tutorials and have been experimenting with them.  I got the texture to load and even got the triangle/needle drawn in and rotating properly (using PgUp/PgDn for now - it'll be a shmseg read later).

What I'm stumped on now is why does the whole thing turn the same color as the triangle/needle? :confused: (link to the texture bitmap above)

```

#include <stdio.h>
#include <SDL/SDL.h>
#include <GL/gl.h>

GLfloat xspeed = 0.0f;
GLfloat yspeed = 0.0f;

GLfloat angle = -118.0f;
GLfloat rotationSpeed = 0.0f;

// the ID of the texture we're going to create
GLuint texture;

// =================================================================

int handleInput()
{
    SDL_Event event;
    while(SDL_PollEvent( &event ))
    {
	if( event.type == SDL_QUIT ) return 1;
	if( event.type == SDL_KEYDOWN )
	{
	    if( event.key.keysym.sym == SDLK_ESCAPE ) return 1;
	    if( event.key.keysym.sym == SDLK_PAGEUP ) rotationSpeed += 1.0f;
	    if( event.key.keysym.sym == SDLK_PAGEDOWN ) rotationSpeed -= 1.0f;
	}
    }
    
    return 0;
}

// =================================================================

void draw()
{
//  glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
      
    // Draw background with texture
    glPushMatrix();
    glTranslatef(0.0f, 0.0f, 0.0f );
    glBindTexture( GL_TEXTURE_2D, texture );
    glEnable( GL_TEXTURE_2D );
    glBegin(GL_QUADS);
      // upper-left corner of square and texture
      glTexCoord2f( 0.0f, 0.0f );
      glVertex3f( 0.0f, 0.0f, 0.0f );
      // upper-right corner
      glTexCoord2f( 1.0f, 0.0f );
      glVertex3f( 256.0f, 0.0f, 0.0f );
      // bottom-right corner
      glTexCoord2f( 1.0f, 1.0f );
      glVertex3f( 256.0f, 256.0f, 0.0f );
      // bottom-left corner
      glTexCoord2f( 0.0f, 1.0f );
      glVertex3f( 0.0f, 256.0f, 0.0f );
    glEnd();
    glDisable( GL_TEXTURE_2D );
    glPopMatrix();
  

    // draw the triangle
    glPushMatrix();
    glTranslatef( 128.0f, 128.0f, 1.0f );
    glRotatef(angle,0.0,0.0,1.0);
    glBegin(GL_TRIANGLES);
        glColor3f(1.0,0.0,0.0);
        glVertex3d( 000,-120,-001);
        glVertex3d(-004, 000,-001);
        glVertex3d( 004, 000,-001);
    glEnd();
    glPopMatrix();
    
    SDL_GL_SwapBuffers();
    
    angle += rotationSpeed;
    
  if( angle > 157.0f ) angle = 157.0f;
  if( angle < -118.0f ) angle = -118.0f;
    
} 

// =================================================================

int main()
{
    SDL_Init( SDL_INIT_VIDEO );
    
/*  SDL_GL_SetAttribute( SDL_GL_RED_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_GREEN_SIZE, 8 );
    SDL_GL_SetAttribute( SDL_GL_BLUE_SIZE, 8 );
    
    SDL_GL_SetAttribute( SDL_GL_DEPTH_SIZE, 8 ); */
    SDL_GL_SetAttribute( SDL_GL_DOUBLEBUFFER, 1 );
    
    SDL_Surface *screen;
    screen = SDL_SetVideoMode( 256, 256, 24, SDL_OPENGL | SDL_HWSURFACE );
    glViewport( 0, 0, 256, 256 );
    
    glMatrixMode( GL_MODELVIEW );
    glLoadIdentity();
    glOrtho( 0.0f, 256.0f, 256.0f, 0.0f, 0.0f, -2.0f );
    
    glClearColor( 0.0f, 0.0f, 0.0f, 0.0f );
    glClearDepth( 2.0f );
    glEnable( GL_DEPTH_TEST );
    glDepthFunc( GL_LEQUAL );
    
    // generate space for the texture and make it the current texture
    glGenTextures( 1, &texture );
    glBindTexture( GL_TEXTURE_2D, texture );
    
    // load the bitmap and lock the memory
    SDL_Surface *tex = SDL_LoadBMP( "tach256_24bpp.bmp" );
    SDL_LockSurface( tex );
    
    // create the texture from the bitmap
    glTexImage2D( GL_TEXTURE_2D, 0, 3, tex->w, tex->h, 0, GL_BGR, GL_UNSIGNED_BYTE, tex->pixels );
    
    // free up the bitmap memory
    SDL_UnlockSurface( tex );
    SDL_FreeSurface( tex );
    
    // draw it nicely
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
    
    while( handleInput() == 0 ) draw();
    
    SDL_Quit();
    return 0;
} //int main() 

```

---

