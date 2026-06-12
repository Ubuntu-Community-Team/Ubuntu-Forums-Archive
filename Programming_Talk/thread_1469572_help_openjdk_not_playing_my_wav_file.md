---
title: "help openjdk not playing my wav file"
date: 2010-05-02
forum: Programming Talk
---

### Post by psychok7 on 2010-05-02
Hi there.. i just installed ubuntu 10.04 and openJdk and i tried using this old program that i wrote that plays a sound wave file. Its not working but i know its not the programs fault because it worked on my previous ubuntu with sun-javajdk. can someone help me change it so it can compile with openjdk? heres the code and the errors: 
"
Exception in thread "main" java.lang.IllegalArgumentException: Invalid format
        at org.classpath.icedtea.pulseaudio.PulseAudioDataLine.createStream(PulseAudioDataLine.java:143)
        at org.classpath.icedtea.pulseaudio.PulseAudioDataLine.open(PulseAudioDataLine.java:100)
        at org.classpath.icedtea.pulseaudio.PulseAudioDataLine.open(PulseAudioDataLine.java:289)
        at org.classpath.icedtea.pulseaudio.PulseAudioClip.open(PulseAudioClip.java:402)
        at org.classpath.icedtea.pulseaudio.PulseAudioClip.open(PulseAudioClip.java:453)
        at Tp4.Playwav.soundplay(Playwav.java:34)
" 

**Heres the code: **

```

import java.io.*;
import java.util.logging.Level;
import java.util.logging.Logger;
import javax.sound.sampled.*;
public class Playwav {
    protected String wavefile;
    public Playwav(String wavefile){
        this.wavefile=wavefile;
        try {
            soundplay(this.wavefile);
        } catch (Exception ex) {
            Logger.getLogger(Playwav.class.getName()).log(Level.SEVERE, null, ex);
        }
    }
    public Playwav(){

    }

    public void soundplay(String wavefile) throws Exception {
         File soundFile = new File(wavefile);
         AudioInputStream soundIn = AudioSystem.getAudioInputStream(soundFile);
         AudioFormat format = new AudioFormat(AudioFormat.Encoding.PCM_SIGNED,
                       AudioSystem.NOT_SPECIFIED,
                       16, 2, 4,
                       AudioSystem.NOT_SPECIFIED, true);
         DataLine.Info info = new DataLine.Info(Clip.class, format);

         Clip clip = (Clip)AudioSystem.getLine(info);
         clip.open(soundIn);
         clip.start();
         while(clip.isRunning())
         {
            Thread.yield();
         }

    }

}

```

i call sounfile with this arguments: 

alarm.soundplay("24test.wav");

Thanks

---

### Post by lykeion on 2010-05-21
Why do you define the format like this:
```
AudioFormat format = new AudioFormat(AudioFormat.Encoding.PCM_SIGNED,
                       AudioSystem.NOT_SPECIFIED,
                       16, 2, 4,
                       AudioSystem.NOT_SPECIFIED, true);
```
instead of getting the format from the actual sound file like this:
```
AudioFormat format = soundIn.getFormat();
```
By making this adjustment this should work with both sun-java6-jdk and openjdk

P.S wrap your code with code tags to make it readable

---

### Post by psychok7 on 2010-05-21
> **lykeion said:**
> Why do you define the format like this:
```
AudioFormat format = new AudioFormat(AudioFormat.Encoding.PCM_SIGNED,
                       AudioSystem.NOT_SPECIFIED,
                       16, 2, 4,
                       AudioSystem.NOT_SPECIFIED, true);
```
instead of getting the format from the actual sound file like this:
```
AudioFormat format = soundIn.getFormat();
```
By making this adjustment this should work with both sun-java6-jdk and openjdk

P.S wrap your code with code tags to make it readable

thanks it works fine now

---

