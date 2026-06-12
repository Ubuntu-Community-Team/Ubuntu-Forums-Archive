---
title: "Head First Exception"
date: 2007-02-25
forum: Programming Talk
---

### Post by @trophy on 2007-02-25
So this weekend I thought I'd get back into doing some Java since I havn't done it in a real long time... I dug out my Head First Java book (best book on Java, IMHO) and typed up the code for the program where you make midi drum loops... and it compiles splendidly, but when you press play the loop plays through once, and then the program throws an audio device not available exception, which it continues to do until you log out and log back in.  I thought this was some sort of error in Ubuntu, until I rebooted into XP, and it did the same thing there... so what gives?  

Has anybody else had this problem with playing midi stuff in Java?

The code is attached...

---

### Post by Tomosaur on 2007-02-26
I took a look, you've put your setUpMidi call in the wrong place. Instead of inside the buildGUI() method, it should be the first call in the buildTrackAndStart() method, like this:

```

public void buildTrackAndStart() {
		setUpMidi();
		int[] trackList = null;
		
		sequence.deleteTrack(track);
		track = sequence.createTrack();
		
		for (int i =0; i < 16; i++){
			trackList = new int[16];
			
			int key = instruments[i];
			
			for (int j = 0; j < 16; j++){
				JCheckBox jc = (JCheckBox) checkboxList.get(j+(16*i));
				if (jc.isSelected()) {
					trackList[j] = key;
				}else {
					trackList[j] = 0;
				} // end if
			} // end inner loop
			
			makeTracks(trackList);
		} // end outer loop
		
		track.add(makeEvent(192,9,1,0,15));
		
		try{
			sequencer.setSequence(sequence);
			sequencer.start();
			sequencer.setTempoInBPM(bpm);
		} catch (Exception e){
			e.printStackTrace();
		}
	} // end buildTrackAndStart

```

In your stop listener method, you should also close the sequencer stream, like this:
```

public class MyStopListener implements ActionListener {
		public void actionPerformed(ActionEvent a){
			sequencer.stop();
			sequencer.close();
		}
	} // end inner class

```
You may also want to disable the stop button while the track isn't playing, otherwise you'll get an exception.

---

### Post by @trophy on 2007-02-26
Thanks!  I hadn't used Java in forever, and just COULD NOT see the problem... and LOL in case anybody was wondering, I typed that code directly from the book, and have since gone back and checked it, so yeah... it's printed wrong in the book.  Serves me right for buying it before the second edition came out LOL.  Anyways I'll make the changes... thanks!!!

---

