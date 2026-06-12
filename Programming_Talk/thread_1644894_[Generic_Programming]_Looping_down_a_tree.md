---
title: "[Generic Programming] Looping down a tree"
date: 2010-12-13
forum: Programming Talk
---

### Post by durand on 2010-12-13
Hi,

I've got a programming problem that I'm not sure how to code. It's a general what-algorithm-should-I-use sort of problem. The basic context is that I want to separate a comic page into its individual panels.

[IMG]http://dl.dropbox.com/u/336801/comic.png[/IMG]

What I do is scan through each line in the vertical direction and if the line has more than, say, 5 black pixels, it is not a separator. Otherwise it is. I then repeat this in the horizontal direction like in the image above. This is done by manually writing 2 loops. What I would like to do is have an automatic while/for loop which repeats the scanning in the vertical direction again, then in the horizontal direction and continue until it is impossible to split the image into smaller panels.

Is there a way to do this? I've looked for a few tree algorithms but I couldn't find one that I understood well enough to write my own version of.

My python code is below, crop_panels() is the relevant function.

Thanks!

```

#!/usr/bin/env python

from __future__ import division
import sys
import os
import numpy
from PIL import Image
import datetime

def detect_white(image):
    """This function takes a PIL image and returns a numpy array of booleans"""
    
    # Save a b&w image for testing
    image.convert('1', dither=0).save('black_white.png')
    
    # Make a color matrix of the image
    image_array = image.convert('1', dither=0).load()
    
    pixel_array = []
    # Array of pixels
    for index in range(image.size[1]):
        pixel_array.append([])
        for i in range(image.size[0]):
            # If color is greater than 250, then it's white (True)
            pixel_array[index].append(image_array[i, index] >= 250)
    
    # Convert list of lists into a numpy array
    pixel_array = numpy.array(pixel_array)
    
    # Return size and array as a tuple
    
    return pixel_array

def detect_stripes(area_array, threshold):
    """This function detects horizontal (=) stripes in an area of an image"""
    # Get width and height (shape of matrix)
    height, width = area_array.shape
    # Calculate number of pixels allowed to be False for it to still be a stripe
    false_pixels = int(height * threshold)
    
    # Fill a list with all pixels
    stripes = range(height)
    
    # Loop through each row in the image, checking whether the pixels are True
    for line_index, line in enumerate(area_array):
        # Start with zero false pixels
        num_false_pixels = 0
        for pixel in line:
            # If the number of allowed false pixels is reached, go to the next line
            if pixel == False:
                if num_false_pixels >= false_pixels:
                    stripes.remove(line_index)
                    break
                else:
                    num_false_pixels += 1
    stripes.append(0) # Assume that there is a stripe at the start and end of the image
    stripes.append(height)
    return stripes

def clean_stripes(stripes):
    """This function consolidates stripes that are close together"""
    
    clean_stripes = []
    i = 0
    # Go through the stripes
    while i < len(stripes):
        try:
            total = stripes[i]
            number_of_lines = 1
            while stripes[i] + 1 == stripes[i + 1]:
                i += 1
                number_of_lines += 1
                total += stripes[i]
        except IndexError: # If the value is the last in the list
            pass
        try:
            clean_stripes.append(int(total/number_of_lines))
        except ZeroDivisionError:
            clean_stripes.append(stripes[i])    
        i += 1
    # Remove duplicates
    clean_stripes = list(set(clean_stripes))
    clean_stripes.sort()
    return clean_stripes
    
def crop_panels(image):
    """This function returns a tree of panels"""
    
    # Orientation - 0 is horizontal (=), 1 is vertical (||), swap every loop
    pixel_array = detect_white(image)
    # Get width and height (shape of matrix)
    height, width = pixel_array.shape    
    crop_array = [] # [(top_x, top_y, bottom_x, bottom_y), [(top_x, top_y, bottom_x, bottom_y)]]
    
    # Scan horizontally
    stripes = clean_stripes(detect_stripes(pixel_array, HORIZONTAL_THRESHOLD))
    
    # Convert to crop boxes and append
    for stripe_index, stripe in enumerate(stripes):
        try:
            crop_array.append((0, stripe, width, stripes[stripe_index + 1]))
        except IndexError: # Last stripe
            pass
    
    
    # Scan vertically
    for box_index, box in enumerate(crop_array):
        box_array = []
        stripes = clean_stripes(detect_stripes(pixel_array[box[1]:box[3],box[0]:box[2]].T, VERTICAL_THRESHOLD))

        for stripe_index, stripe in enumerate(stripes):
            try:
                box_array.append((stripe, crop_array[box_index][1], stripes[stripe_index + 1], crop_array[box_index][3]))
            except IndexError: # Last stripe
                pass
        
        # Replace coordinates with new panels if found
        if len(box_array) > 0:
            crop_array[box_index] = box_array
        else: # Otherwise use old panels
            try:
                crop_array[box_index] = [(0, crop_array[box_index], width, crop_array[box_index + 1])]
            except IndexError: # If it's the last, use the height
                crop_array[box_index] = [(0, crop_array[box_index], width, height)]
    
    return crop_array

def output_panels(image, panel_array):
    """This function takes a panel array and outputs individual images"""
    
    for indexi, i in enumerate(panel_array):
        for indexj, j in enumerate(i):
            image.crop(j).save('%s_%s-%s.png'%(INPUT_FILE, indexi, indexj))

    
def init():
    """Run application"""
    global INPUT_FILE, HORIZONTAL_THRESHOLD, VERTICAL_THRESHOLD
    # Get input file
    INPUT_FILE = sys.argv[1]
    # Percentage of line to be black but still a stripe
    HORIZONTAL_THRESHOLD = 0.01
    VERTICAL_THRESHOLD = 0.0
    
    # Get image
    image = Image.open(INPUT_FILE)
    
    # Crop panels out and output images
    output_panels(image, crop_panels(image))
    
    
if __name__ == "__main__":
    init()

```

