---
title: "Getting bizarre values"
date: 2009-08-22
forum: Programming Talk
---

### Post by tom66 on 2009-08-22
I wrote a fast blitting library for working with PPMs:

```

#include <stdio.h>
#include <stdlib.h>

struct ppmRGB
{
	char r, g, b;
};

struct ppmdata
{
	int version;
	int width;
	int height;
	int max;
	struct ppmRGB *data;
};

void readPPM(FILE *fp, struct ppmdata *ppm)
{
	char linebuff[255];
	int counter = 0, exit = 0, maxv = -1;
	size_t size_alloc;
	
	if(ppm == NULL)
		return;
	
	ppm->version = 0;
	ppm->width = 0;
	ppm->height = 0;
	ppm->max = 0;
	ppm->data = 0;
	
	/* reset file pointer, and read header. */
	fseek(fp, 0, SEEK_SET);
	
	while(!feof(fp) && exit == 0)
	{
		fgets(linebuff, 250, fp);
		if(linebuff[0] == '#')
			continue; // it's a comment, skip it
		counter++;
				
		if(counter == 1)
		{
			// TYPE OF FILE (P1-P6). Currently only supported: P6.
			if(linebuff[0] == 'P' && linebuff[1] == '6')			
			{
				printf("set file version 6\n");
				ppm->version = 6;
			}
			else
			{
				fprintf(stderr, "invalid file version %s\n", linebuff);
				return;
			}
		}
		else if(counter == 2)
		{
			// WIDTH, HEIGHT for image.
			sscanf(linebuff, "%d %d", &ppm->width, &ppm->height);
			printf("got file dimensions %dx%d\n", ppm->width, ppm->height);
		}
		else if(counter == 3)
		{
			// Read max-value specification.
			sscanf(linebuff, "%d", &maxv);
			
			if(maxv == 255)
			{
				ppm->max = maxv;
				printf("read MAX-V %d\n", maxv);
			}
			else
			{
				fprintf(stderr, "invalid MAX-V %d\n", maxv);
				return;
			}
		}
		else if(counter > 3)
		{
			printf("end parsing header, now reading bytes\n");
			exit = 1;
		}
	}
	
	printf("FILE: version=%d, width=%d, height=%d, maxv=%d\n", ppm->version, ppm->width, ppm->height, ppm->max);
	
	// allocate a suitable structure for the pixel data, store it as one long chain of bytes.
	size_alloc = sizeof(struct ppmRGB *) * ppm->width * ppm->height;
	printf("allocating %d bytes, %d KB, %d MB for pixel data\n", size_alloc, size_alloc / 1024, size_alloc / 1024 / 1024);
	ppm->data = (struct ppmRGB *)malloc(size_alloc);
	printf(" ... OK\n");
}

void setPixelPPM(struct ppmdata *ppm, int x, int y, int r, int g, int b)
{
	ppm->data[(y * ppm->height) + x].r = r;
	ppm->data[(y * ppm->height) + x].g = g;
	ppm->data[(y * ppm->height) + x].b = b;
}

void writePPM(FILE *fp, struct ppmdata *ppm)
{
	printf("%d, %d : ppm->width, ppm->height\n", ppm->width, ppm->height);
	fprintf(fp, "P%d\n", ppm->version);
	fprintf(fp, "#\n");
	fprintf(fp, "%d %d\n", ppm->width, ppm->height);
	fprintf(fp, "%d\n", ppm->max);
}

int main(int argc, char *argv[])
{
	FILE *fp = fopen("input.ppm", "rb");
	struct ppmdata *ppm;
	int i;
	
	readPPM(fp, &ppm);
	
	for(i = 0; i < 100; i++)
	{
		printf("set pixel %d, %d\n", 10 + i, 10 + i);
		setPixelPPM(&ppm, 10 + i, 10 + i, 0xFF, 0xAA, 0xDD);
	}
	
	printf("write PPM data\n");
	
	fp = fopen("output.ppm", "wb");
	writePPM(fp, &ppm);
	printf("end write PPM data\n");
	fclose(fp);
	
	exit(0);
	return 0;
}

```

However, the ppm->width value is always random. ppm->height is correct. What's causing this?

