---
title: "Something went seriously wrong when loading OpenGL textures"
date: 2008-11-09
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-09
I wanted a function, which can load OpenGL texture into a variable with a single function call.

Started doing something and here's the result:
```
GLuint [color=#0000FF]LoadTexImG[/color]( [color=#B00040]char[/color] filename[] )
{
    [color=#408080]*/* Create storage space for the texture */*[/color]
    SDL_Surface [color=#666666]*[/color]TexImg; 
    GLuint texture;

    [color=#408080]*/* Load The Bitmap, Check For Errors, If Bitmap's Not Found Quit */*[/color]
    [color=#008000]**if**[/color] (  ( TexImg [color=#666666]=[/color] IMG_Load(filename) )  )
    {
        
        [color=#408080]*/* color format of image */*[/color]
        GLenum SourceFormat[color=#666666]=[/color]GL_BGR; [color=#408080]*/* GL_RGB */*[/color]
        [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]flags[color=#666666]&[/color]SDL_SRCALPHA)
                SourceFormat[color=#666666]=[/color]GL_RGBA;
        [color=#008000]**else**[/color] [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BitsPerPixel[color=#666666]==[/color][color=#666666]8[/color])
                SourceFormat[color=#666666]=[/color]GL_COLOR_INDEX;
        
        [color=#408080]*/* Create The Texture */*[/color]
        glGenTextures( [color=#666666]1[/color], [color=#666666]&[/color]texture );

        [color=#408080]*/* Typical Texture Generation Using Data From The Bitmap */*[/color]
        glBindTexture( GL_TEXTURE_2D, texture );

        [color=#408080]*/* Generate The Texture */*[/color]
        glTexImage2D( GL_TEXTURE_2D, [color=#666666]0[/color], TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BytesPerPixel, 
                      TexImg[color=#666666]->[/color]w, TexImg[color=#666666]->[/color]h, [color=#666666]0[/color], SourceFormat,
                      GL_UNSIGNED_BYTE, TexImg[color=#666666]->[/color]pixels );

        [color=#408080]*/* Linear Filtering */*[/color]
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
        
        [color=#408080][i]/*
        int width = TexImg->w;
        int height = TexImg->h;
        */[/i][/color]
    }
    [color=#008000]**else**[/color]
    {
        [color=#408080]*/* something went wrong when loading texture, report error message */*[/color]
        printf( [color=#BA2121]"Failed to load texture, reason: %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], IMG_GetError() );
    }

    [color=#408080]*/* Free up any memory we may have used */*[/color]
    [color=#008000]**if**[/color] ( TexImg )
	    SDL_FreeSurface( TexImg );
    
    [color=#008000]**return**[/color] texture;
}

```
As you can see, I use SDL and OpenGL. It can load almost every possible image format due to SDL_image, I tested bmp, tga and png.
Usage: *GLuint tex = LoadTexImG("data/texture.bmp");* and when using this texture: *glBindTexture(GL_TEXTURE_2D, tex);*

But if I call that function multiple times for different textures, all texture data will be replaced with the latest one loaded. What is the problem, how to fix it?


Thanks.

---

### Post by hessiess on 2008-11-09
I dont know OGL or SDL, but from your discription it sounds like you are
creating a block of memory with multiple pointers pointing to it, so when you load a new texture, it replaces the memory being pointed to, so all the pointers return the new texture.

---

### Post by slavik on 2008-11-09
I don't remember the specifics of glGenTextures, but that's where your problem lies. :) Please read the red book, you have to use a different index/id everytime you want a new piece of memory for the texture.

---

### Post by crazyfuturamanoob on 2008-11-10
> **slavik said:**
> I don't remember the specifics of glGenTextures, but that's where your problem lies. :) Please read the red book, you have to use a different index/id everytime you want a new piece of memory for the texture.

But why? That is a local variable, which gets out of scope when exiting function.

And it returns GLuint, which holds the texture, right?


Also, when digging glGenTextures from manuals, noticed there is this function too: glDeleteTextures()

Is it needed in the end of program, or will all the textures remain in my system's video memory until I reboot?

---

### Post by snikrot on 2008-11-10
I did something like you describe once. I posted the code below. Hope this might help. What you have to keep in mind though is that one your texture array is build, you either have to build it again, or everything is replaced by a single texture.

