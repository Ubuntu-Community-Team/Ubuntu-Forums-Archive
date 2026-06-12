---
title: "Cant Create a png file. Plz help"
date: 2010-04-25
forum: Programming Talk
---

### Post by Mathew Roy on 2010-04-25
Hi all
I was trying to create a png file through program. But the program when executed reports segmented fault. I am unable to fix it myself because I am  newbie in graphics field. I dont knw anything abt how to hangle a png.

This is the code i created.
[PHP]

#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <stdarg.h>

#include<png.h>

int x, y;

int width=640, height=900;
png_byte color_type=6;
png_byte bit_depth=8;

png_structp png_ptr;
png_infop info_ptr;
int number_of_passes;
png_bytep * row_pointers;

void r8_png_file(char *file_name)
{
    FILE *fp = fopen(file_name, "wb");
    if (!fp)
    {
        printf("Error opening file.\n");
    } 
    png_ptr = png_create_write_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    if(!png_ptr)
        printf("Structure creation failed\n");
    info_ptr = png_create_info_struct(png_ptr);
    if(!info_ptr)
        printf("creation of info_ptr failed");
    png_init_io(png_ptr, fp);
    png_set_IHDR(png_ptr, info_ptr, width, height,bit_depth, color_type,
                 PNG_INTERLACE_NONE, PNG_COMPRESSION_TYPE_BASE, 
                 PNG_FILTER_TYPE_BASE);
    png_write_info(png_ptr, info_ptr);
    png_write_image(png_ptr, row_pointers);
    png_write_end(png_ptr, NULL);
    
    /* cleanup heap allocation */
    for (y=0; y<height; y++)
        free(row_pointers[y]);
    free(row_pointers);

    fclose(fp);
}

void process()
{
    for(y=0;y<height;y++)
    {
        png_byte* row = row_pointers[y];
        for(x=0;x<width;x++)
        {
            png_byte* ptr = &(row[x*4]);
            ptr[0]=ptr[1]=ptr[2]=ptr[3]=255;
        }
    }
}


int main()
{
    char pth[50];
    printf("File=");
    scanf("%s",pth);
    printf("Processing..");
    process();
    r8_png_file(pth);
    return 0;
}
[/PHP]Something is seriously wrong in the above program. Plz help me fix the error in the above code, and mention why the code is wrong.

---

### Post by Mathew Roy on 2010-04-26
HI some1 plz help...
Theach me how to create a png file of given dimensions. Plzzz.

---

### Post by lisati on 2010-04-26
The first thing that I spotted is that if, for example, the file open fails, you should have code for the program die gracefully, rather than continuing on as if it worked.

---

### Post by Bachstelze on 2010-04-26
gdb tells me the segfault happens here:

```
Program received signal SIGSEGV, Segmentation fault.
0x0000000000400c25 in process () at png.c:53
53              png_byte* row = row_pointers[y];
(gdb) print row_pointers
$1 = (png_bytep *) 0x0

```

Maybe you need to initialise [font=monospace]row_pointers[/font], and probably allocate it some memory, too.

---

### Post by Mathew Roy on 2010-04-26
> **Bachstelze said:**
> 
Maybe you need to initialise [FONT=monospace]row_pointers[/FONT], and probably allocate it some memory, too.

Can u plz tell me how to do it?. Because I am a newbie in graphics field. I personally don't know anything about png.h and its functions. 
I did this much by going through different programs that use png files. But in all that what i see is that the programs firstt reads a png files and manipulate it. But what i need is different. I want to create a new png file of given dimensions (pixels) and create it.
Well I will try your suggestion.
Thatk u 4 trying to help me.

---

### Post by Bachstelze on 2010-04-26
> **Mathew Roy said:**
> Can u plz tell me how to do it?. Because I am a newbie in graphics field. I personally don't know anything about png.h and its functions. 
I did this much by going through different programs that use png files. But in all that what i see is that the programs firstt reads a png files and manipulate it. But what i need is different. I want to create a new png file of given dimensions (pixels) and create it.
Well I will try your suggestion.
Thatk u 4 trying to help me.

It's really more basic C knowledge than PNG-related stuff. I suggest you learn more about how C works before you try to use any external library.

---

