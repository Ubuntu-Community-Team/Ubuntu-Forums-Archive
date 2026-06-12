---
title: "[C] Get stream lenght. How?"
date: 2009-04-19
forum: Programming Talk
---

### Post by roccivic on 2009-04-19
Hi all,

I'm looking for way of getting the length of a file in bytes in C (not the space it uses on the storage device, just the actual size of the file).
So far I came up with with the example program below. It works just fine, but it's slow. What I do is scan through the whole stream until I bump into EOF, and on a 1GB file this takes about a minute on my machine.

Is there an easier way?

Thanks, Rouslan

```
#include <stdio.h>

long	fsiz = 0;

long	get_file_size( char *filename ) {
	FILE	*input;

	input = fopen( filename, "rb" );
	while ( 1 ) {
		if ( fgetc( input ) == EOF ) {
			fsiz = ftell( input );
			rewind( input );
			return fsiz;
		}
	}
	fclose( input );
}

int	main( int argc, char *argv[] ) {
	if ( argc != 2 ) {

		printf( "Usage: %s filename...\n", argv[0] );
		return 1;

	}
	else {
		printf( "File %s is %ld bytes long.\n", argv[1], get_file_size( argv[1] ) );
		return 0;

	}
}
```

---

### Post by cb951303 on 2009-04-19
you can use fseek and ftell

```

fseek(stream, 0, SEEK_END);
long int fileSize = ftell(stream);

```

---

### Post by roccivic on 2009-04-19
Is that cross-platform and will it work for both text and binary files?

Thanks ;)

---

### Post by cb951303 on 2009-04-19
> **roccivic said:**
> Is that cross-platform and will it work for both text and binary files?

Thanks ;)

they are standard library functions so yes it's cross platform. if not your compiler suite sucks :)

with binary files there are no problems. fseek works ok with text as long as offset is 0.

ftell may not give the right answer for text files but since you used it on your own code I figured you are aware of it.

EDIT: if you only need to know the file size, you may open text files as binary too. that would solve your problem.

---

