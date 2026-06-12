---
title: "Trying to play a sound file using c++"
date: 2006-11-10
forum: Programming Talk
---

### Post by BatteryCell on 2006-11-10
Hello, I cant seem to get qsound  to work.  For instance:
```

#include"qsound.h"
#include <iostream>
QSound mysound("1.wav");
int main()
{
  if(mysound.isAvailable())
  {
  std::cout<<"Should Work";
  }
mysound.play();
return 1;
}

```

Should play 1.wav and print "Should Work" to the screen, but it does neither.  How do I make it so that qsound sees my "sound facilities" as trolltech calls them?

---

### Post by llonesmiz on 2006-11-11
From the docs:

>  On Microsoft Windows the underlying multimedia system is used; only WAVE format sound files are supported. 
** On X11 the [Network Audio     System]("ftp://ftp.x.org/contrib/audio/nas/") is used if available, otherwise all operations work silently. NAS supports WAVE and AU files.** 
 On Macintosh, ironically, we use QT ([QuickTime]("http://quicktime.apple.com/")) for sound, this means all QuickTime formats are supported by Qt/Mac. 
 On Qt/Embedded, a built-in mixing sound server is used, which accesses /dev/dsp directly. Only the WAVE format is supported. 
The Network Audio System is not installed by default in Ubuntu (I don't know about Kubuntu) maybe you should install it (I don't really know if there is some configuration required). The needed package seems to be "nas". You should look it up in synaptic and read the description.

You can also use other alternatives like sdl_sound or sdl_mixer, gstreamer and openal.
An example using alut (an utility library for openal):

```
#include <stdlib.h>
#include <AL/alut.h>

int
main (int argc, char **argv)
{
  ALuint helloBuffer, helloSource;
  alutInit (&argc, argv);
  helloBuffer = alutCreateBufferFromFile ("1.wav");
  alGenSources (1, &helloSource);
  alSourcei (helloSource, AL_BUFFER, helloBuffer);
  alSourcePlay (helloSource);
  alutSleep (1); //you need to put here the length in seconds of the file
  alutExit ();
  return EXIT_SUCCESS;
}
```it's C but you can use it in a C++ program. To use this you need to install libalut-dev and libopenal-dev.

sudo apt-get install libalut-dev libopenal-dev.

in order to compile it you need to use:

g++ -o program_name source_name.cc  `pkg-config --cflags --libs freealut`

---

