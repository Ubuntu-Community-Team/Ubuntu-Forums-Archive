---
title: "Declaring a global array, and give the size later when assigning values?"
date: 2008-11-12
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-12
Title says it all. How?

Edit: In C, of course. Forgot.

---

### Post by dwhitney67 on 2008-11-12
For example:

Main.c:
[php]
#include <stdlib.h>
#include <stdio.h>

extern void function();

// global variable declaration
int* array = 0;

int main()
{
  const size_t num_items = 10;

  // global variable initialization
  array = malloc(sizeof(int) * num_items);
  
  function();

  printf("array[5] = %d\n", array[5]);

  free(array);

  return 0;
}
[/php]

Other.c:
[php]
extern int* array;

void function()
{
  array[5] = 10;
}
[/php]

P.S.  It is an accepted belief (almost fact) that using global variables leads to poor programming technique and to bad software designs.  If you must use a global variable, ensure that it is declared static, and thus only accessible within the module in which it is defined.  Avoid defining global variables within header files.

For example, the following header file provides the basic interface for a queue:

Queue.h:
[php]
#ifndef QUEUE_H
#define QUEUE_H

#include <unistd.h>
#include <stdbool.h>

typedef int Q_DATA_TYPE;

void        init_queue(const size_t q_depth);
void        destroy_queue();

void        insert_item(const Q_DATA_TYPE item);
Q_DATA_TYPE pop_item();

bool        is_empty();

#endif
[/php]

With this interface, a program can employ the use of a queue.  If this queue is needed by more than one function, then the queue object should be passed around as a function-parameter; not declared global.  Back to the header file above, note that there are no global variables defined.  The variables will be defined (as static), but only within the implementation file of queue.c.

---

### Post by crazyfuturamanoob on 2008-11-12
> **dwhitney67 said:**
> For example:

Main.c:
[php]
#include <stdlib.h>
#include <stdio.h>

extern void function();

// global variable declaration
int* array = 0;

int main()
{
  const size_t num_items = 10;

  // global variable initialization
  array = malloc(sizeof(int) * num_items);
  
  function();

  printf("array[5] = %d\n", array[5]);

  free(array);

  return 0;
}
[/php]

Other.c:
[php]
extern int* array;

void function()
{
  array[5] = 10;
}
[/php]

Is that other.c really needed? Can't I just use **array[5] = 10;** inside my main program?

---

### Post by dwhitney67 on 2008-11-12
> **crazyfuturamanoob said:**
> Is that other.c really needed? Can't I just use **array[5] = 10;** inside my main program?
You could, but then what is the point of having a global variable?

---

### Post by crazyfuturamanoob on 2008-11-12
> **dwhitney67 said:**
> You could, but then what is the point of having a global variable?

I am coding an SDL/OpenGL graphics library for my upcoming game, which can do a lot useful things, including texture loading.

Here is how the library works:
```
[color=#408080][i]/* now, when importing
graphics.c, one of the first lines declares 
GLuint array "texture", but doesn't declare it's size. 

also, a linked list for filenames is declared */[/i][/color]
[color=#BC7A00]#include "graphics.c"
[/color]
[color=#408080]*/* init opengl */*[/color]
initGL();

[color=#408080][i]/* now, this function adds string to the filename list 
and returns the texture index, which is saved in a & b */[/i][/color]
[color=#B00040]int[/color] a [color=#666666]=[/color] addTexture( [color=#BA2121]"data/file.bmp"[/color] );
[color=#B00040]int[/color] b [color=#666666]=[/color] addTexture( [color=#BA2121]"data/file2.png"[/color] );

[color=#408080][i]/* this function gives the texture array a size, which is
the amount of strings in the filename array. 

it also calls glGenTextures(amountOfFiles, &texture) 

finally, it loads textures and saves them in that array */[/i][/color]
LoadTextures();

[color=#408080][i]/* now it is easy to switch between textures, when
we got them loaded & created in texture, and again,
a & b are the indexes of textures. with these indexes,
we can find the correct textures from the list */[/i][/color]
glBindTexture(GL_TEXTURE_2D, texture[a]);

```


