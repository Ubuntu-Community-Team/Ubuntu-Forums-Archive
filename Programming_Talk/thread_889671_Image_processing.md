---
title: "Image processing"
date: 2008-08-14
forum: Programming Talk
---

### Post by StOoZ on 2008-08-14
I dont think there is such a thing , but is there anyway to determine whether an image is watermarked or not?
dont want to remove / nor modify the image , just to see whether the image is watermarked or not.

thanks

---

### Post by Zugzwang on 2008-08-14
No way! The point is that you cannot distinguish between some noise in an image (for example) and a good watermark.

A more theoretical reason: For every image you have you can generate a watermarking algorithm that outputs it from a slightly modified version of it. So without knowing what you are precisely looking for, you cannot detect this.

---

### Post by StOoZ on 2008-08-14
dammit.
at first I thought that watermarks , in general , have a some common properties , so i'll just use a proper lib (boost::GIL) and look for these , but then , obviously , watermarks are an integrated part of the image , so , how to do this ? no idea...

---

### Post by mike_g on 2008-08-14
The only real way to get a watermark is to have a copy of the original non-watermarked image. However, if the image does not have a lot of different colours then you should be able to pick up a pattern. This wont work for photographs tho; or most images for that matter. 

I made a watermark encoder in C. Actually, its slightly different in that it hides the content of a textfile in the least significant bit of each colour component of each pixel. To obtain the text again you then need to pass both the modified and original image. Heres the code if you want to play around with it:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_EXT_LEN 5

typedef struct
{
	unsigned char depth;
	unsigned char channels;
	int w, h;
	void* data;
}Image;

void GetExtension(const char* filename, char* ext);
Image* LoadBMP(const char* filename);
int SaveBMP(Image* image, const char* filename);
void FreeImage(Image *image);
int Encode(const char* bitmap, const char* textfile);
int Decode(const char* bitmap1, const char* bitmap2);

int main(int argc, char* argv[])
{
	if(argc != 3)
	{
		fprintf(stderr, "Usage:\n");	
		fprintf(stderr, "To encode: %s bitmap textfile\n", argv[0]);
		fprintf(stderr, "To decode: %s bitmap bitmap\n", argv[0]);  
		return 1; 
	}
	
	char ext[MAX_EXT_LEN+1];
	GetExtension(argv[2], ext);

	if(strcmp(ext, "bmp") == 0)		
		return Decode(argv[1], argv[2]);
	Encode(argv[1], argv[2]);

	return 0;
}

int Encode(const char* bitmap, const char* textfile)
{
	Image *ip = LoadBMP(bitmap);
	if(! ip) return 2;

	FILE *fp = fopen(textfile, "r");
	if(! fp)
	{
		fprintf(stderr, "Unable to open %s\n", textfile);
		FreeImage(ip);
		return 3;
	}

	//Get textfile size
	int i, text_bytes=0;
	while( (i=fgetc(fp)) != EOF )
		text_bytes++;
	rewind(fp);
	
	//Check enough space on image for encoding
	int image_bytes = ip->w * ip->h * 3;
	int text_bits = text_bytes * 8;
	if(text_bits > image_bytes)
	{
		fprintf(stderr, "Aborted: Not enough pixels in %s to encode %s text\n", bitmap, textfile);
		FreeImage(ip);
		fclose(fp);
		return 4;
	}	

	//Do encoding
	int byte, bit;
	unsigned char c, mask;
	unsigned char* ptr = ip->data;
	for(byte=0; byte<text_bytes; byte++)
	{
		c = fgetc(fp);
		mask = 128;
		for(bit=0; bit<8; bit++, mask>>=1, ptr++)
			if(mask & c)*ptr^=1;
	}	
	
	return SaveBMP(ip, "encoded.bmp");
}