Quick note: throughout the rest of the program, the width is correct. It's only until it comes to save, does it get corrupted.

---

### Post by PmDematagoda on 2009-08-22
I'm surprised that your program does not segfault because of this:-
```
int main(int argc, char *argv[])
{
	FILE *fp = fopen("input.ppm", "rb");
[COLOR="Red"]**	struct ppmdata *ppm;**[/COLOR]
	int i;
	
	readPPM(fp, [COLOR="Red"]**&ppm)**[/COLOR];
	
	for(i = 0; i < 100; i++)
	{
		printf("set pixel %d, %d\n", 10 + i, 10 + i);
		setPixelPPM(&ppm, 10 + i, 10 + i, 0xFF, 0xAA, 0xDD);
	}
	
	printf("write PPM data\n");
	
	fp = fopen("output.ppm", "wb");
	writePPM(fp, &ppm);
	printf("end write PPM data\n");
	fclose(fp);
	
	exit(0);
	return 0;
}
```
where you have a pointer to a variable that isn't initialised to NULL, which doesn't seem to have any known memory allocated to it and you are actually passing the memory location of the pointer instead of just a pointer which would be (struct ppmdata **ppm) and not the one specified in the function prototype.

Is it a mistake in the source you posted?

---

### Post by MadCow108 on 2009-08-22
it would be easier to help if we had the input file too.

what I see is this:
size_alloc = sizeof(struct ppmRGB *) * ppm->width * ppm->height;
here you allocate space for width*height pointers not structs
is that intended?

---

### Post by tom66 on 2009-08-22
@MadCow108: Yeah I noticed that and corrected that in the source file up there. It should be allocating for 3 bytes not 4 (for int pointers).

How do I initialise a single pointer? I always thought if you did this:

```

struct ABC { int a; char b; short c; }

void main()
{
   struct ABC *myabc;
   myabc->a = 553;
   printf("myabc->a = %d\n", myabc->a);
}

```

it was completely legal C (excluding the fact that main() should return int). So how to I allocate memory for a single pointer?

---

### Post by MadCow108 on 2009-08-22
either on stack:
```

struct bla a;
a.b=0;
struct bla *ptr_a = &a;

```
or on heap:
```

struct bla * ptr_a;
ptr_a = (struct bla*) malloc(sizeof(struct bla));
ptr_a->b=0;
...
free(ptr_a);

```

---

### Post by PmDematagoda on 2009-08-22
> **tom66 said:**
> @MadCow108: Yeah I noticed that and corrected that in the source file up there. It should be allocating for 3 bytes not 4 (for int pointers).

How do I initialise a single pointer? I always thought if you did this:

```

struct ABC { int a; char b; short c; }

void main()
{
   struct ABC *myabc;
   myabc->a = 553;
   printf("myabc->a = %d\n", myabc->a);
}

```

it was completely legal C (excluding the fact that main() should return int). So how to I allocate memory for a single pointer?
What you did above is definitely the first step for a segmentation fault(i.e,  accessing an incorrect part of memory).

In C, this would be how to initialise a pointer:-
```
struct ABC { int a; char b; short c; }

void main()
{
   struct ABC *myabc;
/* It may also be like this:-
 * struct ABC *myab = NULL;
*/
   myabc = NULL;

/* But the initialisation(above) is not essential if you atleast allocate memory for the structure before using it. */
   myabc = (struct ABC *) malloc ( sizeof(struct ABC) );

/* The below is fine, except you are almost guaranteed to get a garbage value and you seem to be misusing the type of char instead of using int. */
   printf("myabc->a = %d\n", myabc->a);
}
```

---

### Post by PmDematagoda on 2009-08-22
By the way, are you reading the errors and warnings that GCC is spewing out when you try and compile the program? Because I get this:-
```
ppm_stuff.c: In function ‘main’:
ppm_stuff.c:117: warning: passing argument 2 of ‘readPPM’ from incompatible pointer type
ppm_stuff.c:18: note: expected ‘struct ppmdata *’ but argument is of type ‘struct ppmdata **’
ppm_stuff.c:122: warning: passing argument 1 of ‘setPixelPPM’ from incompatible pointer type
ppm_stuff.c:95: note: expected ‘struct ppmdata *’ but argument is of type ‘struct ppmdata **’
ppm_stuff.c:128: warning: passing argument 2 of ‘writePPM’ from incompatible pointer type
ppm_stuff.c:102: note: expected ‘struct ppmdata *’ but argument is of type ‘struct ppmdata **’
```
even if I try and compile the program without the -Wall argument.

