---
title: "assaultcube 1.0 and libopenal.so.1"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by animalprimate on 2008-11-23
when i try to run the new assault cube I keep getting this message,

```

.//bin_unix/linux_client: error while loading shared libraries:
libopenal.so.1: cannot open shared object file: No such file or directory

```

ive been trying new sensible packages but I still get that message whenever i run

```

./assaultcube.sh

```

i hope that you can help me get it running that would make me so happy.

heres a small guide with the installation steps below:

[href]http://assault.cubers.net/docs/v1.0/getstarted.html[/href] from this link
**Linux**
You'll need to make sure the appropriate OpenGL drivers are installed, plus these libraries:
* *libSDL 1.2*
* *libSDL_image*
* *OpenAL*
(Note: To use the client provided with the Linux package, you will need OpenAL-Soft instead of OpenAL, otherwise you will need to compile your own client if you would rather use normal OpenAL)... im really baffled.

---

### Post by Bill Cosby on 2008-11-25
After you install the openal package you need to do this:

```

$ cd /usr/lib
$ sudo ln -s libopenal.so.0 libopenal.so.1

```

---

### Post by go_beep_yourself on 2008-11-25
Has anybody been able to compile the latest AssaultCube? I keep getting an error about Sound.cpp when running make. Sauerbraten compiled flawlessly though.

---

### Post by djbushido on 2008-11-25
this may not be the best reply, but if you can run assault cube, i would recommend looking at urban terror as an alternative. You can install from repo's (universe i believe), and is quake 3 based so it runs fairly fast on older comp's. While this doesn't solve the problem, i do highly recommend this game.

---

### Post by carlinuxlearner on 2008-11-28
> **go_beep_yourself said:**
> Has anybody been able to compile the latest AssaultCube? I keep getting an error about Sound.cpp when running make. Sauerbraten compiled flawlessly though.

Yep, just did it yesterday, I'm running 8.04 64bit.