glGenTextures is the reason, why I need to do this.

---

### Post by crazyfuturamanoob on 2008-11-12
Damn, glGenTextures accepts only real GLuint arrays, not mallocated things.

How to make it a real array? A real, global array, that glGenTextures could use?

---

### Post by Tony Flury on 2008-11-12
Can you post the quote or site link from where you get the idea that 
> 
Damm, glGenTextures accepts only GLuint arrays not mallocated things.


In C once you have the space malloced, there is no difference between a "real" array, and a malloced array.

A code library should be unable to tell the difference - unless it makes some significant (and probably dangerous) assumptions of where memory might be getting allocated.

After all when you pass an array to a library function, what you actually pass is a pointer to a block of memory.

All you need to do is ensure that you allocate the memory in the same way - so take care if it is a mult dimensional array.

---

### Post by crazyfuturamanoob on 2008-11-12
Perhaps you might be able to fix this? Just scroll down and see LoadTextures() function. That's what makes the error.
I also got another file, main.c, which includes everything needed and initializes a window, does some other stuff, but it doesn't make errors.
```
[color=#408080]*/* initialize a linked list for texture filenames to load */*[/color]
[color=#008000]**struct**[/color] string
{
    [color=#008000]**struct**[/color] string [color=#666666]*[/color]next;
    [color=#B00040]int[/color] index;
    [color=#B00040]char[/color] [color=#666666]*[/color]chars;
};
[color=#008000]**struct**[/color] filelist
{
    [color=#008000]**struct**[/color] string [color=#666666]*[/color]filenames;
};
[color=#008000]**struct**[/color] filelist [color=#666666]*[/color]textures_to_load;
[color=#B00040]int[/color] num_textures2load [color=#666666]=[/color] [color=#666666]0[/color];

[color=#408080]*/* now some functions to edit the linked list */*[/color]
[color=#008000]**struct**[/color] string [color=#666666]*[/color][color=#0000FF]create_string[/color]( [color=#B00040]char[/color] stuff[] )
{
    [color=#008000]**struct**[/color] string [color=#666666]*[/color]str;
    str [color=#666666]=[/color] malloc( [color=#008000]**sizeof**[/color]([color=#008000]**struct**[/color] string) );
    
    [color=#008000]**if**[/color] (str [color=#666666]==[/color] [color=#008000]NULL[/color])
        [color=#008000]**return**[/color] [color=#008000]NULL[/color];
    
    memset( str, [color=#666666]0[/color], [color=#008000]**sizeof**[/color]([color=#008000]**struct**[/color] string) );
    
    str[color=#666666]->[/color]chars [color=#666666]=[/color] ([color=#B00040]char[/color] [color=#666666]*[/color]) stuff;
    
    [color=#008000]**static**[/color] [color=#B00040]int[/color] index [color=#666666]=[/color] [color=#666666]0[/color];
    str[color=#666666]->[/color]index [color=#666666]=[/color] index;
    index [color=#666666]+=[/color] [color=#666666]1[/color];
    
    [color=#008000]**return**[/color] str;
}

[color=#B00040]void[/color] [color=#0000FF]link_string[/color]( [color=#008000]**struct**[/color] string [color=#666666]*[/color]str )
{
    str[color=#666666]->[/color]next [color=#666666]=[/color] textures_to_load[color=#666666]->[/color]filenames;
    textures_to_load[color=#666666]->[/color]filenames [color=#666666]=[/color] str;
}

[color=#408080]*/* this function adds texture to the list of textures to load */*[/color]
[color=#B00040]int[/color] [color=#0000FF]add_texture[/color]( [color=#B00040]char[/color] filename[] )
{
    [color=#008000]**struct**[/color] string [color=#666666]*[/color]str [color=#666666]=[/color] create_string( filename );
    link_string( str );
    
    num_textures2load [color=#666666]+=[/color] [color=#666666]1[/color];
    
    [color=#008000]**return**[/color] str[color=#666666]->[/color]index;
}

[color=#408080]*/****************************************************************************/*[/color]

[color=#408080]*/* This is our SDL surface */*[/color]
SDL_Surface [color=#666666]*[/color]surface;

GLuint[color=#666666]*[/color] texture [color=#666666]=[/color] [color=#666666]0[/color];

[color=#408080]*/* general OpenGL initialization function */*[/color]
[color=#B00040]int[/color] [color=#0000FF]initGL[/color]( GLvoid )
{
    [color=#408080]*/* Enable Texture Mapping ( NEW ) */*[/color]
    glTexEnvi( GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE );
    glEnable( GL_TEXTURE_2D );

    [color=#408080]*/* Enable smooth shading, you can see this when using lightning */*[/color]
    glShadeModel( GL_SMOOTH );

    [color=#408080]*/* Set the background black */*[/color]
    glClearColor( [color=#666666]0.0f[/color], [color=#666666]0.0f[/color], [color=#666666]0.0f[/color], [color=#666666]0.0f[/color] );

    [color=#408080]*/* Depth buffer setup */*[/color]
    [color=#408080]*/* glClearDepth( 1.0f ); */*[/color]

    [color=#408080]*/* Disables Depth Testing, this is 2D */*[/color]
    glDisable( GL_DEPTH_TEST );

    [color=#408080]*/* The Type Of Depth Test To Do */*[/color]
    [color=#408080]*/* glDepthFunc( GL_LEQUAL ); */*[/color]

    [color=#408080]*/* Really Nice Perspective Calculations */*[/color]
    [color=#408080]*/* glHint( GL_PERSPECTIVE_CORRECTION_HINT, GL_NICEST ); */*[/color]
    
    [color=#408080]*/* enable blending */*[/color]
    glEnable( GL_BLEND );
    glBlendFunc( GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA );
    
    [color=#408080]*/* enable alpha transparency */*[/color]
    glEnable( GL_ALPHA_TEST );
    glAlphaFunc( GL_NOTEQUAL, [color=#666666]0.0f[/color] );
    
    [color=#408080]*/* init list of tex filenames to load */*[/color]
    textures_to_load [color=#666666]=[/color] malloc( [color=#008000]**sizeof**[/color]([color=#008000]**struct**[/color] filelist) );
    textures_to_load[color=#666666]->[/color]filenames [color=#666666]=[/color] [color=#008000]NULL[/color];
    
    glDisable( GL_TEXTURE_2D );
    
    [color=#008000]**return**[/color]( TRUE );
}


[color=#408080]*/* function to reset our viewport after a window resize */*[/color]
[color=#B00040]int[/color] [color=#0000FF]resizeWindow[/color]( [color=#B00040]int[/color] width, [color=#B00040]int[/color] height )
{
    [color=#408080]*/* Protect against a divide by zero */*[/color]
    [color=#008000]**if**[/color] ( height [color=#666666]==[/color] [color=#666666]0[/color] )
	height [color=#666666]=[/color] [color=#666666]1[/color];

    [color=#408080]*/* Setup our viewport. */*[/color]
    glViewport( [color=#666666]0[/color], [color=#666666]0[/color], ( GLint )width, ( GLint )height );

    [color=#408080][i]/*
     * change to the projection matrix and set
     * our viewing volume.
     */[/i][/color]
    glMatrixMode( GL_PROJECTION );
    glLoadIdentity( );

    [color=#408080]*/* Set our perspective */*[/color]
    gluOrtho2D([color=#666666]0[/color], width, height, [color=#666666]0[/color]);

    [color=#408080]*/* Make sure we're chaning the model view and not the projection */*[/color]
    glMatrixMode( GL_MODELVIEW );

    [color=#408080]*/* Reset The View */*[/color]
    glLoadIdentity( );

    [color=#008000]**return**[/color]( TRUE );
}

[color=#B00040]void[/color] [color=#0000FF]LoadTextures[/color]( )
{
    [color=#408080]*/* num_textures2load is an integer, which indicates the amount of textures added */*[/color]
    
    [color=#408080]*/** initialize the real list **/*[/color]
    texture [color=#666666]=[/color] malloc( [color=#008000]**sizeof**[/color](GLuint) [color=#666666]*[/color] num_textures2load );
    
    [color=#408080]*/* debugging help */*[/color]
    printf([color=#BA2121]"all good for now[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    
    [color=#408080]*/** generate the textures **/*[/color]
    glGenTextures( num_textures2load, (GLuint [color=#666666]*[/color]) [color=#666666]&[/color]texture );
    
    [color=#408080]*/* storage for each image file */*[/color]
    SDL_Surface [color=#666666]*[/color]TexImg;
    
    [color=#008000]**struct**[/color] string [color=#666666]*[/color]str;
    [color=#008000]**for**[/color] (str [color=#666666]=[/color] textures_to_load[color=#666666]->[/color]filenames; str; str [color=#666666]=[/color] str[color=#666666]->[/color]next)
    {
        [color=#408080]*/** printf("Texture %i filename: %s\n", str->index, str->chars); **/*[/color]
        
        [color=#408080]*/* load the current image */*[/color]
        TexImg [color=#666666]=[/color] IMG_Load(str[color=#666666]->[/color]chars);
        
        [color=#408080]*/* color format of image */*[/color]
        GLenum SourceFormat[color=#666666]=[/color]GL_BGR; [color=#408080]*/* GL_RGB */*[/color]
        [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]flags[color=#666666]&[/color]SDL_SRCALPHA)
                SourceFormat[color=#666666]=[/color]GL_RGBA;
        [color=#008000]**else**[/color] [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BitsPerPixel[color=#666666]==[/color][color=#666666]8[/color])
                SourceFormat[color=#666666]=[/color]GL_COLOR_INDEX;
        
        [color=#408080]*/* select the correct texture slot */*[/color]
        glBindTexture( GL_TEXTURE_2D, texture[ str[color=#666666]->[/color]index ] );
        
        [color=#408080]*/* Generate The Texture */*[/color]
        glTexImage2D( GL_TEXTURE_2D, [color=#666666]0[/color], TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BytesPerPixel,
            TexImg[color=#666666]->[/color]w, TexImg[color=#666666]->[/color]h, [color=#666666]0[/color], SourceFormat, GL_UNSIGNED_BYTE, TexImg[color=#666666]->[/color]pixels );
        
        [color=#408080]*/* Linear Filtering */*[/color]
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    }
    
    SDL_FreeSurface( TexImg );
    
}

```
I don't think anyone will even read that code, but there's always hope. :)

