---
title: "HOW-TO: Convert a video on youtube to animated gif"
date: 2008-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by tpp on 2008-04-06
Hi, I don't know if people still use animated gifs at all but I see them used on forums etc. I just wanted to make one and found that the other guides out there didn't get me quite what I wanted. I.e. it wasn't easy to select the exact frames I wanted with mplayer and the other guides seem to use all the frames which can be bulky and slow. I've found this worked well and just wanted to write it up in case I ever want to do it again.

# Youtube to animated gif HOW-TO:

1) Download youtube-dl ([http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)). Run the youtube-dl to rip the video from Youtube into flash video format:

[I]./youtube-dl -o example.flv "http://www.youtube.com/watch?v=cdaAWFoWr2c"
[/I]
2) Convert the flash video format into an avi:
[I]
ffmpeg -i example.flv example.avi[/I]

3) Launch avidemux (sudo apt-get it first) and open the avi file you just created, select the range of frames you want to rip from the avi using the 'A' and 'B' buttons at the bottom, then go to File->Save->Save Selection As jpeg Images and save the images into a new directory.

4) Now this step is optional, but I have found that including all the frames in the gif will make it too large and it will also look slow. I found a rather hacky way around this by writing a perl script to remove frames. Create a new file in a text editor called 'chop.pl' in the same directory of the images. Copy and paste the following into it, changing the variables for youself:
[I]
#!/usr/local/bin/perl
# start_frame should be the smallest number in the filenames of the jpegs e.g example0000.jpg
$start_frame = 0000;
# end_frame should be the largest number in the filenames of the jpegs e.g example1855.jpg
$end_frame   = 1855;
# scaling factor is how many frames you want to remove, 5 for example will remove 4/5's of the frames
$scaling_factor = 5;
# name should be the string appearing in the filenames of the jpegs before the numbers 
$name = "example";

# Compute number of digits needed to display number
use POSIX;
$width = floor(log10($end_frame))+1;

# Remove frames
for ($i = $start_frame; $i <= $end_frame; ++$i)
{
    $str = sprintf("%04d", $i);
  
    $check = $i % $scaling_factor;
    if($check != 0) {
       	  system("rm $name$str.jpg");
    }
}
[/I]
5) Execute the script:

[I]perl chop.pl
[/I]
6) Open up GIMP and open the first jpeg in the series. Go to File->Open As Layers and select the rest of the series. Now go to Filters->Animation->Optimize For Gif. And then save the thing as a gif and enabled animation and voila.

---

### Post by Six_Digits on 2008-04-08
Thank you!

---

### Post by spo0neybard on 2008-05-14
For those who think "Oh my gosh,
I have to import all those images
as layers one by one! Highlight the images
then just click and drag them into the layers
box. (Dialogs > Layers)

---

### Post by theaceoffire on 2008-09-26
I would suggest the Phatch Photo Batch Processor for reducing size, changing resolution, etc.

^_^ Took me *forever to figure this out, thanks for the post!

---

### Post by dopple on 2009-08-15
You the man. I've been having problems with the "extract video range" feature and this has solved my problem> Wish I'd seen this post 2 days ago.

---

### Post by BassKozz on 2009-09-09
Thanks for the post, but I am having trouble using your perl script.
I get the following error when I run it:
> Illegal octal digit '9' at chop.pl line 5, at end of line
BEGIN not safe after errors--compilation aborted at chop.pl line 12
Here is what the script looks like.
```
#!/usr/local/bin/perl
# start_frame should be the smallest number in the filenames of the jpegs e.g example0000.jpg
$start_frame = 0003;
# end_frame should be the largest number in the filenames of the jpegs e.g example1855.jpg
$end_frame = 0480;
# scaling factor is how many frames you want to remove, 5 for example will remove 4/5's of the frames
$scaling_factor = 5;
# name should be the string appearing in the filenames of the jpegs before the numbers
$name = "AG";

# Compute number of digits needed to display number
use POSIX;
$width = floor(log10($end_frame))+1;

# Remove frames
for ($i = $start_frame; $i <= $end_frame; ++$i)
{
$str = sprintf("%04d", $i);

$check = $i % $scaling_factor;
if($check != 0) {
system("rm $name$str.jpg");
}
}

```

EDIT:
Nevermind, I figured it out, I just had to remove the 0 from 0480, so now the line reads:
```
$end_frame = 480;
```
And it worked :-D
Thanks !

---

### Post by MaindotC on 2009-09-27
Nice thread!  Too bad you aren't a regular - 2 beans :( +1 for you.

---

### Post by Xirev on 2010-08-10
Thanks a lot!

---

### Post by rocuan on 2010-10-25
Great example thank you!
even easier way :
```
sudo apt-get install youtube-dl ffmpeg avidemux mplayer

youtube-dl -o [COLOR=DarkGreen]example.flv[/COLOR] "http://www.youtube.com/watch?v=cdaAWFoWr2c"

ffmpeg -i [COLOR=DarkGreen]example.flv example.avi[/COLOR]

avidemux --load [COLOR=DarkGreen]example.avi[/COLOR] --begin **[COLOR=Navy]A[/COLOR]** --end **[COLOR=Navy]B[/COLOR]** --save [COLOR=DarkGreen]output.avi[/COLOR] --quit

mplayer [COLOR=DarkGreen]output.avi[/COLOR] -nosound -vo gif89a:fps=15:output=[COLOR=DarkGreen]example.gif[/COLOR] -vf scale=200:150
```

---

### Post by sisko256 on 2010-11-13
Even easier:

```
sudo apt-get install youtube-dl mplayer

youtube-dl -o example.flv "http://www.youtube.com/watch?v=BNR74UCidBI"

mplayer example.flv -nosound -vo gif89a:fps=15:output=solid.gif -vf scale=240:180 -ss 3:26 -endpos 7

```Result: [http://i.imgur.com/xJhoK.gif](http://i.imgur.com/xJhoK.gif)

There are sites (like [http://www.gifsoup.com/](http://www.gifsoup.com/)) that will automate this process for you but you often have register or supply an email... I like the command line way best.

---

