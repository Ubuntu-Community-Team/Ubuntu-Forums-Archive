---
title: "webcam access through java"
date: 2009-12-28
forum: Programming Talk
---

### Post by ivh90 on 2009-12-28
i am working on this project where i need to capture images from my laptop's webcam and do some image manipulation 
what is the easiest way to capture an image from my webcam and store it in lets say BufferedImage object for example

---

### Post by kahumba on 2009-12-28
I'd say the easy way is use flash instead, it has built-in support for webcams and a nice interface to them.
If you insist using Java, it's generally a bloody mess, google for "java webcam".

---

### Post by ve4cib on 2009-12-28
A slightly hacky-sounding work-around might be to call an external command-line tool to save an image from the camera to a directory somewhere, and then open the image just like you would any other file on your HD.  It's not as elegant as accessing the camera directly, but it might do the trick.

---

### Post by shadylookin on 2009-12-28
> **kahumba said:**
> I'd say the easy way is use flash instead, it has built-in support for webcams and a nice interface to them.
If you insist using Java, it's generally a bloody mess, google for "java webcam".

Pretty much this. I'm working on a project that uses webcams and getting Java media framework setup and working with it was such a hassle that I switched to flex.

---

### Post by ivh90 on 2009-12-28
thx for the replies 
it really annoys me how difficult somethings can be 

why cant be simple straight forward like:

BufferedImage img= webcam.captureImage();

i googled this a lot and i am sure others did before me but no luck 
i am really surprised how there isnt much documentation for this ! 

any advice ?

---

### Post by ve4cib on 2009-12-28
You *might* be able to pilfer and port some code from [fswebcam](http://www.firestorm.cx/fswebcam/).  It's not written in Java, but you might be able to sift through the code, see how they do things, and write your own Webcam class in Java.

---

### Post by Queue29 on 2009-12-29
I know the .NET platform has a nice built in webcam library, but I'm not sure about Mono, so I guess you could look into that. With Java you'd have to find a 3rd party library or write it yourself.

---

### Post by ivh90 on 2009-12-30
thx guys but i cant find any kind of documentation on this subject !

---

### Post by bender1234 on 2009-12-30
> **ivh90 said:**
> i am working on this project where i need to capture images from my laptop's webcam and do some image manipulation 
what is the easiest way to capture an image from my webcam and store it in lets say BufferedImage object for example

Hey you can use JMF, which sadly is just terrible. It only supports 640x480 modes, and well it stops there. JMF is also horrible to deploy, you need to run a tool to initialize your webcams each time you plug them in or changes ports(if you use usb). JMF can only handle one camera pr usb channel, and that tool takes forever to run. I don't quite recall but either JMF didn't work with applets, or if it did it was a nightmare to get working. Perhaps some of these limitations are windows only, I'm not sure. Suspect that JMF is using that pre directshow dinosaur, video for windows or what-it's-name.

I ended up making my own native .dll file(as I to often do with this language) using directshow, which in turn made me just cut the middleman and go c++ instead(No point using slow, resource hungry java when crossplatform functionality breaks anyways). There are probably some other standardized 3rd party libraries you can use for this(perhaps some gstreamer based thing?). Once you get that JMF cr** up and running, it's not that much code to make it's few features work. I can post some source code if you want to have a look at it. You're probably running ubuntu so directshow isn't of any interest to you I guess? :) I don't know it's linux counterpart gstreamer at all.

Had to add that it's a couple of years since I had a look at JMF. It might have had some improvements, but I doubt it. Sun uses forever to add functionality.

merry x-mas!
Bender

---

### Post by scphan on 2010-01-06
To set up the env., move the *.so files to the /usr/lib and invoke "ldconfig" and then include the *.jar files in your runtime.

I used a Logitech Orbit webcam.

Go through the tutorial at ibm's developer/newto website for JMF which shows you how to use Manager and MediaLocator's (which you'll need).
[http://www.ibm.com/developerworks/java/newto/](http://www.ibm.com/developerworks/java/newto/)
[http://www.ibm.com/developerworks/java/newto/](http://www.ibm.com/developerworks/java/newto/)
[http://www.ibm.com/developerworks/java/edu/j-dw-javajmf-i.html](http://www.ibm.com/developerworks/java/edu/j-dw-javajmf-i.html)
You need to sign up before retrieving tutorials but it's very quick and they pretty interesting articles that are user-friendly.

You then need to create a player of the webcam (I used Manager.createRealizedPlayer( MediaLocator loc )) and pass in the MediaLocator object created from your URL (in my case it was "v4l://0", run JMFRegistry and detect the webcam from there to get your "locator" string).

Then start the player.

Then wait/sleep for about 2.5 sec's for the webcam to start up.

Then start drawing ;-).

Here's my code for retrieving the image on the go:
public Image getCurrentImage() throws RuntimeException
{
	final FrameGrabbingControl frameGrabber = (FrameGrabbingControl) this.camPlayer.getControl( FrameGrabbingControl.class.getName() );
	final Buffer buf = frameGrabber.grabFrame();
	final Image img = (new BufferToImage((VideoFormat) buf.getFormat()).createImage( buf ));

	if ( img==null )
		throw new RuntimeException( "null image retrieved from buffer" );

	return img;
}

Take note that I used Swing to redraw the images but AWT is faster.
Also you can go ahead and cast the returned Image to a BufferedImage and use it to do image processing (either with Java2D's library or with JAI ;-)).

Sun's JMF was going good when Intel and Silicon were both partnering with Sun to develop it, that was until Microsoft budged Intel out of the group ;-( back when 1.0 came out. Eh.

---

### Post by patrickballeux on 2010-02-21
> **ivh90 said:**
> i am working on this project where i need to capture images from my laptop's webcam and do some image manipulation 
what is the easiest way to capture an image from my webcam and store it in lets say BufferedImage object for example

See my project WebcamStudio on Sourceforge.  I am using GStreamer-Java.  No need for JMF.

In the source code, look for the class VideoSourceV4L


Using gstreamer, it is really easy to do.

---

