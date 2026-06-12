---
title: "Java sound notification"
date: 2008-05-08
forum: Programming Talk
---

### Post by Geir102 on 2008-05-08
Hi, I'm creating a java application. And I want it to play a simple sound notification. Any one know a simple way to to this? Google just comes up with big messy code...

---

### Post by achelis on 2008-05-08
Hi.

To load an audio file you can use this:

```
	public Clip loadAudioFile(String filename) throws UnsupportedAudioFileException, IOException, LineUnavailableException 
	{
		File file = new File(filename);
		AudioInputStream stream = AudioSystem.getAudioInputStream(file);
		AudioFormat format = stream.getFormat();

		DataLine.Info info = new DataLine.Info(Clip.class, format);
		Clip clip = (Clip) AudioSystem.getLine(info);
		clip.open(stream);
		return clip;
	}
```

And to play the clip:

```

clip.setFramePosition(0);
clip.start();

```

I haven't used sound a lot in Java, so there is probably better ways to do it, but this should get you started :)

---

### Post by Zugzwang on 2008-05-08
> **Geir102 said:**
> Hi, I'm creating a java application. And I want it to play a simple sound notification. Any one know a simple way to to this? Google just comes up with big messy code...

You shoudln't give up so quickly. Searching for "Java play audio file", the third result I get at google is: [http://www.javaworld.com/javatips/jw-javatip24.html]("http://www.javaworld.com/javatips/jw-javatip24.html"). This looks quite easy, doesn't it?

---

### Post by Geir102 on 2008-05-08
thanks alott for the quick answers:) this helps a lott

---

