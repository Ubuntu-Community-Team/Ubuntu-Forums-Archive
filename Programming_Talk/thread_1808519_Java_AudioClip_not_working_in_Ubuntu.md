---
title: "Java AudioClip not working in Ubuntu"
date: 2011-07-20
forum: Programming Talk
---

### Post by Carenthir on 2011-07-20
I'm learning Java and doing great so far, I've been messing with graphics and stuff and even programmed two little games, but I just decided to start messing with sound today. So I've been trying different sound packages but I could get no sound with any of them in Ubuntu. Well about an hour ago I decided just to try it in Windows..and sure enough it worked. So why is my app not working in Ubuntu? Here's this code..

<code>
import java.applet.AudioClip;
import java.awt.Graphics;

import javax.swing.JApplet;


public class testSound extends JApplet {
	 private AudioClip testClip;

	  public void init( ) {  
		  testClip = getAudioClip(getCodeBase(),"EpochsEnd.mid");  
	  }

	  public void paint(Graphics g) {  
		  g.drawString("Epoch's End", 25, 25);  
	  }

	  public void stop( ) {  
		  testClip.stop( ); 
	  }

	  public void start( ) { 
		  testClip.loop( );  
	  } // end of testSound

}
</code>

---

### Post by Zugzwang on 2011-07-20
Try playing something else than a MIDI file. You might not be running a MIDI emulator to hear those.

---

### Post by PaulM1985 on 2011-07-20
I have seen this problem a few times before but unfortunately I have never seen a solution.
Sorry.
Paul

---

### Post by Carenthir on 2011-07-20
I just tried a .wav file, and the sound DID INDEED WORK. However..it came through my laptop speakers and not my USB headset, I can probably find something on fixing that. Anyway how would I go about getting some sort of "Midi Emulator?"

---

### Post by PaulM1985 on 2011-07-20
I found this...
[http://www.java-tips.org/java-se-tips/javax.sound.midi/how-to-load-and-play-midi-audio-19.html](http://www.java-tips.org/java-se-tips/javax.sound.midi/how-to-load-and-play-midi-audio-19.html)

Paul

---

### Post by Carenthir on 2011-07-20
Thanks, but I actually found that exact code somewhere else. However it didn't work, so I thought I'd try rewriting it adding each statement in a try and catch block so I could specifically find out which statement wasn't working. 

Sequencer sequencer = MidiSystem.getSequencer();

That was throwing the MidiUnavaiableException. And if I'm understanding that statement correctly, that's the program actually trying to get the Midi Device ready for sequencing an audio file. I tried something else with that, having Java code query my system to see if I have midi devices. And it actually returned "Real Time Sequencer." Now I also read somewhere that the code may not be able to use the device if another program has not released the device. So I rebooted..but it still throws that exception. So... yeah. :confused:



Edit: Thought I'd add that Banshee can play Midi perfectly fine.

---

### Post by PaulM1985 on 2011-07-20
Have you tried:
```

sudo update-alternatives --config java

```

Paul

---

### Post by Carenthir on 2011-07-20
I got it fixed! I'm still relatively new to Ubuntu, so I didn't know anything about that. However I tried it and I noticed that it referenced openDJK when I had actually removed that a few days ago because I was having problems in my Java programs and I thought maybe I would try the official jdk from Oracle. But I wondered why openJDK still showed up in the alternatives list. So I tried removing the ones from oracle and reinstalling openJDK and the midi works! My other programs I coded work fine too, little slower to load up but that's fine long as they work! Lol. Well thanks for all the help, much appreciated. =)

---

