---
title: "Stack corruption driving me insane"
date: 2011-06-29
forum: Programming Talk
---

### Post by Teacakes on 2011-06-29
Hi guys,

I've been stuck on this problem for ages and I can't seem to figure it out, so I'm hoping that whoever reads this can. I'm writing a small game engine as a hobby in my spare time, but it's not working exactly as planned.

The problem is whenever the member function 'LoadTexture(char *cName)' is called the MSVC debugger says "Run-Time Check Failure #2 - Stack around the variable 'Image' was corrupted." Usually I have no problem googling my programming problems, but I've been stuck on this one for hours without a straight answer.

Here is the header file for the class:
```
// GraphicsDevice.h

#ifndef H_GRAPHICS_DEVICE
#define H_GRAPHICS_DEVICE

#include "GraphicsInstance.h"
#include <SFML/Window.hpp>
#include <SFML/Graphics.hpp>
#include <GL/gl.h>
#include <GL/glu.h>
#include <vector>

using std::vector;

#define MAX_WINDOWS 10
#define MAX_ENTITIES 10000
#define ARRAY_RESIZE_AMOUNT 50 //defines how often arrays resize (50 means arrays expand 50 spaces at a time)
#define MAX_DEPTH 100000//the maximum positive or negative number a graphics instance's depth can be

using namespace std;

//This can be inhereted by for purposes of expanding the engine with another rendering API
class GraphicsDevice
{
public:
	GraphicsDevice(void);
	~GraphicsDevice(void);
	int			CreateRenderingWindow(int WinWidth, int WinHeight, int ColourDepth, char *Title, bool Fullscreen, int AntiAliasing);
	int			DestroyRenderingWindow();
	int			UpdateGraphics();
	int			UpdateWindow();
	NanoTexture *LoadTexture(char *cName);//loads a texture and returns a pointer to it, or just a pointer if its already loaded
	int	InstanceAttach(GraphicsInstance *Instance);
	int InstanceDetach(GraphicsInstance *Instance);
	void SetBackgroundColour(float Red, float Green, float Blue);
	float GetFrameTime(void);
	void ResortDepth(void);
	sf::RenderWindow *GetSFMLWindow();

private:
	//private member functions:
	void Reshape(int x, int y);		//reshapes the opengl viewport given the new width and height of the window
	void RotatePoint(float cx, float cy, float angle, float *px, float *py); //rotates (px, py) around (cx, cy)

	//resorts the GraphicsInstances from back to front based on their depth, where N is the number of GraphicsInstances
	void SortEntities (int N);

	//rendering settings:
	sf::RenderWindow *wWindow;
	bool bWinFocused;
	int iWinWidth;
	int iWinHeight;
	bool bWinClosed;
	int iColourDepth;
	int iAntiAliasing;

	//instance information:
	unsigned int	iInstanceCount;
	vector<GraphicsInstance *> Entities;
	unsigned int iInstanceArraySize;

	//resources:
	unsigned int iTextureCount;
	unsigned int iTextureArraySize;
	vector<auto_ptr<NanoTexture> > pTextures;
	vector<GLuint>	vTexture;

	//bg colour:
	float fBGRed;
	float fBGGreen;
	float fBGBlue;

	//depth sorting:
	bool bDepthSortNeeded;

	//only for testing purposes:
	int x;
	float fps;
};

#endif
```

