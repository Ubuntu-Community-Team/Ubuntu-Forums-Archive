---
title: "*** glibc detected *** ./a.out: realloc(): invalid next size: 0x087901c8 ***"
date: 2009-08-18
forum: Programming Talk
---

### Post by tom66 on 2009-08-18
I get an error when running my program:

```

	/* snip... */
	
	/* Then, we need to read the additional archives, up to 999. */
	_rar_data->_fp_extra_count = 0;
	while (_rar_data->_fp_extra_count <= 999) {
		sprintf(volume_buffer, "%s.part%03d.rar", volume_name, _rar_data->_fp_extra_count);
		printf("stat: %s", volume_buffer);
		
		/* Check if file exists using stat. If it doesn't, stop looking for files. */
		if (stat(volume_buffer, &statbuf) == -1) {
			printf(" -- no file: End search\n", volume_buffer);
			//break;
		}
		
		tfp = fopen(volume_buffer, "r");
		printf("alloc: %d .. %d\n", sizeof(FILE *) * _rar_data->_fp_extra_count, _rar_data->_fp_extra_count);
		_rar_data->_fp_additional = (FILE **)realloc(_rar_data->_fp_additional, sizeof(FILE *) * _rar_data->_fp_extra_count);			
		_rar_data->_fp_additional[_rar_data->_fp_extra_count] = tfp;
		_rar_data->_fp_extra_count++;
	}
	
	/* snip... */

```

The output is:

```

stat: test.part000.rar -- no file: End search
alloc: 0 .. 0
stat: test.part001.rar -- no file: End search
alloc: 4 .. 1
stat: test.part002.rar -- no file: End search
alloc: 8 .. 2
stat: test.part003.rar -- no file: End search
alloc: 12 .. 3
stat: test.part004.rar -- no file: End search
alloc: 16 .. 4
*** glibc detected *** ./a.out: realloc(): invalid next size: 0x087901c8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cbf454]
/lib/tls/i686/cmov/libc.so.6[0xb7cc30b1]
/lib/tls/i686/cmov/libc.so.6(realloc+0x106)[0xb7cc3de6]
./a.out[0x8048b88]
./a.out[0x8048cb1]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c66685]
./a.out[0x8048821]

...

```

Why is it able to allocate 5 entries but then gives up?

---

### Post by dwhitney67 on 2009-08-18
A problem I see is that realloc() expects to reallocate memory for a pointer that is already pointing to allocated memory.

Because you provided only a snip of your program, I cannot ascertain if you have initialized _rar_data->_fp_additional to anything other than null.

Perhaps consider something like:
```

_rar_data->_fp_additional  = 0;
_rar_data->_fp_extra_count = 0;
...
while (_rar_data->_fp_extra_count <= 999) {
   FILE* tfp = fopen(volume_buffer, "r");

   if (!tfp) continue;   // don't rely on stat(); the file could be deleted from the system between its use and fopen().

   ++_rar_data->_fp_extra_count;

   if (_rar_data->_fp_additional == 0) {
      _rar_data->_fp_additional = malloc(sizeof(FILE*));
   }
   else {
      _rar_data->_fp_additional = realloc(_rar_data->_fp_additional, sizeof(FILE *) * _rar_data->_fp_extra_count);
   }		

   _rar_data->_fp_additional[_rar_data->_fp_extra_count -1] = tfp;
}

```

P.S.  Do you not feel that the underscore character in your variable names makes readability easier or harder?  I vote for the latter.

---

### Post by tom66 on 2009-08-18
I use underscores to differentiate member variables and local variables, otherwise they get mixed up.

Anyway, here is the code that should matter. I'm writing a library to decode RAR files...

