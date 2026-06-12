---
title: "Problem using SDL with native android"
date: 2010-10-30
forum: Programming Talk
---

### Post by sarabisan on 2010-10-30
I've been developing with android for sometime, and I think that it's a great platform. Recently, I also started using a library called allegro. I was looking for a port of allegro to android, but no one made something like that, at least not yet. However, there have been a couple of unofficial ports of SDL to android. So, I looked up a guide to using SDL for android, and I found one: [http://jiggawatt.org/badc0de/android/index.html#gifflen](http://jiggawatt.org/badc0de/android/index.html#gifflen).

I got the ARM tool chain from that site, and also recompiled SDL with the modifications. Before I started using SDL, I just wanted to check if it worked. I tried to do the part about "Hello, World". So I made a file called hello.c, with the following content:


#include 

int main(int argc, char **argv)
{
	printf("Hello, world!\n");
	return 0;
}


I compiled it with:


arm-none-linux-gnueabi-gcc -static -o hello hello.c


Then, I tried to use adb to send the file an emulator's file system:


adb push hello /data/misc/hello


Then, so that I could execute it:


adb shell chmod 777 /data/misc/hello


And then I tried to run it with:


adb shell /data/misc/hello


It gives me:


[1]   Segmentation fault      /data/misc/hello


What did I do wrong?

I'm using Ubuntu 10.04.

---

### Post by slouken on 2011-01-14
You might be happy to know that SDL 1.3 officially supports Android, and I put together a pre-release demo:
[http://www.libsdl.org/tmp/android-project.zip](http://www.libsdl.org/tmp/android-project.zip)

From the README:
This is a test of the SDL libraries on the Android platform.

It currently has working versions of the SDL, SDL_image, SDL_mixer, and SDL_ttf libraries.

Your sources go into jni/src, and you should edit jni/src/Android.mk to include them.

It is currently set up to build the aliens demo, and you should run data.sh to push the data to the device, before you run it.

You build with ndk-build, and install to the device with: ant install

For a full README, see README.android in the SDL source archive.

Enjoy!
-- 
    -Sam Lantinga, Founder and President, Galaxy Gameworks LLC

---

### Post by grenoml on 2011-05-07
Hi Sam,
  I was able to get the game running on the emulator but then it hangs when I try to use the Back key and eventually I get the ANR message.  How can I fix this so that the Back key will go back to the previous activity?

Update:
I'm seeing this in the log many lines:
W/AudioTrack(  535): obtainBuffer timed out (is the CPU pegged?) 0x2a6c50 user=00000200, server=00000000
...

looks like it is hung.

Here is /data/anr/traces.txt:
DALVIK THREADS:
(mutexes: tll=0 tsl=0 tscl=0 ghl=0 hwl=0 hwll=0)
"main" prio=5 tid=1 WAIT
  | group="main" sCount=1 dsCount=0 obj=0x4001f1a8 self=0xce48
  | sysTid=562 nice=0 sched=0/0 cgrp=default handle=-1345006528
  | schedstat=( 975302082 1348735975 250 )
  at java.lang.Object.wait(Native Method)
  - waiting on <0x4051eb50> (a java.lang.VMThread)
  at java.lang.Object.wait(Object.java:358)
  at java.lang.Thread.join(Thread.java:914)
  at org.libsdl.app.SDLSurface.surfaceDestroyed(SDLActivity.java:280)
  at android.view.SurfaceView.reportSurfaceDestroyed(SurfaceView.java:587)
  at android.view.SurfaceView.updateWindow(SurfaceView.java:481)
  at android.view.SurfaceView.onWindowVisibilityChanged(SurfaceView.java:213)
  at android.view.View.dispatchWindowVisibilityChanged(View.java:4027)
  at android.view.ViewGroup.dispatchWindowVisibilityChanged(ViewGroup.java:720)
  at android.view.ViewGroup.dispatchWindowVisibilityChanged(ViewGroup.java:720)
  at android.view.ViewGroup.dispatchWindowVisibilityChanged(ViewGroup.java:720)
  at android.view.ViewRoot.performTraversals(ViewRoot.java:782)
  at android.view.ViewRoot.handleMessage(ViewRoot.java:1859)
  at android.os.Handler.dispatchMessage(Handler.java:99)
  at android.os.Looper.loop(Looper.java:123)
  at android.app.ActivityThread.main(ActivityThread.java:3647)
  at java.lang.reflect.Method.invokeNative(Native Method)
  at java.lang.reflect.Method.invoke(Method.java:507)
  at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:839)
  at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:597)
  at dalvik.system.NativeStart.main(Native Method)

This is running is the Android 2.3.1 Dalvik emulator.

It's hung at line 280 in SDLActivity.java:
mSDLThread.join();

---

