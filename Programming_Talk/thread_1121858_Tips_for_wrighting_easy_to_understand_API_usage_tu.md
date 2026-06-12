---
title: "Tips for wrighting easy to understand API usage tutorials?"
date: 2009-04-10
forum: Programming Talk
---

### Post by hessiess on 2009-04-10
As you may already know, I have bean developing a 2D graphics engine, but as writing documentation isn't my best aria, the documentation may suffer. Has anyone got any tips for writing easy to understand tutorials?

This is what I currently have for one of the basic usage tutorial:

[PHP]/*
This is a simple application that demonstrates the basic usage
of the Quad-Ren graphics library.

First we need to include the Quad-Ren header file.
*/
#include <quad-ren/quad-ren.h>

int main()
{
/*
To display anything we first need to create an instance of
qr_renderer. The constructor takes four arguments, these are: 

 *View port aspect ratio
    The aspect ratio of the view port, it is automatically
    leterboxed to maintain the aspect ratio, regardless of
    the window size.

 *Projection Width
    The width of the view port in relative co-ordinate space.

 *Full screen
    This parameter controls if the application will run	
    full screen or windowed.

 *Window resolution
    The default size of the window in pixels, passing 0
    creates a maximised window. This parameter is ignored
    if full screen is set to true, in which case Quad-Ren
    will render at the screens maximum resolution.
*/
    qr_renderer *renderer = new qr_renderer(vector2d_i(16, 9),
	10.0 ,false ,vector2d_i(0, 0));

/*
Set the window title.
*/
    renderer -> set_window_title("Hello World! - Quad-Ren 0.4");

/*
next we fetch a pointer to the resource manager from the renderer.
*/
    qr_resource_manager *res_man = renderer ->
	get_resource_manager();

/*
We are going to display an image containing the "hello world!"
message. First we create a new sprite object for the image.

The qr_sprite constructor takes two arguments, a pointer to the
resource manager and the total number of frames which the sprite
is going to store.
*/
    qr_sprite *message = new qr_sprite(res_man, 1);

/*
The image we want to display is stored in the "media" folder and
is in the PNG format. PNG images are supported natively and can
be loaded easily with a call to the load_png_frame method.

All frames in an animation must be powers of 2, square and the
same size. 
*/
    message -> load_png_frame(
	"../media/hello_world.png", 1);

/*
Before a sprite can be used it must first be converted, this
converts all of the image data into the correct format for
the renderer. Be aware that once a sprite has bean converted,
it is no longer editable.
*/
    message -> convert_data();

/*
The easiest way to display a sprite is to attach it to the
background quad, which is always the same size as the view
port, and moves to follow the camera. Lets attach the sprite
containing the hello world image to the background quad.
*/
    renderer -> set_bg_sprite(message);

/*
Thats it for set-up, to render the scene the run method
of the renderer is ran inside of a for loop. The run()
method returns true until the user closes the window or
an event receiver returns false.  
*/
    while(renderer -> run())
    {
    }

/*
When the above while loop exits application exits we need
to free the renderer, sprites and any other allocated
resources. This can be achieved by calling drop on the
renderer, which then instructs the resource manager to
delete all registered resources.
*/
    renderer -> drop();
}[/PHP]

Thanks in advance for any advice.

---

### Post by cmay on 2009-04-10
this you posted looks alright.

 thing i see is to use as many examples in code as possible. as example in c library there is many functions that many can just see what they does and how to use them before getting an example of the usage.  the time functions seems to puzzle many .

i think its great the part you posted from just reading over it i would say its easy enough to learn from .  many small tutorials can be made this way from a simple and very well documented piece of code which makes it easy for many to follow. even me that do not yet know that much c can grasp a bit of it. that is a good sign. :)

---

### Post by hessiess on 2009-04-10
Thanks, how does this one look?

[PHP]/*
This tutorial shows how keyboard input is read in Quad-Ren, the
result is a space ship which can be controlled using the arrow
keys.

Include the Quad-Ren header file and math.h for cos and sin.
*/

#include <quad-ren/quad-ren.h>
#include <math.h>

qr_renderer *renderer;

/*
All input in Quad-Ren is handled using event receiver objects
which can be attached to scene nodes. We create a new event
receiver to move a scene node with the arrow keys. To begin
we derive a class from qr_event_receiver.

This class contains a member variable which will be used to
store the state of keyboard keys.
*/
class new_event_receiver : public qr_event_receiver
{
    bool keys_down[QR_KEYSYM_COUNT];

public:
/*
The classes constructor initialises the keys_down array,
setting all elements to false.
*/
    new_event_receiver()
    {

	for(int i = 0; i < QR_KEYSYM_COUNT; i++)
	    keys_down[i] = false;
    }

/*
The virtual method on_event is the core of an event
receiver, this method gets called whenever an event
occurs. The event, a pointer to the scene node
which the event receiver is registered and the time
delta are passed as parameters.
*/
    bool on_event(qr_event *event, qr_scene_node *node, float time_delta)
    {

/*
Key press/release events are only generated when the key
changes from not pressed to pressed and vice versa, because
of this we use the keys_down array to store the state of
a key.
*/
	switch (event -> type)
	{
	case(QR_KEYDOWN):
	    keys_down[event -> keysym] = true;
	    break;
	case(QR_KEYUP):
	    keys_down[event -> keysym] = false;
	    break;
	}

/*
Next we get the location and rotation from the scene node.
*/
	vector2d_f pos  = node -> get_location();
	float rot       = (node -> get_rotation() + 90) / (180 / 3.142);

/*
Now we calculate a vector pointing in the forward direction
of the scene node.
*/
	vector2d_f forw = vector2d_f((cos(rot) * 0.003) * time_delta, (sin(rot) * 0.003) * time_delta);

/*
Next we check to see what keys are currently pressed, and
calculate the scene nodes new location and rotation.
*/
	if(keys_down[QRK_RIGHT])
	{
	    rot -= 0.002 * time_delta;
	}

	if(keys_down[QRK_LEFT])
	{
	    rot += 0.002 * time_delta;
	}

	if(keys_down[QRK_UP])
	{
	    pos = vector2d_f(pos.X - forw.X, pos.Y - forw.Y);
	}

	if(keys_down[QRK_DOWN])
	{
	    pos = vector2d_f(pos.X + forw.X, pos.Y + forw.Y);
	}

/*
After we have calculated the nodes new potion all that is
left to do in the event receiver is apply it to the scene
node and return true to inform the engine that it should
not quit.
*/
	node -> set_rotation((rot * (180 / 3.142)) - 90);
	node -> set_location(pos);

	return true;
    }
};

