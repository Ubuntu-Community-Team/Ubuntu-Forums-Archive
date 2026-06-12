---
title: "Program Will not run."
date: 2008-04-10
forum: Programming Talk
---

### Post by namegame on 2008-04-10
I have written a program to convert an image from color to Sepia color tone. However, when I try to run it using ```
./a.out input.ppm output.ppm 
```, it will not run.

```

#include <stdio.h>
#include <stdlib.h>
#include "img.h"

int main(int argc, char *argv[]){

        int x;
        int y;
        int width;
        int height;
        int index;
        pixel_t *pixel;

        unsigned char *inputImage;
        unsigned char *outputImage;

        inputImage = (unsigned char *)malloc (sizeof(pixel_t) * width * height);
        outputImage = (unsigned char *)malloc (sizeof(pixel_t) * width * height);


        FILE *input;
        FILE *output;


        if (argc < 3){
           fprintf(stderr,"Incorrect input.\n");
           fprintf(stderr,"Exiting.");
           exit(1);
           }

        input = fopen(argv[1], "r");
        output = fopen(argv[2], "w");

        if ( input == NULL || output == NULL){
           fprintf(stderr,"Error opening file.\n");
           fprintf(stderr,"Exiting.");
           exit(2);
           }


        readHeader (&width, &height, input);

        pixel = (pixel_t *) malloc(sizeof(pixel_t));

        input = malloc (sizeof(pixel_t) * width * height);
        output =  malloc(sizeof(pixel_t) * width * height);


        fread(inputImage, sizeof(pixel_t), width * height, input);
             for(y = 0; y < height; y++){

            for(x = 0; x < width; x++){

            index = sizeof(pixel_t) * y * width + sizeof(pixel_t) * x;
               pixel->r = inputImage[index];
               pixel->g = inputImage[index + 1];
               pixel->b = inputImage[index + 2];

            grayPixel(pixel);
            sepiaPixel(pixel);

            outputImage[index] =  pixel->r;
            outputImage[index + 1] =  pixel->g;
            outputImage[index + 2] =  pixel->b;
          }
        }

        makeHeader( width, height, input);
        fwrite(outputImage, sizeof(pixel_t), width * height, output);

        free(inputImage);
        free(outputImage);
        fclose(input);
        fclose(output);

return 0;
}


void grayPixel(pixel_t *pixel){
        int sum;
        pixel->r = pixel->r * 0.3;
        pixel->g = pixel->g * 0.5;
        pixel->b = pixel->b * 0.2;
        sum = pixel->r + pixel->g + pixel->b;
        pixel->r = sum;
        pixel->g = sum;
        pixel->b = sum;
}


void sepiaPixel(pixel_t *pixel){
        if (pixel->r < 60){
                pixel->r = pixel->r * 0.9;
                pixel->g = pixel->g * 0.9;
                pixel->b = pixel->b * 0.9;
        }
        else if (pixel->r >= 60 && pixel->r < 190){
                pixel->b = pixel->b * 0.8;
        }
        else {
                pixel->b = pixel->b * 0.9;
        }

}


```

Any suggestions/ideas will be welcome.

---

### Post by Can+~ on 2008-04-10
Difficult to tell where the error is.

On a side note, if you really really need to use sepia tones, there's a utility on bash called "imagemagick", which can produce [sepia tones](http://www.imagemagick.org/script/command-line-options.php#sepia-tone):

[PHP]convert -sepia-tone 80% input_image.png output_image.png[/PHP]

---

### Post by namegame on 2008-04-10
I appreciate the info, however, this is an assignment due in my computer science class. I know this forum is touchy on people asking about homework, however, I feel as if I am well within the rules.

---

### Post by Can+~ on 2008-04-10
> **namegame said:**
> I appreciate the info, however, this is an assignment due in my computer science class. I know this forum is touchy on people asking about homework, however, I feel as if I am well within the rules.

When you do:

[PHP]outputImage[index + 2][/PHP]

I noticed that input/outputImage are made out of *pixel_t*, that would mean, that each [x] you advance, you're actually advancing 1 pixel. So if you do [index + x] you're advancing x amount of pixels, instead of accessing the RGB values they contain.

I think it would be:

[PHP]pixel->r = inputImage[index]->r;
pixel->g = inputImage[index]->g;
pixel->b = inputImage[index]->b;[/PHP]

If you access element [index+x] on the end of the image, it will point outside of the malloc space, causing segmentation fault.

---

### Post by namegame on 2008-04-11
that makes sense to me, however, in a previous program, the code was as I originally stated, and it worked flawlessly, the changes in this program were file I/O, command line arguments, and using typedef struct. I didn't really change much of the "meat" of the program.

---

### Post by WW on 2008-04-11
The variable **input** is of type FILE*, so this line
[php]
      input = malloc (sizeof(pixel_t) * width * height);
[/php]
does not make sense.  You've changed **input** to point to a block of memory, but then you call fread with **input** as the last argument.  You have a similar problem with the variable **output**.

---

