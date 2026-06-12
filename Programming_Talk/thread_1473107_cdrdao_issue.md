---
title: "cdrdao issue"
date: 2010-05-04
forum: Programming Talk
---

### Post by nmccrina on 2010-05-04
I'm writing a script to rip my cds. I like having a big wav file for archiving, plus flacs for playing, and none of the rippers I could find seemed to do what I want. Anyway, my script is in Python, though all the dirty work is done with stuff like cdparanoia, cdrdao, cuebreakpoints, and shnsplit so it's basically a shell script on steroids. :)

It works superbly on regular CDs, but when I tried to rip a CD that had a data track (you know, autorun type stuff if I was on Windows), cdrdao would fail to create a TOC file because it claimed it couldn't get a lock on the device.

```
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
```

 I noticed that in Nautilus there appeared to be two mounted discs, one with the songs and one with the multimedia stuff. I'm pretty sure that having these two things mounted is what's throwing off cdrdao, but if I try to eject just the multimedia part, the entire disc gets ejected.

I know this is a pretty niche thing, but does anyone have any ideas on how to make 'cdrdao read-toc' work in this situation? If you want to see my script to see what the hell I'm talking about I could post it. :)

---

### Post by nmccrina on 2010-05-04
```
import subprocess
import os

class CdRipper:
	def __init__(self):
		"""Initialize variables that will be used later."""
		self.program_directory = "/home/nfm/bin"
		self.music_directory = "/home/nfm/Music"
		self.album_artist = ""
		self.artist_directory = ""
		self.album_title = ""
		self.album_directory = ""
		self.album_date = ""
		self.same_artist = True;
		self.path = ""

	# End method __init__

	def getAlbumData(self):
		"""Ask user to input data for the album as a whole."""

		# Check if the nominal album artist is the artist
		# for every song on the album. For most albums this
		# will be yes, but not for compilations.
		temp = raw_input("Compilation (y/n): ")
		if temp[0] is "y":
			self.same_artist = False;
	
		self.album_artist = raw_input("Enter album artist: ")
		self.artist_directory = self.album_artist.replace(" ", "_").replace("*", "_").replace(":", "_").replace("\\", "_").replace("/", "_").replace("<", "_").replace(">", "_").replace("|", "_").replace("\"", "_").replace("?", "_").replace("'", "_").replace(".", "_")
		self.album_title = raw_input("Enter album title: ")
		self.album_directory = self.album_title.replace(" ", "_").replace("*", "_").replace(":", "_").replace("\\", "_").replace("/", "_").replace("<", "_").replace(">", "_").replace("|", "_").replace("\"", "_").replace("?", "_").replace("'", "_").replace(".", "_")
		self.album_date = raw_input("Enter album release date: ")

		self.path = self.music_directory + "/" + self.artist_directory + "/" + self.album_directory
		
	# End method getAlbumData

	def createDirectories(self):
		"""Create directories, if needed, under the music directory.

		Directory structure is Music/<album-artist>/<album-title>

		"""
		if not os.path.exists(self.path):
			subprocess.call(['mkdir', '-p', '-v', self.path])

	# End method createDirectories

	def ripCD(self):
		"""Call cdparanoia to rip the CD to a single WAV file.

		The WAV file name will be the album title, with spaces and
		illegal characters converted to underscores (in other words,
		the same as the name of the album directory).
		"""
		outfile = self.path + "/" + self.album_directory + ".wav"
		subprocess.call(['cdparanoia', '"[00:00:00.00]-"', outfile])

	# End method ripCD

	def generateTOC(self):
		"""Call cdrdao to generate a TOC for the CD.

		The toc file name will be the album title.
		"""
		outfile = self.path + "/" + self.album_directory + ".toc"
		subprocess.call(['cdrdao', 'read-toc', outfile])

	# End method generateTOC

	def splitFile(self):
		"""Use the cuebreakpoints and shnsplit tools to split the
		single WAV file into a WAV for each track on the album."""
		
		toc_file = self.path + "/" + self.album_directory + ".toc"
		wav_file = self.path + "/" + self.album_directory + ".wav"

		p1 = subprocess.Popen(['cuebreakpoints', toc_file], stdout=subprocess.PIPE)
		p2 = subprocess.Popen(['shnsplit', '-o', 'wav', wav_file], stdin=p1.stdout, stdout=subprocess.PIPE)
		output = p2.communicate()[0]

		# The resulting files will be put in the same directory the
		# program was called from. We need to move them back to the
		# album directory.
		for f in os.listdir(self.program_directory):
			if f.endswith("wav"):
				f1 = self.program_directory + "/" + f
				subprocess.call(['mv', '-v', f1, self.path])
		
	# End method splitFile

	def convertToFlac(self):
		"""Use the flac tool to compress each split WAV file. Loop through
		the split WAv files, asking the user for the name of each track, 
		and rename the resulting compressed file <track-number>_<track-title>.flac"""
		track_number = 1
		for f in sorted(os.listdir(self.path)):
			# Make sure we aren't trying to convert the album WAV or TOC files
			if f.startswith("split"):

				# If the user indicated the album was a compilation earlier,
				# ask for the artist of each track. Otherwise, use the
				# album artist already given
				if self.same_artist:
					track_artist = self.album_artist
				else:
					track_artist = raw_input("Enter artist for track " + str(track_number) + ": ")

				# Get the track title
				track_title = raw_input("Enter title of track " + str(track_number) + ": ")

				# Create the vorbis comment tags for the flac file
				title_field = "TITLE=" + track_title
				album_field = "ALBUM=" + self.album_title
				tracknumber_field = "TRACKNUMBER=" + str(track_number)
				artist_field = "ARTIST=" + track_artist
				date_field = "DATE=" + self.album_date

				input_file = self.path + "/" + f

				subprocess.call(['flac', '--best', '--verify', '--delete-input-file', '-T', title_field, '-T', album_field, '-T', tracknumber_field, '-T', artist_field, '-T', date_field, '--endian=little', '--channels=2', '--bps=16', '--sample-rate=44100', '--sign=signed', input_file])

				# Construct the final filename for the flac file
				outfile = self.path + "/" + str(track_number) + "_" + track_title.replace(" ", "_").replace("*", "_").replace(":", "_").replace("\\", "_").replace("/", "_").replace("<", "_").replace(">", "_").replace("|", "_").replace("\"", "_").replace("?", "_").replace("'", "_").replace(".", "_") + ".flac"

				# Rename the flac file
				input_file = input_file[0:-3] + "flac"
				subprocess.call(['mv', '-v', input_file, outfile])

				track_number = track_number + 1

	# End method convertToFlac
				
	
# End class CdRipper

ripper = CdRipper()
ripper.getAlbumData()
ripper.createDirectories()
ripper.ripCD()
ripper.generateTOC()
ripper.splitFile()
ripper.convertToFlac()
```

---