And here is the source file:
```
#include "stdafx.h"
#include "GraphicsDevice.h"

GraphicsDevice::GraphicsDevice(void)
{
	//instances
	iInstanceCount		= 0;
	iInstanceArraySize	= 0;
	wWindow				= NULL;

	//rendering settings:
	bWinFocused = false;
	iWinWidth	= 0;
	iWinHeight	= 0;
	bWinClosed	= true;
	iColourDepth	= 0;
	iAntiAliasing	= 0;

	//resources:
	iTextureCount		= 0;
	iTextureArraySize	= 0;

	//bg colour:
	float fBGRed	= 0;
	float fBGGreen	= 0;
	float fBGBlue	= 0;

	//depth sorting:
	bDepthSortNeeded = false;

	//only for testing purposes:
	x		= 0;
	fps		= 0;
}

GraphicsDevice::~GraphicsDevice(void)
{
	//release textures
	for (UINT i=0; i<iTextureCount; i++) 
	{
		std::cout << "Deleting texture with ID " << i << " out of " << iTextureCount-1 << endl;
		//glDeleteTextures(1, (GLuint*)pTextures[i].get()->TextureID);
		glDeleteTextures(1, (GLuint*)vTexture[i]);
	}

	if (bWinClosed == false)
	{
		wWindow->Close();
		delete wWindow;
	}
}

int GraphicsDevice::CreateRenderingWindow(int WinWidth, int WinHeight, int ColourDepth, char *Title, bool Fullscreen, int AntiAliasing)
{
#ifdef _DEBUG
	cout << "Creating rendering window with the following properties:\n" << "\tWidth: " << WinWidth << "\n\tHeight: " << WinHeight 
		<< "\n\tColour Depth: " << ColourDepth << "\n\tFullscreen: " << Fullscreen << "\n\tAnti-aliasing: " << AntiAliasing <<"\n";
#endif

	if (bWinClosed == false)
	{
#ifdef _DEBUG
		cout << "Error: Cannot create new rendering window because one already exists\n";
#endif
	}

	//record arguments
	iAntiAliasing = AntiAliasing;
	iColourDepth = ColourDepth;
	iWinWidth = WinWidth;
	iWinHeight = WinHeight;

	//set settings
	sf::WindowSettings Settings;
	Settings.DepthBits         = 24; // Request a 24 bits depth buffer
	Settings.StencilBits       = 8;  // Request a 8 bits stencil buffer
	Settings.AntialiasingLevel = iAntiAliasing;  // Request 2 levels of antialiasing

	//create the new window
	if (Fullscreen == true)
	{
		wWindow = new sf::RenderWindow(sf::VideoMode(iWinWidth, iWinHeight, iColourDepth), 
		Title, sf::Style::Fullscreen, Settings);
		
	}
	else
	{
		wWindow = new sf::RenderWindow(sf::VideoMode(iWinWidth, iWinHeight, iColourDepth), 
		Title, /*sf::Style::Fullscreen, sf::Style::Close*/sf::Style::Resize, Settings);
	}

	//windows start focused:
	bWinFocused = true;
	bWinClosed = false;

#ifdef _DEBUG
	cout << "Window created successfully\n";
#endif

	return 0;
}

int GraphicsDevice::DestroyRenderingWindow()
{
	//destroy the window
	if (bWinClosed == false)
	{
		wWindow->Close();
		bWinClosed = true;
#ifdef _DEBUG
		cout << "Rendering window destroyed.\n";
#endif
	}
	else
	{
#ifdef _DEBUG
		cout << "Error: Cannot destroy rendering window because it doesn't exist.\n";
#endif
		return -1;
	}

	return 0;
}

int GraphicsDevice::UpdateGraphics()
{
	//check if the window has been closed
	if (bWinClosed == true)
	{
#ifdef _DEBUG
		cout << "Error: Cannot swap buffers for closed window.\n";
#endif
		return -1;
	}

	//Check to see if GraphicsInstances need to be put in order
	if (bDepthSortNeeded == true)
	{
		SortEntities(iInstanceCount);
		bDepthSortNeeded = false;
	}

	//Must be called before rendering to a window (only needed when doing multiple windows but meh)
	wWindow->SetActive();

	//resize the openGL viewport to the window we are currently rendering. TODO: PUT ON RESIZE EVENT
	Reshape(iWinWidth, iWinHeight);

	//enable depth testing
	glClearDepth(1.0f);							// Depth Buffer Setup
	glEnable(GL_DEPTH_TEST);						// Enables Depth Testing
	glDepthFunc(GL_LEQUAL);
	
	//set the clear colour
	glClearColor(fBGRed, fBGGreen, fBGBlue, 1);

	//clear the screen
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

	int vPort[4];

	glGetIntegerv(GL_VIEWPORT, vPort);

	glMatrixMode(GL_PROJECTION);
	glPushMatrix();
	glLoadIdentity();

	glOrtho(0, vPort[2], 0, vPort[3], MAX_DEPTH*-1, MAX_DEPTH);//last two arguments are near (close to the screen) and far (view distance) clipping
	glMatrixMode(GL_MODELVIEW);
	glPushMatrix();

	//prevents pixel blur occuring since pixel coordinates are not properly aligned to the window
	glLoadIdentity();
	glTranslatef (0.375, 0.375, 0);//0.5 was formerly 0.375

	//enable transparency rendering in gl primatives (if glEnable (GL_BLEND);)
	glBlendFunc (GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

	//make the depth buffer read only while we render(for transparency effects) //NOW WE DON"T NEED THIS BECAUSE EVERYTHING IS BEING DRAWN IN ORDER
	glDepthMask(GL_FALSE);

	//variables we need for rendering:
	NanoTexture *ntRenderTexture = NULL; //this is used to handle each GraphicsInstance's texture
	float		fRenderAngle	= 0.0f; //this is used to handle each GraphicsInstance's rotation
	float		fDepth			= 0;	//this is used to handle each GraphicsInstance's depth
	float		fRenderPointTLX, fRenderPointTRX, fRenderPointBLX, fRenderPointBRX; //the X points for OpenGL to render
	float		fRenderPointTLY, fRenderPointTRY, fRenderPointBLY, fRenderPointBRY; //the Y points for OpenGL to render
	
	//Render all entities:
	for (unsigned int i = iInstanceCount-1; i>=0; i--)//for all attached instances GraphicsInstance (in reverse so they render properly)
	{
		if (Entities[i])				//if this one exists
		{
			if (Entities[i]->GetVisible() == true)	//if this GraphicsInstance is set to visible
			{
				ntRenderTexture = Entities[i]->GetTexture();
				if (ntRenderTexture != NULL)				//if this GraphicsInstance has an image to render
				{
					//Collect needed details about the given Instance:
					fRenderAngle	= Entities[i]->GetRotation();
					fDepth			= (float)(Entities[i]->GetDepth()*-1);//we multiply by -1 so higher depth goes deeper into the screen

					//cout << "Drawing instance at depth " << Entities[i]->GetDepth() << endl;

					//Set up the initial position of the 4 points:
					fRenderPointTLX = Entities[i]->GetPositionX() - Entities[i]->GetOriginX();
					fRenderPointTLY = Entities[i]->GetPositionY() - Entities[i]->GetOriginY();

					fRenderPointTRX = fRenderPointTLX + Entities[i]->GetScaleX();
					fRenderPointTRY = fRenderPointTLY;

					fRenderPointBLX = fRenderPointTLX;
					fRenderPointBLY = fRenderPointTLY + Entities[i]->GetScaleY();

					fRenderPointBRX = fRenderPointTRX;
					fRenderPointBRY = fRenderPointBLY;

					//Rotate the 4 points:
					if (fRenderAngle != 0)//if the rotation has been modified
					{
						RotatePoint(Entities[i]->GetPositionX(), Entities[i]->GetPositionY(), fRenderAngle, &fRenderPointTLX, &fRenderPointTLY);
						RotatePoint(Entities[i]->GetPositionX(), Entities[i]->GetPositionY(), fRenderAngle, &fRenderPointTRX, &fRenderPointTRY);
						RotatePoint(Entities[i]->GetPositionX(), Entities[i]->GetPositionY(), fRenderAngle, &fRenderPointBRX, &fRenderPointBRY);
						RotatePoint(Entities[i]->GetPositionX(), Entities[i]->GetPositionY(), fRenderAngle, &fRenderPointBLX, &fRenderPointBLY);
					}

					// Bind our texture
					glEnable(GL_TEXTURE_2D);
					glBindTexture(GL_TEXTURE_2D, (GLuint)ntRenderTexture->TextureID);
					glColor4f(1.f, 1.f, 1.f, 1.f);

					//modify rendering settings
				if (Entities[i]->GetQualityTransparent() == false)
					{
						glAlphaFunc(GL_GREATER, (GLclampf)0.9);//set the alpha test to ignore all pixels below 90% alpha, and make top 10% opaque
						glEnable(GL_ALPHA_TEST);//enable the alpha test
					}
					else
					{
						glEnable(GL_BLEND);//enable alpha blending
					}

					//Check if the depth is appropriate (DEBUG ONLY)
#ifdef _DEBUG
					if (fDepth < (MAX_DEPTH*-1) || fDepth > MAX_DEPTH)
					{
						cout << "Warning: Attempting to render object with depth less than -" << MAX_DEPTH
							<< " or greater than " << MAX_DEPTH << ". Texture may not appear\n";
					}
#endif

					/*Render the GraphicsInstance using the collected details (all points on the 
					Y axis are multiplied by -1 to invert the y axis so a higher y moves
					points downwards. Not that the second argument of glTexCoord2f must also
					be inverted)*/
					glBegin(GL_QUADS);

					//Bottom-left
					glTexCoord2f(0, 1);
					glVertex3f(fRenderPointBLX, (fRenderPointBLY * -1) + iWinHeight, fDepth);

					//Bottom-right
					glTexCoord2f(1, 1);
					glVertex3f(fRenderPointBRX, (fRenderPointBRY * -1) + iWinHeight, fDepth);

					//Top-right
					glTexCoord2f(1, 0);
					glVertex3f(fRenderPointTRX, (fRenderPointTRY * -1) + iWinHeight, fDepth);

					//Top-left
					glTexCoord2f(0, 0);
					glVertex3f(fRenderPointTLX, (fRenderPointTLY * -1) + iWinHeight, fDepth);

					glEnd();

					//unmodify rendering settings
					if (Entities[i]->GetQualityTransparent() == false)
					{
						glDisable(GL_ALPHA_TEST);//enable the alpha test
					}
					else
					{
						glDisable(GL_BLEND);//enable alpha blending
					}
				}
			}
		}
		else
		{
#ifdef _DEBUG
			cout << "Bug: NULL Instance attached\n";
#endif
		}

		//Check if we are on the last loop(fixes a bug to do with the loop running in reverse)
		if (i==0)
			break;
	}

	//make the depth buffer writable again (for transparency effects) //NOW WE DON"T NEED THIS BECAUSE EVERYTHING IS BEING DRAWN IN ORDER
	glDepthMask(GL_TRUE);

#ifdef _DEBUG
	//display frame time
	x++;
	fps += GetFrameTime();

	if (fps > 5)
	{
		cout << "FPS: " << x/(float)5 << endl;
		x = 0;
		fps = 0;
	}

	/*
	if (x > 20000)
	{
		cout << "Average fps:" << fps/(float)x << endl;
		x = 0;
		fps = 0;
	}*/
#endif

	//update the window
	wWindow->Display();

	return 0;
}

int GraphicsDevice::UpdateWindow()
{
	sf::Event Event;
		
	while (wWindow->GetEvent(Event))
	{
		// Window closed
		if (Event.Type == sf::Event::Closed)
		{
			wWindow->Close();
			bWinClosed = true;
		}

		// Window resize
		if (Event.Type == sf::Event::Resized)
		{
			iWinWidth = Event.Size.Width;
			iWinHeight = Event.Size.Height;
		}

		// Window focused
		if (Event.Type == sf::Event::GainedFocus)
		{
			bWinFocused = true;
		}

		// Window focused
		if (Event.Type == sf::Event::LostFocus)
		{
			bWinFocused = false;
		}
	}
	return 0;
}

NanoTexture *GraphicsDevice::LoadTexture(char *cName)
{
	unsigned int iTex, n = 0;
	
	// do we already have this texture? if so, ignore
	for (iTex=0; iTex<iTextureCount; iTex++) 
	{
		if (pTextures[iTex].get()->sName.c_str()==cName) 
		{
			return pTextures[iTex].get();//Error is non fatal
		}
	}

	// allocate ARRAY_RESIZE_AMOUNT new memory slots for textures if necessary
	if (iTextureCount == iTextureArraySize) 
	{
		iTextureArraySize += ARRAY_RESIZE_AMOUNT;
		pTextures.resize(iTextureArraySize);
		vTexture.resize(iTextureArraySize);
#ifdef _DEBUG
		cout << "Expanding texture memory to " << iTextureArraySize << " textures\n";
#endif
	}


	//create new nanoTexture
	pTextures[iTextureCount].reset(new NanoTexture);

	//save texture name
	pTextures[iTextureCount].get()->sName = cName;

	//create new sf::Image
	sf::Image Image;

	//Loads the texture in SFML 
#ifdef _DEBUG
 	cout << "Loading '" << pTextures[iTextureCount].get()->sName << "' with ID " << iTextureCount << "\n";
#endif

	if (Image.LoadFromFile(pTextures[iTextureCount].get()->sName))
	{
#ifdef _DEBUG
		cout << "Error: Failed loading the texture '" << pTextures[iTextureCount].get()->sName << "'\n";
#endif
		return NULL;
	}

	//record the textures dimensions
	pTextures[iTextureCount].get()->fWidth	= (float)Image.GetWidth();
	pTextures[iTextureCount].get()->fHeight	= (float)Image.GetHeight();

	//record openGL info for the texture
	glGenTextures(1, &vTexture[iTextureCount]);
	glBindTexture(GL_TEXTURE_2D, vTexture[iTextureCount]);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
	glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
	gluBuild2DMipmaps(GL_TEXTURE_2D, GL_RGBA, Image.GetWidth(), Image.GetHeight(), 
		GL_RGBA, GL_UNSIGNED_BYTE, Image.GetPixelsPtr());
	
	//records the texture id
	pTextures[iTextureCount].get()->TextureID = (unsigned int)vTexture[iTextureCount];

	//we now have another texture loaded	
	iTextureCount++;

	//everything is good
	return pTextures[iTextureCount-1].get();
 }

int GraphicsDevice::InstanceAttach(GraphicsInstance *Instance)
{
	//check if the given Instance is real
	if (!Instance)
	{
#ifdef _DEBUG
		cout << "Error: Cannot attach non-valid GraphicsInstance\n";
#endif
		return -1;
	}

	//check if the Instance already exists
	for (unsigned int i = 0; i<iInstanceArraySize; i++)
	{
		if (Entities[i]==Instance)
		{
			return 0;
		}
	}

	//check if we have room for more entities. If not, then make room.
	while (iInstanceCount>=iInstanceArraySize)
	{
		iInstanceArraySize += ARRAY_RESIZE_AMOUNT;
		Entities.resize(iInstanceArraySize);
	}

	//point to the Instance
	Entities[iInstanceCount] = Instance;
	
	//make sure it knows it's attached
	if (Entities[iInstanceCount]->GetAttached() == false)//if it doesn't know
		Entities[iInstanceCount]->Attach(this);

	iInstanceCount++;
	return 0;
}

int GraphicsDevice::InstanceDetach(GraphicsInstance *Instance)
{
	//check if the Instance already exists
	for (unsigned int i = 0; i<iInstanceArraySize; i++)
	{
		if (Entities[i]==Instance)
		{
			//make sure the instance knows it's being detached
			if (Entities[i]->GetAttached() == true)//if it doesn't know  //i formerly iInstanceCount
				Entities[i]->Attach(this);

			//shift all entities above the requested one down the list one slot
			for (unsigned int ii = i; ii<iInstanceArraySize-1; ii++)	//run this loop till the second last Instance
			{
				Entities[ii] = Entities[ii+1];//make this one equal to the one in front of it
			}

			Entities[iInstanceArraySize-1] = NULL;

			//Decrement the total number of entities
			iInstanceCount -= 1;

			//Shrink the array if needed
			if ((iInstanceArraySize-i)>ARRAY_RESIZE_AMOUNT)
			{
				iInstanceArraySize -= ARRAY_RESIZE_AMOUNT;
				Entities.resize(iInstanceArraySize);
			}

			return 0;
		}
	}

	//if nothing was found
#ifdef _DEBUG
	cout << "Error: Can't detach GraphicsInstance that doesn't exist\n";
#endif
	return -1;
}

void GraphicsDevice::SetBackgroundColour(float Red, float Green, float Blue)
{
	fBGRed		= Red;
	fBGGreen	= Green;
	fBGBlue		= Blue;
}

float GraphicsDevice::GetFrameTime(void)
{
	return wWindow->GetFrameTime();
}

void GraphicsDevice::Reshape(int x, int y)
{
	if (y == 0 || x == 0) return;  //Nothing is visible then, so return
	glViewport(0, 0, x, y);
}

void GraphicsDevice::RotatePoint(float cx, float cy, float angle, float *p_x, float *p_y)
{
  float s = sin(angle);
  float c = cos(angle);

  // translate point back to origin:
  *p_x -= cx;
  *p_y -= cy;

  // rotate point
  float xnew = (*p_x) * c - (*p_y) * s;
  float ynew = (*p_x) * s + (*p_y) * c;

  // translate point back:
  *p_x = xnew + cx;
  *p_y = ynew + cy;
}

void GraphicsDevice::ResortDepth(void)
{
	//this means it will sort all the depths just before the frame is rendered, preventing multiple changes
	//in depth during one frame wasting cpu cycles
	bDepthSortNeeded = true;
}

void GraphicsDevice::SortEntities (int N)
{
	GraphicsInstance *t; // the temporary value
    unsigned int n = N, parent = N/2, index, child; // heap indexes
    // loop until array is sorted
    for (;;) 
	{ 
        if (parent > 0) 
		{ 
            // first stage - Sorting the heap 
            t = Entities[--parent];  // save old value to t
        } 
		else 
		{
            // second stage - Extracting elements in-place
            n--;						// make the heap smaller
            if (n == 0) return;			// When the heap is empty, we are done
            t = Entities[n];			// save lost heap entry to temporary
            Entities[n] = Entities[0];	// save root entry beyond heap
        }

        // insert operation - pushing t down the heap to replace the parent
        index = parent; // start at the parent index
        child = index * 2 + 1; // get its left child index
        while (child < n) 
		{
            // choose the largest child
            if (child + 1 < n  &&  Entities[child + 1]->GetDepth() > Entities[child]->GetDepth()) 
			{
                child++; // right child exists and is bigger
            }
            // is the largest child larger than the entry?
            if (Entities[child]->GetDepth() > t->GetDepth()) 
			{
                Entities[index] = Entities[child]; // overwrite entry with child
                index = child; // move index to the child
                child = index * 2 + 1; // get the left child and go around again
            } 
			else 
			{
                break; // t's place is found
            }
        }
        // store the temporary value at its new location 
        Entities[index] = t; 
    }
}

sf::RenderWindow *GraphicsDevice::GetSFMLWindow()
{
	return wWindow;
}

```

