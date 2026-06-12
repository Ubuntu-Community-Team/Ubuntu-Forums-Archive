---
title: "Howto:  Batch Encode and Upload Videos to an Ipod using thinliquidfilm"
date: 2007-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dumbkiwi on 2007-01-18
**What is thin liquid film**

thin liquid film (TLF) is an application which allows linux users to quickly and easily convert video files into a format suitable for playing on the video capable ipods.  TLF uses the ffmpeg engine to do the encoding. It is written in pyqt, so it should work with a default kde installation, and is very easy to install.  If you are not using kubuntu, you will need to install the kubuntu-desktop package (unless someone else has a suggestion as to a better way of getting the pyqt package installed).

**howto install thin liquid film ...**

requirements ...

thin liquid film (TLF) requires:

    * pyqt - these are the python bindings for qt. These are now part of the standard kde modules, so if you've got kde, then you should have pyqt (see above regarding installing the kubuntu-desktop package if you don't have kde);

    * ffmpeg - this is a very standard linux package, and should be part of your distributions standard install, or at least in their repositories. However, you need to make sure that ffmpeg has been compiled with support for xvid and h264 codecs. See below for details on how to tell;

    * libgpod python bindings - this is not essential for the enocoding part of the application. However, without it, you will not be able to upload to your ipod. These python bindings are part of the libgpod package, which is a dependency of both gtkpod and amarok. However, ubuntu keeps the bindings in a second package, so you will need to install the python-gpod package;

    * a 5G ipod - although, you can use TLF without an ipod, I'm not sure why you would bother :), unless you want to convert your home videos for your friends :);

**the trouble with ffmpeg ...**

As I said above, you need a version of ffmpeg that has been compiled with support for the mpeg4 and h264 codecs. You can work this out with the following command:

```
ffmpeg -formats | grep h264
```
and
```
ffmpeg -formats | grep xvid
```

If they are supported, you will get output that looks like:

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Jan 18 2007 19:00:22, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
 DE h264            raw H264 video format
 DEV DT h264
```
and
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Jan 18 2007 19:00:22, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
  EV    xvid

```
I know that the standard *ubuntu ffmpeg package does not include support for the required codecs. There is a very good tutorial on compiling ffmpeg for *ubuntu edgy at [http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/).

You will need to download TLF from [http://thinliquidfilm.org](http://thinliquidfilm.org). You will then need to untar the file. You can do that with this command:
```
tar -jxpf tlf-version.tar.bz2
```
You'll need to replace version with the correct version number of the tarball you downloaded. Then change to the resulting directory. TLF comes with an installation script called install.py so you'll need to run the script like this:

```
sudo ./install.py
Password:
```

The install script does not require any input. It installs all the files necessary for TLF to /usr/local/thinliquidfilm. It will create an executable file called thinliquidfilm in /usr/local/bin, which should be in your path, and will install a TLF servicemenu entry for konqueror. You will have to manually add a menu entry to TLF in kde or gnome.

**Opening video files in thinliquidfilm ...**

You can add video files to TLF in any one of three ways:

    * command line - when you launch TLF, you can add any number of files for encoding as command line arguments, for example:
```
thinliquidfilm /full/pathto/file1.avi relative/pathto/file2.avi
```

    * Konqueror - you can right click on any supported video file in konqueror, and there should be an option to add those files to TLF for encoding under the Actions submenu.

    * "Add Files" button - once TLF is open, click on the Add Files button to open a file dialog, and add one or more files to either the encoding or transfer list in the usual way.  TLF will then add the files to the file list in the encoding or transfer file list (depending on which is showing), together with some information about the video - like filetype, number of frames, aspect ratio and bitrate.

**settings for encoding video files ...**

[IMG]http://thinliquidfilm.org/images/screenie.png[/IMG]

You set the output parameters for encoding videos in the Output Settings tab.

    * Passes - this sets the number of passes the encoder will use to encode the video file. Two pass encoding should produce a better quality video file, but has to pass over the file twice, so will take longer.

    * Size/Quality - choose whether you want to create a video that is suitable for the Ipod only, or for both the Ipod and TV. The ipod supports two video widths: 320 and 640. The 320 width will look great on an ipod and will produce a small file and will encode faster, but if you want to watch it on TV, it will look crappy and pixelated. So if you want to watch the video on TV as well as the ipod, use the Ipod and TV option. The aspect ratio of your source video will be preserved.

    * Video Codec - set which of the ipod supported video codecs you want to use. h264 should theoretically give you better quality at lower bitrates and therefore produce a smaller file, but will take longer to encode.

    * Audio Quality - high quality will encode the audio at 160 kb/s (the maximum permitted on the ipod). Low quality encodes at 128kb/s, which provides acceptable quality, but a smaller file size.

    * Destination - set the destination path for the encoded video file. You can either enter the path, or click on the browse button to find the right directory.

    * Save As Default Settings - press this button to save the settings currently displayed in the settings panel, so that TLF opens with these settings as the defaults the next time.

You can preview what the encoded video will look like using the preview button.

**upload information**

[IMG]http://thinliquidfilm.org/images/screenie2.png[/IMG]
You set the file information for uploading to your ipod in the Output Settings tab.

    * Title - set the name for the file that will appear on your ipod.

    * Artist, Album, Genre - you can set these if you want, although I'm not sure what use they really are.

    * Playlist - this allows you to set an existing playlist, or a new one. Enter the name of an existing video playlist, or a new one altogether. When uploaded, the video files will appear in the specified playlist.

    * Ipod Mountpoint - this is where your ipod is, or will be mounted. You an save this as a permanent setting by clicking on the Save Mountpoint button.

**batch settings**

You can change the settings for multiple files by selecting the files you want to change, and then making the changes in the settings panel. The settings displayed in the settings panel will then be applied to all of the highlighted files.

**help/support**

If you want help or support for thinliquidfilm, post on the forums at [http://thinliquidfilm.org/forum](http://thinliquidfilm.org/forum)

---

### Post by ephman on 2007-01-22
i seem to get this error when i try to install.  any ideas?


ephman@wintermute:~/thinliquidfilm$ sudo ./install.py
Traceback (most recent call last):
  File "./install.py", line 14, in ?
    ind = data.index('bin')
ValueError: list.index(x): x not in list

thanks,

ephman

---

### Post by dumbkiwi on 2007-01-22
Do you you have konqueror installed?

---

### Post by ephman on 2007-01-23
no.  thanks for the tip.

ephman

---

### Post by 8bit on 2007-07-15
For some reason I can no longer convert using the H264 codec but xvid works. This is only a minor problem for me.

The main issue I have is that when I encode a file and play it using Linux, it plays and sounds fine but when I upload it to my video iPod I have no sound.

Also, TLF won't let me select a VOB file.

Any suggestions?

---