IMO, you should be vary of any warning that GCC spews out because that might mean that something in your program is bound to go wrong.

---

### Post by tom66 on 2009-08-22
Thanks, I think I know where I was going wrong now. GCC throws no warnings, even with -Wall.

---

### Post by PmDematagoda on 2009-08-22
> **tom66 said:**
> Thanks, I think I know where I was going wrong now. GCC throws no warnings, even with -Wall.

That is really strange, how are you compiling the program?

---

### Post by tom66 on 2009-08-22
No, I corrected the problems. "gcc test.c -Wall", no warnings. gcc 4.3.2.

---

### Post by PmDematagoda on 2009-08-22
> **tom66 said:**
> No, I corrected the problems. "gcc test.c -Wall", no warnings. gcc 4.3.2.

Well, I have GCC 4.4.1, but even your version of GCC should work, could someone else(MadCow108 ?) try compiling the OPs program and see?

The messages from GCC are really useful, and they can really help you to try and pin point where any problems in the program are coming from.

---

### Post by tom66 on 2009-08-22
I changed my pointer (in "main()"):
	struct ppmdata *ppm;
to:
	struct ppmdata ppm;

That solved the problem.

However I have another problem.

When I try to implement my getpixel routine:

```

struct ppmRGB getPixelPPM(struct ppmdata *ppm, int x, int y)
{
	return ppm->data[(y * ppm->height) + x];
}

```

I get a weird color: -1, -86, -35. This color is NOT one of the colors I set. I suspect it's similar to my other problem. So here is the full code, see if you can help out a real novice. (The only reason I'm using C is because I need it to be super-fast).

