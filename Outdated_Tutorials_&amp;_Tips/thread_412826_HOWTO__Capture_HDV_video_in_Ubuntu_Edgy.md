---
title: "HOWTO:  Capture HDV video in Ubuntu Edgy"
date: 2007-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by ArtInvent on 2007-04-18
HowTo: Capture HDV in Ubuntu Edgy

To advance the state of HDV video editing in Ubuntu and Gnu/Linux in general, a decent HowTo is needed to for capturing HDV footage from a camcorder, over IEEE1394 (firewire), and onto your hard drive. While editing in Cinelerra of HDV is still difficult, CPU intensive and buggy, at least for me so far, with footage at least viewable and ready to edit sitting on user's drives, maybe that will stir the pot a little and motivate developers to improve things. First things first.

Capture of HDV at this time is kludgy but quite possible. The only thing resembling a howto out there I found was on the braindead.nu blog, but it is somewhat cryptic and incomplete and had a basic error. The following is basically an amalgam of that and a couple of other sources. There may well be errors in the present howto, so feel free to point them out and I can correct the original post. I am not a video guru and only worked this out only yesterday so this may need some refining. "YMMV."


OVERVIEW OF CAPTURE USING TEST-MPEG2.  It seems that the simplest and most reliable method of capture is to use an obscure and basically undocumented script tool called test-mpeg2. This tool was not exactly intended for camera capture per se but seems to do the job. There is another method requiring compiling a special kernel which I tend to avoid doing in general. Lots of Googling lead me to test-mpeg2. This is not a package available in any of the repos, unfortunately. Instead, it is a script that is part of a developmental version of something called libiec61883 which a key linux package for managing firewire video connections. To the best of my understanding, the script was really written to test the ability of MythTV or other TV PVR recording software to record video from a cable box's firewire out port, hence the name. So basically the script just records an MPEG2 transport stream from the firewire connection to a file. HDV happens to be also an mpeg2 transport stream. Anyway, you may well find the libiec61883 package in the Ubuntu repos and already installed on your machine, but understand that test-mpeg2 is not included in the version available for Edgy. A system wide 'locate' confirmed that I did not have it. So this means one has to download a tar.gz of the correct version of libiec61883, and compile and (almost) install that version in order to just get the script.

PREPARATION.  First of course make sure your cam and firewire are actually configured and can at least capture ordinary DV. Previously I've captured and edited plain old DV footage in Kino. I've read that Kino and it's capture utility DVGrab are working on HDV capture, but at the moment they are stuck on regular DV. Also, it's clear from the lead developer that Kino will never be able edit HDV without a major rewrite which seems iffy. But Kino is great at capturing regular DV, so it makes a good test to see if your camera and firewire connection are working in the first place. My IEEE1394 port and camera were recognized fine and I could indeed capture DV but not HDV.

MAKE SURE YOU HAVE DEPENDENCY PACKAGES. You will need everything related to firewire generically know as ieee1394. If your firewire is working, you probably already have most of this. Also, if you have Kino installed and the restricted codecs for video files you probably have most of the dependencies. Obviously you will need every codec related to mpeg video and sound. NOTE - Make sure you also install the development package 'libraw1394.dev' in addition to the regular 'libraw1394'. 

GET AND COMPILE SOURCE OF LIBIEC61883.  This tedious step is necessary just to get a copy of test-mpeg2. Download the tar.gz available at libiec6183 project website linux1394.org - 

[http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz](http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz)

My compile went like this. I extracted the tarball to a folder in my home folder. Then I looked at the INSTALL instructions there. If you have all the required other packages, in a terminal you can cd to that directory and run './configure' and it should complete with no errors. (I ran ./configure but ran into a problem at the end. This was how I discovered the libraw1394.dev dependency. If you get any such dependency errors, you may be able to track down the package you are missing, install it, and re-run './configure'. This is what I did and it completed fine on the second try.)

Next run 'make' to compile the package. This should also complete with no errors.

'make-install' would ordinarily be the next step in the compile-and-install trifecta, but here it's not really necessary since all we are really after is the little test-mpeg2 script. (You should already have the Ubuntu-specific libiec61883 package installed and working so why mess with it.)

LOCATE THE SCRIPT.  You should now have the file 'test-mpeg2' in the 'examples' subfolder of the install folder. Examining the text of the script, there is a note that it is keyed to the folder it was compiled in. It won't work if it's moved to another directory. I don't know why it's written this way, but this seems to be why you have to compile the whole shebang yourself rather than just download a 'test-mpeg2' script from someplace. Sigh. If you want to run it more easily, you could create a symbolic link to it in the /usr/local/sbin directory.

CONNECT CAMERA TO FIREWIRE.  Next up is to connect your camera to the firewire port, remembering that most cameras require connection via AC rather than just battery. Then turn the camera on to play or to capture if you have that setting. Now run a command called 'plugreport' which will check the status of the firewire connection. The important part of the output should be 'Node O' at the top and also "iPCR[0] online=1" near the bottom.