archive.cpp
```

#include "archive.hpp"

RARArchive::RARArchive()
{
	_file_version = 3000; 			/* The archive version. Currently restricted to RARv3 (3000). */
	_error_state = 0;		 		/* The error state, currently no error. */
	
	/* The RAR data needs to be initialized. */
	_rar_data = new RARArchiveData;
	_rar_data->_fp = NULL;
	_rar_data->_fp_additional = NULL;
	_rar_data->_fp_extra_count = 0;
}

RARArchive::~RARArchive()
{
	fclose(_rar_data->_fp); 
	delete _rar_data;
}

// --------------------------------------------------------
//  Initialize the RAR archive with a file pointer and 
//  file name. Try to open up all splits, if they exist. 
//  Then proceed to read the header and information about 
//  the archive. 
// --------------------------------------------------------
void RARArchive::init_archive(FILE *fp, const char *file_name)
{
	char *volume_name, *volume_buffer;
	int c, i = 1;
	FILE *tfp;
	struct stat statbuf;
	
	_rar_data->_fp = fp;
	if (_rar_data->_fp == NULL) {
		_error_state = ERR_FILE_IO;
		return;
	}
	
	/* Allocate space for various buffers. */
	volume_name = new char[strlen(file_name) - 4];			/* file_name_without_extension */
	volume_buffer = new char[strlen(file_name) + 12];		/* file_name_without_extension.partNNN.rar */
	
	/* Are there any additional archives? The format is "archivename.partNNN.rar". 
	 * We need to figure out the volume_name. */
	for (c = 0; c < strlen(file_name); c++) {
		if (file_name[c] == '.')
			break;
		sprintf(volume_name, "%s%c", volume_name, file_name[c]); /* There *must* be a better way to do this! */
	}
	
	/* Then, we need to read the additional archives, up to 999. */
	_rar_data->_fp_extra_count = 0;
	while (_rar_data->_fp_extra_count <= 999) {
		sprintf(volume_buffer, "%s.part%03d.rar", volume_name, _rar_data->_fp_extra_count);
		printf("stat: %s", volume_buffer);
		
		/* Check if file exists using stat. If it doesn't, stop looking for files. */
		if (stat(volume_buffer, &statbuf) == -1) {
			printf(" -- no file: End search\n", volume_buffer);
			//break;
		}
		
		tfp = fopen(volume_buffer, "r");
		printf("alloc: %d .. %d\n", sizeof(FILE *) * _rar_data->_fp_extra_count, _rar_data->_fp_extra_count);
		_rar_data->_fp_additional = (FILE **)realloc(_rar_data->_fp_additional, sizeof(FILE *) * _rar_data->_fp_extra_count);			
		printf("ptr from realloc: %p\n", _rar_data->_fp_additional);
		*_rar_data->_fp_additional[_rar_data->_fp_extra_count] = &tfp;
		_rar_data->_fp_extra_count++;
	}
	
	/* Read the first 7 bytes (the marker bytes) of the master archive and verify them. */
	fseek(_rar_data->_fp, 0, SEEK_SET);
	fread(_marker, 7, 1, _rar_data->_fp);
	if (strcmp(_marker, RAR_MARKER) != 0) {
		_error_state = ERR_INVALID_MARKER;
		return;
	}
}

// --------------------------------------------------------
//  Return a string representing the current error code.
// --------------------------------------------------------
const char* RARArchive::get_error_string()
{
	switch(this->get_error())
	{
		case 0: 		return "No error";
		case 8100: 		return "Invalid or corrupt file marker (damaged archive?)";
		case 8101: 		return "Bad CRC32 code (damaged archive?)";
		case 8102: 		return "Out of memory";
		case 8103: 		return "General file I/O error";
		default: 		return "Unknown error";
	}
}

```

archive.hpp
```

/* Error codes. */
#define ERR_INVALID_MARKER 		8100
#define ERR_INVALID_CRC			8101
#define ERR_MEMORY				8102
#define ERR_FILE_IO				8103

/* A 7-byte marker sequence. */
const char RAR_MARKER[7] = "Rar!\x1a\x07"; // NULL byte is assumed.

/* The CRC32 polynominal. */
const int32_t CRC32_POLY = 0xedb88320;

class RARArchive
{
private:
	/* The archive version. Currently restricted to RARv3 (3000). */
	int _file_version;
	
	/* The marker block (7 bytes). For good archives this should be RAR_MARKER. */
	char _marker[7];
	
	/* The archive reader/writer error state, if any. */
	int _error_state;
	
	/* The RARArchive data. */
	RARArchiveData *_rar_data;
	
	/* Entries for each file or folder in the archive. The pointer refers to 
	 * the first file in the archive. */
	RARArchiveFile *_file;

public:
	RARArchive();
	~RARArchive();
	
	/* Opens an archive given by a file pointer. If an error occurs, the error
	 * state is set and nothing further happens. */
	void init_archive(FILE *fp, const char *file_name);
	
	/* Gets the error state and returns it in some form. */
	int get_error() { return _error_state; }
	const char *get_error_string();
};


```

archive-data.hpp
```

/* This class stores the data for a RARArchive. It's used so multiple
 * classes can access it easily. */
class RARArchiveData
{
public:
	/* The file pointer to the FIRST archive (and sometimes the only one). 
	 * This could be a temporary file, which we use as a scratch space. */
	FILE *_fp;
	
	/* The file pointers to additional archives. (Archives can be split.) */
	FILE **_fp_additional;
	int _fp_extra_count;
};

```

---

### Post by dwhitney67 on 2009-08-18
> **tom66 said:**
> I use underscores to differentiate member variables and local variables, otherwise they get mixed up.
...
I thought you were writing code in C.  What the flock are you using realloc() and fopen() for??

Use 'new' to allocate memory for your app (and obviously 'delete' to free the memory).  Use 'fstream' to obtain a file handle.

And as for using an array, use an STL vector instead.

Anyhow, I hope my suggestion provided earlier helps you get past your current hurdle.

P.S.
```

#include <vector>
#include <fstream>

std::vector<std::fstream*> files;

while (files.size() <= 999) {
   std::fstream* rarFile = new std::fstream(volume_buffer, std::ios::in);

   if (rarFile && *rarFile) {   // check pointer and verify file was opened.
      files.push_back(rarFile);
   }
   else {
      break; // in case you don't find 1000 files.
   }
}

```

---

### Post by tom66 on 2009-08-18
I prefer mixing the two useful features of both languages: the powerful classes of C++, with the powerful memory operations of C.

I'll try your suggestions. Thanks.

---

### Post by pepperphd on 2009-08-19
Those memory operations frustrated you to the point of posting on this forum.  Sometimes stability is worth losing a few milliseconds of execution time.

---

### Post by nvteighen on 2009-08-19
> **tom66 said:**
> I prefer mixing the two useful features of both languages: the powerful classes of C++, with the powerful memory operations of C.


Ok, if that's what you want, then you want Objective-C (not kidding).

C++'s goals, no matter whether you like the language or not (I hate it), are not to be just a "C with Classes"... But that's ObjC's design principle, actually.

---