Pics.h
```

// Pics.h: interface for the CPics class.
//
//////////////////////////////////////////////////////////////////////

#if !defined(AFX_PICS_H__7DAFAB44_15D8_4023_B7CD_2C7495D67A9B__INCLUDED_)
#define AFX_PICS_H__7DAFAB44_15D8_4023_B7CD_2C7495D67A9B__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000

#include <windows.h>		// Header File For Windows
#include <stdio.h>			// Header File For Standard Input/Output
#include <stdlib.h>
#include <gl\gl.h>			// Header File For The OpenGL32 Library
#include <gl\glu.h>			// Header File For The GLu32 Library
#include <gl\glaux.h>		// Header File For The Glaux Library
#include "LoadFile.h"

class CPics  
{
private:
	GLuint *texture;			// Storage for textures after the textures have been initialized.
	int SizeT;					// Total size of the array
	AUX_RGBImageRec **TextureImage; //Array to temporarily hold the ImageRecords. This is used before initialization.

public:
	int AddPic(char *Filename);				   //Add a BitmapImage to the array TextureImage
	int LoadAll();							   //Load all pictures as textures into the texture array. After this you cannot add
											   //anything exept when you reload the whole array.
	GLuint GetPic(int Position);			   //Find the position of a texture in texture array based upon the position in the
											   //TextureImage array
	CPics();									   //Creation. When created there is room for 1 picture.
	virtual ~CPics();						   //Destroy. When destroyed the TextureImage array is emptied.

};

#endif // !defined(AFX_PICS_H__7DAFAB44_15D8_4023_B7CD_2C7495D67A9B__INCLUDED_)


```


Pics.cpp
```

// Pics.cpp: implementation of the CPics class.
//
//////////////////////////////////////////////////////////////////////

#include "stdafx.h"
#include "Pics.h"

//////////////////////////////////////////////////////////////////////
// Construction/Destruction
//////////////////////////////////////////////////////////////////////

//////////////////////////////////////////////////////////////////////
// Construction/Destruction
//////////////////////////////////////////////////////////////////////

CPics::CPics()
{
	CPics::SizeT=0;
	CPics::TextureImage = (AUX_RGBImageRec**) malloc(((CPics::SizeT)+1)*sizeof(AUX_RGBImageRec*));
	CPics::texture = (GLuint *) malloc(1*sizeof(GLuint));
}

CPics::~CPics()
{
	//if the picture array is destroyed, also destroy every picture in the textureimage array.
	for(int loop=(CPics::SizeT);loop>0; loop--)
	{
		if (TextureImage[loop-1])							// If Texture Exists
		{
			if (TextureImage[loop-1]->data)			// If Texture Image Exists
			{
				free(TextureImage[loop-1]->data);	// Free The Texture Image Memory
			}
			free(TextureImage[loop-1]);				// Free The Image Structure
		}
	}
}

//////////////////////////////////////////////////////////////////////
// Load all textures into a texture array
//////////////////////////////////////////////////////////////////////

int CPics::LoadAll()
{
	int Status=FALSE;

	//if there is any picture initialized build for all the pictures 3 textures with different filters.
	if((CPics::SizeT)>0)
	{
		Status=TRUE;

		CPics::texture = (GLuint *) realloc((CPics::texture),(CPics::SizeT)*1*(sizeof(GLuint)));
		glGenTextures(1* CPics::SizeT , CPics::texture);
		
		int loop=0;
		while((loop/1)<(CPics::SizeT))
		{
			// Create MipMapped Texture
			glBindTexture(GL_TEXTURE_2D, texture[loop+0]);
			glTexParameteri(GL_TEXTURE_2D,GL_TEXTURE_MAG_FILTER,GL_LINEAR_MIPMAP_LINEAR);
			glTexParameteri(GL_TEXTURE_2D,GL_TEXTURE_MIN_FILTER,GL_LINEAR_MIPMAP_NEAREST);

			glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP);
			glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP);

			gluBuild2DMipmaps(GL_TEXTURE_2D, 3, TextureImage[loop/1]->sizeX, TextureImage[loop/1]->sizeY, GL_RGB, GL_UNSIGNED_BYTE, TextureImage[loop/1]->data);

			loop = loop+1;
		}	
		
	}
	return Status;
}


//////////////////////////////////////////////////////////////////////
// Add a picture into a picture array
//////////////////////////////////////////////////////////////////////

int CPics::AddPic(char *Filename)
{
	int Pos;

	//if a picture has to be added make the TextureImage bigger so 1 picture can be added.
	CPics::TextureImage = (AUX_RGBImageRec**) realloc((CPics::TextureImage), ((CPics::SizeT)+1)*sizeof(AUX_RGBImageRec*));
	
	CLoadFile temp;
	//if the file of the picture exists, add 1 picture in the last position.
	if(CPics::TextureImage[(CPics::SizeT)]=temp.LoadBMP(Filename))
	{
		Pos=(CPics::SizeT);

		(CPics::SizeT)++;
	}
	//if the picture doesn't exists make the TextureImage 1 smaller so it's the old size again.
	else
	{
		CPics::TextureImage = (AUX_RGBImageRec**) realloc((CPics::TextureImage), (CPics::SizeT)*sizeof(AUX_RGBImageRec*));
		return -1;
	}
	//return the current position times 3 because all textures are loaded in three fold.
	return Pos*1;
}

//////////////////////////////////////////////////////////////////////
// Get a picture out of the loaded texture array
//////////////////////////////////////////////////////////////////////

GLuint CPics::GetPic(int Position)
{
	if((CPics::SizeT)>0)
	{
		return CPics::texture[Position];
	}
	return -1;
}

```