RUN A PREP COMMAND.  Next it seems necessary to run a little command as below. What does it do? -n 0 specifies an id of your camera FireWire node from plugreport, and the rest tells adapter to enable the use of Point2Point (p2p) connection for the output (oPCR) instead of a broadcast connection (bcast_connection from plugreport). Whatever, here it is:

  plugctl -n 0 oPCR[0].n_p2p_connections=1

Note that it may be necessary to run this command every time you connect the camera or cycle it on-off.

CAPTURE.  We can finally attempt a capture. Your camera should be cued up to the point you wish to start capturing. Use the following command, prefacing as required with the directory location of the test-mpeg2 file.

  test-mpeg2 -r 0 > CaptureFile.m2t

It should return "starting to receive"  Capture has begun, and at this point you can press play on the camera control. To stop capturing hit CTR-C and press stop on the camera controls 

For me this put the captured file in my home directory. I believe m2t is a correct filetype for this which indicates an mpeg-2 transport stream, which is somewhat different from a straight mpeg or mpg file, though that may work as a filetype also. Some sources indicate that .ts is the filetype to use. 


PLAYBACK.  The m2t file will probably not play right or at all in MoviePlayer. I find it plays best in VLC Media Player. If you see interlace problems, choose a de-interlace setting. I find that 'linear' gives the smoothest results, and maybe try 'blend'. The files also played for me pretty well in gxine. Also in Firefox, as I have the correct video plugin, though it lacked de-interlacing. 

If your playback has some issues, it is likely that the capture is fine but you are having issues with the codec, the very high resolution of HD video, or hardware inadequacies. Note that playback of HD is very hardware intensive.  It's pretty essential to have a recent video card with hardware decoding, and to make sure it's enabled. Problems may look like excessive camera jitter when playing back the file on computer. Fast pans or other major imagery changes may look jerky as compared to viewing a straight camera connection to the TV. Slow pans and slight movement may still look wonderful, pure HD goodness. If you have fast newish hardware and still have issues, try adjusting the de-interacing and try different playback software. 

TRANSCODING.  This is a good time to marvel at how VLC is much more than just a media player. It has a transcoding function built into the player, even a pretty good 'wizard' for simplifying this function. You can transcode your footage into all kinds of other codecs such as mp4, divx, even wmv (ugh), and you can even extract the audio to an mp3 file or other codec. This is great for sharing your footage and posting to the web etc. Of course a more flexible alternative is the linux transcoding standby, ffmpeg. There is already a lot of documentation on ffmpeg.