I was having the same error message as "animalprimate", so after fighting with it for quite some time (I even tried installing the package from getdeb thinking it would resolve the dependencies, but it didn't cause it's .93 or whatever and what I want to run is 1.0) I finally just gave up and just fallowed the instructions from here [http://gwos.org/doku.php/guides:64bit:assultcube]("http://gwos.org/doku.php/guides:64bit:assultcube")

C@RL

---

### Post by go_beep_yourself on 2008-12-01
> **carlinuxlearner said:**
> Yep, just did it yesterday, I'm running 8.04 64bit.

I was having the same error message as "animalprimate", so after fighting with it for quite some time (I even tried installing the package from getdeb thinking it would resolve the dependencies, but it didn't cause it's .93 or whatever and what I want to run is 1.0) I finally just gave up and just fallowed the instructions from here [http://gwos.org/doku.php/guides:64bit:assultcube]("http://gwos.org/doku.php/guides:64bit:assultcube")

C@RL

oh, I see. I'm supposed to type make install and not make. For sauerbraten, I typed make and then make install. I'll give it a try now. Thanks.

---

### Post by go_beep_yourself on 2008-12-01
Nope, :( Same errors as before, and I already had all those dependency packages for compiling from when I compiled sauerbraten.

[PHP]
...
make[2]: Leaving directory `/home/chris/Downloads/AssaultCube_v1.0/source/enet'
make[1]: Leaving directory `/home/chris/Downloads/AssaultCube_v1.0/source/enet'
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o client.o client.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o clientgame.o clientgame.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o clients2c.o clients2c.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o command.o command.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o console.o console.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o docs.o docs.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o editing.o editing.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o entities.o entities.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o log.o log.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o main.o main.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o menus.o menus.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o physics.o physics.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o protocol.o protocol.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendercubes.o rendercubes.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendergl.o rendergl.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o renderhud.o renderhud.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendermodel.o rendermodel.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o renderparticles.o renderparticles.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rendertext.o rendertext.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o rndmap.o rndmap.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o scoreboard.o scoreboard.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o server.o server.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o serverbrowser.o serverbrowser.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o serverms.o serverms.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o shadow.o shadow.cpp
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include -I../src `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -rdynamic   -c -o sound.o sound.cpp
sound.cpp:11:20: error: AL/al.h: No such file or directory
sound.cpp:12:21: error: AL/alc.h: No such file or directory
sound.cpp:26: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
sound.cpp:27: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
sound.cpp: In function &#8216;void alclearerr()&#8217;:
sound.cpp:33: error: &#8216;alGetError&#8217; was not declared in this scope
sound.cpp: In function &#8216;bool alerr(bool, int)&#8217;:
sound.cpp:38: error: &#8216;ALenum&#8217; was not declared in this scope
sound.cpp:38: error: expected `;' before &#8216;er&#8217;
sound.cpp:39: error: &#8216;er&#8217; was not declared in this scope
sound.cpp:44: error: &#8216;AL_INVALID_NAME&#8217; was not declared in this scope
sound.cpp:45: error: &#8216;AL_INVALID_ENUM&#8217; was not declared in this scope
sound.cpp:46: error: &#8216;AL_INVALID_VALUE&#8217; was not declared in this scope
sound.cpp:47: error: &#8216;AL_INVALID_OPERATION&#8217; was not declared in this scope
sound.cpp:48: error: &#8216;AL_OUT_OF_MEMORY&#8217; was not declared in this scope
sound.cpp:53: error: &#8216;er&#8217; was not declared in this scope
sound.cpp: At global scope:
sound.cpp:71: error: &#8216;ALuint&#8217; does not name a type
sound.cpp:156: error: &#8216;ALuint&#8217; has not been declared
sound.cpp:174: error: &#8216;ALsizei&#8217; has not been declared
sound.cpp:174: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
sound.cpp:174: error: ISO C++ forbids declaration of &#8216;ALuint&#8217; with no type
sound.cpp: In constructor &#8216;source::source()&#8217;:
sound.cpp:77: error: class &#8216;source&#8217; does not have any field named &#8216;id&#8217;
sound.cpp:80: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:80: error: &#8216;alIsSource&#8217; was not declared in this scope
sound.cpp: In member function &#8216;void source::reset()&#8217;:
sound.cpp:100: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:100: error: &#8216;alIsSource&#8217; was not declared in this scope
sound.cpp:119: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:119: error: &#8216;AL_REFERENCE_DISTANCE&#8217; was not declared in this scope
sound.cpp:119: error: &#8216;alSourcef&#8217; was not declared in this scope
sound.cpp:120: error: &#8216;AL_ROLLOFF_FACTOR&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::generate()&#8217;:
sound.cpp:144: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:144: error: &#8216;alGenSources&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::delete_()&#8217;:
sound.cpp:152: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:152: error: &#8216;alDeleteSources&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::buffer(int)&#8217;:
sound.cpp:162: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:162: error: &#8216;AL_BUFFER&#8217; was not declared in this scope
sound.cpp:162: error: &#8216;alSourcei&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::looping(bool)&#8217;:
sound.cpp:170: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:170: error: &#8216;AL_LOOPING&#8217; was not declared in this scope
sound.cpp:170: error: &#8216;alSourcei&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::queuebuffers(int, int)&#8217;:
sound.cpp:177: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:177: error: &#8216;buffer_ids&#8217; was not declared in this scope
sound.cpp:177: error: &#8216;alSourceQueueBuffers&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::unqueueallbuffers()&#8217;:
sound.cpp:184: error: &#8216;ALint&#8217; was not declared in this scope
sound.cpp:184: error: expected `;' before &#8216;queued&#8217;
sound.cpp:185: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:185: error: &#8216;AL_BUFFERS_QUEUED&#8217; was not declared in this scope
sound.cpp:185: error: &#8216;queued&#8217; was not declared in this scope
sound.cpp:185: error: &#8216;alGetSourcei&#8217; was not declared in this scope
sound.cpp:189: error: &#8216;ALuint&#8217; was not declared in this scope
sound.cpp:189: error: expected `;' before &#8216;buffer&#8217;
sound.cpp:190: error: ISO C++ forbids taking the address of an unqualified or parenthesized non-static member function to form a pointer to member function.  Say &#8216;&source::buffer&#8217;
sound.cpp:190: error: &#8216;alSourceUnqueueBuffers&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::gain(float)&#8217;:
sound.cpp:198: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:198: error: &#8216;AL_GAIN&#8217; was not declared in this scope
sound.cpp:198: error: &#8216;alSourcef&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::pitch(float)&#8217;:
sound.cpp:205: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:205: error: &#8216;AL_PITCH&#8217; was not declared in this scope
sound.cpp:205: error: &#8216;alSourcef&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::position(const vec&)&#8217;:
sound.cpp:212: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:212: error: &#8216;AL_POSITION&#8217; was not declared in this scope
sound.cpp:212: error: &#8216;ALfloat&#8217; was not declared in this scope
sound.cpp:212: error: expected primary-expression before &#8216;)&#8217; token
sound.cpp:212: error: &#8216;alSourcefv&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::position(float, float, float)&#8217;:
sound.cpp:219: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:219: error: &#8216;AL_POSITION&#8217; was not declared in this scope
sound.cpp:219: error: &#8216;alSource3f&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::velocity(float, float, float)&#8217;:
sound.cpp:226: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:226: error: &#8216;AL_VELOCITY&#8217; was not declared in this scope
sound.cpp:226: error: &#8216;alSource3f&#8217; was not declared in this scope
sound.cpp: In member function &#8216;vec source::position()&#8217;:
sound.cpp:234: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:234: error: &#8216;AL_POSITION&#8217; was not declared in this scope
sound.cpp:234: error: &#8216;ALfloat&#8217; was not declared in this scope
sound.cpp:234: error: expected primary-expression before &#8216;)&#8217; token
sound.cpp:234: error: &#8216;alGetSourcefv&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::sourcerelative(bool)&#8217;:
sound.cpp:242: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:242: error: &#8216;AL_SOURCE_RELATIVE&#8217; was not declared in this scope
sound.cpp:242: error: &#8216;AL_TRUE&#8217; was not declared in this scope
sound.cpp:242: error: &#8216;AL_FALSE&#8217; was not declared in this scope
sound.cpp:242: error: &#8216;alSourcei&#8217; was not declared in this scope
sound.cpp: In member function &#8216;int source::state()&#8217;:
sound.cpp:248: error: &#8216;ALint&#8217; was not declared in this scope
sound.cpp:248: error: expected `;' before &#8216;s&#8217;
sound.cpp:249: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:249: error: &#8216;AL_SOURCE_STATE&#8217; was not declared in this scope
sound.cpp:249: error: &#8216;s&#8217; was not declared in this scope
sound.cpp:249: error: &#8216;alGetSourcei&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::secoffset(float)&#8217;:
sound.cpp:256: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:256: error: &#8216;AL_SEC_OFFSET&#8217; was not declared in this scope
sound.cpp:256: error: &#8216;alSourcef&#8217; was not declared in this scope
sound.cpp: In member function &#8216;float source::secoffset()&#8217;:
sound.cpp:265: error: &#8216;ALfloat&#8217; was not declared in this scope
sound.cpp:265: error: expected `;' before &#8216;s&#8217;
sound.cpp:266: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:266: error: &#8216;AL_SEC_OFFSET&#8217; was not declared in this scope
sound.cpp:266: error: &#8216;s&#8217; was not declared in this scope
sound.cpp:266: error: &#8216;alGetSourcef&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::playing()&#8217;:
sound.cpp:275: error: &#8216;AL_PLAYING&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::play()&#8217;:
sound.cpp:281: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:281: error: &#8216;alSourcePlay&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::stop()&#8217;:
sound.cpp:288: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:288: error: &#8216;alSourceStop&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool source::rewind()&#8217;:
sound.cpp:295: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:295: error: &#8216;alSourceRewind&#8217; was not declared in this scope
sound.cpp: In member function &#8216;void source::printposition()&#8217;:
sound.cpp:303: error: &#8216;ALint&#8217; was not declared in this scope
sound.cpp:303: error: expected `;' before &#8216;s&#8217;
sound.cpp:304: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:304: error: &#8216;AL_SOURCE_TYPE&#8217; was not declared in this scope
sound.cpp:304: error: &#8216;s&#8217; was not declared in this scope
sound.cpp:304: error: &#8216;alGetSourcei&#8217; was not declared in this scope
sound.cpp: At global scope:
sound.cpp:576: error: &#8216;ALuint&#8217; does not name a type
sound.cpp:578: error: &#8216;ALenum&#8217; does not name a type
sound.cpp:696: error: &#8216;ALuint&#8217; has not been declared
sound.cpp: In constructor &#8216;oggstream::oggstream()&#8217;:
sound.cpp:608: error: &#8216;bufferids&#8217; was not declared in this scope
sound.cpp:608: error: &#8216;alGenBuffers&#8217; was not declared in this scope
sound.cpp: In destructor &#8216;virtual oggstream::~oggstream()&#8217;:
sound.cpp:618: error: &#8216;bufferids&#8217; was not declared in this scope
sound.cpp:618: error: &#8216;alIsBuffer&#8217; was not declared in this scope
sound.cpp:621: error: &#8216;alDeleteBuffers&#8217; was not declared in this scope
sound.cpp: In member function &#8216;void oggstream::reset()&#8217;:
sound.cpp:637: error: &#8216;format&#8217; was not declared in this scope
sound.cpp:637: error: &#8216;AL_NONE&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool oggstream::open(const char*)&#8217;:
sound.cpp:676: error: &#8216;format&#8217; was not declared in this scope
sound.cpp:676: error: &#8216;AL_FORMAT_STEREO16&#8217; was not declared in this scope
sound.cpp:676: error: &#8216;AL_FORMAT_MONO16&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool oggstream::stream(int)&#8217;:
sound.cpp:703: error: &#8216;ALsizei&#8217; was not declared in this scope
sound.cpp:703: error: expected `;' before &#8216;size&#8217;
sound.cpp:705: error: &#8216;size&#8217; was not declared in this scope
sound.cpp:713: error: &#8216;size&#8217; was not declared in this scope
sound.cpp:720: error: &#8216;format&#8217; was not declared in this scope
sound.cpp:720: error: &#8216;size&#8217; was not declared in this scope
sound.cpp:720: error: &#8216;alBufferData&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool oggstream::update()&#8217;:
sound.cpp:733: error: &#8216;ALint&#8217; was not declared in this scope
sound.cpp:733: error: expected `;' before &#8216;processed&#8217;
sound.cpp:735: error: &#8216;struct source&#8217; has no member named &#8216;id&#8217;
sound.cpp:735: error: &#8216;AL_BUFFERS_PROCESSED&#8217; was not declared in this scope
sound.cpp:735: error: &#8216;processed&#8217; was not declared in this scope
sound.cpp:735: error: &#8216;alGetSourcei&#8217; was not declared in this scope
sound.cpp:738: error: &#8216;ALuint&#8217; was not declared in this scope
sound.cpp:738: error: expected `;' before &#8216;buffer&#8217;
sound.cpp:739: error: &#8216;struct source&#8217; has no member named &#8216;id&#8217;
sound.cpp:739: error: &#8216;buffer&#8217; was not declared in this scope
sound.cpp:739: error: &#8216;alSourceUnqueueBuffers&#8217; was not declared in this scope
sound.cpp:741: error: &#8216;struct source&#8217; has no member named &#8216;id&#8217;
sound.cpp:741: error: &#8216;alSourceQueueBuffers&#8217; was not declared in this scope
sound.cpp: In member function &#8216;bool oggstream::playback(bool)&#8217;:
sound.cpp:826: error: &#8216;bufferids&#8217; was not declared in this scope
sound.cpp:830: error: &#8216;bufferids&#8217; was not declared in this scope
sound.cpp: At global scope:
sound.cpp:846: error: &#8216;ALuint&#8217; does not name a type
sound.cpp: In constructor &#8216;sbuffer::sbuffer()&#8217;:
sound.cpp:849: error: class &#8216;sbuffer&#8217; does not have any field named &#8216;id&#8217;
sound.cpp: In member function &#8216;bool sbuffer::load()&#8217;:
sound.cpp:861: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:863: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:863: error: &#8216;alGenBuffers&#8217; was not declared in this scope
sound.cpp:896: error: &#8216;AL_FORMAT_STEREO16&#8217; was not declared in this scope
sound.cpp:896: error: &#8216;AL_FORMAT_MONO16&#8217; was not declared in this scope
sound.cpp:896: error: &#8216;alBufferData&#8217; was not declared in this scope
sound.cpp:917: error: &#8216;ALenum&#8217; was not declared in this scope
sound.cpp:917: error: expected `;' before &#8216;format&#8217;
sound.cpp:922: error: &#8216;format&#8217; was not declared in this scope
sound.cpp:922: error: &#8216;AL_FORMAT_STEREO8&#8217; was not declared in this scope
sound.cpp:922: error: &#8216;AL_FORMAT_MONO8&#8217; was not declared in this scope
sound.cpp:926: error: &#8216;AL_FORMAT_STEREO16&#8217; was not declared in this scope
sound.cpp:926: error: &#8216;AL_FORMAT_MONO16&#8217; was not declared in this scope
sound.cpp:934: error: &#8216;format&#8217; was not declared in this scope
sound.cpp:934: error: &#8216;alBufferData&#8217; was not declared in this scope
sound.cpp: In member function &#8216;void sbuffer::unload()&#8217;:
sound.cpp:949: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:951: error: &#8216;id&#8217; was not declared in this scope
sound.cpp:951: error: &#8216;alIsBuffer&#8217; was not declared in this scope
sound.cpp:951: error: &#8216;alDeleteBuffers&#8217; was not declared in this scope
sound.cpp:952: error: &#8216;id&#8217; was not declared in this scope
sound.cpp: In constructor &#8216;location::location(int, const worldobjreference&, int)&#8217;:
sound.cpp:1015: error: &#8216;struct sbuffer&#8217; has no member named &#8216;id&#8217;
sound.cpp:1024: error: &#8216;struct sbuffer&#8217; has no member named &#8216;id&#8217;
sound.cpp: In member function &#8216;void location::update()&#8217;:
sound.cpp:1137: error: &#8216;AL_PLAYING&#8217; was not declared in this scope
sound.cpp:1140: error: &#8216;AL_STOPPED&#8217; was not declared in this scope
sound.cpp:1141: error: &#8216;AL_PAUSED&#8217; was not declared in this scope
sound.cpp:1142: error: &#8216;AL_INITIAL&#8217; was not declared in this scope
sound.cpp: In function &#8216;void var_soundvol()&#8217;:
sound.cpp:1295: error: &#8216;AL_GAIN&#8217; was not declared in this scope
sound.cpp:1295: error: &#8216;alListenerf&#8217; was not declared in this scope
sound.cpp: In function &#8216;void initsound()&#8217;:
sound.cpp:1325: error: &#8216;device&#8217; was not declared in this scope
sound.cpp:1326: error: &#8216;context&#8217; was not declared in this scope
sound.cpp:1329: error: &#8216;alcIsExtensionPresent&#8217; was not declared in this scope
sound.cpp:1331: error: expected initializer before &#8216;*&#8217; token
sound.cpp:1332: error: &#8216;devices&#8217; was not declared in this scope
sound.cpp:1338: error: expected initializer before &#8216;*&#8217; token
sound.cpp:1338: error: &#8216;c&#8217; was not declared in this scope
sound.cpp:1349: error: &#8216;alcOpenDevice&#8217; was not declared in this scope
sound.cpp:1353: error: &#8216;alcCreateContext&#8217; was not declared in this scope
sound.cpp:1356: error: &#8216;alcMakeContextCurrent&#8217; was not declared in this scope
sound.cpp:1358: error: &#8216;AL_INVERSE_DISTANCE_CLAMPED&#8217; was not declared in this scope
sound.cpp:1358: error: &#8216;alDistanceModel&#8217; was not declared in this scope
sound.cpp:1361: error: &#8216;ALC_DEVICE_SPECIFIER&#8217; was not declared in this scope
sound.cpp:1361: error: &#8216;alcGetString&#8217; was not declared in this scope
sound.cpp:1361: error: &#8216;AL_RENDERER&#8217; was not declared in this scope
sound.cpp:1361: error: &#8216;alGetString&#8217; was not declared in this scope
sound.cpp:1361: error: &#8216;AL_VENDOR&#8217; was not declared in this scope
sound.cpp:1362: error: &#8216;AL_VERSION&#8217; was not declared in this scope
sound.cpp:1379: error: &#8216;alcDestroyContext&#8217; was not declared in this scope
sound.cpp:1380: error: &#8216;alcCloseDevice&#8217; was not declared in this scope
sound.cpp: In function &#8216;void soundcleanup()&#8217;:
sound.cpp:1533: error: &#8216;alcMakeContextCurrent&#8217; was not declared in this scope
sound.cpp:1534: error: &#8216;context&#8217; was not declared in this scope
sound.cpp:1534: error: &#8216;alcDestroyContext&#8217; was not declared in this scope
sound.cpp:1535: error: &#8216;device&#8217; was not declared in this scope
sound.cpp:1535: error: &#8216;alcCloseDevice&#8217; was not declared in this scope
sound.cpp: In function &#8216;void updateaudio()&#8217;:
sound.cpp:1639: error: &#8216;context&#8217; was not declared in this scope
sound.cpp:1639: error: &#8216;alcSuspendContext&#8217; was not declared in this scope
sound.cpp:1731: error: &#8216;AL_ORIENTATION&#8217; was not declared in this scope
sound.cpp:1731: error: &#8216;ALfloat&#8217; was not declared in this scope
sound.cpp:1731: error: expected primary-expression before &#8216;)&#8217; token
sound.cpp:1731: error: &#8216;alListenerfv&#8217; was not declared in this scope
sound.cpp:1732: error: &#8216;AL_POSITION&#8217; was not declared in this scope
sound.cpp:1732: error: expected primary-expression before &#8216;)&#8217; token
sound.cpp:1734: error: &#8216;alcProcessContext&#8217; was not declared in this scope
sound.cpp: At global scope:
sound.cpp:1453: warning: &#8216;__dummy_registermusic&#8217; defined but not used
sound.cpp:1454: warning: &#8216;__dummy_music&#8217; defined but not used
sound.cpp:1484: warning: &#8216;__dummy_registersound&#8217; defined but not used
sound.cpp:1487: warning: &#8216;__dummy_mapsound&#8217; defined but not used
sound.cpp:1514: warning: &#8216;__dummy_applymapsoundchanges&#8217; defined but not used
sound.cpp:1552: warning: &#8216;__dummy_mapsoundreset&#8217; defined but not used
sound.cpp:1759: warning: &#8216;__dummy_unmuteallsounds&#8217; defined but not used
sound.cpp:1760: warning: &#8216;__dummy_mutesound&#8217; defined but not used
sound.cpp:1761: warning: &#8216;__dummy_soundmuted&#8217; defined but not used
sound.cpp:1818: warning: &#8216;__dummy_sound&#8217; defined but not used
sound.cpp:1855: warning: &#8216;__dummy_voicecom&#8217; defined but not used
sound.cpp:1869: warning: &#8216;__dummy_soundtest&#8217; defined but not used
make: *** [sound.o] Error 1
chris@ubuntu:~/Downloads/AssaultCube_v1.0/source/src$ [/PHP]

---

### Post by go_beep_yourself on 2008-12-01
Installing libopenal-dev solved the problem. Whoever wrote that guide needs to fix it.

---

### Post by ibuclaw on 2008-12-01
If you want software compiled, you require the -dev packages, as they contain the headers required by the source code.

This is an elementary mistake if you've never tried compiling before. But just make sure that you keep that in mind in the future.


Also, just so you know, I've never got any good gameplay out of assaultcube before...
I can join multiplayer games, but I never seem to be "in the game".
Either on a completely different map or some 6 foot below the map the other players are playing...

But I'll check out this new version, to see if it's any different though (I think it was 0.93 I last tried it).

Regards
Iain

---

### Post by go_beep_yourself on 2008-12-01
> **tinivole said:**
> If you want software compiled, you require the -dev packages, as they contain the headers required by the source code.

Yeah, I know that. I've done plenty of compiling before both in Linux and my computer science courses. I had all the *-dev packages, but that one. Sauerbraten didn't need it. I thought I'd give it a try, and it worked, so now I've got the game in 64-bit and most others, something you can't do in Winblows.

---

### Post by ibuclaw on 2008-12-01
Cools, as soon as compiledkernel comes back online, I'll notify him of the page that needs updating, as he controls the gwos.org servers ... along with some other nasty stuff ;)

I expect him to appear sometime in the next couple of hours...

Regards
Iain

---

### Post by MRGt on 2008-12-29
Thanks for this thread 

I download a .tar file expand it, down the libraries and get the openal.so.1 error, then i did what Bill Cosby Say in Reply #2 and voila!! 

Im playing all the sunday. Now i thank to all of you for this Tread

---

### Post by justplayin on 2008-12-30
I downloaded the filesAssaultCube_v1.0.tar.bz2 and AssaultCube_v1.0.1-Update.tar.bz2 for Version 1.0 and 1.0.1, copied the files from AssaultCube_v1.0.1-Update.tar.bz2 to the root directory AssaultCube_v1.0 and replaced the old folders with the new ones provided in AssaultCube_v1.0.1-Update.tar.bz2. But the game didn't run, it always gave me the error:

```
juz@juz:~/Downloads/Spiele/assaultcube/AssaultCube_v1.0$ sh assaultcube.sh
.//bin_unix/linux_client: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory

```

I had libsdl1.2debian libsdl-image1.2 libsdl-mixer1.2 installed.

The trick with creating a symlink 

```
sudo ln -s /usr/lib/libopenal.so.0 /usr/lib/libopenal.so.1

```

didn't work, when starting assaultcube I got the error:

```
juz@juz:~/Downloads/Spiele/assaultcube/AssaultCube_v1.0$ ./assaultcube.sh
.//bin_unix/linux_client: error while loading shared libraries: libopenal.so.1: cannot open shared object file: Error 40

```

I didn't try installing libopenal-dev, maybe I should have done that.
But what worked for me was to follow the instructions under 
[http://assault.cubers.net/wiki/Ubuntu_Support#Compiling_OpenAL_1.0]("http://assault.cubers.net/wiki/Ubuntu_Support#Compiling_OpenAL_1.0")

---

### Post by animalprimate on 2009-03-03
youre welcome! geez, not sure anyones ever thanked me here, i played this game hard for some time, but im over it now, good fun. i allways mod the players colors to be completely red vs completely blue, and change the grenades colors too see them fly through air easily.  plus changing scope view to include all of screen.  one more thing i found usefull was making a little dot right at the center of my screen when zoomed in with sniper cause that way its easier to get no scopes! tremendous! thanks for all your advice to other posters that joined this happening thread, gratitude.

---

