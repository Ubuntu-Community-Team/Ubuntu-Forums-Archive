---
title: "Java + Jmf + Ubuntu"
date: 2008-03-05
forum: Programming Talk
---

### Post by fcsa on 2008-03-05
hello ..

i have a problem.. i already search on forum a lot..but i couldnt find the solution or something exactly like that..so..i'd like to ask some help over here..

i already installed jdk..jmf.. jmfregistry detects my webcam without problems.. i can use jmstudio to record some video and at kopete i could use my webcam..

the great problem is... i have a JAVA program that needs to connect to my webcam and take a picture.. but everytime i run my application i never can detect any device.. 
i tryed the device path like.. v4l://0... v4l2://0.. and a lot of others..
if someone is not familiar with code.. 
thats it:
this.mediaLocator = new MediaLocator("v4l://0");

somebody can help me?

---

### Post by fcsa on 2008-03-06
any help?
im desperate..:(

---

### Post by naugiedoggie on 2008-03-07
> **fcsa said:**
> hello ..

i have a problem.. i already search on forum a lot..but i couldnt find the solution or something exactly like that..so..i'd like to ask some help over here..

i already installed jdk..jmf.. jmfregistry detects my webcam without problems.. i can use jmstudio to record some video and at kopete i could use my webcam..

the great problem is... i have a JAVA program that needs to connect to my webcam and take a picture.. but everytime i run my application i never can detect any device.. 
i tryed the device path like.. v4l://0... v4l2://0.. and a lot of others..
if someone is not familiar with code.. 
thats it:
this.mediaLocator = new MediaLocator("v4l://0");

somebody can help me?

Hello,

Have you done the tutorials and sample applications at the Sun site?  It sounds like you are not really sure about how the JMF works.  

Also, how are you writing the code?  I see that there is a JMF plugin template for [NetBeans]("http://www.netbeans.org").  It's for a movie player, but it may provide you with the code pattern you need to see how to modify it for your own purposes.

Thanks.

mp

---

### Post by fcsa on 2008-03-07
hello there.. 
first..thanks for ur reply..

now.. i saw the samples and tutorials from the sun.. and i guess i followed everything like they said..
its true i could fully comprehend how jmf works.. but i guess for this case i could understand...

here is my code to start a mediaLocator and a player..

CaptureDeviceInfo di = CaptureDeviceManager.getDevice(Configuracoes.getInstacia().getCaminhoDriverCamera());
Vector device = CaptureDeviceManager.getDeviceList(new VideoFormat(VideoFormat.YUV));			
			System.out.println("devices::"+device.size());
			Iterator ite = device.iterator();
			while(ite.hasNext()){
				di = (CaptureDeviceInfo) ite.next();				
				System.out.println("device name:"+di.getName());
			}
			this.mediaLocator = new MediaLocator("v4l://0");		
			Manager.setHint(Manager.LIGHTWEIGHT_RENDERER, new Boolean(true)); 
		player = Manager.createRealizedPlayer(mediaLocator);
			player.start();			
			if ((this.componentVideo = player.getVisualComponent()) != null) {				
				getVideoPanel().add(componentVideo, BorderLayout.CENTER);
				getVideoPanel().setSize(componentVideo.getSize());				
			}
			else {
				labelMessageCam.setText("No Images.");
				getVideoPanel().add(labelMessageCam,BorderLayout.CENTER);
			}

i hope it could be helpful.
thanks

---

### Post by fcsa on 2008-03-07
i finally got this to work...
i had to copy all *.so files from jmf/lib to /usr/lib..
after that.. i did.. "ldconfig"..
after that.. i could detect my devices from my java application..

i hope its could help someone else.. :)

see u

---

