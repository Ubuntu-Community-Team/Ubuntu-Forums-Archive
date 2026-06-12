---
title: "Simple PulseAudio Client"
date: 2010-09-29
forum: Programming Talk
---

### Post by travisl_10 on 2010-09-29
Hello, I'm learning how to develop a client for PulseAudio.

Right now I'm trying to compile a simple PulseAudio program:
```
#include <pulse/simple.h>

int main(int argc, char *argv[])
{
    pa_simple *s;
    pa_sample_spec ss;
    
    ss.format = PA_SAMPLE_S16NE;
    ss.channels = 2;
    ss.rate = 44100;
    
    s = pa_simple_new(
        NULL,               // Use the default server.
        "Fooapp",           // Our application's name.
        PA_STREAM_PLAYBACK, 
        NULL,               // Use the default device.
        "Music",            // Description of our stream.
        &ss,                // Our sample format.
        NULL,               // Use default channel map
        NULL,               // Use default buffering attributes.
        NULL                // Ignore error code.
    );
    
    pa_simple_free(s);
    
    return 0;
} 
```

I have downloaded the development headers, and I use this gcc command:
gcc -o test5 test5.c -lpulse (test5.c is the filename)
... but I'm getting this error:
/tmp/cctdZCVI.o: In function `main':
test5.c:(.text+0x66): undefined reference to `pa_simple_new'
test5.c:(.text+0x76): undefined reference to `pa_simple_free'
collect2: ld returned 1 exit status

Does anybody know what I am doing wrong? Any help would be greatly appreciated :)

---

### Post by Zugzwang on 2010-09-30
It appears as if you also need to link against another library, namely "libpulse-simple". So add "-lpulse-simple" to your compiling & linking command. You might need to put that *before* -"lpulse".

---

### Post by qwerty12 on 2010-09-30
Hi,

> **travisl_10 said:**
> 
I have downloaded the development headers, and I use this gcc command:
gcc -o test5 test5.c -lpulse (test5.c is the filename)
... but I'm getting this error:
/tmp/cctdZCVI.o: In function `main':
test5.c:(.text+0x66): undefined reference to `pa_simple_new'
test5.c:(.text+0x76): undefined reference to `pa_simple_free'
collect2: ld returned 1 exit status

Does anybody know what I am doing wrong? Any help would be greatly appreciated :)

Use pkg-config: gcc -o test5 test5.c $(pkg-config --cflags --libs pulse-simple)

---

### Post by travisl_10 on 2010-09-30
It worked, thanks everyone!

For future reference, where are you two getting this information from? I was looking at the documentation on the PulseAudio site but couldn't find it there...

---

### Post by Zugzwang on 2010-10-01
> **travisl_10 said:**
> It worked, thanks everyone!

For future reference, where are you two getting this information from? I was looking at the documentation on the PulseAudio site but couldn't find it there...

First of all, from your error message: "undefined reference to" is a linker error that states that some functions are missing in the linking process. Thus, the header file has been found (as compiling worked). An "undefined reference to ..." error can have two possible meanings:
[LIST]
[*]You forgot to define one of *your* functions
[*]You forgot to link against a needed library, or the libraries given to the linker are written in the incorrect order
[/LIST]
Due to the simplicity of your program, case number one cound be ruled out. It remained case two. Then, I realised that you actually linked against "libpulse". So probably you had to link against something else as well. The logical next step is to look at the Ubuntu pulseaudio development package (libpulse-dev). Having a look at its [file list]("http://packages.ubuntu.com/lucid/i386/libpulse-dev/filelist"), you can see that there are a couple of library files (ending with .so) included. One of them has the name "libpulse-simple". It appeared logical that this file contains the definitions for the functions that you were missing in the build process. Note that there are also ".pc" files in the package. These are for usage with "pkgconfig", which is a program that helps you feeding the correct parameters to the compiler and the linker automatically.

The facts that pkgconfig is good for this, what an "undefined reference to ..." error means, that ".so" is the library part to link against and ".pc" files are pkgconfig files is probably known to people who did a lot of C or C++ Linux programming. But I don't know any reference for this. Also, I've never use pulseaudio from the programming side, but just followed the steps above.

