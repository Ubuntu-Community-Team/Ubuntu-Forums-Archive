---
title: "Python - Wave cutting/slicing(/whatever)"
date: 2009-01-09
forum: Programming Talk
---

### Post by Timo Veldt on 2009-01-09
Hi,

I'm using The Python Wave module and I'm trying to cut a certain segment from an existing wave file (e.g. I have a wave file of say 60 seconds and I want to create a new file containing 10 seconds of the original, but not just any 10 seconds, I want 10 through 20 from the original file).

I have been looking through the documentation but I haven't found anything like this yet.

I am already able to cut certain fragments from the original, but these turned out to be other fragments than the ones I wanted.

Code fragment (see attachment for whole class):

```
...
*def writeTimeInterval(self, start, end):*
#This a class method of a class that stores most parameters of the input wave file in internal attributes, hence the self.framerate and self.readPath, etc.[I]
[INDENT][/I]#The number of audioframes before the interval I want[I]
preFrames = start*self.framerate

[/I]# The number of audioframes including the fragment I want[I] 
intervalFrames = end*self.framerate

inputFile = wave.open(self.readPath, 'r')

[/I]#Read in the frames before the interval[I]
preInterval = inputFile.readframes(preFrames)

[/I]#From the start of the original to the end of the original (I hope, or should I rewind?))[I]
interval = inputFile.readframes(intervalFrames)

inputFile.close()

[/I]#since readframes returns a **string** of bytes, I assumed I could use lstrip, which is probably completely wrong[I]
interval = interval.lstrip(preInterval)

outputFile = wave.open(self.writePath, 'w')
outputFile.setnchannels(self.nrOfChannels)
outputFile.setframerate(self.framerate)
outputFile.setsampwidth(self.sampleWidth)
outputFile.writeframes(interval)
outputFile.close()[/I]
[/INDENT]
```

---

