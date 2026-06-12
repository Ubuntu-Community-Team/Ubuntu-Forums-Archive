---
title: "What's the common method for resizing photos?"
date: 2010-02-04
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-02-04
How do computers downsize images for displaying?  Say you take a photo with your new 15 MP camera at full resolution.  Then you display the photo in full-screen format on a 15 inch monitor running at a resolution of 800 x 600.  Ignoring the issue of aspect ratio, how does the computer downsample the pixels from a large image into a smaller frame?  Several pixels would be mapped to one pixel during this downsizing.  How does this work?

Sorry if this is not the best place to ask the question, this forum is the most relevant that I know of, but would be happy to take my question someplace else if someone can point me where.

---

### Post by kahumba on 2010-02-04
One could skip lines. i.e. if the image is 1600x1600 and you need 400x400 you read every 4th line, it's however more difficult to implement but it's fast - unlike reading the whole image and then scaling it to 400x400.

---

### Post by NovaAesa on 2010-02-04
Just read the whole image into an array, then overlay the new pixel grid. Then you could just take the average of the pixels from the original image that are in the new grid. Then output the new grid as the resized image. If you are changing sizes to go between standard image sizes, then you shouldn't have too many problems with things such as pixels lying on the middle of a grid line.

---

### Post by saulgoode on 2010-02-04
> **SNYP40A1 said:**
> Ignoring the issue of aspect ratio, how does the computer downsample the pixels from a large image into a smaller frame?  Several pixels would be mapped to one pixel during this downsizing.  How does this work?

Generally speaking, you would take the average value of the "several pixels" (that get mapped to a single pixel). For example, if you were scaling a 1000x1000-pixel image down to 500x500 then each of the pixels in the smaller image would be the average of a 2x2 grid of pixels in the larger. But this isn't really how it's done.

The "averaging" of the larger image's pixels is basically the equivalent of blurring that image. So the typical downscaling process is to first effectively blur the original image (the amount of blurring being inversely proportional to the scaling factor), and then to interpolate the value of each of the target pixels from the blurred image.

However, in actuality the two steps, blurring and interpolating, are combined into a single step (this is possible since the blurring operation and the interpolation step can be accomplished with matrix-based convolutions, and the two convolution matrices can be combined and applied in one step).

---

### Post by Some Penguin on 2010-02-04
You'd probably want to also consider edge detection.

There are a LOT of resizing algorithms out there.  If you want to look at source, the 'ImageMagick' package is open-source and has an awful lot of image processing routines, including resizing.

---

### Post by PaulM1985 on 2010-02-04
I generally get an average of the surrounding pixels dependant on the scale that I am doing.  If I am halving the image, I would take a weighted average of the central pixel and the 8 pixels surrounding it.

For the central pixel I would have: Colour * 0.5
For the eight surrounding: Colour * 0.0625.

The iterate over every other pixel in the large image, putting the result in every pixel in the half sized image.

For larger scaling I would use a larger catchment.

Hope this makes sense.

Paul

---

### Post by Sporkman on 2010-02-04
Ditto on the averaging.

I have a tool on my website you can use to try this yourself. Click on the "build one" link in my sig, and enter the following:

```
/* Load an image and manually scale it down 50% */

print("Please upload an image:  ");

/* Limit image size to 2000x2000 pixels */

input inp_img = print_input_image(2000,2000);

print("\n\n");

print_input_button("Scale to half size");

print("\n\n");

load_user_input();

image img;
string err_msg;

get_input_image(inp_img,img,err_msg);

if ( err_msg=="" )
{
   /* Image upload was successfull */

   image new_img;

   /* Make a new image half the size */
   resize_image(new_img,image_wd(img)/2,image_ht(img)/2);

   int i, j;

   for ( j=0; j<image_ht(new_img); ++j )
   {
      for ( i=0; i<image_wd(new_img); ++i )
      {
         rgb p00 = image_p(img,2*i,2*j);
         rgb p01 = image_p(img,2*i,2*j+1);
         rgb p10 = image_p(img,2*i+1,2*j);
         rgb p11 = image_p(img,2*i+1,2*j+1);
         
         rgb p;

         set_rgb_r(p,(rgb_r(p00)+rgb_r(p01)+rgb_r(p10)+rgb_r(p11))/4);
         set_rgb_g(p,(rgb_g(p00)+rgb_g(p01)+rgb_g(p10)+rgb_g(p11))/4);
         set_rgb_b(p,(rgb_b(p00)+rgb_b(p01)+rgb_b(p10)+rgb_b(p11))/4);

         set_image_p(new_img,i,j,p);
      }
   }

   print("\nScaled-down result:\n\n");
   print_image(new_img);
}
else
{
   /*
      Image upload was not successful - you can check err_msg
      for the specific reason.
   */

   print("\nSorry - there was an error!\n\n");
}

```

Compile then run. That will scale down a photo you upload by 50%. Try playing around with it for different scalings.

---

### Post by SNYP40A1 on 2010-02-04
Thanks everyone, I appreciate the suggestions and code.  What happens if the scaling is not a factor of 2?  Say downsizing from 700x700 to 500x500?  The actual application for this is plotting data on an XY plot.  Say I have 513 points and want to plot the data across a chart that is, say, 367 pixels wide.  How would I plot the data?

Note, I tried to figure out how JFreeChart does it, but the library is so complicated it would take me a very long time to trace through it all.  Figured there must be a common method -- same method used to resize images.

---

### Post by Sporkman on 2010-02-04
> **SNYP40A1 said:**
> Thanks everyone, I appreciate the suggestions and code.  What happens if the scaling is not a factor of 2?  Say downsizing from 700x700 to 500x500?  The actual application for this is plotting data on an XY plot.  Say I have 513 points and want to plot the data across a chart that is, say, 367 pixels wide.  How would I plot the data?

Note, I tried to figure out how JFreeChart does it, but the library is so complicated it would take me a very long time to trace through it all.  Figured there must be a common method -- same method used to resize images.

For each pixel in the target (shrunken) image, determine what range of pixels from the original image should be squeezed into it, then take a weighted average of those pixels. I say "weighted" because the boundaries of the range will probably fall on fractional coordinates of the original image.

That's what's going in my example above, except it's simpler as it's by 2, so there's no fancy weighted-averaging going on.

---

### Post by SNYP40A1 on 2010-02-04
> **Sporkman said:**
> For each pixel in the target (shrunken) image, determine what range of pixels from the original image should be squeezed into it, then take a weighted average of those pixels. I say "weighted" because the boundaries of the range will probably fall on fractional coordinates of the original image.

That's what's going in my example above, except it's simpler as it's by 2, so there's no fancy weighted-averaging going on.

I think that sounds like the best approach.  Does anyone know of an open-source algorithm or software library that does this?  I could make it myself, but prefer not to re-invent the wheel or miss out on a more robust implementation if it's already been done.  It would probably be part of a charting utility where one inputs a list of ordered pairs (x, y) and a new list of ordered pairs is returned such that the length of the list is the requested length.

---