### Post by phrostbyte on 2010-04-26
> **Mathew Roy said:**
> Can u plz tell me how to do it?. Because I am a newbie in graphics field. I personally don't know anything about png.h and its functions. 
I did this much by going through different programs that use png files. But in all that what i see is that the programs firstt reads a png files and manipulate it. But what i need is different. I want to create a new png file of given dimensions (pixels) and create it.
Well I will try your suggestion.
Thatk u 4 trying to help me.

You should not dereference an uninitalized pointer. You will have to use malloc or something similar. 

Watch this maybe:
[http://www.youtube.com/watch?v=6pmWojisM_E](http://www.youtube.com/watch?v=6pmWojisM_E)

---

### Post by Mathew Roy on 2010-04-26
OK! I understand my first mistake. Wouldn't a return -1; fix it. K I will fix it.

---

### Post by Mathew Roy on 2010-04-26
> Originally Posted by [B]Bachstelze
[/B]It's really more basic C knowledge than PNG-related stuff. I suggest you learn more about how C works before you try to use any external library.

Actually I am not bad at C. I would consider myself as a moderate level programmer. It is just the PNG related stuff that is giving me a hard time. I failed to figure out how the PNG stuff works.
For example I donot know what is this[FONT=monospace] "row_pointers" [/FONT] is and of what type.

---

### Post by lisati on 2010-04-26
> **Mathew Roy said:**
> Actually I am not bad at C. I would consider myself as a moderate level programmer. It is just the PNG related stuff that is giving me a hard time. I failed to figure out how the PNG stuff works.
For example I donot know what is this[FONT=monospace] "row_pointers" [/FONT] is and of what type.

I had a quick look at the code again, and I can't see where row_pointers is initialized either. It appears to be used as a list of pointers connected with processing the image one row of pixels at a time.  If it's not being properly initialized, it could hold any old rubbish, which could help explain the seg fault.

---

### Post by Mathew Roy on 2010-04-26
> **lisati said:**
> I had a quick look at the code again, and I can't see where row_pointers is initialized either. It appears to be used as a list of pointers connected with processing the image one row of pixels at a time.  If it's not being properly initialized, it could hold any old rubbish, which could help explain the seg fault.

Well what you have said is very true. So I tried to initialise row_pointers like this.
[PHP]
row_pointers = (png_bytep*) malloc(sizeof(png_bytep) * height);    
for (y=0; y<height; y++)
        row_pointers[y] = (png_byte*) malloc(info_ptr->rowbytes);
[/PHP]But this inclusion also doesn't help, because in my program there is garbage value in info_ptr->rowbytes.
But I dont know what value should be given in rowbytes. I after a small research came to know that info_ptr holdes a number of different values that is essential foe a png image. But I dont knw what values are to be filled in the structure. 
I am attaching a file that you may find helpful.

Can you please tell me what all information are to be filled in the structure (info_ptr) and their values. I just dont know what to do. What value I should assign  info_ptr->rowbytes?

Please help me.

---

### Post by phrostbyte on 2010-04-26
info_ptr is also uninitalized. It is undefined behaviour to read a variable that has only been declared and not set. info_ptr isn't even a pointer, so you wouldn't use (->) syntax to access its fields anyway. You probably meant to make it a pointer through.

This comprehensive document describes the API of libpng:
[http://www.libpng.org/pub/png/libpng-1.2.5-manual.html](http://www.libpng.org/pub/png/libpng-1.2.5-manual.html)

You really have little choice other then reading through it carefully.

---

### Post by Mathew Roy on 2010-04-29
Thank u everybody 4 helping me. Finally I was able to create it an much more...
Here is the sorce code.
[PHP]

#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <stdarg.h>

#include<png.h>
/*----------------------------------------------------------------------------*/
struct details
{
    int width,height;
    png_byte color_type,bit_depth;
}bk_d , img_d;

/*----------------------------------------------------------------------------*/
void process();
void merge(int,int);
void help();
int create_png_file();
int read_bk(char *);
int read_img(char *);
int r8_png(const char *,struct details );
/*----------------------------------------------------------------------------*/
char header[8];
int width=640, height=3508;
png_byte color_type=6;
png_byte bit_depth=8;

png_structp png_ptr;
png_infop info_ptr;
int number_of_passes;
png_bytep * row_pointers, *row_p_img;
/*----------------------------------------------------------------------------*/


int main(int argc, char **argv)
{
    char c,*fle=NULL;
    printf("%d",argc);
    if(argc==1)
    {
        help();
        return -1;
    }
    else
    {
        while((c = getopt (argc,argv,"f:F:W:w:H:h: S:"))!=-1)
        {
            switch(c)
            {
                case 'f':
                case 'F':
                    fle=optarg;
                    break;
                case 'W':
                case 'w':
                    width=atoi(optarg);
                    break;
                case 'H':
                case 'h':
                    height=atoi(optarg);
                    break;
                case 'S':
                    if(strcmp(optarg,"A4")==0)
                    {
                        printf("Size A4 selected\n");
                        width = 2480;
                        height= 3508;
                    }
                    else if(strcmp(optarg,"legal")==0 ||strcmp(optarg,"LEGAL")==0)
                    {
                        printf("Size legal selected");
                        width =2550;
                        height=4200;
                    }
                    else
                    {
                        printf("Unknown Size");
                        return 1;
                    }
                    break;
                case '?':
                    if(optopt =='W'||optopt =='w')
                    {
                        fprintf(stderr, "Option \"%c\" requires an argument.\n" ,optopt);
                        printf("Please inter the width.\n");
                        printf("Width = ");
                        scanf("%d",&width);
                    }
                    else if (optopt =='H'||optopt =='h')
                    {
                        fprintf(stderr, "Option \"%c\" requires an argument.\n" ,optopt);
                        printf("Please inter the height.\n");
                        printf("Height = ");
                        scanf("%d",&height);
                    }
                    else if(optopt=='F'||optopt=='f')
                    {
                        printf("Output file missing..\n");
                        abort();
                    }
                    else 
                    fprintf(stderr, "Unknown option -%c ",optopt);
                    break;
                default:
                    return 2;
            }
        }
    }
    if(fle)
    {
        int x,y,n,i;
        char fle_p[80];
        create_png_file(fle);
        printf("Enter x and y:-");
        scanf("%d%d",&x,&y);
        if(read_bk(fle)!=0)
        {
            printf("ERROR in reading Background image");
            return 4;
        }
        printf("No of pics to b pasted = ");
        scanf("%d",&n);
        for(i=0;i<n;i++)
        {
            printf("Enter file to b pasted = ");
            scanf("%s",fle_p);
            getchar();
            if(read_img(fle_p)!=0)
            {
                printf("ERROR in reading image :- %s\n",fle_p);
                return 4;
            }
            merge(x,y);
            x+=img_d.width-2;
        }
        r8_png(fle,bk_d);
        return 0;
    }
    else
        printf("File missing...\n");
    return 3;
}
/*----------------------------------------------------------------------------*/
int create_png_file(char *file_name)
{
    int y;
    FILE *fp = fopen(file_name, "wb");
    if (!fp)
    {
        printf("Error opening file.\n");
        return -1;
    } 
    png_ptr = png_create_write_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    if(!png_ptr)
        printf("Structure creation failed\n");
    info_ptr = png_create_info_struct(png_ptr);
    if(!info_ptr)
        printf("creation of info_ptr failed");
    png_init_io(png_ptr, fp);
    png_set_IHDR(png_ptr, info_ptr, width, height,bit_depth, PNG_COLOR_TYPE_RGBA,
                 PNG_INTERLACE_NONE, PNG_COMPRESSION_TYPE_BASE, 
                 PNG_FILTER_TYPE_BASE);
    png_write_info(png_ptr, info_ptr);
    printf("Processing..\n");
    fflush(stdout);
    process();
    png_write_image(png_ptr, row_pointers);
    png_write_end(png_ptr, NULL);
    
    /* cleanup heap allocation */
    for (y=0; y<height; y++)
        free(row_pointers[y]);
    free(row_pointers);
    fclose(fp);
    return 0;
}
/*----------------------------------------------------------------------------*/
int read_bk(char *bk)
{
    int y;
    png_structp png_ptr_bk;
    png_infop info_ptr_bk;
    FILE *f;
    f=fopen(bk,"rb");
    if(!f)
    {
        printf("Error opening file :- %s\n",bk);
        return -1;
    }
    fread(header, 1, 8, f);
    png_ptr_bk = png_create_read_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    if (!png_ptr_bk)
    {
        printf("png_create_read_struct failed");
        return -2;
    }
    info_ptr_bk = png_create_info_struct(png_ptr_bk);
    if (!info_ptr_bk)
    {
        printf("png_create_info_struct failed");
        return -2;
    }
    png_init_io(png_ptr_bk, f);
    png_set_sig_bytes(png_ptr_bk, 8);
    png_read_info(png_ptr_bk, info_ptr_bk);
    /*Allocate Memory for row_pointers*/
    row_pointers = (png_bytep*) malloc(sizeof(png_bytep) * info_ptr_bk->height);
    for (y=0; y<info_ptr_bk->height; y++)
        row_pointers[y] = (png_byte*) malloc(info_ptr_bk->rowbytes);
    /*read background image into row_pointers*/
    png_read_image(png_ptr_bk, row_pointers);
    fclose(f);
    
    /*Set struct details background*/
    bk_d.width     = info_ptr_bk->width;
    bk_d.height    = info_ptr_bk->height;
    bk_d.color_type= info_ptr_bk->color_type;
    bk_d.bit_depth = info_ptr_bk->bit_depth;
    return 0;
}
/*----------------------------------------------------------------------------*/
int read_img(char *img)
{
    int y;
    png_structp png_ptr_img;
    png_infop info_ptr_img;//,temp;
    FILE *f2;
    f2 =fopen(img,"rb");
    if(!f2)
    {
        printf("Error opening file :- %s\n",img);
        return -1;
    }
    fread(header, 1, 8, f2);
    png_ptr_img = png_create_read_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    if (!png_ptr_img)
    {
        printf("png_create_read_struct failed");
        return -2;
    }
    info_ptr_img = png_create_info_struct(png_ptr_img);
    if (!info_ptr_img)
    {
        printf("png_create_info_struct failed");
        return -2;
    }
    //read image into memory
    png_init_io(png_ptr_img,f2);
    png_set_sig_bytes(png_ptr_img,8);
    png_read_info(png_ptr_img, info_ptr_img);
    
    row_p_img = (png_bytep*) malloc(sizeof(png_bytep) * info_ptr_img->height);
    for (y=0; y<info_ptr_img->height; y++)
        row_p_img[y] = (png_byte*) malloc(info_ptr_img->rowbytes);
    
    png_read_image(png_ptr_img, row_p_img);    
    fclose(f2);
    /*Set struct details for image*/
    img_d.width     = info_ptr_img->width;
    img_d.height    = info_ptr_img->height;
    img_d.color_type= info_ptr_img->color_type;
    img_d.bit_depth = info_ptr_img->bit_depth;
    return 0;
}
//    merge(bk_x,bk_y);
    /*    
    for(y1=bk_y, y2=0 ; y2<info_ptr_img->height ; y1++, y2++)
    {    
        png_byte* r_bk = row_pointers[y1];
        png_byte *r_img= row_p_img[y2];
        for (x1=bk_x,x2=0; x2<info_ptr_img->width; x1++,x2++) 
        {
            png_byte* ptr_bk = &(r_bk[x1*4]);
            png_byte *ptr_img= &(r_img[x2*4]);
            if(ptr_img[3]==255)
            {
                ptr_bk[0]=ptr_img[0];
                ptr_bk[1]=ptr_img[1];
                ptr_bk[2]=ptr_img[2];
                printf(",");fflush(stdout);
            }
            else if(ptr_img[3]<10)
            {
                ptr_bk[0]=255;
                ptr_bk[1]=255;
                ptr_bk[2]=255;

            }
            else
            {
                png_composite(ptr_bk[0], ptr_img[0], ptr_img[3], ptr_bk[0]);
                png_composite(ptr_bk[1], ptr_img[1], ptr_img[3], ptr_bk[1]);
                png_composite(ptr_bk[2], ptr_img[2], ptr_img[3], ptr_bk[2]);
                printf(".");fflush(stdout);
            }

        }
    }
    temp=info_ptr_bk;
    printf("Combining..dne\n");
    f1 = fopen(bk, "wb");
    fread(header, 1, 8, f1);
    png_ptr_bk = png_create_write_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    info_ptr_bk = png_create_info_struct(png_ptr_bk);
    png_init_io(png_ptr_bk, f1);
    
    png_set_IHDR(png_ptr_bk, info_ptr_bk, temp->width, temp->height,
             temp->bit_depth, temp->color_type, PNG_INTERLACE_NONE,
             PNG_COMPRESSION_TYPE_BASE, PNG_FILTER_TYPE_BASE);
    
    printf("IHDR done\n");
    png_write_info(png_ptr_bk, info_ptr_bk);
    printf("r8 info...");
    fflush(stdout);
    png_write_image(png_ptr_bk, row_pointers);
    png_write_end(png_ptr_bk, NULL);
    fclose(f1);
    printf("File Closed..\n");
    fflush(stdout);
    //Deallocating memory used for background
    for (y=0; y<info_ptr_bk->height; y++)
        free(row_pointers[y]);
    free(row_pointers);
    printf("bk done.");
    fflush(stdout);*/
    //Deallocating memory used for image
    /*
    for (y=0; y<info_ptr_img->height; y++)
        free(row_p_img[y]);
    free(row_p_img);
    fclose(f2);
     
    
    if(r8_png(bk,bk_d)==0)
    {
        printf("R8tn successfull.\n");
        fflush(stdout);
    }
    
    return 0;
}*/
/*----------------------------------------------------------------------------*/
void merge(int x,int y)
{
    int y1,y2,x1,x2;
    if ((img_d.color_type != PNG_COLOR_TYPE_RGBA) || (bk_d.color_type != PNG_COLOR_TYPE_RGBA))
    {
        printf("NOT RGBA");
        fflush(stdout);
        abort();
    }
    printf("Merging...");
    fflush(stdout);
    
    for(y1=y, y2=0 ; y2<img_d.height ; y1++, y2++)
    {    
        png_byte *r_bk = row_pointers[y1];
        png_byte *r_img= row_p_img[y2];
        for (x1=x,x2=0; x2<img_d.width; x1++,x2++) 
        {
            png_byte *ptr_bk = &(r_bk[x1*4]);
            png_byte *ptr_img= &(r_img[x2*4]);
            if(ptr_img[3]==255)
            {
                ptr_bk[0]=ptr_img[0];
                ptr_bk[1]=ptr_img[1];
                ptr_bk[2]=ptr_img[2];
            }
            else if(ptr_img[3]<10)
            {
                continue;
            }
            else
            {
                png_composite(ptr_bk[0], ptr_img[0], ptr_img[3], ptr_bk[0]);
                png_composite(ptr_bk[1], ptr_img[1], ptr_img[3], ptr_bk[1]);
                png_composite(ptr_bk[2], ptr_img[2], ptr_img[3], ptr_bk[2]);
                printf(".");fflush(stdout);
            }
        }
    }
    printf("Completed.\n");
    fflush(stdout);
    
    for (y=0; y<img_d.height; y++)
        free(row_p_img[y]);
    free(row_p_img);
}
/*----------------------------------------------------------------------------*/
int r8_png(const char *fle,struct details a)
{
    int y;
    char header[8];
    FILE *f=fopen(fle,"wb");
    fread(header, 1, 8, f);
    png_ptr = png_create_write_struct(PNG_LIBPNG_VER_STRING, NULL, NULL, NULL);
    info_ptr = png_create_info_struct(png_ptr);
    png_init_io(png_ptr, f);
    if (setjmp(png_jmpbuf(png_ptr)))
    {
        printf("[write_png_file] Error during writing header");
        return -1;
    }
    png_set_IHDR(png_ptr, info_ptr, a.width, a.height,
             a.bit_depth, a.color_type, PNG_INTERLACE_NONE,
             PNG_COMPRESSION_TYPE_BASE, PNG_FILTER_TYPE_BASE);
    
    png_write_info(png_ptr, info_ptr);
    /* write bytes */
    if (setjmp(png_jmpbuf(png_ptr)))
        printf("[write_png_file] Error during writing bytes");
    
    png_write_image(png_ptr,row_pointers);
    png_write_end(png_ptr, NULL);
    /*Free Memory*/
    for (y=0; y<a.height; y++)
        free(row_pointers[y]);
    free(row_pointers);
    
    fclose(f);
    printf("File Closed.\n");
    return 0;
}
void process()
{
    int x,y;
    row_pointers = (png_bytep*) malloc(sizeof(png_bytep) * height);    
    for (y=0; y<height; y++)
        row_pointers[y] = (png_byte*) malloc(info_ptr->rowbytes);    
    for(y=0;y<height;y++)
    {
        png_byte* row = row_pointers[y];
        for(x=0;x<width;x++)
        {
            png_byte* ptr = &(row[x*4]);
            ptr[0]=ptr[1]=ptr[2]=ptr[3]=255;
        }
    }
}

void help()
{
    printf("This program may be used to create a balnk png file of required dimensions (pixels)\n");
    printf("arguments -f<output file> -w<Width> -h<height>\n");
    printf("plz note:-width and height in pixels\n");
}
[/PHP]

---

