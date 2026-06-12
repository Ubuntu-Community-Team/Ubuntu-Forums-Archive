---
title: "LineUnavailableException in org.classpath.icedtea.pulseaudio"
date: 2009-11-12
forum: Programming Talk
---

### Post by devent on 2009-11-12
Hi,
I'm working on a Java sound application under Ubuntu 9.10. But I get this exception if I try to play a audio file (wav file). The code is nothing fancy:
```
audioStream = AudioSystem.getAudioInputStream(file)
line = createLine(audioStream)
line.start()
byte[] data = new byte[BUFFER_SIZE]
while (playing && (bytesRead=audioStream.read(data, 0, data.length)) != -1) {
  line.write(data, 0, bytesRead)
}
audioStream.reset()
//...
line.drain()
line.close()
```


```
Caused by: javax.sound.sampled.LineUnavailableException
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.openImpl(PulseAudioMixer.java:714)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.openLocal(PulseAudioMixer.java:588)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.openLocal(PulseAudioMixer.java:584)
	at org.classpath.icedtea.pulseaudio.PulseAudioMixer.open(PulseAudioMixer.java:579)
	at org.classpath.icedtea.pulseaudio.PulseAudioDataLine.open(PulseAudioDataLine.java:95)
	at org.classpath.icedtea.pulseaudio.PulseAudioSourceDataLine.open(PulseAudioSourceDataLine.java:75)
	at org.classpath.icedtea.pulseaudio.PulseAudioDataLine.open(PulseAudioDataLine.java:296)
	at org.classpath.icedtea.pulseaudio.PulseAudioSourceDataLine.open(PulseAudioSourceDataLine.java:51)
```

The Java version is:
```
$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-1ubuntu3)
OpenJDK Server VM (build 14.0-b16, mixed mode)
```

I used Sidux (Debian Sid) before and it worked normally and under Windows XP it works, too. So it must be some configuration of PulseAudio in Ubuntu 9.10 maybe? Would be really glad if someone could solve this.

---

### Post by myrtle1908 on 2009-11-12
Well the problem is obviously that pulseaudio is unable to obtain a line out to play your sound.  However, I'd say the problem relates more to the fact that you are using the OpenJDK VM rather than the Sun one.

Are you using OpenJDK for a reason?  Better to use Sun.

---

### Post by devent on 2009-11-13
I installed the jdk from sun and now it works. So it's really an issue with openjdk and pulseaudio.

> Are you using OpenJDK for a reason? Better to use Sun. 

Well, with the one from sun you have to accept the licence. I always stay with open source applications and libraries.

---

