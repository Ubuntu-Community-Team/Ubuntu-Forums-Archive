---
title: "play video file using pygame in python 2.7.3"
date: 2015-11-29
forum: Programming Talk
---

### Post by mitmag on 2015-11-29
I am trying to play an MPG file using pygame in python 2.7.3.
Has  anyone worked out the code to do this? Thanks in advance!
This acts like it is playing, but nothing shows on the screen!
Here is my code:

import pygame, sys 
 
FPS = 30 
 
pygame.init() 
clock = pygame.time.Clock() 
 
size = (640,480) 
screen = pygame.display.set_mode(size) 
 
movie = pygame.movie.Movie("shoot.MPG") 
#screen = pygame.display.set_mode(movie.get_size()) 
movie_screen = pygame.Surface(size).convert() # was movie.get_size() 
 
movie.set_display(movie_screen) 
movie.play() 
 
 
playing = True 
while playing: 
    for event in pygame.event.get(): 
        if event.type == pygame.QUIT: 
            movie.stop() 
            playing = False 
 
    screen.blit(movie_screen,(0,0)) 
    pygame.display.update() 
    clock.tick(FPS) 
 
pygame.quit()

---

### Post by brian-mccumber on 2015-11-29
Here is a link to a code sample that plays a .mpg file with pygame - [https://mail.python.org/pipermail/tutor/2008-May/061748.html](https://mail.python.org/pipermail/tutor/2008-May/061748.html)

It's a little dated but maybe it will help a little.

---

### Post by mitmag on 2015-11-29
This acts much like my program!
Seems to play but nothing shows on screen!
If you have the time, take a look at my code!
Thanks much!

---

### Post by brian-mccumber on 2015-11-30
Maybe you don't have the right codec installed on your computer. I had to install a restricted codec package before I could play dvd movies and the like when I first installed Ubuntu. I can't test this because I don't have the pygame lib or a mp3 file. Will the mp3 play in the Ubuntu video player? It could be codec and it could be a corrupted mp3.

---

### Post by mitmag on 2015-11-30
Actually this is an MP4 file that was converted with ffmpeg to an MPG file.
Said file plays perfectly in Movie Player and SM player. The program works
perfectly, but nothing shows on the screen!

---

### Post by brian-mccumber on 2015-11-30
Well like I said before I can't test the code to help debug it, I don't have pygame installed and I don't have the video file. Maybe there is something going on with the video format from the conversion that python doesn't like, try to insert another movie into your code, like a mp3 that hasn't been run through the converter and see if it plays or another video with a different format just to see if the code is working correctly. If it does then it's a problem with the file format from the conversion if it doesn't then the problem is in the code somewhere.

I have to go put some tires on Grandma's car but when I get back I'll install pygame and if you can upload a copy of the video here maybe I can help you debug this in a few hours or so.

---

### Post by mitmag on 2015-11-30
Sorry I could not get back to you earlier! It has been kind of hectic today!
The following will play a mpg file. There is still a problem: the ffmpeg
command I posted earlier let me play the file with the following code but
it also stripped out all the audio. Check it out:


#!/usr/bin/python

import pygame

pygame.init()
pygame.mixer.init()
playing = 1
screen = pygame.display.set_mode((1024, 768))
background = pygame.Surface((1024, 768))

screen.blit(background, (0, 0))
pygame.display.update()

movie = pygame.movie.Movie("shoot.mpg")
mrect = pygame.Rect(0,0,875,700)
movie.set_display(screen, mrect.move(100, 50))
#movie.set_volume(1)

movie.play()

while playing:     #video.get_busy():
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            playing = 0
            
pygame.quit()


If you have an mpg file that has not been messed with plug it
in and see if you have video plus audio. Thanks!

---

### Post by brian-mccumber on 2015-11-30
It's ok I got back from town later than I expected too.

Does the sound work if you uncomment the line movie.set_volume(1)?

I don't have a mp3 or a mpg on either of my computers, maybe you can attach a small one that hasn't been run through a converter to a message here then I could test this out.

---

### Post by mitmag on 2015-11-30
On fourth line that reads:
pygame.mixer.init()

Should read:
pygame.mixer.quit()

I tried to upload a fresh file but it said it was too big for a zip file.

Maybe tomorrow I can find a smaller one.

Take care and I will be in touch tomorrow!

---

### Post by mitmag on 2015-12-01
Still have not found a small mpg file to upload!
I was going to post a link, but the mpg's are not
too common any more. It seems the problem is
in the conversion because I have a large mpg
file that plays perfectly. When you get time, look
around on the internet to see if you can download
an mpg file to test it out. Thanks for your time!

---

### Post by brian-mccumber on 2015-12-02
Sorry for the delay I didn't get home till late last night and I just went to bed. 

Yeah I figured something was messed up in the file after the conversion. That was my first thought. I will look around when I get home later, I can probably find something I can run through the code.

So have you actually tried making a game with pygame? Like making a character someone can control with the arrow keys or something? Apparently pygame can be used to make a video player, since that is basically what that code does.

---

### Post by mitmag on 2015-12-02
Finally got this solved!
Had to upgrade ffmpeg to 2.8.3!
You will have to compile ffmpeg from source. On the ./configure line add --enable-libmp3lame. This will allow ffmpeg to grab the sound.
There are many ffmpeg tutorials on the internet if you have problems.
New command to convert mp4 to mpg is as follows:

ffmpeg -i infile.mp4 -maxrate 60000k -bufsize 500kB -qscale:v 2 -vcodec mpeg1video -acodec libmp3lame -intra -s xga outfile.mpg

This will create video 1024x768 with sound and picture quality as good as original.

If you have problems, adjust maxrate and bufsize.

Corrected python file is as follows:

import pygame 
 
pygame.init() 
pygame.mixer.quit() 
playing = 1 
screen = pygame.display.set_mode((1024, 768)) 
background = pygame.Surface((1024,768)) 
 
screen.blit(background, (0, 0)) 
pygame.display.update() 
 
movie = pygame.movie.Movie("file.mpg") 
mrect = pygame.Rect(0,0,1024,768)                 
movie.set_display(screen, mrect.move(0, 0)) 
 
movie.play() 
 
while playing:     
    for event in pygame.event.get(): 
        if event.type == pygame.QUIT: 
            playing = 0 
             
pygame.quit()

Enjoy!
Hope this helps someone.

---

