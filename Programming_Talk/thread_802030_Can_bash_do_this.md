---
title: "Can bash do this?"
date: 2008-05-21
forum: Programming Talk
---

### Post by xzero1 on 2008-05-21
I am attempting to filter the output of ffmpeg with a ladspa dyson compression using a bash script. Here are my feeble attempts:

```
#!/bin/bash -x

#works but not feasable for streams!
ffmpeg -i "$1" -f wav snark
applyplugin snark ->"$2" dyson_compress_1403.so dysonCompress 0 1 .5 .99

#works (testing the syntax)!
exec ffmpeg -i "$1" -f wav ->"$2" & vlc -<"$2"

#not yet
exec ffmpeg -i "$1" -f wav ->"$2"& applyplugin -<"$2" foo2.wav dyson_compress_1403.so dysonCompress 0 1 .5 .99
```I would like to get the "not yet" working. Any ideas?
Thanks.

This seems promising:
```
mkfifo pipe
ffmpeg -i *.mp3 -f wav pipe & applyplugin pipe foo2.wav dyson_compress_1403.so dysonCompress 0 1 .5 .99
```The problem is with the pipe source since this *does* work:
```
mkfifo pipe
cat foo >pipe & applyplugin pipe foo2.wav dyson_compress_1403.so dysonCompress 0 1 .5 .99
```...but is not what I need.

---

### Post by geirha on 2008-05-21
I'm not familiar with the applyplugin command, but have you tried using bash pipes (|)?
```
ffmpeg -i *.mp3 -f wav - | applyplugin - foo2.wav dyson...
```

---

### Post by xzero1 on 2008-05-21
I tried this:
> ffmpeg -i *.mp3 -f wav - | applyplugin - foo2.wav dyson_compress_1403.so dysonCompress 0 1 .5 .99and get "Failed to open input file "-": No such file or directory"

For reference apply-plugin is part of a ladspa-sdk package and applies a ladspa filter to an input wave file.
```
applyplugin
Usage:    applyplugin [flags] <input Wave file> <output Wave file>
    <LADSPA plugin file name> <plugin label> <Control1> <Control2>...
    [<LADSPA plugin file name> <plugin label> <Control1> <Control2>...]...
Flags:    -s<seconds>    Add seconds of silence after end of input file.

To find out what control values are needed by a plugin, use the
"analyseplugin" program and check for control input ports.
```Ok, a little farther...
```
mkfifo pipe
ffmpeg -i *.mp3 -f wav \->pipe
```starts a pipe but seems to corrupt the stream a bit -- which is why applyplugin won't accept it. I capture the pipe with
```
cat <pipe >foo
```to inspect it. Also the created file is a bit smaller than it should be.

comparting the created file beginnings yields:

```
correct file using ffmpeg -i *.mp3 -f wav foo
52 49 46 46 00 00 00 00 57 41 56 45 66 6D 74 20 10 00
``````
bad file using ffmpeg -i *.mp3 -f wav \->foo
52 49 46 46 A4 CA F8 0A 57 41 56 45 66 6D 74 20 10 00
```Why won't it work?

Maybe ffmpeg is *not* as pipe friendly...

:)working but flaky code (decode, filter then play a decoded wav file):

```
mkfifo pipe1
lame --mp3input --decode  *.mp3 pipe1 & applyplugin pipe1 file1 dyson_compress_1403.so dysonCompress 0 1 .5 .99 & vlc file1
```...which implies that 
```
ffmpeg -i *.mp3 -f wav pipe
```should work:confused:
But I can't blame bash!:)

---

