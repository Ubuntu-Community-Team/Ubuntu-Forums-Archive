---
title: "php images..."
date: 2006-02-21
forum: Programming Talk
---

### Post by grim918 on 2006-02-21
Does anyone know how to rescale images with php. I been using the getimagesize(). Then i just divide the width and height by what ever number that i want to rescale it. My problem is that i want any image regardless of it's size to rescale to a default width of 100 pixels. Here is my code:

<?php 
$src = "pic.jpg";
$diff= 100;
$size = getimagesize($src);
$width = $size[0] - ($size[0] - $diff); //rescales width to 100pixels
?>

this will rescale an images width to 100 pixels. my problem is how do i deal with the height of the image. I don't know how to keep it proportional. Am I doing this right or is there a better method. Thank you for any help you can give me.

---

### Post by heimo on 2006-02-21
grim918:
[php]
$src = "pic.jpg";
$diff= 100;
$size = getimagesize($src);
$width = $size[0] - ($size[0] - $diff); //rescales width to 100pixels
[/php] 
 :shock: Oh... Are you actually resizing those images, or just using $width and $height to make it scale using img-tag properties in html?

What I think I'm seeing in your code... Let's say you want $width to be 100. Why... is it needed to calculate it from images width? Won't the $width always get value 100 anyway?

Maybe this helps a bit (you'd probably need to clean it / make sure no stupid things happen with odd image sizes - like 0x0):
[php] $src = "pic.jpg";
$width=100;
list($pic_width,$pic_height) = getimagesize($src);
$height=round($pic_height/($pic_width/$width));

printf('pw: %s ph: %s w:%s h:%s',
        $pic_width,
        $pic_height,
        $width,
        $height
);
[/php]

---

### Post by grim918 on 2006-02-21
No im not actually resizing the images. i want to use with the <img> tag.
I'm working on a script that will allow users to upload a picture of varying size, but i want that picture to display with the <img> tag at a width of 100 pixels. Thank you for your help, I will try out that method as soon as I get home from school.

---

### Post by nemik on 2006-02-21
> **grim918]Does anyone know how to rescale images with php. I been using the getimagesize(). Then i just divide the width and height by what ever number that i want to rescale it. My problem is that i want any image regardless of it's size to rescale to a default width of 100 pixels. Here is my code:

<?php 
$src = "pic.jpg" said:**
>  - ($size[0] - $diff); //rescales width to 100pixels
?>

this will rescale an images width to 100 pixels. my problem is how do i deal with the height of the image. I don't know how to keep it proportional. Am I doing this right or is there a better method. Thank you for any help you can give me.

well first find the ratio of height to width of the original image:

$height_to_width_ratio = $size[1] / $size[0];

the do your code:
$diff= 100;
$width = $size[0] - ($size[0] - $diff); //rescales width to 100pixels

then multiply the width by the ratio to get the height:

$height = $width * $height_to_width_ratio;

I hope this makes sense.

---

### Post by grim918 on 2006-02-21
this makes perfect sense. Thank you.

---

