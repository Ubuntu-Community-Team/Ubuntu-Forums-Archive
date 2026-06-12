---
title: "python/shell recognize that the given file path is audio/video"
date: 2009-11-02
forum: Programming Talk
---

### Post by giuspen on 2009-11-02
hi,
is there a way through python/shell to recognize a file as audio or video?
actually I check for the file extension into a list 
[PHP]AUDIO_TYPES = ['.mp3','.MP3','.mpa','.MPA','.flac','.FLAC','.ogg','.OGG','.wav','.WAV','.wma','.WMA']
VIDEO_TYPES = ['.avi','.AVI','.wmv','.WMV','.mpg','.MPG','.mpeg','.MPEG']
AUDIO_VIDEO_TYPES = set(AUDIO_TYPES.extend(VIDEO_TYPES))
if os.path.splitext(source_path)[1] in AUDIO_VIDEO_TYPES:
            source_path_list.append(source_path)[/PHP]
but this is not very reliable as the extensions are so many.
thanks in advance.

---

### Post by Arndt on 2009-11-02
> **giuspen said:**
> hi,
is there a way through python/shell to recognize a file as audio or video?
actually I check for the file extension into a list 
[PHP]AUDIO_TYPES = ['.mp3','.MP3','.mpa','.MPA','.flac','.FLAC','.ogg','.OGG','.wav','.WAV','.wma','.WMA']
VIDEO_TYPES = ['.avi','.AVI','.wmv','.WMV','.mpg','.MPG','.mpeg','.MPEG']
AUDIO_VIDEO_TYPES = set(AUDIO_TYPES.extend(VIDEO_TYPES))
if os.path.splitext(source_path)[1] in AUDIO_VIDEO_TYPES:
            source_path_list.append(source_path)[/PHP]
but this is not very reliable as the extensions are so many.
thanks in advance.

There is the 'file' command. I don't know if it recognizes all of those. Also, as I just discovered, some of these may consist of pure text, referring to other files. Then 'file' will just report them as text.

---

### Post by giuspen on 2009-11-02
> **Arndt said:**
> There is the 'file' command. I don't know if it recognizes all of those. Also, as I just discovered, some of these may consist of pure text, referring to other files. Then 'file' will just report them as text.

that's great thx

---

### Post by Arndt on 2009-11-02
> **giuspen said:**
> that's great thx

In python, by the way, you can use the 'magic' module. That may be better than calling the external 'file' program, but I expect they do the same thing.

---

### Post by ghostdog74 on 2009-11-02
the file command also makes use of magic files. check the man page for more.

---

### Post by giuspen on 2009-11-02
here's a script that works fine:
[PHP]filetype = subprocess.Popen('file -i "%s"' % source_path, shell=True, stdout=subprocess.PIPE).communicate()[0]
if "audio" in filetype: source_path_list.append(source_path)[/PHP]

---

