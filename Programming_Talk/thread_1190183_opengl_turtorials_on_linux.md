---
title: "opengl turtorials on linux?"
date: 2009-06-17
forum: Programming Talk
---

### Post by monkeyslayer56 on 2009-06-17
ive been useing google but all i can find in teh way of opengl tutorials is either written in 2000 or for windows. also idk for sure but on some of teh tuts i did find i would copy and paste the source code and get an error :( don't know if i don't have something set up write or if its my IDE because on one of the tuts(still looking at) it had a very simple program and a makefile i used make instead of my IDE and it compiled flawlessly wile in the ide (code blocks) it would get like 50 errors so if anyone can help with either of those i would be very thankful and sry if this is a noob question

---

### Post by ibuclaw on 2009-06-17
Make sure that you have the GL development packages installed, and you are setting the linker flags probably in codeblocks.

Also, if you are able to post the compile error message, please do. As that will help us identify the problem.

Regards
Iain

---

### Post by monkeyslayer56 on 2009-06-17
well since i seem to get similar errors on all of the examples for opengl i have found i will just post this most recent one and its errors and hopefully then i'll be able to get codeblocks set up right 
 
build in codeblocks:```
/home/josh/Documents/cube/main.o||In function `update(int)':|
main.cpp|| undefined reference to `glutPostRedisplay'|
main.cpp|| undefined reference to `glutTimerFunc'|
/home/josh/Documents/cube/main.o||In function `drawScene()':|
main.cpp|| undefined reference to `glClear'|
main.cpp|| undefined reference to `glMatrixMode'|
main.cpp|| undefined reference to `glLoadIdentity'|
main.cpp|| undefined reference to `glTranslatef'|
main.cpp|| undefined reference to `glLightModelfv'|
main.cpp|| undefined reference to `glLightfv'|
main.cpp|| undefined reference to `glLightfv'|
main.cpp|| undefined reference to `glRotatef'|
main.cpp|| undefined reference to `glBegin'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glNormal3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glNormal3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glNormal3f'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glNormal3f'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glEnd'|
main.cpp|| undefined reference to `glEnable'|
main.cpp|| undefined reference to `glBindTexture'|
main.cpp|| undefined reference to `glTexParameteri'|
main.cpp|| undefined reference to `glTexParameteri'|
main.cpp|| undefined reference to `glColor3f'|
main.cpp|| undefined reference to `glBegin'|
main.cpp|| undefined reference to `glNormal3f'|
main.cpp|| undefined reference to `glTexCoord2f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glTexCoord2f'|
main.cpp|| undefined reference to `glVertex3f'|
main.cpp|| undefined reference to `glTexCoord2f'|
||More errors follow but not being shown.|
||Edit the max errors limit in compiler options...|
||=== Build finished: 50 errors, 0 warnings ===|

```


output from useing make file and the make comand: ```
g++ -Wall -o cube main.cpp imageloader.cpp -lglut
imageloader.cpp: In function ‘Image* loadBMP(const char*)’:
imageloader.cpp:141: warning: suggest parentheses around && within ||

```

when useing codeblocks it did not make the excutable wile with the make file it only spit those lines out and did make the excutable witch acording to the turtorial works like it should

im aatching the source file from the site 
and here is that particular one [http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/video.php]("http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/video.php")

this is the main thing holding me back are those errors witch at first i though were because i was using windows tutorials now im not so sure

---

### Post by Lux Perpetua on 2009-06-17
Compile with -lGL -lGLU -lglut.

---

### Post by moma on 2009-06-18
Hello

See also this thread and check the provided links
[http://ubuntuforums.org/showthread.php?p=7331457#post7331457](http://ubuntuforums.org/showthread.php?p=7331457#post7331457)

---

### Post by monkeyslayer56 on 2009-06-18
well for that program i found out it was mostly a linker problem and i had to add the opengl and the glut libarys to the linker options and also had to open the imageloader.cpp in the project *goes off to hopefully learn opengl*

---

