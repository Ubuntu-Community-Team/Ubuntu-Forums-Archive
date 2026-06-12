---
title: "Moving pictures &amp; any file"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by josephmills on 2011-10-01
Hi there I would like to thanks you for taking the time to read this.

I am trying to move around a lot of files mainly icons. So I will use icons for an example. 

under /usr/share/icons/oxygen/48/preferences-desktop-default-applications.png 


this is the icon that is for applications under the menu 

[img]http://img268.imageshack.us/img268/138/snapshot1pn.png[/img]  


Now I should not that there are more then just one size of these icons and here is where my question comes into play. Is it easier for me to open gimp as root then just copy and paste the new icon over each one and re-size then delete the background. leaving nothing but my (my)icon. This works and I have done this in the past. But is there a way that I could just make a image that is bigger then all the icons. then have it replace all the icons that I want it to and re-size it self's ?  

lets use /usr/share/icons/oxygen/48/preferences-desktop-default-applications.png 

my icon is called ourshare.png and it is in ~/Pictures it is 200x200 px 

sudo mv ~/Pictures/ourshare.png /usr/share/icons/oxygen/48/preferences-desktop-default-applications.png 



now I know that that will move it and rename it (I think) 
next is dealing with all the sizes 

Is there a command that will take ourshare.png move it and rename it and also re-size it using the size of the folder in this ex-sample 48x48 pix ? 

under /usr/share/icons/oxygen/
you can see that there is a bunch of different files and all called by there image size so I thought that that might help. I think that something like this would be cool and could be used for altering all icons if it would work. 


So I guess my question is what is the most sustainable way of going about this? 

1) gimp and re-sizing and scaling <--- not hard takes up some time 
2) figure out a script like I talked about above
3) is there a different way to go about this that I am not thinking about 

Once again thanks for taking the time to read this and I look forward to hearing from you in the near future 
thanks 
Joseph

---

### Post by towheedm on 2011-10-02
ImageMagick allows image manipulations from the command line.  Using this in a shell script should do what you want.

Description: image manipulation programs
 ImageMagick is a software suite to create, edit, and compose bitmap images.
 It can read, convert and write images in a variety of formats (over 100)
 including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PhotoCD, PNG, Postscript,
 SVG, and TIFF. Use ImageMagick to translate, flip, mirror, rotate, scale,
 shear and transform images, adjust image colors, apply various special
 effects, or draw text, lines, polygons, ellipses and Bézier curves.
 All manipulations can be achieved through shell commands as well as through
 an X11 graphical interface (display).

---

### Post by papibe on 2011-10-02
> **towheedm said:**
> ImageMagick allows image manipulations from the command line.  Using this in a shell script should do what you want.
+1

There are several command line programs that are part of that suit, like example mogrify, convert, etc.

For example: to resize a picture:
```
$ mogrify -resize 640x480 picture.jpg
```
As for any command line and script, I would recommend backing up your pics in case of any problem.

Regards.

---

### Post by josephmills on 2011-10-03
Wow thanks you all rock.

---

