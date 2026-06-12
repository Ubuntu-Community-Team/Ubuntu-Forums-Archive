---
title: "fgets cant read string object"
date: 2007-08-21
forum: Programming Talk
---

### Post by desijays on 2007-08-21
I cant seem to read info from a file into a string object using fgets? 

Could someone point out the problem to me? Heres the code..Its quite small

```

ptr_ArtAsset = fopen( "C:\\Desktop\\DESKTOP\\SDL\\Debug\\resource.txt", "rt" );

	if( ptr_ArtAsset )
		std::cout << "file opened\n";


	fgets( const_cast<char *>(obj_path.c_str()), obj_path.capacity(), ptr_ArtAsset );
	std::cout << obj_path;

	if( !(fclose( ptr_ArtAsset )) )
		std::cout << "file closed\n";

```

Or if not 'fgets'.......is there any other alternative?

---

### Post by aks44 on 2007-08-21
> **desijays said:**
> Could someone point out the problem to me? Heres the code..Its quite small

```
const_cast<char *>(obj_path.c_str())
```

The prototype of c_str() is **const char* std::string::c_str() const** for a good reason.

Note the two **const**s, they mean that:
1) c_str() does not modify the object (this is the second const at the end of the definition)
2) it returns a **pointer to const** characters, ie. you MUST NOT even try to modify the pointed-to data.

Again, the compiler gave you an error for a good reason. Getting rid of an error in the dirtiest way (here, a cast) is generally not the way to go.

Your problem comes from the fact that you're trying to mix C code with C++.
Get rid of those fopen / fgets / fclose, and use **ifstream** (in <iostream>) as your input file. ;)


If you have a C background as I suspect, I'd recommend you to unlearn C for a moment, until you can really grasp C++ concepts. Just because C++ can do the same as C and way more doesn't mean the C concepts must be used blindly.

BTW [Bruce Eckel's Thinking in C++]("http://mindview.net/Books/TICPP/ThinkingInCPP2e.html") might be a good read for you (and it is available both as hard cover and as a PDF download).

---

### Post by manimal on 2007-08-21
Does the code output anything?  I am not so familiar with C++, but this C code works for me:

```
#include <stdio.h>
#include <stdlib.h>

#define STR_LEN 1000

int main() {
	FILE *ptr_ArtAsset=NULL;
	char str[STR_LEN];

	ptr_ArtAsset = fopen( "Put_file_name_here", "rt" );

	if( ptr_ArtAsset )
		printf("file opened\n");

	while (!(feof(ptr_ArtAsset))) {
		fgets( str, STR_LEN, ptr_ArtAsset );
		printf("%s",str);
	}

	if( !(fclose( ptr_ArtAsset )) )
		printf("file closed\n");
		
	return EXIT_SUCCESS;
}
```

I agree with the above poster that you should really try to avoid mixing C and C++ unless you know what you are doing.  I think my advice might be to forget all the C++ nonsense though and just use plain C. :)

---