int Decode(const char* bitmap1, const char* bitmap2)
{
	Image *a = LoadBMP(bitmap1);
	if(! a) return 5;
	Image *b = LoadBMP(bitmap2);
	if(! b)
	{
		FreeImage(a);
		return 6;
	}
	
	//Chek images are of same size
	int a_size = a->w*a->h*a->channels;
	int b_size = b->w*b->h*b->channels;
	if(a_size != b_size)
	{
		FreeImage(a);
		FreeImage(b);	
		fprintf(stderr, "Image files are not of same size\n");
		return 7;
	}	

	//Open a file for writing to
	FILE *fp = fopen("decoded.txt", "w");
	if(! fp)
	{
		FreeImage(a);
		FreeImage(b);	
		fprintf(stderr, "Unable to open output file.\n");
		return 7;
	}
	
	// Do decoding
	int max_byte = a_size / 8; 
	int byte, bit;
	unsigned char* ap = a->data;
	unsigned char* bp = b->data;
	unsigned char out, mask;
	for(byte=0; byte<max_byte; byte++)
	{
		out = 0;
		mask = 128;
		for(bit=0; bit<8; bit++, ap++, bp++, mask>>=1)
		{
			if(*ap != *bp) out |= mask;
		}
		if(out == 0) break;	
		fwrite(&out, 1, 1, fp);
	}
	fclose(fp);
	return 0;
}


void GetExtension(const char* filename, char* ext)
{
	int len = strlen(filename);
	int a, b=0, dot_found = 0;
	//Loop backwards to the last dot
	for(a=len; a>= 0; a--)
	{
		if(filename[a] == '.')
		{
			dot_found = 1;
			break;
		}
	}
	a++;
	if(dot_found) //Copy extension
	{		
		for(; a<len && b<=MAX_EXT_LEN; a++, b++)
			ext[b] = filename[a];
	}
	ext[b] = '\0';
}

Image* LoadBMP(const char* filename)
{
	FILE *fp = fopen(filename, "rb");
	if(!fp)
	{
		fprintf(stderr, "Error Opening BMP File: %s File Could Not Be Opened.\n", filename); 	
		return NULL;
	}

	char signature[2];
	fread(signature, 1, 2, fp);
	if(signature[0]!='B' || signature[1]!='M')
	{
		fprintf(stderr, "Error Opening BMP File: %s Invalid Signature: %s\n", filename, signature);
		fclose(fp);
		return NULL;
	}

	// GET IMAGE PROPERTIES
	int width, height;
	short depth;
	fseek(fp, 16, SEEK_CUR);
	fread(&width, 4, 1, fp);
	fread(&height, 4, 1, fp);
	fseek(fp, 2, SEEK_CUR);	
	fread(&depth, 2, 1, fp);

	if(depth != 24)
	{
		fprintf(stderr, "Error Opening BMP File: %s Loader Only Supports 24bit Bitmaps\n", filename);
		fclose(fp);
		return NULL;
	}

	// CREATE AND INIT IMAGE BUFFER
	Image* image = malloc(sizeof(Image));
	if(!image)
	{		
		fprintf(stderr, "Error Loading %s: Unable To Allocate Space For Image\n",  filename);	
		fclose(fp);
		return NULL;

	}
	image->data = malloc(width * height * 3);
	if(! image->data)
	{
		fprintf(stderr, "Error Loading %s: Unable To Allocate Space For Image Data\n",  filename);	
		free(image);
		fclose(fp);
		return NULL;
	}
	image->data = memset(image->data, 0, (width * height * 3));
	image->h = height;
	image->w = width;
	image->depth = 24; 
	image->channels = 3;
	
	// LOAD IMAGE DATA	
	unsigned char *ptr = image->data;
	ptr+=(width*height*3)-(width*3);
	int rows, cols, elem;
	fseek(fp, 54, SEEK_SET);	
	
	//rows inverted so not upside down
	for(rows=0; rows<height; rows++, ptr-=(width*6))
	for(cols=0; cols<width;  cols++)
	for(elem=0; elem<3; elem++, ptr++)
		fread(ptr, 1, 1, fp);
	
	fclose(fp);
	return image;	
}

//Writes unpaletted 24bit bitmaps only
int SaveBMP(Image* image, const char* filename)
{
	FILE *fp = fopen(filename, "wb");
	if(! fp) return 1;
	if(! image) return 2;	
	if(image->channels < 3) return 3;

	int pixel_num = image->w*image->h;
	int data_size = pixel_num*3;
	int file_size = data_size + 54;
	int start_add = 54, header_size = 40;
	int zero = 0, planes = 1, bpp = 24;

	fwrite("BM", 2, 1, fp);
	fwrite(&file_size, 4, 1, fp);
	fwrite(&zero, 4, 1, fp);
	fwrite(&start_add, 4, 1, fp); //This is probably wrong
	fwrite(&header_size, 4, 1, fp); // Size of header
	fwrite(&image->w, 4, 1, fp);
	fwrite(&image->h, 4, 1, fp);
	fwrite(&planes, 2, 1, fp); //number of planes must be 1
	fwrite(&bpp, 2, 1, fp); // BPP
	fwrite(&zero, 4, 1, fp); // No comprssion
	fwrite(&data_size, 4, 1, fp);
	fwrite(&zero, 4, 4, fp); //Stuff we dont care about
	
	int row, col, row_size = image->w*image->channels;
	int alpha_skip = image->channels-3;
	unsigned char *ip = (unsigned char*)image->data;
	ip += (row_size*image->h) - row_size;

	for(row=0; row<image->h; row++, ip -= (row_size*2))
	for(col=0; col<image->w; col++)	
	{
		fwrite(ip, 1, 1, fp); ip++;
		fwrite(ip, 1, 1, fp); ip++;
		fwrite(ip, 1, 1, fp); ip++;	
		ip += alpha_skip;
	}
	return 0;
}