And when I try to compile it, I get *Segmentation Fault* right after "all good for now".

Edit:

To save you from a lot reading, here's the place where I declare the "array":
> GLuint* texture = 0;
Perhaps that's the place where it goes wrong?

Or then it's the LoadTextures function. I put it here too, although it is already there above.
```
[color=#B00040]void[/color] [color=#0000FF]LoadTextures[/color]( )
{
    [color=#408080]*/* num_textures2load is an integer, which indicates the amount of textures added */*[/color]
    
    [color=#408080]*/** initialize the real list **/*[/color]
    texture [color=#666666]=[/color] malloc( [color=#008000]**sizeof**[/color](GLuint) [color=#666666]*[/color] num_textures2load );
    
    [color=#408080]*/* debugging help */*[/color]
    printf([color=#BA2121]"all good for now[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    
    [color=#408080]*/** generate the textures **/*[/color]
    glGenTextures( num_textures2load, (GLuint [color=#666666]*[/color]) [color=#666666]&[/color]texture );
    
    [color=#408080]*/* storage for each image file */*[/color]
    SDL_Surface [color=#666666]*[/color]TexImg;
    
    [color=#008000]**struct**[/color] string [color=#666666]*[/color]str;
    [color=#008000]**for**[/color] (str [color=#666666]=[/color] textures_to_load[color=#666666]->[/color]filenames; str; str [color=#666666]=[/color] str[color=#666666]->[/color]next)
    {
        [color=#408080]*/** printf("Texture %i filename: %s\n", str->index, str->chars); **/*[/color]
        
        [color=#408080]*/* load the current image */*[/color]
        TexImg [color=#666666]=[/color] IMG_Load(str[color=#666666]->[/color]chars);
        
        [color=#408080]*/* color format of image */*[/color]
        GLenum SourceFormat[color=#666666]=[/color]GL_BGR; [color=#408080]*/* GL_RGB */*[/color]
        [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]flags[color=#666666]&[/color]SDL_SRCALPHA)
                SourceFormat[color=#666666]=[/color]GL_RGBA;
        [color=#008000]**else**[/color] [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BitsPerPixel[color=#666666]==[/color][color=#666666]8[/color])
                SourceFormat[color=#666666]=[/color]GL_COLOR_INDEX;
        
        [color=#408080]*/* select the correct texture slot */*[/color]
        glBindTexture( GL_TEXTURE_2D, texture[ str[color=#666666]->[/color]index ] );
        
        [color=#408080]*/* Generate The Texture */*[/color]
        glTexImage2D( GL_TEXTURE_2D, [color=#666666]0[/color], TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BytesPerPixel,
            TexImg[color=#666666]->[/color]w, TexImg[color=#666666]->[/color]h, [color=#666666]0[/color], SourceFormat, GL_UNSIGNED_BYTE, TexImg[color=#666666]->[/color]pixels );
        
        [color=#408080]*/* Linear Filtering */*[/color]
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    }
    
    SDL_FreeSurface( TexImg );
    
}

```