EDIT: I think I'm supposed to use a [http://en.wikipedia.org/wiki/Breadth-first_traversal](http://en.wikipedia.org/wiki/Breadth-first_traversal)

---

### Post by Queue29 on 2010-12-13
You familiar with recursion?

All you need is a recursive function which looks for separators: If it finds none, you've hit the base case (an individual panel) and you can store it away. Otherwise, you crop/cut up the image appropriately and recursively call the function on each new image.

---

### Post by durand on 2010-12-13
Yeah, I've been playing with recursive functions to do that but it's giving me a headache. I guess I'll just start with a simpler problem and practise first.

---

### Post by Vaphell on 2010-12-13
in pseudocode it would be something along the lines of

```

cut_to_pieces( piece, orientation )
{
  if orientation == horizontal
    orientation = vertical
  else
    orientation = horizontal
#to alternate -> H,V,H,V

  if separator not found
    exit current function #this piece is indivisible, end of recursion is here
  else
    for each found_piece in piece
      cut_to_pieces( found_piece, orientation )
}

main
{
  cut_to_pieces( image, vertical )
}

```

you can simulate these mechanics on something simpler, like ordinary string with parentheses
str=(A)([B][C])([D][(E)(F)]) where alternate () and [] are equivalent of horizontal/vertical
recursion is quite expensive though

---

### Post by squenson on 2010-12-13
Interesting problem!

I am not sure that your algorithm will work in all cases. For example, imagine a page of a size 3x3:```
123
456
789
```with five images 12, 47, 36, 89 and 5 There is no horizontal nor vertical line which can be considered as a separator.

Having said that, a possible algorithm could be to work with horizontal and vertical segments and try defining the largest rectangle starting from the top left corner; then to repeat the operation from the found borders.

Of course, all this supposes that the cases have horizontal and vertical borders...

---

### Post by durand on 2010-12-13
Hi Vaphell, your code works but I can't see of a way to modify it to store something in a list of increasing dimensions, like I have been doing. Though thinking about it, I could just have a second list and substitute one cropping box for a set of cropping box without increasing dimensions. I'll try that tomorrow.

squenson, yeah, that is another problem. A third is if the separators are not perfectly horizontal or vertical. I was basically going to do as you suggested, but the problem is it involves masses of computer time. Maybe I could detect stripes of 50 pixels or more, generate an equation for it and then see if they intersect? I have no idea how to go about that though :S

Thanks everyone for their suggestions!

---

### Post by Vaphell on 2010-12-14
what do you mean by list of increasing dimensions? you copy the data over for further division?
if so you can work on a single global instance of your image data and calculate only bounding boxes recursively ( so the function would use only coordinates as parameters -> cut( top_y, bottom_y, left_x, right_x ) ). Inside the function only the subset of pixels would be tested, x from leftx to rightx, y from bottomy to topy. Add results to some global list that is used to actually cut the stuff out of the input image at the end.

 

and yeah, all these exceptions are nasty - though nobody said that the pattern recognition is easy :-)

---

### Post by Arndt on 2010-12-14
> **Vaphell said:**
> 
you can simulate these mechanics on something simpler, like ordinary string with parentheses
str=(A)([B][C])([D][(E)(F)]) where alternate () and [] are equivalent of horizontal/vertical
recursion is quite expensive though

In what sense is recursion expensive?

---

### Post by Vaphell on 2010-12-14
in the obvious sense that it can be a memory hog - you can't run 1000000 recursions happily and expect not running out of memory. Of course not the case with few layers, unless the boatloads of data are copied without much thought.

---

### Post by Arndt on 2010-12-14
> **Vaphell said:**
> in the obvious sense that it can be a memory hog - you can't run 1000000 recursions happily and expect not running out of memory. Of course not the case with few layers, unless the boatloads of data are copied without much thought.

In some languages, you can, but I suppose you are talking about Python.

---

### Post by durand on 2010-12-14
> **Vaphell said:**
> what do you mean by list of increasing dimensions? you copy the data over for further division?
if so you can work on a single global instance of your image data and calculate only bounding boxes recursively ( so the function would use only coordinates as parameters -> cut( top_y, bottom_y, left_x, right_x ) ). Inside the function only the subset of pixels would be tested, x from leftx to rightx, y from bottomy to topy. Add results to some global list that is used to actually cut the stuff out of the input image at the end.

 

and yeah, all these exceptions are nasty - though nobody said that the pattern recognition is easy :-)

I think thats what I will do. My current way of storing the crop coordinates is by using lists inside lists.

1 dimension - [(top_x, top_y, bottom_x, bottom_y)]
2 dimensions - [[(top_x, top_y, bottom_x, bottom_y), (top_x, top_y, bottom_x, bottom_y)], [(top_x, top_y, bottom_x, bottom_y), (top_x, top_y, bottom_x, bottom_y), (top_x, top_y, bottom_x, bottom_y)]]
3 dimensions - [[[(top_x, top_y, bottom_x, bottom_y)], [(top_x, top_y, bottom_x, bottom_y), (top_x, top_y, bottom_x, bottom_y)]], [[(top_x, top_y, bottom_x, bottom_y)]]]

Each dimension is added when I scan in the next direction. This was to be able to trace the route of the cropping so I can see where each section of a crop comes from but it does create a few annoying problems so I think I'll just have a 1 dimensional list containing all the boxes.

Thanks :)

---