LoadFile.h
```

// LoadFile.h: interface for the CLoadFile class.
//
//////////////////////////////////////////////////////////////////////

#if !defined(AFX_LOADFILE_H__13B07015_9B8A_4716_AEAD_8DFB9E6E847A__INCLUDED_)
#define AFX_LOADFILE_H__13B07015_9B8A_4716_AEAD_8DFB9E6E847A__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000

#include <windows.h>
#include <stdio.h>
#include <gl\glaux.h>		// Header File For The Glaux Library

class CLoadFile  
{
public:
	CLoadFile();
	virtual ~CLoadFile();

	AUX_RGBImageRec * LoadBMP(char *Filename);
	void LoadRawFile(LPSTR strName, int nSize, BYTE *pHeightMap);

};

#endif // !defined(AFX_LOADFILE_H__13B07015_9B8A_4716_AEAD_8DFB9E6E847A__INCLUDED_)

```

Loadfile.cpp
```

// LoadFile.cpp: implementation of the CLoadFile class.
//
//////////////////////////////////////////////////////////////////////

#include "stdafx.h"
#include "LoadFile.h"

//////////////////////////////////////////////////////////////////////
// Construction/Destruction
//////////////////////////////////////////////////////////////////////

//////////////////////////////////////////////////////////////////////
// Construction/Destruction
//////////////////////////////////////////////////////////////////////

CLoadFile::CLoadFile()
{

}

CLoadFile::~CLoadFile()
{

}

AUX_RGBImageRec * CLoadFile::LoadBMP(char *Filename)				// Loads A Bitmap Image
{
	FILE *File=NULL;									// File Handle

	if (!Filename)										// Make Sure A Filename Was Given
	{
		return NULL;									// If Not Return NULL
	}

	File=fopen(Filename,"r");							// Check To See If The File Exists

	if (File)											// Does The File Exist?
	{
		fclose(File);									// Close The Handle
		return auxDIBImageLoad(Filename);				// Load The Bitmap And Return A Pointer
	}

	return NULL;										// If Load Failed Return NULL
}

void CLoadFile::LoadRawFile(LPSTR strName, int nSize, BYTE *pHeightMap)
{
	FILE *pFile = NULL;

	// Let's open the file in Read/Binary mode.
	pFile = fopen( strName, "rb" );

	// Check to see if we found the file and could open it
	if ( pFile == NULL )	
	{
		// Display our error message and stop the function
		MessageBox(NULL, "Can't find the height map!", "Error", MB_OK);
		return;
	}

	// Here we load the .raw file into our pHeightMap data array.
	// We are only reading in '1', and the size is the (width * height)
	fread( pHeightMap, 1, nSize, pFile );

	// After we read the data, it's a good idea to check if everything read fine.
	int result = ferror( pFile );

	// Check if we received an error.
	if (result)
	{
		MessageBox(NULL, "Can't get data!", "Error", MB_OK);
	}

	// Close the file.
	fclose(pFile);
}

```

---

### Post by slavik on 2008-11-10
> **crazyfuturamanoob said:**
> But why? That is a local variable, which gets out of scope when exiting function.

And it returns GLuint, which holds the texture, right?


Also, when digging glGenTextures from manuals, noticed there is this function too: glDeleteTextures()

Is it needed in the end of program, or will all the textures remain in my system's video memory until I reboot?
don't know about the deleting part. but the GLuint that is returned is an index, if you reuse the same index to store textures in, you will overwrite/lose whatever you had there. think of this as file descriptors ...

---

### Post by crazyfuturamanoob on 2008-11-10
snikrot has made the job already in C++, but how can I mix C and C++ in the same program?