int main()
{
/*
Like in the other tutorials we set up the renderer.
*/
    renderer = new qr_renderer(vector2d_i(16, 9),
	10.0 ,false ,vector2d_i(0, 0));

    qr_resource_manager *res_man = renderer ->
	get_resource_manager();

    renderer -> set_window_title("Event System - Quad-Ren 0.4");

/*
Like the animation example, we load a space image for the background
from a PNG image and attach it to the background quad.
*/
    qr_sprite *background = new qr_sprite(res_man, 1);

    background -> load_png_frame(
	"../media/star_background.png", 1);

    background -> convert_data();
    renderer -> set_bg_sprite(background);

/*
Now we load the sprite for the space ship from a QRDD file.
*/
    qr_sprite *ship_sprite;
    ship_sprite = qrdd_file_handler::load_sprite(res_man, "../media/pod.QRDD");

/*
Next we create a quad for the space ship and attach the sprite
to it. We also rotate it by 180 degrees to make it point Upwards.
*/
    qr_scene_node *ship = new qr_quad(res_man);
    ship -> set_sprite(ship_sprite);
    ship -> set_rotation(180);

/*
Here we create an instance of our event receiver and attach it 
to the space ship quad.
*/
    qr_event_receiver *receiver = new new_event_receiver();
    ship -> set_event_receiver(receiver);

/*
As per usual, we run the renderer inside a while loop.
*/
    float frame = 1;
    while(renderer -> run())
    {
/*
We get the time delta for frame rate independent animation.
*/
	float time_delta = renderer -> get_time_delta() / 10;

/*
Next we increment the frame count, multiplied by the time delta
to be frame-rate independent. We also set the frame to 1 if it
goes over 20 to make the animation loop.
*/
	frame += 0.32 * time_delta;
	if(frame > 20)
	    frame = 1;

	ship -> set_frame(frame);
    }

/*
Drop the renderer on exit.
*/
    renderer -> drop();
}[/PHP]

---

### Post by cmay on 2009-04-11
that looks ok too. 
[FONT=monospace] [/FONT]i could read it all and test drive the tutorial if you have some where i can get it.
i would like to do that as i am learning c right now and i could learn something from the practice.  

if there is a place to download it i would be happy to go over it and let you know how it is learning from it from a newbies point of view. 
but it looks good so far.

---

### Post by sujoy on 2009-04-11
@cmay
see his sig, for download location!

@hessiess
yes the documentation looks quite good so far :)

---

### Post by hessiess on 2009-04-11
> **cmay said:**
> that looks ok too. 
[FONT=monospace] [/FONT]i could read it all and test drive the tutorial if you have some where i can get it.
i would like to do that as i am learning c right now and i could learn something from the practice.  

if there is a place to download it i would be happy to go over it and let you know how it is learning from it from a newbies point of view. 
but it looks good so far.

The tutorials are for vers 0.4, which is in SVN/ just about to be released, you can download the source from the SVN repository with the flowing command.

```

svn co https://quad-ren.svn.sourceforge.net/svnroot/quad-ren/qr_0.2

```

to compile cd into the qr_0.2 directory and run:

```

./setup.sh

```

then run the useural:
```

./configure
make
sudo make install

```

You will need automake, autoconf, libtool, libpng, sdl and the opengl headers to compile the lib from SVN.

```

sudo apt-get install build-essential automake autoconf libtool libpng-dev sdl-dev glutg3-dev

```
(the package names should be about right (im using Arch right now))

The source code and animations for the examples can be downloaded from the following directory in SVN.
```

svn co https://quad-ren.svn.sourceforge.net/svnroot/quad-ren/examples

```

---

### Post by cmay on 2009-04-11
thanks. i will try to get this downloaded later on tonight. i will post here when i been trough it.

---

### Post by hessiess on 2009-04-13
QR 0.4 has bean released, you con download the deb if you wish.

---

### Post by cmay on 2009-04-13
thanks. 
i already did that. i had some problems getting the libpng package installed but last night i read trough all the sources in the 0.3 package from your website. 
it is very well documented and it looks good. i can get something out of studying it too. 
good luck with the project.

---

