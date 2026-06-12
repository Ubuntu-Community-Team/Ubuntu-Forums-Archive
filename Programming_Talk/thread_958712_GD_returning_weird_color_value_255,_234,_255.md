---
title: "GD returning weird color value: 255, 234, 255"
date: 2008-10-25
forum: Programming Talk
---

### Post by tom66 on 2008-10-25
I am writing a pixelization script/program, to be integrated as part of another program involving motion detection. However, it is not working: each pixel value queried brings up a value of 255/234/255 or something similar, where it should bring up the value in the top left corner of every 10 or so pixels in both dimensions. 

```

void image_pixelize(gdImagePtr im, int bw, int bh, pixelize_mode mode)
{
	int x = 0, y = 0;
	int sx = 0, sy = 0;
	int color = 0;
	double total_red = 0, total_blue = 0, total_green = 0;
	float mean_red_f = 0.0, mean_green_f = 0.0, mean_blue_f = 0.0;
	int mean_red = 0, mean_green = 0, mean_blue = 0;
		
	sprintf(_debug_msg, "PIXELIZE. Using mode: %d. bw=%d, bh=%d", mode, bw, bh);
	DEBUG(_debug_msg);

	/* process the image, block-by-block */
	for(x = 0; x < gdImageSX(im); x += bw)
	{
		for(y = 0; y < gdImageSY(im); y += bh)
		{
			if(mode == PIXELIZE_TOP_LEFT_COLOR)
			{
				color = gdImageGetPixel(im, x, y);
			}
			else if(mode == PIXELIZE_TOP_RIGHT_COLOR)
			{
				color = gdImageGetPixel(im, x + (bw - 1), y);
			}
			else if(mode == PIXELIZE_BOTTOM_LEFT_COLOR)
			{
				color = gdImageGetPixel(im, x, y + (bh - 1));
			}
			else if(mode == PIXELIZE_BOTTOM_RIGHT_COLOR)
			{
				color = gdImageGetPixel(im, x + (bw - 1), y + (bh - 1));
			}
			else if(mode == PIXELIZE_MEAN)
			{
				/* use arithmetic mean to calculate the color */
				/* use 'double' to store the values: they might get large quickly */
				for(sx = x; sx < (x + bw); x++)
				{
					for(sy = y; sy < (y + bh); y++)
					{
						if(sx < gdImageSX(im))
						{
							if(sy < gdImageSY(im))
							{
								color = gdImageGetPixel(im, sx, sy);
						
								total_red += gdImageRed(im, color);
								total_green += gdImageGreen(im, color);
								total_blue += gdImageBlue(im, color);
							}
						}
					}
				}
				
				/* average them out, rounding them later */
				mean_red_f = total_red / (bw * bh);
				mean_green_f = total_green / (bw * bh);
				mean_blue_f = total_blue / (bw * bh);
				
				mean_red = (int)floor(mean_red_f);
				mean_green = (int)floor(mean_green_f);
				mean_blue = (int)floor(mean_blue_f);
				
				/* compute the color */
				color = gdImageColorAllocate(im, mean_red, mean_green, mean_blue);
			}
			
			sprintf(_debug_msg, "Processed (%d, %d, %d, %d) as %d. ", x, y, x + bw, y + bh, color);
			// DEBUG(_debug_msg);
			
			/* add rectangle to image, being careful not to overwrite current position */
			gdImageFilledRectangle(im, x, y, x + bw, y + bh, color);
		}
	}
}

```

Any and all help appreciated. Thanks!

---

### Post by pp. on 2008-10-25
How are we to know that a whitish colour is not the correct result? And what do you mean by a value 'or so'?

---

### Post by tom66 on 2008-10-25
'or so' means an amount of uncertainty. It could have been 255, 238, 255 or 255, 244, 255, but I can't remember. It is constant across the whole image. The value is incorrect; it should be returning rarely, if ever, that, and only as a legitimate color value. It is not doing that, as far as I can work out. 

Thanks.

---

### Post by pp. on 2008-10-26
Is it possible that the colour which you can't remember is the colour of the top left corner of your image? Also, is it possible that you called your procedure with a mode of PIXELIZE_TOP_LEFT_COLOR?

