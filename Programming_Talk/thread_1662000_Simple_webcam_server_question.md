---
title: "Simple webcam server question"
date: 2011-01-07
forum: Programming Talk
---

### Post by skullmunky on 2011-01-07
To be honest the question is not simple but I'm sure the answer is.

I need a simple webcam server that will serve a stream of jpegs over HTTP or socket requests.  I'm working on an Android app that uses live camera preview, which is currently supported in the Android SDK emulator, so for now the only way to do emulator testing is to capture the webcam stream and use a network connection to get it into the emulator.  I'm working from Tom Gibara's example code here:

[http://www.tomgibara.com/android/camera-source]("http://www.tomgibara.com/android/camera-source")

The client part is pretty straightforward, but it's the server that's giving me headaches.  He includes sample code for a simple Java server using JMF.  However, as we all know, JMF is pretty awful, and not surprisingly I can't get it to even install anymore.  I won't waste time with that here, maybe in another thread, but the upshot is I'm wondering if I can just use something else sane (like maybe a little bit of GStreamer and maybe Python) that would send images in a way that would still be understood by the Android client.  

Here's the relevant part of Tom Gibara's code on the Android client side, in [http://www.tomgibara.com/android/SocketCamera.java]("http://www.tomgibara.com/android/SocketCamera.java")

```

		Socket socket = null;
		try {
			socket = new Socket();
			socket.bind(null);
			socket.setSoTimeout(SOCKET_TIMEOUT);
			socket.connect(new InetSocketAddress(address, port), SOCKET_TIMEOUT);

			//obtain the bitmap
			InputStream in = socket.getInputStream();
			Bitmap bitmap = BitmapFactory.decodeStream(in);

```

Here's the relevant snippet from the server ([http://www.tomgibara.com/android/WebcamBroadcaster.java]("http://www.tomgibara.com/android/WebcamBroadcaster.java"))

```

Buffer buffer = c.grabFrame();
					BufferToImage btoi = new BufferToImage((VideoFormat)buffer.getFormat());
					BufferedImage image = (BufferedImage) btoi.createImage(buffer);
					
					if (image != null) {
						OutputStream out = socket.getOutputStream();
						if (RAW) {
							image.getWritableTile(0, 0).getDataElements(0, 0, width, height, data);
							image.releaseWritableTile(0, 0);
							DataOutputStream dout = new DataOutputStream(new BufferedOutputStream(out));
							for (int i = 0; i < data.length; i++) {
								dout.writeInt(data[i]);
							}
							dout.close();
						} else {
							ImageIO.write(image, "JPEG", out);
						}
					}

```

This is the part I want to redo in something else besides Java and JMF.  But I don't 100% know what it's doing.  Any suggestions?  I feel like GStreamer ought to be able to do this automagically.

---

### Post by shadylookin on 2011-01-07
take the picture on the android phone and send it as a post parameter to a web page would probably be the easiest way to do it if I'm understanding your problem correctly.

---

### Post by skullmunky on 2011-01-07
Actually the problem is the other way around - I'm working with the Android Emulator, not actual hardware, and the emulator doesn't support the camera yet.

Turns out the solution is actually quite easy, because GStreamer is wonderful.  

This pipe creates a server which streams the webcam as jpeg images.

```

gst-launch v4l2src ! jpegenc ! tcpserversink port=9889

```

I used the SocketCamera class from 
[here]("http://www.inter-fuser.com/2009/09/live-camera-preview-in-android-emulator.html"), which based on [http://www.tomgibara.com/android/camera-source]("http://www.tomgibara.com/android/camera-source")

And added it into the Camera Preview sample that comes with the Android API Demos pack.  voila, it works!  I love you, GStreamer.:guitar:

---

