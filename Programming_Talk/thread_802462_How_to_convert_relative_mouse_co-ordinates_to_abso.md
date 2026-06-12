---
title: "How to convert relative mouse co-ordinates to absolute co-ordinates?"
date: 2008-05-21
forum: Programming Talk
---

### Post by montylee on 2008-05-21
Hi there!

I want to record and play mouse events on my Linux machine.
Basically i store all the mouse events entered by the user into a text file. For this, i am simply reading the device file: /dev/input/event1 using read() and storing the events into a text file. While playback i read() the text file and write() the events to the device file /dev/input/event1.


Here's my code:

**Recording**
```
FILE *deviceConnection,*record_file;
struct input_event myEvent;

deviceConnection = fopen(argv[1], "rw");
record_file = fopen(argv[2], "rw+");

while (1) {
	printf(".");
        // read from the device file into the input_event structure */
	fread(&myEvent, sizeof(struct input_event), 1, deviceConnection);
	// Write the events to the text file */
       fwrite(&myEvent, sizeof(struct input_event), 1, record_file);
       fflush(record_file);		
}
fclose(deviceConnection);
fclose(record_file);

```

**Playback**

```
FILE *record_file;
struct input_event myEvent;
char filename[128] ;
int devHandle = -1;

devHandle = open(argv[1], O_RDWR);
record_file = fopen(argv[2], "r+");

while (!feof(record_file))
{
	fread(&myEvent, sizeof(struct input_event), 1, record_file);
	if (myEvent.value != 0) {
		printf ("We are in Key Press \n");
		write(devHandle, &(myEvent), sizeof(struct input_event);
	}
}

close (devHandle);
fclose(record_file);

```

Now, i am able to record and play the mouse events but while playback the mouse events are played relative to the current mouse position. This is because a standard mouse supports only relative events (A mouse supports key events: EV_KEY and Relative events: EV_REL). 

Note: Absolute events (EV_ABS) are supported by pointing devices like joysticks etc.

Now, i want to get absolute mouse co-ordinates so that the mouse events can be played accurately irrespective of the current mouse position.

How can i achieve this? Can i convert the relative mouse position to absolute position?

---

### Post by montylee on 2008-05-22
:( no replies :(
common guys help me please.
I think to solve this problem i only need to save the exact mouse pointer position at the time when recording is started. Then i can simply record the relative events as i am doing now and compute the absolute co-ordinates by adding them to the initial mouse pointer position.

The problem is how can i get the exact initial mouse co-ordinates when the recording is started...

Any ideas?

---

### Post by soapytheclown on 2008-05-22
a very quick cut and paste job from a program i wrote to use my wii remote to control my mouse, these are the main parts that i used to make the mouse move to absolute co-ordinates on the screen. Hope You can understand them and use it in what you're doing :)

[PHP]
//includes
#include <X11/Xlib.h>
#include <X11/keysym.h>
#include <X11/extensions/XTest.h>

        //need to set these 2 to values
        int mouse_x; 
        int mouse_y;

	//open display
	Display *display = XOpenDisplay(0);
	
	//test for display
	if(!(display=XOpenDisplay(NULL))){
		printf("Could Not Open Display");
		exit(1);
	}
        
        //actual movement
        XTestFakeMotionEvent(display, -1,  mouse_x,  mouse_y, 0);
        //console feedback
        printf("X: %i, Y: %i\n",mouse_x, mouse_y );
        //close display
        XCloseDisplay(display);
[/PHP]

note: you'll need libx11-dev libxcb-xtest0-dev (i think) for this to work

---

### Post by montylee on 2008-05-23
Thanks for the reply!

oops, i can't really use X11 stuff for this. I have to use only low level APIs.

I researched around a bit and i think that getting absolute coordinates is not possible without using X11 APIs.

---

