---
title: "PHP: How to dynamically add images in a row downwards with exact spacing?"
date: 2010-10-27
forum: Programming Talk
---

### Post by hockey97 on 2010-10-27
I already coded my website. I already made the htm, css, php code.

I hand code the site. I am trying to display images with using css top values to be dynamically changed to display images downwards with exact same space between each image.

I currently did the css style for 2 images and then took the difference in the top value and then added that difference to the 2nd images top value to make that value to be put in place for the 3rd image top value. The problem is that the more images that are displayed farther spaced. In otherwords the space between each image starts to increase. I don't want that to happen I want the spacing to be exact the whole time. So the more images there is to display the bigger spacing is which I don't want. I want the spacing to be the same regardless how many images there are displayed.

So here is a example concept what I am doing: 

image 1 top 40px , image 2 top 120px; 

120 - 40 = 80;

image 3 = image 2 top value + 80 which is 200. 

What I just posted isn't code it's just the concept of what I am doing.

I assume this keeps the same spacing inbetween images but the real results shows the more images there are to be displayed the spacing inbetween increases. 

So in other words images 1 to 3 are ok exact same spacing. Yet images 4 to 6 increases the spacing by 10% then 7 to 9 it increases the spacing by 40% then like 10 to 14 it increases the spacing by 60%. These show up as huge gaps between the images starting at the 10th image. SO the spaces increase rapidly when there is more images displayed.

I am getting the images from the database and displaying them.

What I want to know is how can you display the images to have the same spacing inbetween each image. This is what I can't do.

the images are being displayed in a row going down and I don't mean row as in a html table. I mean just describing how the images are displayed using css and php to change the top values as more images are to be displayed. So the top value increase causing the images to be displayed in a row downwards. Each image has the same left value but for every image there is they have the top value increased.

The code works fine it's just I think my concept is flawed.

what I am doing is for example  image 1 top val.

I would take write php code like : $image1_top = $image1_top + '400'; 

the variable above I just showed would be in a while loop which counts backwards from the total images needed to be displayed. So for every interval or loop that gets completed. I would add 400 to the css value of the next image.

---

