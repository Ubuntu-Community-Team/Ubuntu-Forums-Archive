---
title: "Code Sample: simple media player with MLT++"
date: 2009-05-30
forum: Programming Talk
---

### Post by skullmunky on 2009-05-30
I'm just excited I figured this out, since the documentation is a little sparse so far, and thought I'd share this fun little code snippet.  One of the things we all want to be able to do is play and manipulate video.  This is often a bit of a challenging task, but the MLT toolkit makes it very easy.  The MLT wiki has a simple video player example written in C; this is a conversion into C++ with the MLT++ library.  It just opens an SDL window and plays the video file you give it.  

To use MLT, you should probably be running 9.04 (or higher).  Install libmlt++-dev.  

Enjoy!  

```

/*

  MLT++ Player Example
  
  g++ simpleplayer.cxx -I/usr/include/mlt -I/usr/include/mlt++ -lmlt++ -lmlt -o simpleplayer

  Usage: simpleplayer <file>
  
  http://www.mltframework.org/twiki/bin/view/MLT/Framework
  
*/

#include <iostream>
#include <unistd.h>
#include <Mlt.h>

int main( int argc, char *argv[] )
{
  Mlt::Profile *profile;
  Mlt::Repository *repository;
  Mlt::Consumer *consumer;
  Mlt::Producer *producer;
  
  // get default profile  
  profile= new Mlt::Profile();
  
  // initialise the factory
  repository = Mlt::Factory::init();
  
  if (repository)
  {	
	// Create the default consumer
	consumer = new Mlt::Consumer( *profile,"sdl");

	// Create via the default producer
	producer = new Mlt::Producer( *profile,NULL, argv[ 1 ] );

	// Connect the producer to the consumer
	consumer->connect(*producer);

	// Start the consumer
	consumer->start();

	// Wait for the consumer to terminate
	while( !consumer->is_stopped() )
	    sleep( 1 );

	// Close the consumer
	delete(consumer);

	// Close the producer
	delete(producer);

	// Close the factory
	Mlt::Factory::close();
    }
    else
    {
	// Report an error during initialisation
	std::cerr << "Unable to locate factory modules\n";
    }

    // End of program
    return 0;
}

```

---

