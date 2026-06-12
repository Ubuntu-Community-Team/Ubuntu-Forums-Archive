---
title: "C++/SDL/OpenGL My onscreen object's movement isn't syncing with time (w/ code sample)"
date: 2006-09-04
forum: Programming Talk
---

### Post by enigma_0Z on 2006-09-04
Hi all.


It's probably a coding mistake on my part but...

I'm making a game, and I need them to move based on ticks, that way they don't slow down when the computer slows down. However, if I interrupt the opengl program (and cause a large number of ticks between frames), some objects start falling behind. Which objects depends on which ones it's drawing...

Code for updating object position (nPTicks and nCTicks are Previous and Current ticks, passed in from another function)
```
void TestObject::Think(int nPTicks, int nCTicks)
{
	// Calculate ticks between thinking...
	int nTicks = nCTicks - nPTicks;
	
	// Do movement processing
	if (bXMovePlus)
	{
		nXLocation += nXSpeed * (float)nTicks/1000;
		if (nXLocation >= (nXRange/2)) 
		{
			nXLocation = (nXRange/2);
			bXMovePlus = false;
		}
	}
	else
	{
		nXLocation -= nXSpeed * (float)nTicks/1000;
		if (nXLocation <= -(nXRange/2)) 
		{
			nXLocation = -(nXRange/2);
			bXMovePlus = true;
		}
	}
}
```

Corresponding code to draw object:
```
void TestObject::Display()
{
	glColor3f(nR, nG, nB);

	//glTranslatef(nXTSpeed, 0.0f, 0.0f);
	glBegin(GL_QUADS);
		glVertex2f(nXLocation + nX1, nY1      );
		glVertex2f(nXLocation + nX1, nY1 + nY2);
		glVertex2f(nX2 + nXLocation, nY1 + nY2);
		glVertex2f(nX2 + nXLocation, nY1      );
	glEnd();
	
	glFlush();
}
```

where X1 is the location of the object, and nXLocation is the offset for the movement (they just move left & right across a range)

In order to process and draw each object, I've got a linked list that is iterated through:

Code for processing objects. it is called once a loop...
```
void MoleEngine::DoProcess()
{
	// Set the previous ticks
	nPTicks = nCTicks;
	
	// Get the current ticks
	nCTicks = SDL_GetTicks();
	
	// Monitor for especially long frames
	if ((nCTicks - nPTicks) > 50)
		cout << "---------------- LARGE # OF TICKS ----------------" << endl;

	// Check for events
	CheckEvents();
	
	// Calculate FPS
	CalcFPS();
	
	// Process each object for this scene
	ProcessScene();
}
```

Code for ProcessScene()

olScene is the list. Next() goes to next pointer in list, returns true if not last item.
```
void MoleEngine::ProcessScene()
{
	if (!bPaused)
	{
		// If the scene is not empty...
		if (olScene->pHead != 0)
		{
			olScene->SeekToHead();
			olScene->pCurr->Think(nPTicks, nCTicks);
			while(olScene->Next())
				olScene->pCurr->Think(nPTicks, nCTicks);
		}
	}
}
```

Finally, draw scene code:
```
void MoleEngine::DoRender()
{
	glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
	
	// If the scene is not empty...
	if (olScene->pHead != 0)
	{
		olScene->SeekToHead();
		olScene->pCurr->Display();
		while(olScene->Next())
			olScene->pCurr->Display();
	}
	
	glFinish();
	
	SDL_GL_SwapBuffers();

	nFrames++;
}
```

Anyway, is there anything obvious that I missed?

---

### Post by LordHunter317 on 2006-09-04
[QUOTE=enigma_0Z;1460949]How is DoProcess() getting invoked?  The answer likely depends on that.

And is your code threaded or not?

---