Could anyone give a possible cause as to what's causing this error? As you can probably tell I'm fairly new to C++, so any other programming tips would be appreciated.

Edit: When I don't declare 'sf::Image Image;' as a local variable to 'LoadTexture(char *cName)' and instead declare it as a private member of the class, upon the class being destroyed it says displays an error notifying me of heap corruption, instead of the usual stack corruption notification. I hope that helps.

---

### Post by GeneralZod on 2011-06-29
Can you give a sample call to LoadTexture?

One thing that immediately sets off alarm bells is your usage of char* as if they were strings; e.g.

```

pTextures[iTex].get()->sName.c_str()==cName

```

checks that the *pointer* returned by pTextures[iTex].get()->sName.c_str() is equal to the *pointer* cName (not that the strings are equal!) - this is pretty unlikely to be the case in practice :)

And

```

pTextures[iTextureCount].get()->sName = cName;

```

This stores the *pointer* cName into sName, which might not be what you want - if cName was e.g. passed in as a local stack object from a function and then that function went out of scope, sName would be a dangling pointer.  (There are plenty of other situations that would cause a similar problem).

Edit:

Some general points: generally when writing C++ apps, std::string is preferred to raw char*'s.  Also, many people prefer that the scope of variables be as minimal as possible, which usually means (at least) that they be declared as close to the point at which they are first used as is possible.  e.g.  in LoadTexture, we'd have

```

	for (unsigned int iTex=0; iTex<iTextureCount; iTex++) 

```

instead of declaring iTex at the top of the block (assuming there are no other references to iTex outside that for ... loop - I didn't see any at a quick glance :))

Also, as a purely subjective and stylistic choice - many people thoroughly loathe Hungarian Notation ;)

---

### Post by Teacakes on 2011-06-29
> 
```

pTextures[iTextureCount].get()->sName = cName;

```

This stores the *pointer* cName into sName, which might not be what you want - if cName was e.g. passed in as a local stack object from a function and then that function went out of scope, sName would be a dangling pointer.  (There are plenty of other situations that would cause a similar problem).

Ah ok, thanks for that. Now I feel very silly....

...but as I said, I'm still getting comfortable with C++ :)

---

### Post by Teacakes on 2011-07-02
Hey guys,

I ported the entire class from SFML to SDL, as well as cleaning up the code and comments in general. The problem somehow disappeared after the port was completed. Thanks for the help, I'll be sure to post on here again next time google fails me :)

---

