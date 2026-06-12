---
title: "Fastest ubuntu image library for annotating"
date: 2011-05-19
forum: Programming Talk
---

### Post by aznnico on 2011-05-19
I am currently working with images and would like to know the fastest image processing library regarding annotating. I'm currently using this command:

convert orig.tif -background Red -density 300 -font /usr/share/fonts/truetype/msttcorefonts/Arial.ttf -pointsize 12 -gravity south -splice 0x150 -gravity southwest -annotate +50+50 "left corner" -gravity southeast -annotate +50+50 'right corner' +repage endorsed.tif  

I'm calling this within the subprocess.call method in python. If I do this in command line, I get around 1 second total time:

real    0m0.162s
user    0m0.940s
sys     0m0.030s

My program averages 1.96 seconds:

[**copied_from** avg] 0:00:00.071887
[**mysql** avg] 0:00:00.000265
[**cropped** avg] 0:00:00.433935
[**rm** avg] 0:00:00.007758
[**copied_to** avg] 0:00:00.147880
[**endorsed** avg] 0:00:01.963496
[**mssql** avg] 0:00:00.000010

I'm not sure why there's a discrepancy between calling it from command line or through python's subprocess.call(cmd,shell=True). Either way, both of these are too slow.

I'm basically cropping and annotating images. It seems that cropping is fast enough with imagemagick's convert, but annotating is too slow. Does anyone know of a faster image library? I'm comfortable using python/ruby, but at this point, any solution that is faster would be helpful.

Thanks everyone.

---

### Post by cgroza on 2011-05-19
Did you take a look at Python Imaging API (PIL)?

---

### Post by aznnico on 2011-05-20
I have tried PIL. I get the following results: 

$ python pil_crop.py 
0:00:00.112008

$ python pil_endorse.py 
0:00:00.115496

This seems to be significantly faster than ImageMagick, although I haven't tried it through the API yet. 

Has anyone tried VIPS? vips.ecs.soton.ac.uk/index.php?title=Speed_and_Memory_Use This looks promising.

---