---

### Post by Tony Flury on 2008-11-12
What error do you get ?

is a compiler or a run time error ?

---

### Post by crazyfuturamanoob on 2008-11-12
> **Tony Flury said:**
> What error do you get ?

is a compiler or a run time error ?

Hard to say, Segmentation Fault. Doesn't anyhow relate to my compiler, it's the code which makes the error.

---

### Post by Tony Flury on 2008-11-12
Have you tried to use gdb to debug the code - step through it one line at a time in order to find where it actually fails.

One thing though

```

GLuint* texture = 0;
.....
.....
.....
    texture = malloc( sizeof(GLuint) * num_textures2load );
    
    /* debugging help */
    printf("all good for now\n");
    
    /** generate the textures **/
    glGenTextures( num_textures2load, (GLuint *) &texture );

```

in the first few lines above - texture already is of type (GLuint *) - so on the last line, you don't need to cast it - and you don't need the &

I think that line should probably be : 
```

    glGenTextures( num_textures2load, texture );

```

try that -

---

### Post by crazyfuturamanoob on 2008-11-12
> **Tony Flury said:**
> Have you tried to use gdb to debug the code - step through it one line at a time in order to find where it actually fails.

One thing though

```

GLuint* texture = 0;
.....
.....
.....
    texture = malloc( sizeof(GLuint) * num_textures2load );
    
    /* debugging help */
    printf("all good for now\n");
    
    /** generate the textures **/
    glGenTextures( num_textures2load, (GLuint *) &texture );

```

