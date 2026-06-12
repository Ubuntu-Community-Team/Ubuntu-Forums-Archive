---
title: "Video Converter Ogg Mpeg Avi"
date: 2008-04-20
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-04-20
I am looking to build Video format converter
[LIST]
[*]MPEG
[*]OGG Video
[*]AVI
[*]Whatever else is Popular, I will do research
[/LIST]

My main goal with this is to make a quick(or Java quick see below) GUI program that can convert Most Video files to another Popular format and back. Their will be no combining or splitting of videos in the first version

I want this to be GUI so ... for me that leaves me to Java and Python. (Because i don't know any GUI of another language)

I am very proficient at Java but they have no video manipulation libraries. I am okay with using the amazing Unix libraries around such as mEncoder and others. But i don't know how to use them, a tutorial would be perfect. Is it a decent idea to make a encoder/decoder of my own for Java(Java currently has none).

I am okay at Python but have almost zero experience with GUI. And the libraries(PyMedia) i have found aren't supported by Ubuntu repositories.

I am open for ideas that don't involve learning much of another language.

---

### Post by mssever on 2008-04-21
I'd recommend against Java, especially if there aren't any pre-existing libraries. Java programs always feel slow (to me, at least) and they don't integrate well into Ubuntu. For one thing, Ubuntu doesn't ship Sun Java by default, and other Java implementations are inferior. For another, last I heard, the choices for Java GUI toolkits were AWT and Swing, neither of which play nice on Linux (or any other system, for that matter). If GTK is available for Java, then my argument is moot, provided you actually use GTK.

All GUI toolkits worth their salt should match the platform's GUI toolkits. That means that on Linux, it needs to look just like GTK or Qt. (This is also why Python's Tkinter is completely unacceptable as a GUI toolkit.)

---

### Post by Quikee on 2008-04-21
Use Python with GStreamer (or Java with GStreamer if there exist bindings for Java). 

It is pretty easy to create a conversion program once you know how GStreamer works. You can also easily create things like on-the-fly-previews which can be harder if you use CLI encoders (you just route the pipeline to a audio/video sink instead muxing it into a container and output it to a file). 

Check out oggconvert in the repository - it is done this way but it is too limiting IMHO as it could be a much better general solution.

---

### Post by jespdj on 2008-04-21
> **mssever said:**
> I'd recommend against Java, especially if there aren't any pre-existing libraries. Java programs always feel slow (to me, at least)...
Java is not slow. In the days up to Java 1.2 (in 1999 or so) Java was indeed not very fast, but Sun's Java 6 is very fast and efficient. Your perception is based on prejudice instead of objective evidence.

