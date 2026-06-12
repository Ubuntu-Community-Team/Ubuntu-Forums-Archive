---
title: "I can't figure out why this is segfaulting for the life of me (C++)"
date: 2007-07-06
forum: Programming Talk
---

### Post by danhm on 2007-07-06
For one of my astronomy professors, I'm writing a small program in C++ that takes a whole bunch of data points  from satellites and formats them into something ArcMap (GIS software) can use. There are three files that are read in -- a file containing longitudes, a file containing latitudes, and a file contain some sort of data about the perspective lat/lon point (right now it is albedo values, but could be anything). 

Currently, my program can successfully read in the files, "guess" what any missing longitude or latitude value should have been (sometimes the satellite returned something that wasn't a number when it should have), and I can output these values into a simple list format (ID #, Longitude, Latitude, Data newline). The problem arises when I try to output these into a "box" format. They are a little more complicated than the list. They are listed as:

ID #, Top left lon, data value
top right lon, top right lat
bottom right lon, bottom right lat
bottom left lon, bottom left lat
END

I think that should be enough background information. If not, feel free to ask me for more.

The offending code (with some extra cout statements I left in for debugging the segfault) is:

```

//This takes an integer, which is really a location in formatted. It assumes that the point given to it is

//the top left corner of the box it makes up. It gets its neighboring points and stores them to be ouput

//later. Should the point fall in the right-most column or the bottom row (places where there are no points

//to the right or below it), this will project points to be used, so a box can still be drawn.

void merger :: makeBoxes (int whichone) {

	cout << "on try #" << whichone << endl;



	/*	

	+1 moves to the right by one. -1 moves to the left by one

	+WIDTH moves directly below. -WIDTH moves directly above.

	*/



	if( whichone+WIDTH < MAX - 1 && !onRight(whichone)){

		cout << "made it in\n";

		data_points[whichone].topleftLon     = data_points[whichone].longitude_point;

		data_points[whichone].topleftLat     = data_points[whichone].latitude_point;

		data_points[whichone].toprightLon    = data_points[whichone+1].longitude_point;

		data_points[whichone].toprightLat    = data_points[whichone+1].latitude_point;

		data_points[whichone].bottomleftLon  = data_points[whichone+WIDTH].longitude_point;

		data_points[whichone].bottomleftLat  = data_points[whichone+WIDTH].latitude_point;

		data_points[whichone].bottomrightLon = data_points[whichone+WIDTH+1].longitude_point;

		data_points[whichone].bottomrightLat = data_points[whichone+WIDTH+1].latitude_point;

		

	}

	

	else if ( ((whichone+WIDTH) < (MAX - 1)) && onRight(whichone)){

		data_points[whichone].topleftLon     = data_points[whichone-1].longitude_point;

		data_points[whichone].topleftLat     = data_points[whichone-1].latitude_point;

		data_points[whichone].toprightLon    = data_points[whichone].longitude_point;

		data_points[whichone].toprightLat    = data_points[whichone].latitude_point;

		data_points[whichone].bottomleftLon  = data_points[whichone+WIDTH-1].longitude_point;

		data_points[whichone].bottomleftLat  = data_points[whichone+WIDTH-1].latitude_point;

		data_points[whichone].bottomrightLon = data_points[whichone+WIDTH].longitude_point;

		data_points[whichone].bottomrightLat = data_points[whichone+WIDTH].latitude_point;

	}

		

	else if ( ((whichone+WIDTH) > (MAX-1)) && !onRight(whichone)){

		data_points[whichone].topleftLon     = data_points[whichone-1].longitude_point;

		data_points[whichone].topleftLat     = data_points[whichone-1].latitude_point;

		data_points[whichone].toprightLon    = data_points[whichone].longitude_point;

		data_points[whichone].toprightLat    = data_points[whichone].latitude_point;

		data_points[whichone].bottomleftLon  = data_points[whichone-WIDTH].longitude_point;

		data_points[whichone].bottomleftLat  = data_points[whichone-WIDTH].latitude_point;

		data_points[whichone].bottomrightLon = data_points[whichone-WIDTH-1].longitude_point;

		data_points[whichone].bottomrightLat = data_points[whichone-WIDTH-1].latitude_point;

	}

	

	else if ( ((whichone+WIDTH) > (MAX-1)) && onRight(whichone)){

		data_points[whichone].topleftLon     = data_points[whichone-1].longitude_point;

		data_points[whichone].topleftLat     = data_points[whichone-1].latitude_point;

		data_points[whichone].toprightLon    = data_points[whichone].longitude_point;

		data_points[whichone].toprightLat    = data_points[whichone].latitude_point;

		data_points[whichone].bottomleftLon  = data_points[whichone-WIDTH].longitude_point;

		data_points[whichone].bottomleftLat  = data_points[whichone-WIDTH].latitude_point;

		data_points[whichone].bottomrightLon = data_points[whichone-WIDTH-1].longitude_point;

		data_points[whichone].bottomrightLat = data_points[whichone-WIDTH-1].latitude_point;

	}



}

//Is it on the right-most column?
bool merger :: onRight(int whichone) {

	cout << "start " << whichone << endl;

	if (whichone % WIDTH == 0) { //if this is true, it is on the right most column.

		cout << "true\n";

		return true;

		}

	cout << "false\n";

	return false;

}  		


```

data_points is an array of a struct I made, whichone is the location in the array, and WIDTH is how many data points per row.

When I try to run it, it does not get very far.
```

on try #0
start 0
true
start 0
true
Segmentation fault (core dumped)
```


I've been looking at this code for about a day now, and I can't figure out what's happening. I know it isn't going out of the array since I've made it much bigger than it would ever have to be (25,000 when I know it is supposed to be 5,563).

Does anyone have any suggestions? It's really appreciated.

---

### Post by Mr. C. on 2007-07-06
Stop guessing - start using a debugger to check values at the time of the segfault.

MrC

---

### Post by Soybean on 2007-07-06
I agree with Mr. C -- segfaults can be really hard to fix without a debugger. You don't need anything too fancy; I use gdb, and I barely know how to use it. ;) Compile with -g, and then run your program in gdb... when it segfaults, it will tell you where it failed. If it happens to be inside some standard library function or whatever, you can type "up" to go up through the call stack until you're back in your own code. Depending on how it happened, you may also be able to "print X" where X is any of your variables, to see the values that things had when it got to that point. I'm sure it can do some more advanced things too, but that's all I've ever needed.

---

### Post by danhm on 2007-07-06
Thanks for the quick replies.

I'm a little confused about using GDB -- can either of you recommend a guide for it?

---

### Post by Soybean on 2007-07-06
Well, the manual [http://sourceware.org/gdb/current/onlinedocs/gdb_toc.html](http://sourceware.org/gdb/current/onlinedocs/gdb_toc.html) covers everything about it, but it's probably more than you need.

I did a bit of looking around and found this: [http://unknownroad.com/rtfm/gdbtut/gdbtoc.html](http://unknownroad.com/rtfm/gdbtut/gdbtoc.html)
It's a tutorial in question/answer format, and down near the bottom it has a couple of examples, including an example of debugging a segmentation fault. :)

Even that one is a little more sophisticated than what I do, but being a little better than you need to be probably isn't a bad thing. ;)

---

### Post by public_void on 2007-07-06
You can get some GUI front ends for GDB if using the terminal version is tricky.

My guess is that when accessing an element in data_points your going out-of-bounds. Either going over the end or back passed the start, i.e. a minus element. 

A line like this may be the problem, "data_points[whichone-WIDTH-1]" is likely "data_points[-N]".
```
data_points[whichone].bottomrightLon = data_points[whichone-WIDTH-1].longitude_point;
```
Your'll need the debugger to check values.

---

### Post by Mr. C. on 2007-07-06
Start by compiling and loading your program with the -g option.  Then, run:


```
gdb /path/to/myprogram
```

and then

```
run
```

When your program crashes, start looking at the call stack to see where it crashes, and start examining the values of your variables.

The **help** command in GDB will get you the rest of the way.

MrC

---

### Post by danhm on 2007-07-06
Thanks everyone, that'll be handy next time.

Before I checked this thread again, I noticed that my last two else-if statements were redundant, removed them, and now it runs just fine.

---

### Post by Mr. C. on 2007-07-06
Be sure you actually removed the problem (you'll have to understand why it occurred), and not just swept it under the rug.

MrC

---

### Post by maddog39 on 2007-07-06
The debugger I use is called valgrind, and I'd highly recommend it and it helped me greatly in trying to find problems such as segfaults in my program. ([www.valgrind.org](www.valgrind.org))

Just run:
```

valgrind --log-file-exactly=output.txt /path/to/program

```

---

### Post by the_unforgiven on 2007-07-07
> **maddog39 said:**
> The debugger I use is called valgrind, and I'd highly recommend it and it helped me greatly in trying to find problems such as segfaults in my program. ([www.valgrind.org](www.valgrind.org))

Just run:
```

valgrind --log-file-exactly=output.txt /path/to/program

```
valgrind is **not** a debugger - it's a profiler and memory checker (with support for plugins to extend the basic profiling functionality). The most important functionality of a debugger is that it allows you to set breakpoints and step through the code (either one source code line at a time or one machine instruction at a time) which is not available with valgrind - at least as of now.

Here are links to the corresponding wikipedia pages:
[http://en.wikipedia.org/wiki/Debugger](http://en.wikipedia.org/wiki/Debugger)
[http://en.wikipedia.org/wiki/Profiler_%28computer_science%29](http://en.wikipedia.org/wiki/Profiler_%28computer_science%29)

[http://en.wikipedia.org/wiki/Valgrind](http://en.wikipedia.org/wiki/Valgrind)
[http://en.wikipedia.org/wiki/Gdb](http://en.wikipedia.org/wiki/Gdb)

HTH ;)

---

### Post by Modred on 2007-07-07
[quote=the_unforgiven]valgrind is not a debugger - it's a profiler and memory checker[/quote]
While your statement is correct, valgrind's memory checking can be very useful for ironing out mysterious segfaults.

At a bare minimum, valgrind's output could give you more specific information about the segfault so you have a better idea of where to place your breakpoints and what to look for in GDB.

---