Also, you might consider giving people a bit more information, such as how you called your procedure and how large the image to be processed was and, perhaps, a ***few*** of the lines your procedure printed.

---

### Post by tom66 on 2008-10-26
It's possible, but it should be moving across the whole image and producing different colors. (e.g. the top left pixel of every 10th block) Here's the full code:

```

#include <ctype.h>
#include <gd.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <math.h>

#include "motion.h"

#define FRAME_1 "image-001.png"
#define FRAME_2 "image-002.png"

gdImagePtr _frame_ptrs[2];
gdImagePtr _frame_buffer;

FILE* _frame_fp[2];
FILE* _frame_out_buffer;

int _bw = 10;
int _bh = 10;

char _debug_msg[100], _file_tn[30];
	
void image_pixelize(gdImagePtr im, int bw, int bh, pixelize_mode mode)
{
	int x = 0, y = 0;
	int sx = 0, sy = 0;
	int color = 0;
	double total_red = 0, total_blue = 0, total_green = 0;
	float mean_red_f = 0.0, mean_green_f = 0.0, mean_blue_f = 0.0;
	int mean_red = 0, mean_green = 0, mean_blue = 0;
		
	sprintf(_debug_msg, "PIXELIZE. Using mode: %d. bw=%d, bh=%d", mode, bw, bh);
	DEBUG(_debug_msg);

	/* process the image, block-by-block */
	for(x = 0; x < gdImageSX(im); x += bw)
	{
		for(y = 0; y < gdImageSY(im); y += bh)
		{
			if(mode == PIXELIZE_TOP_LEFT_COLOR)
			{
				color = gdImageGetPixel(im, x, y);
			}
			else if(mode == PIXELIZE_TOP_RIGHT_COLOR)
			{
				color = gdImageGetPixel(im, x + (bw - 1), y);
			}
			else if(mode == PIXELIZE_BOTTOM_LEFT_COLOR)
			{
				color = gdImageGetPixel(im, x, y + (bh - 1));
			}
			else if(mode == PIXELIZE_BOTTOM_RIGHT_COLOR)
			{
				color = gdImageGetPixel(im, x + (bw - 1), y + (bh - 1));
			}
			else if(mode == PIXELIZE_MEAN)
			{
				/* use arithmetic mean to calculate the color */
				/* use 'double' to store the values: they might get large quickly */
				for(sx = x; sx < (x + bw); x++)
				{
					for(sy = y; sy < (y + bh); y++)
					{
						if(sx < gdImageSX(im))
						{
							if(sy < gdImageSY(im))
							{
								color = gdImageGetPixel(im, sx, sy);
						
								total_red += gdImageRed(im, color);
								total_green += gdImageGreen(im, color);
								total_blue += gdImageBlue(im, color);
							}
						}
					}
				}
				
				/* average them out, rounding them later */
				mean_red_f = total_red / (bw * bh);
				mean_green_f = total_green / (bw * bh);
				mean_blue_f = total_blue / (bw * bh);
				
				mean_red = (int)floor(mean_red_f);
				mean_green = (int)floor(mean_green_f);
				mean_blue = (int)floor(mean_blue_f);
				
				/* compute the color */
				color = gdImageColorAllocate(im, mean_red, mean_green, mean_blue);
			}
			
			sprintf(_debug_msg, "Processed (%d, %d, %d, %d) as %d. ", x, y, x + bw, y + bh, color);
			// DEBUG(_debug_msg);
			
			/* add rectangle to image, being careful not to overwrite current position */
			gdImageFilledRectangle(im, x, y, x + bw, y + bh, color);
		}
	}
}

int main(int argc, char* argv[])
{
	int i = 0;
	
	int last_sx = 0;
	int last_sy = 0;
	
	/* try to open the files */
	for(i = 0; i < 2; i++)
	{
		sprintf(_debug_msg, "Trying to open file #%d (%s)... ", i + 1, argv[i + 1]);
		DEBUG(_debug_msg);
		
		_frame_fp[i] = fopen(argv[i + 1], "r+b");
		
		if(_frame_fp[i] == NULL)
		{
			perror("DEBUG");
			
			sprintf(_debug_msg, "Could not open file #%d (%s)! ", i + 1, argv[i + 1]);
			FATAL(_debug_msg);
		}
		else
		{
			sprintf(_debug_msg, "Successfully opened file #%d (%s). ", i + 1, argv[i + 1]);
			DEBUG(_debug_msg);
			
			/* try to read the PNGs into memory */
			DEBUG("Trying to read PNG into GD and memory... ");
			_frame_ptrs[i] = gdImageCreateFromPng(_frame_fp[i]);
			
			/* check the PNG is OK */
			if(_frame_ptrs[i] == NULL)
			{
				sprintf(_debug_msg, "Invalid or garbled PNG file #%d (%s). Check format. ", i + 1, argv[i + 1]);
				FATAL(_debug_msg);
			}
			
			/* check images have the same dimensions */
			if(last_sx == 0 || last_sy == 0)
			{
				last_sx = gdImageSX(_frame_ptrs[i]);
				last_sy = gdImageSY(_frame_ptrs[i]);
			}
			else
			{
				if(last_sx != gdImageSX(_frame_ptrs[i]) || last_sy != gdImageSY(_frame_ptrs[i]))
				{
					sprintf(_debug_msg, "Invalid dimensions: %d * %d != %d * %d (previous != current). ", 
						last_sx, last_sy, gdImageSX(_frame_ptrs[i]), gdImageSY(_frame_ptrs[i]));
					FATAL(_debug_msg);
				}
			}
		}
	}
	
	DEBUG("2 files opened. ");
	DEBUG("Pixelizing images. ");
	
	for(i = 0; i < 2; i++)
	{
		/* process each image */
		sprintf(_debug_msg, "Pixelizing image #%d (this might take a second)... ", i + 1);
		DEBUG(_debug_msg);
		
		image_pixelize(_frame_ptrs[i], _bw, _bh, PIXELIZE_TOP_LEFT_COLOR);
		
		/* try to open a file to save to */
		sprintf(_file_tn, "_out_%d.png", i + 1);
		sprintf(_debug_msg, "Saving image #%d (pixelized) as %s... ", i + 1, _file_tn);
		DEBUG(_debug_msg);
		
		_frame_out_buffer = fopen(_file_tn, "w+b");
		gdImagePng(_frame_ptrs[i], _frame_out_buffer);
	}
	
	DEBUG("Cleaning up memory: Destroy images. ");

	for(i = 0; i < 2; i++)
	{
		gdImageDestroy(_frame_ptrs[i]);	
		
		sprintf(_debug_msg, "Destroyed image #%d. ", i + 1);
		DEBUG(_debug_msg);
	}
	
	return 1;
}

```