BTW I'd also like to know how to use python & C together.

Edit: Oh wait, snikrot's libraries use windows.h so it is useless. Damn. :(



Edit2: Tried to fix it with structures, didn't work.
```
[color=#008000]**typedef**[/color] [color=#008000]**struct**[/color]
{
    GLuint data;
    [color=#B00040]int[/color] width, height;
} glTEX;

glTEX [color=#0000FF]LoadTexImG[/color]( [color=#B00040]char[/color] filename[] )
{
    [color=#408080]*/* Create storage space for the texture */*[/color]
    SDL_Surface [color=#666666]*[/color]TexImg; 
    glTEX texture;

    [color=#408080]*/* Load The Bitmap, Check For Errors, If Bitmap's Not Found Quit */*[/color]
    [color=#008000]**if**[/color] (  ( TexImg [color=#666666]=[/color] IMG_Load(filename) )  )
    {
        texture.width [color=#666666]=[/color] TexImg[color=#666666]->[/color]w;
        texture.height [color=#666666]=[/color] TexImg[color=#666666]->[/color]h;
        
        [color=#408080]*/* color format of image */*[/color]
        GLenum SourceFormat[color=#666666]=[/color]GL_BGR; [color=#408080]*/* GL_RGB */*[/color]
        [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]flags[color=#666666]&[/color]SDL_SRCALPHA)
                SourceFormat[color=#666666]=[/color]GL_RGBA;
        [color=#008000]**else**[/color] [color=#008000]**if**[/color] (TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BitsPerPixel[color=#666666]==[/color][color=#666666]8[/color])
                SourceFormat[color=#666666]=[/color]GL_COLOR_INDEX;
        
        [color=#408080]*/* Create The Texture */*[/color]
        glGenTextures( [color=#666666]1[/color], [color=#666666]&[/color]texture.data );

        [color=#408080]*/* Typical Texture Generation Using Data From The Bitmap */*[/color]
        glBindTexture( GL_TEXTURE_2D, texture.data );

        [color=#408080]*/* Generate The Texture */*[/color]
        glTexImage2D( GL_TEXTURE_2D, [color=#666666]0[/color], TexImg[color=#666666]->[/color]format[color=#666666]->[/color]BytesPerPixel, 
                      texture.width, texture.height, [color=#666666]0[/color], SourceFormat,
                      GL_UNSIGNED_BYTE, TexImg[color=#666666]->[/color]pixels );

        [color=#408080]*/* Linear Filtering */*[/color]
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR );
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR );
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
        
    }
    [color=#008000]**else**[/color]
    {
        [color=#408080]*/* something went wrong when loading texture, report error message */*[/color]
        printf( [color=#BA2121]"Failed to load texture, reason: %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], IMG_GetError() );
    }

    [color=#408080]*/* Free up any memory we may have used */*[/color]
    [color=#008000]**if**[/color] ( TexImg )
	    SDL_FreeSurface( TexImg );
    
    [color=#008000]**return**[/color] texture;
}

```
Same result. Crap.

I just realized what's the problem (at last, when the answer has been in this topic for a long time xD).

How to get different name for glGenTextures each time?

---

### Post by snikrot on 2008-11-10
The examples given below aren't just for windows. I programmed them in windows and just added (to be secure) windows.h everywhere.
If I'm right it should also work on Ubuntu.


Python I can't really help you with. (Never written python though I know a lot of other languages.)

Within C you'd probably want to add a static variable 
```

static AUX_RGBImageRec **TextureImage;

```

Then instead of the normal constructor and destructor, you'd want to make a function which mallocs the TextureImage and frees the TextureImage.

The rest of the functions you can still use within C.


The file loading functions you can actually just copy/past to C

---

### Post by crazyfuturamanoob on 2008-11-10
> **snikrot said:**
> The examples given below aren't just for windows. I programmed them in windows and just added (to be secure) windows.h everywhere.
If I'm right it should also work on Ubuntu.


Python I can't really help you with. (Never written python though I know a lot of other languages.)

Within C you'd probably want to add a static variable 
```

static AUX_RGBImageRec **TextureImage;

```

Then instead of the normal constructor and destructor, you'd want to make a function which mallocs the TextureImage and frees the TextureImage.

The rest of the functions you can still use within C.


The file loading functions you can actually just copy/past to C

So what all stuff I can recycle in my C program? Or how could I use C++ code with C?

---

### Post by snikrot on 2008-11-10
probalby this would be enough.