```

#include <stdio.h>
#include <stdlib.h>

struct ppmRGB
{
	char r, g, b;
};

struct ppmdata
{
	int version;
	int width;
	int height;
	int max;
	struct ppmRGB *data;
};

void readPPM(FILE *fp, struct ppmdata *ppm)
{
	char linebuff[255];
	int counter = 0, exit = 0, maxv = -1;
	size_t size_alloc;
	
	if(ppm == NULL)
		return;
	
	ppm->version = 0;
	ppm->width = 0;
	ppm->height = 0;
	ppm->max = 0;
	ppm->data = 0;
	
	/* reset file pointer, and read header. */
	fseek(fp, 0, SEEK_SET);
	
	while(!feof(fp) && exit == 0)
	{
		fgets(linebuff, 250, fp);
		if(linebuff[0] == '#')
			continue; // it's a comment, skip it
		counter++;
				
		if(counter == 1)
		{
			// TYPE OF FILE (P1-P6). Currently only supported: P6.
			if(linebuff[0] == 'P' && linebuff[1] == '6')			
			{
				printf("set file version 6\n");
				ppm->version = 6;
			}
			else
			{
				fprintf(stderr, "invalid file version %s\n", linebuff);
				return;
			}
		}
		else if(counter == 2)
		{
			// WIDTH, HEIGHT for image.
			sscanf(linebuff, "%d %d", &ppm->width, &ppm->height);
			printf("got file dimensions %dx%d\n", ppm->width, ppm->height);
		}
		else if(counter == 3)
		{
			// Read max-value specification.
			sscanf(linebuff, "%d", &maxv);
			
			if(maxv == 255)
			{
				ppm->max = maxv;
				printf("read MAX-V %d\n", maxv);
			}
			else
			{
				fprintf(stderr, "invalid MAX-V %d\n", maxv);
				return;
			}
		}
		else if(counter > 3)
		{
			printf("end parsing header, now reading bytes\n");
			exit = 1;
		}
	}
	
	printf("FILE: version=%d, width=%d, height=%d, maxv=%d\n", ppm->version, ppm->width, ppm->height, ppm->max);
	
	// allocate a suitable structure for the pixel data, store it as one long chain of bytes.
	size_alloc = sizeof(struct ppmRGB) * ppm->width * ppm->height;
	printf("allocating %d bytes, %d KB, %d MB for pixel data\n", size_alloc, size_alloc / 1024, size_alloc / 1024 / 1024);
	ppm->data = (struct ppmRGB *)malloc(size_alloc);
	printf(" ... OK\n");
}

void setPixelPPM(struct ppmdata *ppm, int x, int y, int r, int g, int b)
{
	ppm->data[(y * ppm->height) + x].r = r;
	ppm->data[(y * ppm->height) + x].g = g;
	ppm->data[(y * ppm->height) + x].b = b;
}

struct ppmRGB getPixelPPM(struct ppmdata *ppm, int x, int y)
{
	return ppm->data[(y * ppm->height) + x];
}

void writePPM(FILE *fp, struct ppmdata *ppm)
{
	int i;
	
	printf("%d, %d : ppm->width, ppm->height\n", ppm->width, ppm->height);
	fprintf(fp, "P%d\n", ppm->version);
	fprintf(fp, "# Written by fastBLIT v1.0\n");
	fprintf(fp, "%d %d\n", ppm->width, ppm->height);
	fprintf(fp, "%d\n", ppm->max);
	
	/* write ALL data */
	for(i = 0; i < (ppm->width * ppm->height); i++)
	{
		if(ppm->data[i].g == 0xAA)
		{
			printf("access: %d\n", i);
			fputc(ppm->data[i].r, fp);
			fputc(ppm->data[i].g, fp);
			fputc(ppm->data[i].b, fp);
		}
	}
}

int main(int argc, char *argv[])
{
	FILE *fp = fopen("input.ppm", "rb");
	struct ppmdata ppm;
	struct ppmRGB col;
	int i;
	
	readPPM(fp, &ppm);
	
	for(i = 0; i < 100; i++)
	{
		printf("set pixel %d, %d\n", 10 + i, 10 + i);
		setPixelPPM(&ppm, 10 + i, 10 + i, 0xFF, 0xAA, 0xDD);
		col = getPixelPPM(&ppm, 10 + i, 10 + i);
		printf("get pixel %d, %d: (%d, %d, %d)\n", 10 + i, 10 + i, col.r, col.g, col.b);
	}
	
	printf("write PPM data\n");
	
	fp = fopen("output.ppm", "wb");
	writePPM(fp, &ppm);
	printf("end write PPM data\n");
	fclose(fp);
	
	exit(0);
	return 0;
}

```

---

### Post by tom66 on 2009-08-22
I think I realised my stupid error.

(I never read the data in from the file!!!)

---

### Post by MadCow108 on 2009-08-22
your rgb struct holds char's but you feed it with int's

---

### Post by PmDematagoda on 2009-08-22
In addition to what was said previously, this:-
```
struct ppmRGB getPixelPPM(struct ppmdata *ppm, int x, int y)
{
	return ppm->data[(y * ppm->height) + x];
}
```
is wrong, the data part in the ppmdata structure is a pointer, so the function prototype should be:-
```
struct ppmRGB *getPixelPPM(struct ppmdata *ppm, int x, int y)
{
	return ppm->data[(y * ppm->height) + x];
}
```
and then you should adapt the further used code in lieu with the above change.

---

### Post by MadCow108 on 2009-08-22
no that is correct
its an array of RGB's no array of pointer to rgb's

the reason you get strange values is that char*s only hold values from -127 to 127 but you're assigning values greater than 127
you need to use unsigned chars (or ints)

---

### Post by PmDematagoda on 2009-08-22
> **MadCow108 said:**
> no that is correct
its an array of RGB's no array of pointer to rgb's

the reason you get strange values is that char*s only hold values from -127 to 127 but you're assigning values greater than 127
you need to use unsigned chars (or ints)

You are right, I didn't know about that previously, so thank you for that. :)

---

### Post by tom66 on 2009-08-22
Thanks, you pointed out my mistake. Just gotta figure out my other mistakes. I am getting pixels now but they're not being drawn diagonally/properly.

---