The images are both 320x240, and in the PNG format. I am working on a block size of 10. Making the block size 1 makes no difference.

---

### Post by pp. on 2008-10-26
> **tom66 said:**
> It's possible


Is it the colour, or is it not?

I see that your code appears to save the pixelized image to a file. Have you looked at one of those?

---

### Post by tom66 on 2008-10-26
Yeah, I have looked at both of the files. It is a light pink, as the color would indicate.

By 'it's possible' I mean that it's possible it's the first color in the image, e.g. top left (0, 0), but that still doesn't agree with the rest of the image, which should be of varied colors. 

Thanks,
Tom

---

### Post by tom66 on 2008-10-26
I *think* I may have found the problem. The program was overwriting parts of the image it was working on. It's no longer producing pink, but it is still not pixelizing the image and is returning accurate pixel-for-pixel colors.

---

### Post by pp. on 2008-10-26
Yes, the function overwrote the picture it was processing by the color found in the top left pixel.

Now that you have somehow changed your program so that it does not overwrite its source picture any more, perhaps you repost the changed version or apply the changes to the first post if you still need help with it.

---

### Post by tom66 on 2008-10-26
> **pp. said:**
> Yes, the function overwrote the picture it was processing by the color found in the top left pixel.

Now that you have somehow changed your program so that it does not overwrite its source picture any more, perhaps you repost the changed version or apply the changes to the first post if you still need help with it.

I'm not wanting to post it yet, as I'm still working on it.

---