---

### Post by sruthihsr on 2011-08-04
I am using the following program on Qt to create a simple playback. It is  similar to the example given in pulseaudio website. I am getting a blank noiseinstead of playing the file. I have tried with mp3 and ogg formats.. On debugging I dont see anything written from buffer to server.Please help.

#include <QtGui/QApplication>
#include "qmlapplicationviewer.h"
#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <stdio.h>
#include <unistd.h>
#include <string.h>
#include <errno.h>
#include <fcntl.h>

#include <pulse/simple.h>
#include <pulse/error.h>
#include <pulse/gccmacro.h>
#include <pulse/pulseaudio.h>
#include <pulse/sample.h>
#include <fstream>
using namespace std;


#define BUFSIZE 1024


int main(int argc, char *argv[])
{

    QApplication app(argc, argv);

    QmlApplicationViewer viewer;
    viewer.setOrientation(QmlApplicationViewer::ScreenOrientationAuto);
    viewer.setMainQmlFile(QLatin1String("qml/paudio/main.qml"));
    viewer.showExpanded();
    //ofstream myfile;
     // myfile.open ("abc.mp3");


    /* The Sample format to use */
       /*static const pa_sample_spec ss = {
           .format = PA_SAMPLE_S16LE,
           .rate = 44100,
           .channels = 2
       };*/
    static  pa_sample_spec ss;//= {


        ss.format = PA_SAMPLE_S16LE;
       ss.rate = 24000;
        ss.channels = 1;// ss;





       pa_simple *sa = NULL;

       int ret = 1;
       int error;

       /* replace STDIN with the specified file if needed */
       if (argc >= 1) {
           int fd;
           argv[1]="abc.ogg";

           if ((fd = open(argv[1], O_RDONLY)) < 0) {
               fprintf(stderr, __FILE__": open() failed: %s\n", strerror(errno));
               goto finish;
           }

           if (dup2(fd, STDIN_FILENO) < 0) {
               fprintf(stderr, __FILE__": dup2() failed: %s\n", strerror(errno));
               goto finish;
           }

     close(fd);
       }

       /* Create a new playback stream */
       if (!(sa = pa_simple_new(NULL, argv[0], PA_STREAM_PLAYBACK, NULL, "123abc", &ss, NULL, NULL, &error))) {
           fprintf(stderr, __FILE__": pa_simple_new() failed: %s\n", pa_strerror(error));

           goto finish;
       }

       for (; ; ;){
           uint8_t buf[BUFSIZE];

           ssize_t r;

   #if 0
           pa_usec_t latency;

           if ((latency = pa_simple_get_latency(s, &error)) == (pa_usec_t) -1) {
               fprintf(stderr, __FILE__": pa_simple_get_latency() failed: %s\n", pa_strerror(error));
               goto finish;
           }

           fprintf(stderr, "%0.0f usec    \r", (float)latency);
   #endif

           /* Read some data ... */
           if ((r = read(STDIN_FILENO, buf, sizeof(buf))) <= 0) {
               if (r == 0) /* EOF */
                   break;

               fprintf(stderr, __FILE__": read() failed: %s\n", strerror(errno));
               goto finish;
           }

           /* ... and play it */

           if (pa_simple_write(sa, buf, (size_t) r, &error) < 0) {
               fprintf(stderr, __FILE__": pa_simple_write() failed: %s\n", pa_strerror(error));
               goto finish;
           }
           //s1=(uint8_t)*s;
       }

       /* Make sure that every single sample was played */
       if (pa_simple_drain(sa, &error) < 0) {
           fprintf(stderr, __FILE__": pa_simple_drain() failed: %s\n", pa_strerror(error));
           goto finish;
       }

       ret = 0;

   finish:

       if (sa)
           pa_simple_free(sa);

       //return ret;


   return app.exec();
}

---

### Post by Zugzwang on 2011-08-04
@sruthihsr: Your question wasn't actually related to the one of the OP, so it would have been nice if you started a new thread.

As an answer to your question: I don't see in your code where you actually decode the .ogg or .mp3 file - they use some kind of compression algorithm which you must (in some sense) inverse before playing the sound. Search for suitable tutorials on the web for this.

---