### Post by xlinuks on 2008-03-07
From my experience Java is a great language and technology, especially on the servers with heavy loads. But when you enter the Media Realm, IMHO Java should be your choice unless you don't have another. Last time I tried using it (about half a year ago) the JMF libraries were very buggy and moving slowly forward, they didn't even have support for MP3 because of legal issues, and a few other issues that when all put together let you ask yourself if you really wanna do it in Java. OTOH things might have changed since then (?)
Just a thought, flash 9 having roughly a 2.5MB installer has built in support for webcams, mp3 and video, even for H.264!! Java having a 16MB installer only supports aif and wav files (doesn't even support all of types of .wav) formats and no video.
Just my 0.02$

---

### Post by afarkas on 2009-01-30
fcsa: can I have a great question? Can you tell me what camera do you use?
I tried two camera under ubuntu. One is not v4l camera so it didn't work, the second is a genius, I don't know the type, it's working under ubuntu, I tried it with cheese, but it doesn't work with jmstudio, I can only see flashing horizontal lines. If you could tell me what camera you are using, it would be a great help for me, or if you or anyone could help me.
thx.

---

### Post by scotty64 on 2009-02-28
> **afarkas said:**
> fcsa: can I have a great question? Can you tell me what camera do you use?
I tried two camera under ubuntu. One is not v4l camera so it didn't work, the second is a genius, I don't know the type, it's working under ubuntu, I tried it with cheese, but it doesn't work with jmstudio, I can only see flashing horizontal lines. If you could tell me what camera you are using, it would be a great help for me, or if you or anyone could help me.
thx.

Try webcamstudio: [http://webcamstudio.wiki.sourceforge.net](http://webcamstudio.wiki.sourceforge.net)
It's a great program. You can connect multiple sources plus effects to one virtual webcam that is represented as a vloopback-device. It helped me to get my Philips SPC900NC webcam to work with the terrible camera implementation on Flash Player 10.

---

### Post by Karthick.Mohanraj on 2009-08-08
I have similar kind of problem.
My wecam got detected by JMFINIT and JMFREGISTRY
but when I tried to capture the video using JMSTUDIO, noting is diaplayed.
can somebody help me on this please??

---

### Post by Peter_Rabbit on 2009-11-25
> **fcsa said:**
> i finally got this to work...
i had to copy all *.so files from jmf/lib to /usr/lib..
after that.. i did.. "ldconfig"..
after that.. i could detect my devices from my java application..

i hope its could help someone else.. :)

see u

This didn't work for me, but it is encouraging that someone got jmf to work with ubuntu - has anyone else got it to work?

P

---

### Post by scphan on 2010-01-06
It worked for me ;-), moving all the *.so files to the /usr/lib and then invoking "ldconfig". My app all of a sudden started working!

I'm using Sun jdk1.6.0_16 on Ubuntu Jaunty.

Just to let you before I did that I kept getting Error messages that the player for webcam couldn't be created (used Manager.createRealizedPlayer()).

---

### Post by gaditano on 2012-04-24
I have a problem similar to that reported.
I have a camera connected via a easycap.
I execute gstreamer-properties on UBUNTU 11.10. I can see the camera and it shows the image in the test process.
Now, when I run jminit, there is an error that it shows like:
Name = v4l: $#S (strange symbols)
Obviously when I run the jmregistry not find the camera.
Appreciate it if someone can help me.
Thanks
 
Javier

---

### Post by scphan on 2012-04-24
> **gaditano said:**
> I have a problem similar to that reported.
I have a camera connected via a easycap.
I execute gstreamer-properties on UBUNTU 11.10. I can see the camera and it shows the image in the test process.
Now, when I run jminit, there is an error that it shows like:
Name = v4l: $#S (strange symbols)
Obviously when I run the jmregistry not find the camera.
Appreciate it if someone can help me.
Thanks
 
Javier
Can you copy and paste the whole error message? Don't think I've run into an error like that before.  Also paste the output for 'v4l-info'.

---

### Post by gaditano on 2012-04-25
Hi:

I found the solution. It is to preload the backward compatibility library for v4l to get it to work.

**LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/lib/JMF-2.1.1e/bin/jmfregistry**

Now I have a new issue. I think, it's related to jmf.properties.

It's important to run gstreamer-properties to set the easycap camera as priority.

I ran the jmfresigtry and I can see the camera

But when I ran my application:

```
      listaDispositivos = CaptureDeviceManager.getDeviceList(null);

      Iterator it = listaDispositivos.iterator();

      String nombre="";
      Format[] cfmts;
      while (it.hasNext())
      {
          CaptureDeviceInfo cdi = (CaptureDeviceInfo)it.next();
          nombre=cdi.getName(); //Obtiene el nombre del Dispositivo Detectado

          System.out.println("Nombre: "+nombre);

```


and it cannot see the video. I can see only the sound card.


I have another issue with JMSTUDIO.

When I run it:

**LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so sudo /usr/lib/JMF-2.1.1e/bin/jmstudio **

I receive the following excpetion:

```
Exception in thread "Thread-2" java.lang.NullPointerException
	at com.sun.media.protocol.v4l.V4LSourceStream.read(V4LSourceStream.java:259)
	at com.sun.media.parser.RawBufferParser$FrameTrack.transferData(RawBufferParser.java:725)
	at com.sun.media.protocol.v4l.V4LSourceStream.run(V4LSourceStream.java:338)
	at java.lang.Thread.run(Thread.java:662)
Internal error: doBuildGraph
  Unable to handle format: null
```


Now I will prepare v4l-info

Thanks!!!

---

