---
title: "VTK Simple question."
date: 2009-09-24
forum: Programming Talk
---

### Post by fredscripts on 2009-09-24
Hi!

Anyone into VTK ([www.vtk.org)?](www.vtk.org)?) I have this almost-hello world program that shows an sphere:

```
#include "vtkSphereSource.h"

#include "vtkPolyDataMapper.h"

#include "vtkActor.h"

#include "vtkProperty.h"

#include "vtkRenderWindow.h"

#include "vtkRenderer.h"

#include "vtkRenderWindowInteractor.h"



int main (void)

{



  // create sphere geometry

  vtkSphereSource *sphere = vtkSphereSource::New();

  sphere->SetRadius(1.0);

  sphere->SetThetaResolution(18);

  sphere->SetPhiResolution(18);



  // map to graphics library

  vtkPolyDataMapper *map = vtkPolyDataMapper::New();

  map->SetInput(sphere->GetOutput());



  // actor coordinates geometry, properties, transformation

  vtkActor *aSphere = vtkActor::New();

  aSphere->SetMapper(map);



  aSphere->GetProperty()->SetColor(0,0,1); // sphere color blue



  // a renderer and render window

  vtkRenderer *ren1 = vtkRenderer::New();

  vtkRenderWindow *renWin = vtkRenderWindow::New();

  renWin->AddRenderer(ren1);



  // an interactor

  vtkRenderWindowInteractor *iren = vtkRenderWindowInteractor::New();

  iren->SetRenderWindow(renWin);



  // add the actor to the scene

  ren1->AddActor(aSphere);

  ren1->SetBackground(1,1,1); // Background color white



  // render an image (lights and cameras are created automatically)

  renWin->Render();



  // begin mouse interaction

   iren->Start();

   return (1);

}

```

I would like to add some keyboard response. I mean if I press 'x', that the color of the sphere changes. Using C++.

I cannot find any documentation on google how to do this simple thing. Maybe I'm used to OpenGL and GLUT which has keyboard callbacks and glutPostRedisplay and so and can't figure out here how to do this.


Thanks in advance!

---

### Post by rCXer on 2009-09-24
Wow, a fellow vtk user :guitar: Here's an example.  It opens a blank render window and prints the names of the keys pressed in the console. Btw, a good place to get help are the [vtk mailing lists](http://www.vtk.org/cgi-bin/mailman/listinfo).

```
#include <iostream>
#include "vtkCommand.h"
#include "vtkRenderer.h"
#include "vtkRenderWindowInteractor.h"
#include "vtkRenderWindow.h"
#include "vtkCallbackCommand.h"

using namespace std;

//Calback functions take this form. I have no idea why :(.
void keypressFunction(vtkObject* caller, unsigned long event, void* clientdata, void* calldata)
{
	/*The object that called this function should be the render window interactor.
	Therefore create an render window interactor and cast it as the caller. */
	vtkRenderWindowInteractor *iren = (vtkRenderWindowInteractor*)caller;

	//Stuff to do when key is pressed.  In this case just print the keys symbol.
	cout<< iren->GetKeySym() <<endl;
}

int main(void)
{
	vtkRenderWindow *renWin = vtkRenderWindow::New();	//Creat renWin.
	vtkRenderer *ren = vtkRenderer::New();			//Create renderer...	
	renWin->AddRenderer(ren);				//...and assign it to renWin.

	vtkRenderWindowInteractor *iren = vtkRenderWindowInteractor::New(); 	//Create interactor...
	renWin->SetInteractor(iren);						//...and asign it to renWin.

	vtkCallbackCommand* keypressCommand = vtkCallbackCommand::New();	//Create keypressCommand...
	keypressCommand->SetCallback(keypressFunction);				//...and tell it to go to keypressFunction ...
	iren->AddObserver("KeyPressEvent", keypressCommand);			//...when a "KeyPressEvent" occurs in iren.

	//Put more stuff here
	renWin->Render();	//Render your stuff
	iren->Start();		//Start the interactor

	return 0;
}
```

Here's my CMakeLists.txt (in case you are using cmake). It includes more libraries than you'll ever need.
```

PROJECT(Keypress)

FIND_Package(VTK)
IF(VTK_FOUND)
	INCLUDE(${VTK_USE_FILE})
ELSE(VTK_FOUND)
	MESSAGE(FATAL_ERROR "VTK not found. Please set VTK_DIR.")
ENDIF(VTK_FOUND)

ADD_EXECUTABLE(Keypress Keypress.cpp)
TARGET_LINK_LIBRARIES(Keypress vtkCommon vtkRendering vtkGraphics vtkHybrid vtkImaging vtkIO vtkFiltering vtkCommon)

```

---

### Post by fredscripts on 2009-09-25
Thanks so much. If instead of printing key symbol I wanted to change the background color/do whatever with the elements of the window, do you know how could I do it? Something like /* do sth */ and renWin->Update()?

---

### Post by rCXer on 2009-09-25
Replace...
```

	cout<< iren->GetKeySym() <<endl;

```
...with...
```

	vtkRenderWindow		*renWin = iren->GetRenderWindow();	//Get the render window from our interactor.
	vtkRendererCollection	*rens = renWin->GetRenderers();		//Get the a list of renderers in our render window
	vtkRenderer		*ren = rens->GetFirstRenderer();	//Get the first renderer from list. Since we only have 1 renderer this is the one we want.
	ren->SetBackground(0,1,1);	//Set background to cyan.
	renWin->Render();		//Render our stuff.

```
... and make sure you include...
```

#include "vtkRendererCollection.h"

```
...to the beginning of your file.

All this does is change the background to cyan when a key is pressed.  If you want to work with the actor (the sphere in your case) just get the actor collection from the renderer and then get the first actor.

---

