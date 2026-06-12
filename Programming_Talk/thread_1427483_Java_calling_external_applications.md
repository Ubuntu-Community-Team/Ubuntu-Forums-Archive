---
title: "Java: calling external applications"
date: 2010-03-11
forum: Programming Talk
---

### Post by hyperAura on 2010-03-11
hi, is there anyone who knows how to call external applications? e.g. a music player to play a track through java or maybe a text editor?

ive searched on the internet and ive found some examples using Runtime.exec() but i cant manage to work them..

---

### Post by r-senior on 2010-03-11
Just bashed this into an IDE and it worked fine on Ubuntu:

```

package mypackage;

public class Driver {

    public static void main(String ... args) throws java.io.IOException {
        Runtime.getRuntime().exec("/usr/bin/gedit");
        Runtime.getRuntime().exec("/usr/bin/rhythmbox");
    }

}

```

What problems are you having?

Is it that you are looking for libraries to do things from inside your code, rather than separate programs?

---

### Post by hyperAura on 2010-03-11
well i have just finished a game playing program and i want to add some music to it by pressing a button on the gui so that it will turn on and off the player.. even if i open an application it wont automatically start playing.. i think that what i require might not exist.. :(

---

### Post by hyperAura on 2010-03-11
by application i mean such as the one u have said the rhythmbox..

---

### Post by myrtle1908 on 2010-03-11
> **hyperAura said:**
> well i have just finished a game playing program and i want to add some music to it by pressing a button on the gui so that it will turn on and off the player.. even if i open an application it wont automatically start playing.. i think that what i require might not exist.. :(

Have you tried passing an argument to rythmbox eg. the song to play?

PS.  I'm just guessing as I have never used rhythmbox.

---

### Post by hyperAura on 2010-03-11
no i havent tried that as i dont know the rhythmbox api and i am not quite sure if thats possible..

---

### Post by kahumba on 2010-03-11
Java can play some types of audio: .au and a few types of .wav:
[http://www.exampledepot.com/egs/java.applet/LoadAudioApp.html](http://www.exampledepot.com/egs/java.applet/LoadAudioApp.html)

or, go the (much) more difficult way and learn the java sound api: javax.sound.midi and the likes.

---

### Post by soltanis on 2010-03-12
Yes, it sounds like you want to play the file directly in your app without invoking an external program to do it (or using a media plugin).

Unfortunately Java is incredibly frustrating in this regard (well not just this one...). I don't know of any way you can embed a plugin in your application with Java. You will have to use either the really limited sound API (which you can't count on to play more than a basic wav file or terrible 8 khz u-law sound) or do the difficult sound API route.

You might consider using jogg/jorbis, which are java-based Ogg/Vorbis decoders, if you want anything of better quality. Google for it, they have examples which you can hopefully adapt easily to do basic playout.

---

### Post by hyperAura on 2010-03-12
so lets say if i have an mp3 which i want to play, first i should convert its format to ogg and then i might find a way to play it through java?

---

### Post by kahumba on 2010-03-12
Google for "Java ogg" or so and I'm pretty sure you'll find a (free) Java library that enables Java to play .ogg files.

---

### Post by hyperAura on 2010-03-12
thnx!! i will look for it..

---

### Post by hyperAura on 2010-03-13
Has anyone tried to play mp3 files through java by using JMF and the mp3 plugin??

---

