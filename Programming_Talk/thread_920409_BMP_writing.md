---
title: "BMP writing"
date: 2008-09-15
forum: Programming Talk
---

### Post by kaspar_silas on 2008-09-15
Hi all,

Does anyone happen to have a simple bit of code writing BMP type files that doesn't use non standard libraries. I have wasted most of this weekend messing with various libraries like EasyBMP (I only started c++ recently) and have decided I would prefer a stand alone answer. 

But if anyone has an minimalist example using the EasyBMP library that would be almost as good. The example they give (dataplotter) failed to compile saying BYTE was not declared in the scope. Which is a pity as the example is almost exactly what I am after. 

O yeah, PNG, JPEG or other simple image types are also fine I just thought BMP would be easiest.

Any help is truly truly appreciated. 

maybe I should say what im doing in case anyone is wondering. I am basically reading in a massive 3D array selecting a plane and outputting the image along that slice.

Thanks again

---

### Post by PeterBBB on 2008-09-15
BMP is a Windows format. You could try PPM
[http://en.wikipedia.org/wiki/Netpbm_format](http://en.wikipedia.org/wiki/Netpbm_format)

Its just a text file, no library's needed, just write out the data (see the simple example given). That should get you going and recover from the weekend's disaster.

If the array really is 'massive' you will soon want compression. Hopefully someone will be along later to advise on a robust standard C++ libray for Jpeg

---

### Post by dribeas on 2008-09-15
> **kaspar_silas said:**
> The example they give (dataplotter) failed to compile saying BYTE was not declared in the scope.

Maybe you forgot some of the include's. BYTE is probably defined somewhere else as a typedef to unsigned char. Try adding this:
```

typedef unsigned char BYTE;

```

---

### Post by mike_g on 2008-09-15
Heres a couple of functions I wrote in C for loading/saving bitmap images:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef unsigned char Uint8;

typedef struct
{
    unsigned char depth;
    unsigned char channels;
    int w, h;
    void* data;
}Image;

Image* LoadBMP(const char* filename,  Uint8 alpha_channels);
int SaveBMP(Image* image, const char* filename);
void FreeImage(Image *image);

/************** TEST PROG ***************************/

int main(int argc, char* argv[])
{
    if(argc != 2)
    {
        printf("Usage: %s bmpfile\n", argv[0]);
        return 1;
    }
    Image *image = LoadBMP(argv[1], 1);
    if(! image) return 2;
    SaveBMP(image, "output.bmp");
    FreeImage(image);
    return 0;
}

/****************************************************/

//Loads 24 bit bitmap to in image buffer with given number of alpha channels
Image* LoadBMP(const char* filename, Uint8 alpha_channels)
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
    image->data = malloc(width * height * (3+alpha_channels));
    if(! image->data)
    {
        fprintf(stderr, "Error Loading %s: Unable To Allocate Space For Image Data\n",  filename);    
        free(image);
        fclose(fp);
        return NULL;
    }
    image->data = memset(image->data, 0, (width * height * (3+alpha_channels)));
    image->h = height;
    image->w = width;
    image->depth = 24+(alpha_channels*8); 
    image->channels = 3+alpha_channels;
    
    // LOAD IMAGE DATA    
    unsigned char *ptr = image->data;
    ptr+=(width*height*image->channels)-(width*image->channels);
    int rows, cols, elem, a;
    int last_row = width * 2 * image->channels;
    fseek(fp, 54, SEEK_SET);    
    
    //rows inverted so not upside down
    for(rows=0; rows<height; rows++, ptr-=last_row)
    for(cols=0; cols<width;  cols++)
    {
        for(elem=0; elem<3; elem++, ptr++)
            fread(ptr, 1, 1, fp);
        for(a=0; a<alpha_channels; a++, ptr++)
            *ptr=0;
    }
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
    int ppm_x = 120, ppm_y = 120;
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
    fwrite(&ppm_x, 4, 1, fp); // Windoze image viewer does
    fwrite(&ppm_y, 4, 1, fp); // not like iot if ppm not set
    fwrite(&zero, 4, 2, fp);  //Stuff we dont care about
    
    int row, col, row_size = image->w*image->channels;
    int alpha_channels = image->channels-3;
    unsigned char *ip = (unsigned char*)image->data;
    ip += (row_size*image->h) - row_size;

    for(row=0; row<image->h; row++, ip -= (row_size*2))
    for(col=0; col<image->w; col++)    
    {
        fwrite(ip, 1, 1, fp); ip++;
        fwrite(ip, 1, 1, fp); ip++;
        fwrite(ip, 1, 1, fp); ip++;    
        ip += alpha_channels;
    }
    return 0;
}


void FreeImage(Image *image)
{
    free(image->data);
    free(image);
}
```
PNGs and JPGs are a bit more complex. Theres some code for decdoing PNGs here:
[http://student.kuleuven.be/~m0216922/CG/files/quickcg/quickcg.cpp](http://student.kuleuven.be/~m0216922/CG/files/quickcg/quickcg.cpp)
Alternativly, you could use libpng. I havent got around to dealing with JPGs yet.

---

### Post by kaspar_silas on 2008-09-15
Cheers all

The above example c code and that PPM format are exactly what I was looking for. 


As for the problems with the example using EasyBMP. I don't think I personally missed any headers as I copied the sample files, I didn't type them. Nevertheless I tried dribeas typedef point which solved the BYTE declaration error but  produced a hell of alot of errors like 

.cpp:324: undefined reference to `BMP::TellHeight()' 

I might have another go at solving this error later but I  will go on with the PPM idea for now.

Thanks all

---

### Post by dribeas on 2008-09-15
> **kaspar_silas said:**
> hell of a lot of errors like 

.cpp:324: undefined reference to `BMP::TellHeight()' 


Just for the sake of it... those are linker errors. The code has been compiled but you are not linking your executable against whatever lib provides the implementation of BMP::TellHeight() (and probably all the rest of BMP methods). Are you using the appropriate -l directive for the EasyBMP library?

---

### Post by kaspar_silas on 2008-09-15
> **dribeas said:**
> Just for the sake of it... those are linker errors. The code has been compiled but you are not linking your executable against whatever lib provides the implementation of BMP::TellHeight() (and probably all the rest of BMP methods). Are you using the appropriate -l directive for the EasyBMP library?

Cheers again, your quite right I had not included the EasyBMP.cpp files only the .h ones. But it finally worked hurra.

---