OPENING THE CAPTURES IN CINELERRA.  Everyone should at least try to load and edit these with Cinelerra. It seems to work for some. Now you probably have the m2t file sitting in your home directory. Move it if you wish to a different directory. Start Cinelerra and load the file with File | Load Files . . . Cinelerra should indicate that it is creating a table of contents (toc) for the clip file. Then the clip should appear in the Resources window. If you try playing the file in a Viewer window, it may should play correctly. Scrubbing to the middle of the file may not work, but playback from the beginning works for me. (The composite window is another story.) Make sure that your project format is set up to either 1920x1080 or 1440x1080 (HDV native) and framerate of 29.97 and 1080i. Then go back to the clip, right click and hit "Match project size" and also "Match frame rate." (Some sources recommend that you build a toc for each file before opening in Cinelerra. There is a utility called mpeg3toc which I haven't figured out quite yet.) 

ACTUAL EDITING IN CINELERRA.  I have heard of others editing HDV in Cinelerra just fine, however on my setup editing these files in Cinelerra v2.1.0 hasn't worked. (There is some mention that previous versions of Cinelerra actually worked better with HDV.) I can drop the source files onto the edit timeline with audio fine. But the composite window in Cinelerra doesn't seem to want to play these well. The sound goes fine but the picture goes a frame or two and stops. Then the window stops responding and needs to be killed. Apparently this is a problem with Cinelerra's handling of the mpeg2 codec, a long GOP format that is much more difficult to edit because the compression scheme stretches out over a number of frames. However, lots of other NLE packages on other platforms now seem able to edit HDV just fine so this is clearly surmountable, and hopefully the good folks at Cinelerra are working on it.

Also note that Cinelerra requires a pretty hefty machine. I have a recent dual core Athon with 2GB of dual channel ram. I believe 2GB is what Cinelerra recommends.

A better solution for loading into Cinelerra might be to transcode the footage into a more editable codec. If one used a short GOP or uncompressed format, Cinelerra might not choke on it. Of course, the footage files will be huge. Another option is to resize the footage smaller and edit it as 'proxy', and when finished, perform the exact same steps on the original HD footage. There are some tutorials and howto's of this out there, but the process seems fairly laborious.

However, realize that we now have a workable system for capturing and at least loading the files into a powerful NLE. We're not that far off from a full working HDV workflow solution, folks.


Note that my Canon HV-20 can shoot 24p, but that in this mode the footage is nonetheless actually recorded onto tape as a 1080i60 stream. Don't really know the ins and outs of this at this point, but for our purposes here, I am NOT setting Cinelerra up as 1080p24. Didn't work for me, anyway, and I assume it's because the Canon has already converted to 1080i60. Any suggestions as to best settings for this would be welcome.

OTHER USES OF TEST-MPEG2. Apparently this script can also be used to send video the other way down firewire, from the computer to another device. This means that it may be possible to use it to write back video files to the camera. This could be wonderful as a way after edit and render to then output resulting files to back to tape as both archive and portable media, while we still wait for the HiDef disc format war to end. For this, the syntax would omit the > symbol, I believ, but again, I could find absolutely no official documentation on test-mpeg2. If someone wants to experiment or deconstruct the script file, that would be cool. It might also be cool if someone were able to re-write this script so that it is more portable and not compiler-keyed to one machine.

UBUNTU MINIONS GO FORTH. SHOOT HDV FOOTAGE. CAPTURE. REPORT BACK HERE.

---

### Post by ArtInvent on 2007-05-03
I have still not been able to edit HDV directly in Cinelerra. I believe that the processing power needed is just too great at this time. The problem really is just playing back HDV, especially more than one track of video at once, as when previewing transitions. I did find an outline of a 'proxy' method that supposedly works here:

 [U] [http://cvs.cinelerra.org/docs/wiki]("http://cvs.cinelerra.org/docs/wiki")
[/U]
It's a fairly brief description but I believe there are enough details given to work it out. Basically the idea is that from camera footage files you create matching half resolution 'proxy' files in avi format with the mjpeg codec. (This is a single frame compression codec that is easier to edit.) You edit in Cinelerra with these footage files. When finished, a python script is used to change the Cinelerra project file to reference the original HDV files. Then Cinelerra can open this project and do the final rendering in full high definition without problem. Another nice thing about this approach is that you could probably produce a standard definition DVD from the proxy files directly.

I am still experimenting with this workflow but it does look promising. 

I would also really like to change my 24p footage back into real 24p. The HDV format must be recorded onto tape in 1080i. The Canon HV-20 takes real 24 frame progressive from the sensor and does the 3:2 pull down and interlacing necessary before recording. But I have read that it is possible to do a reverse-pulldown and extract the original 24 frame from that. I have not found anything regarding Linux tools like ffmpeg and mencode with that function. Any help would be appreciated.

---

### Post by ArtInvent on 2007-06-15
After a clean re-install moving to Feisty from Edgy, I had a lot of trouble getting any firewire capture at all to work, even just regular DV on Kino. After a lot of searching and piecing together multiple sources to find the fix, I did get it working again. The raw1394 driver was not getting set up properly. I also had to re-install the LIBIEC61883 package manually of course to get test-mpeg2 capture working.

I've also been experimenting with various editing packages. I tried Cinelerra again and lo and behold, I can actually manage to some editing of the HDV footage. All is not rosy however. Playback is just not very satisfying as the frame rate is less than half of realtime. I set it to drop frames and at least that way the sound stays synced but I can hardly tell what is happening on screen. Not a very nice way to edit. Also, with this capture workflow there is no easy way to divide up the capture into scenes like most good capture utilities will do automatically. Combine that with playback that's awful and even just figuring basic scene in and out points is not much fun. Finally - rendering to a true usable hi def output file hardly works at all. There is no option to output an mpeg 2 transport stream or anything resembling the HDV file format. I haven't been able to render a satisfactory hi def format of any kind. Cinelerra seems to prefer the .mov Quicktime-for-Linux format using mpeg4 for video and audio compression, but no combination of that or any other codec and wrapper seems to be playable. If I set the project to 720p I got some output more usable but the aspect ratio or cropping seemed random and never quite right.

Aside from HD editing issues, Cinelerra is a mixed bag. You can have any number of audio and video tracks, and the 'camera' and 'projector' functions are pretty interesting for compositing these tracks together. But the titling is downright primitive. Weird. And, it does crash regularly. But it comes right back up if you've saved your project diligently. Sometimes the playback just won't stop. Often it shuts down just after rendering.

I've also gotten Jahshaka 2.0 going on Feisty and it looks kind of promising. However, it won't recognize the m2t files or load them. I can't set the project resolution any higher than DV format (720x480). I think that for regular DV and other lower resolution stuff it might be good. They seem to be quite ambitious about effects, animation, and titling, so in that respect it seems a little more ambitious than Cinelerra.

So some progress on the video editing front, but still not there yet for HDV.

---

### Post by eugenia_loli on 2007-07-18
I have added some info about the upcoming fixes on Dan Dennedy's applications about the HV20 here: [http://eugenia.blogsome.com/2007/07/15/social-europe-and-pc/](http://eugenia.blogsome.com/2007/07/15/social-europe-and-pc/)

---

