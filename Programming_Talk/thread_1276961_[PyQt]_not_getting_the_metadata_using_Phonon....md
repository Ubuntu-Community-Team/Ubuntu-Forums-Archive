---
title: "[PyQt] not getting the metadata using Phonon..."
date: 2009-09-27
forum: Programming Talk
---

### Post by meep_meep on 2009-09-27
Hi guys,

I'm just trying to learn a bit of python and pyqt.  I'm making a simple music program with a wikipedia page attached for the artist.

here is my music player class in the code below.... when i press the play button it will load the file using musicLoadFile(filename) and play it using musicPlay().  the meta data is extracted when the file is loaded and obv the idea is that the track name and artist are displayed.... well they do but late.  So i play my track and the getArtist and getTrack functions return empty strings for the first try.  then if i load a new track they will return the name of the previous track...

any ideas why?

```
class musicPlayer():
	def __init__(self):
		self.media = Phonon.MediaObject()
		self.audioOuput= Phonon.AudioOutput(Phonon.MusicCategory)
		Phonon.createPath(self.media, self.audioOuput)
		self.paused= False
	def musicLoadFile(self,filename):
		print "----->Path of file: ~/%s" % filename		
		self.media.setCurrentSource( Phonon.MediaSource("/home/meep/%s" % filename))
		self.metaStuff = self.media.metaData()
		self.artist = self.metaStuff.get(QtCore.QString('ARTIST'), [QtCore.QString()])[0]
		self.track = self.metaStuff.get(QtCore.QString('TITLE'), [QtCore.QString()])[0]	
	def musicPlay(self):			
		self.media.play()
	def musicPause(self):
		if self.paused:
			self.paused=False
			self.media.play()
		else:
			self.paused =True
			self.media.pause()			
	def musicStop(self):
		self.media.stop()
		self.paused=False
	def getArtist(self):		
		print "----Artist----->  %s" % self.artist + "  ----Track----->  %s" % self.track
		return self.artist
	def getTrack(self):
		return self.track
```

any help is welcome....ps im looking for a job so if anyone have anything going in the SE of the UK send me a message. 

meep

---

### Post by meep_meep on 2009-10-09
bump

---

### Post by eightmillion on 2009-10-10
I'm not sure why your metadata isn't updating, but have you thought about instead of setting self.artist and self.track when you load a music file, pull that information when musicPlayer.getArtist is called?

Also Phonon.MediaObject provides a signal "metaDataChanged" that you can hook up to to update self.artist and self.title whenever new media is loaded and the signal gets emitted. That would look something like this:

```

    def __init__(self):
            QtCore.QObject.connect(self.media, QtCore.SIGNAL("metaDataChanged()"),updateData)

    @QtCore.pyqtSignature("metaDataChanged()")
    def updateData(self):
            self.artist = self.media.metaData().get(QtCore.QString('ARTIST'), [QtCore.QString()])[0]
	    self.track = self.media.metaData().get(QtCore.QString('TITLE'), [QtCore.QString()])[0]

```

---