in the first few lines above - texture already is of type (GLuint *) - so on the last line, you don't need to cast it - and you don't need the &

I think that line should probably be : 
```

    glGenTextures( num_textures2load, texture );

```

try that -

No, doesn't work. Still same *Segmentation Fault* right after *"all good for now"*.

Tried gdb, and found it way too complicated for me. I never used debuggers, I always fixed the bugs by hand.

---

### Post by dwhitney67 on 2008-11-12
> **crazyfuturamanoob said:**
> I am coding an SDL/OpenGL graphics library for my upcoming game, which can do a lot useful things, including texture loading.

Would it not be prudent to start off writing smaller applications so that you fully understand the C language before branching into something complicated (e.g. a game).

I've look further down at your other post, and I question the need for the "string" structure.

As for the rest of your code, it is a pain in the rear to read because you have enclosed it in those ridiculous color-coding tags.

It seems to me that you need to provide the openGL library function a list of filenames that represent textures.  Thus why are you not declaring a local array of strings in your main() function?

For example, would the following suffice and hence be easier?  (Btw, I do not know/use openGL, but its interface, as from what you have shown, seems pretty straighforward.)
[php]
int main()
{
  char* textures[] = { "filename1.bmp",
                       "file2.png",
                       "F3.png"
                     };

  const size_t numTextures = sizeof(textures) / sizeof(char*);

  for (int i = 0; i < numTextures; ++i)
  {     
    /* load the current image */
    SDL_Surface* texImg = IMG_Load(textures[i]);
        
    /* color format of image */
    GLenum sourceFormat = GL_RGB;   /* initially assume GL_RGB */

    if (texImg->flags &S DL_SRCALPHA)
    {
      sourceFormat = GL_RGBA;
    }
    else if (texImg->format->BitsPerPixel == 8)
    {
      sourceFormat = GL_COLOR_INDEX;
    }

    /* select the correct texture slot */
    glBindTexture( GL_TEXTURE_2D, i );
        
    /* Generate The Texture */
    glTexImage2D( GL_TEXTURE_2D, 0, texImg->format->BytesPerPixel,
                  texImg->w, texImg->h, 0, sourceFormat,
                  GL_UNSIGNED_BYTE, texImg->pixels );
        
    /* Linear Filtering */
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    
    SDL_FreeSurface( texImg );
  }
}
[/php]

