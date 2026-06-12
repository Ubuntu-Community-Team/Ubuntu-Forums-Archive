---
title: "help writing an audio script"
date: 2011-01-19
forum: Programming Talk
---

### Post by sejan on 2011-01-19
I have been searching the internet for a script to automatically record the audio from a microphone at a specific time every week.  I have found several that automatically record streaming audio from the internet, but I don't know enough about scripting to be able to figure out how to change it to fit my needs.

Any help would be greatly appreciated.


What I've found:
[http://www.mbeckler.org/scripts.php#savestream]("http://www.mbeckler.org/scripts.php#savestream")
[http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/]("http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/")

---

### Post by ajgreeny on 2011-01-19
A simple script run using cron will do that.

A sample script would be ```
#!/bin/bash
arecord -d 10 -c 2 test.wav
```which would record the microphone input, so long as the mic is already set up to work, and you can hear it through the speakers of your machine.  That script would record 10 seconds (-d 10) as a 2 channel (-c 2) audio file called test.wav.

You will probably need to set up the microphone levels carefully before using the script to get the volume right, but that certainly does the trick; I've just tried it out.

---

### Post by Rhubarb on 2011-01-19
You beat me to it ajgreeny :)

I was going to suggest something like:
```
arecord -f cd -d 10 recording.wav
```
Which will record at 16bit 44100Hz Stereo for 10 seconds to a file named recording.wav

If you run:
```
man arecord
```
It'll tell you the syntax about all the cool things you can do with arecord.
- The examples section is particularly good.

You should be able to read up about how to do a cron job, so the command can be run periodically.

---

### Post by soltanis on 2011-01-19
You can also consider compressing the audio using a tool such as oggenc (available from the "vorbis-tools" package: sudo apt-get install vorbis-tools). Set up a pipe to pass uncompressed data into the encoder:

```

#!/bin/sh
arecord -f cd -d 10 | oggenc --quiet --quality=2 --date `date` -o output_file.oga -

```

---

