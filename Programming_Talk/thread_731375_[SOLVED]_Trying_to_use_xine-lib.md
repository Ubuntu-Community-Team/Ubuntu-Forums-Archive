---
title: "[SOLVED] Trying to use xine-lib"
date: 2008-03-21
forum: Programming Talk
---

### Post by t3hi3x on 2008-03-21
I'm working on a program that uses xine-lib. 

Here is an excerpt from the xine.h file

[PHP] int xine_get_pos_length (xine_stream_t *stream,
 int *pos_stream, /* 0..65535 */
 int *pos_time, /* milliseconds */
 int *length_time) /* milliseconds */ [/PHP]

When I try to use this function, I get a segment dump error. I make sure  I declare the int-s.

This is the line of code that does it:

[PHP]xine_get_pos_length(stream, posStream, pos, length);[/PHP]

G++ compiles it just fine, but when the program gets to that line, it bites the dust.

Also have a second question - what is the diffrence in calling out a pointer verses an array?

Array  = int* hi
Pointer = int *hi

is that right?

---

### Post by WW on 2008-03-21
> **t3hi3x said:**
> 
[PHP]xine_get_pos_length(stream, posStream, pos, length);[/PHP]

G++ compiles it just fine, but when the program gets to that line, it bites the dust.

We'll need more information.  How do you declare and initialize the variables **stream**, **posStream**, **pos** and **length**?

---

### Post by t3hi3x on 2008-03-22
Just like the function says:

[PHP]int *posStream;
int *pos;
int *length;
	
xine_get_pos_length (stream, posStream, pos, length);[/PHP]

::EDIT::

Here's the entire code. You need libxine-dev to compile it.

[PHP]#include <unistd.h>
#include <stdlib.h>
#include <xine.h>
/*#include <iostream>*/

#define MRL "mms://jbuflashradio.com/wmatest/"

/*using namespace std;*/

int main(int argc, char *argv)
{
	char *mrl = MRL;

	xine_t *engine;
	xine_audio_port_t *ap;
	xine_video_port_t *vp;
	xine_stream_t *stream;

	engine = xine_new();
	xine_init(engine);
	
	ap = xine_open_audio_driver(engine, NULL, NULL);
	vp = xine_open_video_driver(engine, NULL, XINE_VISUAL_TYPE_NONE, NULL);

	stream = xine_stream_new(engine, ap, vp);

	xine_open(stream, mrl);

	xine_play(stream, 0, 0);
	
	int *posStream;
	int *pos;
	int *length;
	
	
	xine_get_pos_length (stream, posStream, pos, length);


		sleep(10);
	/*cout << "Time = " << pos << " of " << length << "\n";*/

	
	xine_close(stream);

	xine_close_audio_driver(engine, ap);
	xine_close_video_driver(engine, vp);
	xine_exit(engine);

	return 0;
}[/PHP]

---

### Post by WW on 2008-03-22
I don't know if this is your problem, but it would probably be a good idea to be sure xine_open succeeded before continuing to xine_play or xine_get_pos_length.  See, for example, the sample code muxine.c that you can find here: [http://xinehq.de/index.php/samplecode](http://xinehq.de/index.php/samplecode)

---

### Post by t3hi3x on 2008-03-22
Indeed a good idea, but no cigar on fixing it. Still does that Segmentation Failure Core Dump.

What does that mean anyway?

---

### Post by t3hi3x on 2008-03-22
Got it! I took apart Kaffiene, and found where it was at:

[PHP]	
	int posStream;
	int pos;
	int length;
	
	sleep(20);
	
	if( xine_get_pos_length (stream, &posStream, &pos, &length) )
	{ cout << "Time = " << pos << " of " << length << "\n"; }[/PHP]

Thanks for the helps.

Does anyone know why I need the &'s and not the *'s up on the declarations?

---

### Post by WW on 2008-03-22
Ah, I see.  In your first version, you have pointers to integers, but you never actually allocated memory for the integers.  The library function tried to dereference your pointers in order to store values in the integers, but since there was no actual memory allocated for them,  you got a seg fault.

The second defines the integers, and then passes the addresses to the function--that's what the & character is for.

---

### Post by t3hi3x on 2008-03-22
Why does the function have pointers to integers? Wouldn't it just be easier to make them regular ints?

---

### Post by WW on 2008-03-22
Presumably the function is changing the values and returning them to you.  I don't have the docs--what do they say?  If the arguments were just ints, the function could not change the values in the calling program.  C passes arguments to functions using "call-by-value", so to change a variable, you have to pass a pointer to the variable.

---

### Post by t3hi3x on 2008-03-22
That does indeed make sense. Thanks for the insight. It seems, I never will not learn something in C/C++ :)

---