---

### Post by Tony Flury on 2008-11-12
Well I can guarantee you that the error you are getting is nothing to do with the library rejecting malloced data in favour of an array.

did you put any other debug lines in your application. So far you know that you get to "all good for now" - how do you know if you get any point past that ?

Also if you are going to develop complex programs i would strongly suggest that you learn gdb - it is not that complicated.

---

### Post by crazyfuturamanoob on 2008-11-12
I was using that linked list thing for list of strings, because I didn't know it is possible to make a char list having invidual strings.

And there is a HUGE problem with dwhitney67 example code about the function. 

glGenTextures gets an empty memory slot from video memory, with given name. 

And because every loop time it gets an empty texture slot with same name,
all texture data will be filled with the last loaded texture. That how all
textures look same than the last loaded, which means you can load only ONE
texture at a time. And that's ridiculous! Only one texture, the game would suck.

---

### Post by dwhitney67 on 2008-11-12
> **crazyfuturamanoob said:**
> I was using that linked list thing for list of strings, because I didn't know it is possible to make a char list having invidual strings.

And there is a HUGE problem with dwhitney67 example code about the function. 

glGenTextures gets an empty memory slot from video memory, with given name. 

And because every loop time it gets an empty texture slot with same name,
all texture data will be filled with the last loaded texture. That how all
textures look same than the last loaded, which means you can load only ONE
texture at a time. And that's ridiculous! Only one texture, the game would suck.
Like I stated earlier, I do not know openGL (nor care to at this time).  If the openGL library function can handle an array of strings, then give it the entire array at one time.

I did not get the impression that is what you were doing in your code, hence the rationale for the code I presented.

---

### Post by crazyfuturamanoob on 2008-11-12
But actually the whole problem is about glGenTextures().

...

Whatever... I'll try to make up a workaround for it.

---

### Post by dwhitney67 on 2008-11-12
> **crazyfuturamanoob said:**
> But actually the whole problem is about glGenTextures().

...

Whatever... I'll try to make up a workaround for it.
Surprise, surprise... I actually have the manpage for glGenTextures() on my system.  However it is written poorly; there is no indication of what header file(s) or library I must link in to use it.  There also isn't a specification as to what GLsizei nor GLuint represents.

I will assume GLsizei represents a size_t, and GLuint represents an unsigned int.

The interface is specified as:
[php]
       void glGenTextures( GLsizei n,
                           GLuint *textures )
[/php]

Maybe something like the following will suffice:
[php]
...

int main()
{
  GLsizei num_textures = 10;
  GLuint  textures[10];

  ...

  glGenTextures(num_textures, textures);

  ...
}
[/php]

---

### Post by Tony Flury on 2008-11-12
When you do the malloc call what return value are you getting ?

you code is assuming that the malloc is working, and it actually might not be.

you should always follow a malloc with 

```

if pointer == NULL 
{
<error handling code>
}

```

---