void FreeImage(Image *image)
{
	free(image->data);
	free(image);
}
```

---

### Post by StOoZ on 2008-08-14
thanks , will educate from the code.

maybe one day , someone will discover a way to detect watermarks ,without providing the original file.... :KS:guitar:

---

### Post by DavidBell on 2008-08-15
> **StOoZ said:**
> maybe one day , someone will discover a way to detect watermarks ,without providing the original file.... :KS:guitar:

Going the other way, I think if you knew the exact watermark graphic and it was always in a consistent location, you could probably pick images that have it (using edge detection algorithms modified to suit the watermark).

If you are looking for a generic way to detect any watermark that's really hard.

DB

---

### Post by Zugzwang on 2008-08-15
> **DavidBell said:**
> 
If you are looking for a generic way to detect any watermark that's really hard.


As already mentioned above its not hard but technically impossible.

---

### Post by DavidBell on 2008-08-15
Impossible is a pretty strong word, I think if it is a mark that a person can identify by just looking then it's only a matter of time before computers can recognise it as well. Eg some security people think there is evidence that those capcha codes have been broken, and they are specifically designed to be hard for computers

If it's some sort of hidden mark that people can't find easily that would really be stretching it for computers. DB

---

### Post by pmasiar on 2008-08-15
[http://en.wikipedia.org/wiki/Digital_watermarking](http://en.wikipedia.org/wiki/Digital_watermarking)
[http://en.wikipedia.org/wiki/Steganography](http://en.wikipedia.org/wiki/Steganography)

Blind detecting is definitely not easy.

---

### Post by StOoZ on 2008-08-15
the 2nd link is very interesting , the thing about fully hiding one image into another one , is just amazing.

---

### Post by mike_g on 2008-08-15
> some security people think there is evidence that those capcha codes have been broken, and they are specifically designed to be hard for computers
Some captcha codes can be recognised by computers; others cant be read by humans, and they are annoying. Personally I think that it would be better to say name an object in a picture then have captcha codes. It would be easier for peopel to identify and probably harder for computers too.

> the 2nd link is very interesting , the thing about fully hiding one image into another one , is just amazing.
Yeah the wiki page is where I got the inspiration for my prog. You could always hide an image file using it; it just wont work if its got a .bmp extension.

---

### Post by Zugzwang on 2008-08-17
> **DavidBell said:**
> Impossible is a pretty strong word, I think if it is a mark that a person can identify by just looking then it's only a matter of time before computers can recognise it as well. Eg some security people think there is evidence that those capcha codes have been broken, and they are specifically designed to be hard for computers


Hang on - The OP wanted to detect *any* watermark. And it can easily be proven that there's no algorithm to detect *any* of them. Humans will also not be able to distinguish whether the watermark they think to see is actually part of the original image (like for example shadows resulting from carving into stone) or added afterwards. So it *is* impossible. 

Not to mention the inambiguity between the digital watermarks and "visible watermarks". Digital watermarks are also impossible to detect without knowing the hiding algorithm used. And even if one knows it, the decision can only be made with a certain probability (but which is typically very high).

Reason for the impossibility is as follows. Assume we have some fixed image data i_1....i_n (out of the domain I) and some watermark i'_1....i'_m (out of the domain I', for some m,n being natural numbers). Then the watermarking function maps I^n times I'^m to I^n. And since  there are i_1....i_n, i'_1....i'_m that are mapped to some output o_1 .... o_n which is in I^n again, an original image coincides with a watermarked image, therefore watermarks cannot be detected.

There might be methods to detect visual watermarks but there are not fault-free and not what the OP asked for.

---