> **mssever said:**
> ...and they don't integrate well into Ubuntu. For one thing, Ubuntu doesn't ship Sun Java by default, and other Java implementations are inferior. For another, last I heard, the choices for Java GUI toolkits were AWT and Swing, neither of which play nice on Linux (or any other system, for that matter). If GTK is available for Java, then my argument is moot, provided you actually use GTK.
[GTK+ library for Java](http://java-gnome.sourceforge.net/) - there has been GTK+ for Java for a long time.

Have a look at OpenJDK (which is available for Hardy) - it's the open source version of Sun Java 6, with the few parts of Java 6 that couldn't be opened replaced with new, open source parts. It works really well, almost just as well as the old Sun Java 6.

Why do AWT and Swing not play nice on Linux (or any other system)? You sound like the last time you've looked at Java was in 1999 or 2000 or so. Java has come a long way since then.

Besides AWT and Swing there's also SWT, Eclipse's GUI toolkit which works really well.

---

### Post by Tomosaur on 2008-04-21
There is a Java-based video converter, intended for iRiver based portable devices, but will pretty much do whatever you need with a little tinkering: [Iriverter]("http://iriverter.thestaticvoid.org/")

Try tweaking the source of that until it does what you need it to, no point starting from scratch! Also, watch out for the codecs - you may need to replace some of them if you're concerned about binaries, I think some of them included with the latest version are non-free.

---

### Post by mssever on 2008-04-21
> **jespdj said:**
> Why do AWT and Swing not play nice on Linux (or any other system)?

Because they don't provide native look and feel. If wxWidgets is able to provide cross-platform native look and feel, then other cross-platform toolkits ought to do the same.

---

### Post by Tomosaur on 2008-04-21
You **can** get native look and feel with Swing, but you have to do it manually: [http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html#available](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html#available)

There were some problems with native look and feel for GTK in the past, I believe, but I **think** (don't quote me on it :P ) that the latest JDK has pretty much fixed them. I think KDE looks are unsupported for now, but I did read about a way to get it working. I'm not sure on the details though so you'll have to look it up yourself.

EDIT: I have actually just tested with a Java GUI app I've been working on. Make sure you compile to be run with the latest JRE (Java 6) or you'll get a crappy looking GTK style. Also (from the page I linked to): > **Note:** The GTK+ L&F will only run on UNIX or Linux systems with GTK+ 2.2 or later installed, while the Windows L&F runs only on Windows systems. Like the Java (Metal) L&F, the Motif L&F will run on any platformSo basically, code carefully and you should be ok :P

---

### Post by Zugzwang on 2008-04-21
> **mssever said:**
> Because they don't provide native look and feel. If wxWidgets is able to provide cross-platform native look and feel, then other cross-platform toolkits ought to do the same.

Interesting argument. KDE and GNOME applications also provide a different look&feel, but would anybody ever say that they aren't well-integrated into the system? 

As far as the slowness is concerned. You're of course right, Java applications still seem a bit slow, but only on startup to my perception. This however again can also be said of "Konsole" when running it from GNOME, so this is somewhat comparable. 

The last time I ran "jabref" I didn't even notice that it was Java (well, apart from the L&F, but the argument above applies), especially since it could easily be installed using apt-get and run from the menu. :)

---

### Post by Mr.Macdonald on 2008-04-21
I am going to look into using Java for this. I have read the arguments and i am rather okay with the downsides now.

I choose this because i am far better at java than Python or C++.


As for a library, i looked at the Iriverter and decided against it for lack of pure Java. It uses Binary that is machine specific.

If i were to write my own java version of these libaries how would i do it.

What i feel should be done, I don't really know what i am talking about and am just throwing out my idea's
> 
I have talked with people and they say that i should get the "Standards" for the formats like
```

Mp3 to RAW
#12ac3f=#ab13f3
#41a6f7=#b41590
...

```
I don't know if i am explaining it right. A way that i could manually covert a Mp3 to a RAW (By the way what is RAW) format by exchanging the hex values of the file.

Edit:

Just so we don't go off on the look and feel, I don't care about the look at the current stage of this, I just want something that can convert Video formats by using Java. Eventually i will care but not for a long time.

I also would like a Java converting solution but any library is fine as long as it is widely supported on linux or is cross platform(Python, Perl, Java).

---

### Post by jespdj on 2008-04-21
I have no experience with it myself, but you could have a look at the [Java Media Framework]("http://java.sun.com/products/java-media/jmf/").

---

### Post by Tomosaur on 2008-04-21
^^ Ahh yeah, how the hell did I forget about that? Definitely check out the JMF, it probably does exactly what you need.

---

### Post by mssever on 2008-04-21
> **Zugzwang said:**
> Interesting argument. KDE and GNOME applications also provide a different look&feel, but would anybody ever say that they aren't well-integrated into the system?GTK apps match a GNOME system; Qt apps match a KDE system. Swing apps match neither, unless you take the steps Tomosaur mentioned. I run GNOME and run very few non-GTK apps. This, by the way, is the same complaint I have about Python's Tkinter, except that Tkinter is hideous, while Swing is merely ugly (IMHO).

> As far as the slowness is concerned. You're of course right, Java applications still seem a bit slow, but only on startup to my perception. This however again can also be said of "Konsole" when running it from GNOME, so this is somewhat comparable.
Which is one reason why I don't run Konsole. It has a few more features (that I'd probably never need), but you have to start the whole KDE platform to run it. It's been a long time since I've programmed in Java and I don't know it very well, but why should the Java platform be so huge? The Python folks don't seem to need a huge footprint to write cross-platform code.

---

### Post by Mr.Macdonald on 2008-04-21
The JMF is a start but it currently can't do any Ogg video

So ...

Its a start but i still need a Ogg Video



About writing my own transcoding library is this a bad idea


and please don't talk about the appearance because as i said before,

i will care when the time comes.

---

### Post by Tomosaur on 2008-04-21
Well Ogg is an open format, so really all it should take is some reading to understand the format and then some time to implement it in Java. It could still take a fair bit of work but it's certainly possible.

However, ogg is only a CONTAINER format. It's not an actual codec itself. You will still need to be able to decode the internal video and then encode it some other way. Theora is generally used with Ogg (So look up 'Ogg Theora'. 'Ogg Vorbis' is the audio format).

The best way is **always** to check whether someone has already done the thing you're thing to do. Google is your best friend when you're trying to develop something like this. I imagine someone has written a Java transcoding library for any number of formats. If it's GPLd (or some other liberal licence), then just use that, and modify to suit your needs.

Good luck!

---

### Post by Mr.Macdonald on 2008-04-21
When you say container format do you mean term as in their is no Ogg format just branched of formats that use Ogg as a cover term. Like a there IS no Linux operating system (to my knowledge) but there ARE Linux operating systems (plural) such as Ubuntu or Gentoo ...


> Well Ogg is an open format, so really all it should take is some reading to understand the format and then some time to implement it in Java.

does this mean that Mpeg4 would take longer than to get an Theora working.

could someone explain the procedure i would follow for the conversion (in detail, like fake code on how i would read through the file like below)

> Example, It this about write
public String decodeVorbis(String encoded) {
    String decoded = "";
    for (int i=0;i<encoded.getlength;i++) {
         decode += decodeVorbisChar(encoded.charAt(i));
    }
    return decoded;
}
Please return fake code in either Java, Python or C




And could someone explain what the RAW format is?????
   Is it what the music players read and play based upon?????

---

### Post by Tomosaur on 2008-04-22
OK well the RAW format, as far as I'm aware, is an image format. I've never heard of RAW videos before. But anyway, many digital cameras have the ability to save as RAW images - and this means that all of the information captured by the camera is retained. If you then open these RAW images on your computer, you have a greater degree of control over the image quality, colour temperatures etc. These files are larger than JPG files though, so you usually have to enable the RAW format on your camera. I'm not sure how digital video cameras would work here. I imagine theoretically that each frame could be saved as a RAW file, but the amount of space taken up by a minute long movie in this format would probably be far too big for the camera to be useful.

So really I'm not sure exactly why you need to know about the RAW format :S

As for Ogg - ogg is simply a container. All it does is wrap itself around some other media format. It's worth reading [this page](http://en.wikipedia.org/wiki/Ogg#Ogg_codecs) to get a basic overview of how Ogg works.

It's worth remembering that video files generally use this container model. .AVI is a container format, for example.

The general principle is that a video with sound is, at its most simple level, actually 2 data streams: One for the video, and one for the audio. A container format like Ogg or Avi allows these two data files to be packaged together. Ogg Theora is not a 'branch' of Ogg - it is a Theora encoded video file packaged up inside an Ogg container - kind of like how you can have some text file packaged up inside a .zip file.

When you convert video, many conversion programs also allow you to change the audio format aswell as the video format, and package the result up in some other container format.

Let's say you have a video file in Theora format. Where's the audio? You need some other file to contain the audio information. Then you can take the Theora file, and the audio file, and package them up together inside an Ogg container.

All I can say really is that you need to understand this stuff before you go and write a transcoding program :S Some of the info I gave above is just what I've picked up over time - I may well be wrong in some areas, so you're just going to have to read up on it yourself.

Things like .avi and .ogg aren't useful on their own. It's what is inside them that really counts, which is why you shouldn't be writing your own conversion stuff from scratch. There **is** software out there that does what you want. It may not be written in Java, but just go and research it, find the source code relevant to what you want to do, and convert that. There is absolutely no point reinventing this particular wheel, it's all been done a thousand times before.

I really, really recommend you just take another look at Iriverter. Strip out the non-free stuff, then get to work on filling in the gaps. Sometimes you just will not be able to implement some feature without running into potentially dangerous legal territory - that's generally the biggest problem with open-source. If you can't find a legal way around some non-free code, then just forget about it and move on.

---

### Post by Mr.Macdonald on 2008-04-22
I never planned to write one from stratch, even i in my ignorance am not that dumb. But i do plan to grab bits and pieces of code from several projects and compile into a nice Java libary.(If this is needed)

I think i get the whole Ogg thing(i wikied it). I realize that if i were to try and write code to parse an ogg video that i would end up killing my self. But i feel that i would be able to convert some WELL COMMENTED code.

One problem that i have thought about is that i need an intermediate for the conversion.
```
To Covert Mp3 to Ogg Vorbis

Mp3 --Decode---> Intermediate --Encode---> Ogg Vorbis

The Intermediate must stay constant if i am to put many libaries together.

```

If i were to decode a Mp3 with a libary what would it become???

---

### Post by Tomosaur on 2008-04-22
It doesn't really matter what you decode the mp3 file to. Any stream of bytes will do, or you can do it step by step, and re-encode each individual part of the mp3 file as you go along.

Nothing will ever use the intermediary stage except your own software, so you can just do whatever you like there really. I would recommend you just create a Java object called 'decoded' or something, with properties such as 'ID3_TAG_INFO, BIT_RATE, AUDIO_DATA' and so on. You fill these properties as you decode the mp3 file. Then, when encoding the file as something else, you just call each of these properties at the relevant time and do whatever you need to do to fit it to whatever audio format you're encoding to (Not all audio formats have the same features, so occasionally you will just need to drop some information).

For the actual audio data (IE - the stuff you hear when playing the song) - it can pretty much be anything. So long as YOU understand the data, and can convert it to other formats when you need to, there's no problem. The intermediary audio data is useless to anyone except you, so just do whatever really. I'm not personally aware if there's any 'standard' to be used here, so I can only imagine each developer just does it their own way. I would imagine the decoding library would sort this all out for you though, so just read the decoder documentation. I can't imagine it'll be anything more fancy than a big array of bytes.

---

### Post by Quikee on 2008-04-22
However you put it - in the end you will be reimplementing stuff unnecessary. As I already said once: I strongly recommend you look into GStreamer (with python as language, but as far as I saw there are also bindings for Java). 

The good thing about GStreamer is that it is widely used in linux and is gaining popularity on other platforms (Totem uses it for media playing, sound-juicer uses it to extract audio CD's, cheese uses it for web cam, jokosher uses it for sound editig, songbird for cross platform media playing, Firefox and webkit (gtk) will probably use it for html5 <video> and <audio> element)

How GStreamer work is that you construct a pipeline of compatible elements (that can be anything - source, target(sink), encoder, decoder, converter, effects). You can construct such a pipeline programatically and also in CLI using gst-launch command. 

A example of a CLI pipeline that converts ANY(gst supported) audio file into a ogg vorbis quality 5 audio file.

[PHP]gst-launch filesrc location="test.flac" ! decodebin ! audioconvert ! vorbisenc quality=0.5 ! oggmux ! filesink location="test.ogg"[/PHP]

Explanation:
The separator between elements is !

Every element has a source (input) and sink (output). 

The stream of the file goes from left to right and the elements transform this stream in their particular way. 

gst-inspect command is used to see what elements are available and also what are is and element able to do.

Elements:
filesrc is an element that reads from a file and streams into the next element. The "location" property defines the file that will be used - in the example I used test.flac flac file. 

decodebin is a special element that selects the right decoder depending on the format used as its source. Instead of decodebin, flacdec element could be used in this particular example (as the source file is a flac file). The decoder will decode the stream into an uncompressed (raw) form (for example wav) and stream it to the next element.

audioconvert element converts the source stream (now in some raw form) in such a way that it is compatible with its sink element - which is in our case vorbisenc.

vorbisenc takes the source and encodes it into vorbis audio stream with quality 5. The encoded vorbis audio stream will then be send to the sink.

oggmux takes the (compatible) source (vorbis audio stream in our case) and puts it into a ogg container. The stream after this element will be a valid ogg vorbis audio stream but it is yet to be decided what to do with it (it could be streamed over the network to another computer).

filesink takes the source stream and writes it into a file, defined with "location" property. 


Once you master this pipeline creating you can create and use it in a program. From the sheer boredom I yesterday created a not-so-nice gui for the upper example in python. 

The code:
[PHP]#!/usr/bin/python

import pygst
pygst.require("0.10")
import gst
import gtk
import os

class Main(object):
	def __init__(self):
		self.mainWindow = gtk.Window()
		self.vBox = gtk.VBox()

		self.input = gtk.FileChooserButton("Choose a file")

		self.output = gtk.FileChooserButton("Choose a folder")
		self.output.set_action(gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER)

		self.outputFileName = gtk.Entry()

		self.convertButton = gtk.Button("Convert")
		self.convertButton.connect('clicked', self.onConvertClicked)

		self.mainWindow.add(self.vBox)
		self.vBox.pack_start(self.input, True, True, 0)
		self.vBox.pack_start(self.output, True, True, 0)
		self.vBox.pack_start(self.outputFileName, True, True, 0)
		self.vBox.pack_start(self.convertButton, False, False, 0)

		self.preview = True

		self.mainWindow.show_all()

	def onConvertClicked(self, widget):
		self.pipeline = gst.Pipeline("Convert Pipeline")

		sourceFile = self.input.get_filename()
		print sourceFile
		self.filesrc = gst.element_factory_make("filesrc", "source")
		self.filesrc.set_property("location", sourceFile)
		self.pipeline.add(self.filesrc)


		self.decode = gst.element_factory_make("decodebin", "decode")
		self.decode.connect("new-decoded-pad", self.onDynamicPad)
		self.pipeline.add(self.decode)
		self.filesrc.link(self.decode)

		self.convert = gst.element_factory_make("audioconvert", "convert")
		self.pipeline.add(self.convert)

		destinationFile = os.path.join(self.output.get_filename(), self.outputFileName.get_text())
		print destinationFile

		self.vorbisenc = gst.element_factory_make("vorbisenc", "vorbisenc")
		self.pipeline.add(self.vorbisenc)
		self.convert.link(self.vorbisenc)

		self.oggmux = gst.element_factory_make("oggmux", "oggmux")
		self.pipeline.add(self.oggmux)
		self.vorbisenc.link(self.oggmux)
		
		self.sink = gst.element_factory_make("filesink", "sink")
		self.sink.set_property("location", destinationFile)
		self.pipeline.add(self.sink)
		self.oggmux.link(self.sink)

		bus = self.pipeline.get_bus()
		bus.add_signal_watch()
		bus.connect("message::eos", self.onEndOfStream)
		bus.connect("message::state-changed", self.onStateChanged)

		self.pipeline.set_state(gst.STATE_PLAYING)

	def onDynamicPad(self, dbin, pad, islast):
		pad.link(self.convert.get_pad("sink"))

	def onEndOfStream(self, bus, message):
		print "End of stream"

	def onStateChanged(self, bus, message):
		if  (message.src == self.pipeline):
			state = message.parse_state_changed()
			if state[1] == gst.STATE_PAUSED:
				print "Pause"
			elif state[1] == gst.STATE_PLAYING:
				print "Playing"

start=Main()
gtk.main()[/PHP]

In the first button select the source file. in the second target directory and in the third target file. It should start converting if you hit the convert button.

This example only covers converting of audio files. For the videos also to work the pipeline must be branched on some places (because a video usually also has a audio stream or multiple of those and sometimes also subtitles) and merged again into one stream at the end, bu there are a lot of examples that cover this already.

If this does not fit your requests then I don't know what will. ;)

---

### Post by Mr.Macdonald on 2008-04-23
I guess that i will use gstreamer to do the conversions but before i am certain could someone answer these questions

[LIST=1]
[*]Can Gstreamer convert Video, mp4 to .ogv to avi to ... ???
[*]How does java use gstreamer
[*]how would i tell someone that my package has a depends upon gstreamer, do i use a .deb package, if so then could you point me to a tutorial on making them
[*]Please point me to a gStreamer tutorial
[/LIST]

---

### Post by Quikee on 2008-04-23
> **Mr.Macdonald said:**
> I guess that i will use gstreamer to do the conversions but before i am certain could someone answer these questions

[LIST=1]
[*]Can Gstreamer convert Video, mp4 to .ogv to avi to ... ???
[*]How does java use gstreamer
[*]Is ```
gst-launch filesrc location="test.flac" ! decodebin ! audioconvert ! vorbisenc quality=0.5 ! oggmux ! filesink location="test.ogg"
``` how you convert a Flac to Ogg Vorbis
[*]how would i tell someone that my package has a depends upon gstreamer, do i use a .deb package, if so then could you point me to a tutorial on making them
[*]Please point me to a gStreamer tutorial
[/LIST]

[LIST=1]
[*] Yes. GStreamer supports many formats - generally every format that ffmpeg supports as it wraps ffmpeg + its many own plugins.
[*] Type "gstreamer java" in google and you will see. I don't have any experience with gstreamer in java (even though I know gstreamer and program in java for living) so i can't tell if the java bindings are complete or not. I would however recommend you use python over java if you know them both as you said.
[*] I don't really understand the question as I already said the example will convert a flac into ogg vorbis.. however generally such a pipeline will convert ANY supported file into ogg vorbis. The only thing you need to change is the input file.
This pipeline:
```
gst-launch filesrc location="test.mp3" ! decodebin ! audioconvert ! vorbisenc quality=0.5 ! oggmux ! filesink location="test.ogg"
``` would convert a mp3 into ogg for example.
[*] Worry about packaging once you have something to show. 
[*] Google is your friend again. [This one is a good start]("http://www.jonobacon.org/?p=750") and [this]("http://pygstdocs.berlios.de/pygst-tutorial/index.html") and [this for java]("http://code.google.com/p/gstreamer-java/wiki/Tutorials") and [this for a list of tutorials]("http://www.ocf.berkeley.edu/~brandon/wiki/index.php5?title=Main_Page").
[/LIST]

---

### Post by Mr.Macdonald on 2008-04-25
I have been reading about GStreamer-Java and i like it because:
[LIST]
[*]I am good at Java
[*]Actually feel like i have gotten somewhere
[/LIST]


I went through the tutorials in google code and got them to work. One problem i can't figure out how to transcode anything??? Does anyone know how.

Edit:

Actually i haven't accomplished anything. The documentation is sparse and the tutorials are rare and don't teach much.

---

### Post by Mr.Macdonald on 2008-04-26
I started messing around with python gstreamer and actually got stuff to work. i have converted audio and i would now like to know how to convert audio in gstreamer not in python just gstreamer command line.

but if you know how to do it in python that would be great.

---

### Post by Quikee on 2008-04-27
> **Mr.Macdonald said:**
> I started messing around with python gstreamer and actually got stuff to work. i have converted audio and i would now like to know how to convert audio in gstreamer not in python just gstreamer command line.

but if you know how to do it in python that would be great.

As I already said before:
```
gst-launch filesrc location="test.mp3" ! decodebin ! audioconvert ! vorbisenc quality=0.5 ! oggmux ! filesink location="test.ogg"
```

---

### Post by Mr.Macdonald on 2008-04-27
Sorry i had a typo


My last post should have read

I started messing around with python gstreamer and actually got stuff to work. i have converted audio and i would now like to know how to convert **_*Video*_** in gstreamer not in python just gstreamer command line.

but if you know how to do it in python that would be great.

---

### Post by Quikee on 2008-04-27
> **Mr.Macdonald said:**
> Sorry i had a typo


My last post should have read

I started messing around with python gstreamer and actually got stuff to work. i have converted audio and i would now like to know how to convert **_*Video*_** in gstreamer not in python just gstreamer command line.

but if you know how to do it in python that would be great.

Only video or both video+audio. For video only the story more or less the same:

```
gst-launch filesrc location="test.avi" ! decodebin ! ffmpegcolorspace ! theoraenc ! oggmux ! filesink location="test.ogg"
```

---

### Post by Mr.Macdonald on 2008-04-27
Man i can't get it together !!!

I want a **_video and audio_** conversion of Ogg Video (theora and vorbis) to Mpeg4

---

### Post by Quikee on 2008-04-28
> **Mr.Macdonald said:**
> Man i can't get it together !!!

I want a **_video and audio_** conversion of Ogg Video (theora and vorbis) to Mpeg4

This one is a little more tricky as you have to split up the pipeline after decodebin and combine again at muxing.

```
gst-launch-0.10 filesrc location="test.avi" ! decodebin name="decode" \
    decode. ! queue ! ffmpegcolorspace ! theoraenc quality=32 ! oggmux name=mux ! filesink location="test.ogg" \
    decode. ! queue ! audioconvert ! vorbisenc ! queue ! mux.
```

This one will decode the file and reencode it into theora for video and vorbis for audio and combine both strims in an ogg file. You can however change vorisenc with lame for mp3 encoding, theoraenc with xvidenc (with parameters) or x264enc (with parameters) for mpeg4 ASP/AVC coding and mux everything in avi (avimux) or matroska (matroskamux).

Just experiment with different settings.

---

### Post by mysoogal on 2009-05-09
i'm wondering why this isn't working :(

-------------------------------------------------------------------------------------
<?php
convertToFlv( "video.mpeg", "output.ogg" );

function convertToFlv( $input, $output ) {
   echo "Converting $input to $output<br />";
   $command = "gst-launch-0.10 filesrc location="$input" ! decodebin name="decode" \
    decode. ! queue ! ffmpegcolorspace ! theoraenc quality=32 ! oggmux name=mux ! filesink location="$output" \
    decode. ! queue ! audioconvert ! vorbisenc ! queue ! mux.";
   echo "$command<br />";
   shell_exec( $command );
   echo "Converted<br />";
}
?>
----------------------------------------------------------------------------------

if i use mencoders command, " mencoder $input -o $output -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame " it works, i tried to use avidemux2 command doesnt seem to work " avidemux --force-alt-h264 --load "video.mpeg" --save "out.ogm" --output-format ogm --quit "

any way to use gstreamer-tools with php ?

---

