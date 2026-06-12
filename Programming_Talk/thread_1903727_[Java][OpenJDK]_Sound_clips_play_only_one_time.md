---
title: "[Java][OpenJDK] Sound clips play only one time"
date: 2012-01-03
forum: Programming Talk
---

### Post by Erik1984 on 2012-01-03
I have written a puzzle game in Java and I decided to pick up development again. Started programming the game on Windows with the Oracle Java and am now using OpenJDK on Ubuntu 10.04, Lucid Lynx. My IDE is Eclipse. Development Kit version is 6b20-1.9.10-0ubuntu1~10.04.2 (everything installed from the repositories).

The problem is in the title: sound clips can be played once but calling the play() method for those clips a second time yields no sound, no exceptions are thrown either. Playing each clip one time works so all the .wav files are loaded correctly it seems. For debugging purpose I placed some printlines in the SoundHandler.play() method. the line "trying to (re)play clip" is printed everytime the sound should be played. soundClips[clipID].isRunning() however never reports the particular clip is already running.

What am I doing wrong (outside writing bad code :wink:)?

The imports for audio playback:
```

import javax.sound.sampled.AudioFormat;
import javax.sound.sampled.AudioInputStream;
import javax.sound.sampled.AudioSystem;
import javax.sound.sampled.Clip;
import javax.sound.sampled.DataLine;
import javax.sound.sampled.LineEvent;
import javax.sound.sampled.LineListener;
import javax.sound.sampled.LineUnavailableException;
import javax.sound.sampled.UnsupportedAudioFileException;

```The class responsible for loading and playing sounds:
```
class SoundHandler implements LineListener{
    
    public static final int ROTATE = 0;
    public static final int MIRROR = 1;
    public static final int PLACE = 2;
    public static final int FREE_PIECE = 3;
    public static final int DROP_PIECE = 4;
    
    private static SoundHandler thisSoundHandler;
    
    private Clip[] soundClips;
        
    private SoundHandler(){
        soundClips = new Clip[5];
        java.net.URL url;
        url = getClass().getResource("/sounds/17892__zippi1__sound_click2.wav");
        soundClips[ROTATE] = getSoundClipFromURL(url);
        url = getClass().getResource("/sounds/PuzzleGame_mirror.wav");
        soundClips[MIRROR] = getSoundClipFromURL(url);
        url = getClass().getResource("/sounds/17893__zippi1__sound_click3.wav");
        soundClips[PLACE] = getSoundClipFromURL(url);
        url = getClass().getResource("/sounds/15348__Hell_s_Sound_Guy__BUBBLE_POP_.wav");
        soundClips[FREE_PIECE] = getSoundClipFromURL(url);
        url = getClass().getResource("/sounds/13832__adcbicycle__23.wav");
        soundClips[DROP_PIECE] = getSoundClipFromURL(url);
    }
    
    public static SoundHandler getInstance(){
        if(thisSoundHandler == null){
            thisSoundHandler = new SoundHandler();
        }
        return thisSoundHandler;
    }
    
    public Clip getSoundClipFromURL(java.net.URL url){
        Clip thisClip;
        AudioFormat aF;
        AudioInputStream aIS;
        try{
            aIS = AudioSystem.getAudioInputStream(url);
            aF = aIS.getFormat();  
        } catch (IOException e) {
            System.out.println(e.getMessage());
            aIS = null;
            aF = null;
        } catch (UnsupportedAudioFileException e){
            System.out.println("Format not supported: " + e.getMessage());
            aIS = null;
            aF = null;
        }
        DataLine.Info info = new DataLine.Info(Clip.class, aF);
        try{
            thisClip = (Clip)AudioSystem.getLine(info);
            thisClip.open(aIS);
            thisClip.addLineListener(this);
        } catch(LineUnavailableException e){
            e.printStackTrace();
            thisClip = null;
        } catch(IOException e){
            e.printStackTrace();
            thisClip = null;
        }
        return thisClip;
    }
    
    public void play(int clipID){
        if((clipID >=0) && (clipID < soundClips.length) && (soundClips[clipID] != null)){
            System.out.println("Trying to (re)play clip:");
            try{
                if(soundClips[clipID].isRunning()){
                    System.out.println("Clip still running.");
                    soundClips[clipID].stop();                    
                }
                soundClips[clipID].setFramePosition(0);            
                soundClips[clipID].start();
            } catch(Exception e){
                e.printStackTrace();
            }
        }
    }
    
    public void update(LineEvent e){
        /* nothing here yet */
    }
}
```

---

### Post by Erik1984 on 2012-01-04
A little bump.

---

### Post by HotCupOfJava on 2012-01-05
Hmmmmm.... try adding "soundClips[clipID].stop();" directly above "soundClips[clipID].setFramePosition(0);". I know you shouldn't NEED to, but its just a hunch I have. I could be completely wrong.

---

### Post by Erik1984 on 2012-01-05
> **HotCupOfJava said:**
> Hmmmmm.... try adding "soundClips[clipID].stop();" directly above "soundClips[clipID].setFramePosition(0);". I know you shouldn't NEED to, but its just a hunch I have. I could be completely wrong.

Thanks for your idea, you are certainly not 'completely wrong'. It does help to make the sounds 'replayable' but introduces a new problem, the execution of the program halts until the clip has finished playing.

I've discovered that using Clip.isActive() in stead of Clip.isRunning() does get the value True when the clip is still running. However the problem remains that Clip.stop() acts as a blocking command. Could that be a difference in implementation between OpenJDK and the 'official' Sun/Oracle Development Kit and Runtime Environment I used previously on Windows?

---

### Post by HotCupOfJava on 2012-01-07
It SHOULDN'T have such a different implementation, but it may. I haven't used the javax.sound API myself, so I'm not really familiar with it. A peek at the source may yield the answer. Come to think of it, I seem to remember some edge cases where threading was handled differently by different operating systems regardless of the underlying code - I wonder if that has anything to do with this situation...

---

### Post by Erik1984 on 2012-01-07
Thanks again. Do you know other ways of handling playback of (short) audio files in OpenJDK?

---

### Post by HotCupOfJava on 2012-02-17
Okay - I know it has been a while since we discussed this, but I think I may have an idea about the problem.

You obtain your clip from a URL, which means that you are inheriting from an InputStream. I believe it may be acting like an Iterable, where once you've gone over the bytes, it won't let you go over them again unless you re-open the stream as a new instance.

You may need to build some intermediate construct in to save the clips in a fashion that will let them persist. Try reading the AudioInputStream into a byte array (not a buffer) and building your clip from that.

I could be totally wrong of course.....

---