somename.c
```

static AUX_RGBImageRec **TextureImage;

AUX_RGBImageRec * CLoadFile::LoadBMP(char *Filename)				// Loads A Bitmap Image
{
	FILE *File=NULL;									// File Handle

	if (!Filename)										// Make Sure A Filename Was Given
	{
		return NULL;									// If Not Return NULL
	}

	File=fopen(Filename,"r");							// Check To See If The File Exists

	if (File)											// Does The File Exist?
	{
		fclose(File);									// Close The Handle
		return auxDIBImageLoad(Filename);				// Load The Bitmap And Return A Pointer
	}

	return NULL;										// If Load Failed Return NULL
}

void CreatePicsArray()
{
	CPics::SizeT=0;
	CPics::TextureImage = (AUX_RGBImageRec**) malloc(((CPics::SizeT)+1)*sizeof(AUX_RGBImageRec*));
	CPics::texture = (GLuint *) malloc(1*sizeof(GLuint));
}

void DestroyPicsArray()
{
	//if the picture array is destroyed, also destroy every picture in the textureimage array.
	for(int loop=(CPics::SizeT);loop>0; loop--)
	{
		if (TextureImage[loop-1])							// If Texture Exists
		{
			if (TextureImage[loop-1]->data)			// If Texture Image Exists
			{
				free(TextureImage[loop-1]->data);	// Free The Texture Image Memory
			}
			free(TextureImage[loop-1]);				// Free The Image Structure
		}
	}
}

//////////////////////////////////////////////////////////////////////
// Load all textures into a texture array
//////////////////////////////////////////////////////////////////////

int LoadAll()
{
	int Status=FALSE;

	//if there is any picture initialized build for all the pictures 3 textures with different filters.
	if((CPics::SizeT)>0)
	{
		Status=TRUE;

		CPics::texture = (GLuint *) realloc((CPics::texture),(CPics::SizeT)*1*(sizeof(GLuint)));
		glGenTextures(1* CPics::SizeT , CPics::texture);
		
		int loop=0;
		while((loop/1)<(CPics::SizeT))
		{
			// Create MipMapped Texture
			glBindTexture(GL_TEXTURE_2D, texture[loop+0]);
			glTexParameteri(GL_TEXTURE_2D,GL_TEXTURE_MAG_FILTER,GL_LINEAR_MIPMAP_LINEAR);
			glTexParameteri(GL_TEXTURE_2D,GL_TEXTURE_MIN_FILTER,GL_LINEAR_MIPMAP_NEAREST);

			glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP);
			glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP);

			gluBuild2DMipmaps(GL_TEXTURE_2D, 3, TextureImage[loop/1]->sizeX, TextureImage[loop/1]->sizeY, GL_RGB, GL_UNSIGNED_BYTE, TextureImage[loop/1]->data);

			loop = loop+1;
		}	
		
	}
	return Status;
}


//////////////////////////////////////////////////////////////////////
// Add a picture into a picture array
//////////////////////////////////////////////////////////////////////

int AddPic(char *Filename)
{
	int Pos;

	//if a picture has to be added make the TextureImage bigger so 1 picture can be added.
	CPics::TextureImage = (AUX_RGBImageRec**) realloc((CPics::TextureImage), ((CPics::SizeT)+1)*sizeof(AUX_RGBImageRec*));
	
	CLoadFile temp;
	//if the file of the picture exists, add 1 picture in the last position.
	if(CPics::TextureImage[(CPics::SizeT)]=temp.LoadBMP(Filename))
	{
		Pos=(CPics::SizeT);

		(CPics::SizeT)++;
	}
	//if the picture doesn't exists make the TextureImage 1 smaller so it's the old size again.
	else
	{
		CPics::TextureImage = (AUX_RGBImageRec**) realloc((CPics::TextureImage), (CPics::SizeT)*sizeof(AUX_RGBImageRec*));
		return -1;
	}
	//return the current position times 3 because all textures are loaded in three fold.
	return Pos*1;
}

//////////////////////////////////////////////////////////////////////
// Get a picture out of the loaded texture array
//////////////////////////////////////////////////////////////////////

GLuint GetPic(int Position)
{
	if((CPics::SizeT)>0)
	{
		return CPics::texture[Position];
	}
	return -1;
}

```

After this you probably want to use which you'd probably do like this:
```

void somefunction()
{
   CreatePicsArray();

   while()
   {
       //Create some object
       object........

       glBindTexture(GL_TEXTURE_2D, GetPic(texturePosition)); // This Will Select and bind The Picture
   }
   DestroyPicsArray();
}

```

---

