---
title: "Files Magic Numbers"
date: 2007-09-14
forum: Programming Talk
---

### Post by jreis on 2007-09-14
Hello guys:

Here goes my problem:

i have about 1TB of multimedia files (wmv, mov, wma, jpg, png, etc ..) that i need to organize. And i just don't whant to make it by hand ( go figures why :lolflag: ).

So i decided to create a script to print out all this information into a file in a organized way, with meta-data info, path , type of file , ... yahda yahda yahda

Using the magic number (command '**file -b myfile**') i could retrive the type of file, the problem goes when i retrive the information from a *wmv file and from a *wma file, the information retrived is the same - "Microsoft ASF".

I know theres a whay to diferenciate the both of them. but i can't figure it out. Can you help me?:confused:

My other problem is to retrive meta-data info from a file with the bash script? Is it possible?:confused:

I already google it, but i can't nothing that helps ...

Best Regards

jreis

---

### Post by aks44 on 2007-09-14
> **jreis said:**
> the information from a *wmv file and from a *wma file, the information retrived is the same - "Microsoft ASF".

I know theres a whay to diferenciate the both of them. but i can't figure it out.

Just a wild guess... differenciate them according to the file extension? :D There's very little chance that a video file would end in .wma or that an audio file would end in .wmv (unless you messed with the file extensions, which I guess you didn't)...


Sorry I can't help on the other problem. :(

---

### Post by jreis on 2007-09-14
> **aks44 said:**
> Just a wild guess... differenciate them according to the file extension? :D There's very little chance that a video file would end in .wma or that an audio file would end in .wmv (unless you messed with the file extensions, which I guess you didn't)...


Sorry I can't help on the other problem. :(

:popcorn: i thinked about that also, and it is probably the technique that i'm going to use, but i would like to use a more elegante whay to do this. yes i'm beeing stubborn i confess ](*,)

thanks any way

---

### Post by b1g4L on 2007-09-14
I agree with aks44....What better way to distigusih the type of file than by the file extension? I would order by file extension, then for further detail analyze meta data.

---

### Post by jreis on 2007-09-14
> **b1g4L said:**
> I agree with aks44....What better way to distigusih the type of file than by the file extension? I would order by file extension, then for further detail analyze meta data.

Yes, this is the most simple way i agree ... but i can't even get the meta-data from the files. Do you know how to do it?

---

### Post by dwblas on 2007-09-15
To get something simple like path and file name would require some knowledge of a programming language.  If you don't already know how to do this in some language, then a file's metadata is probably more than you want to bite off.  I think that Ogg Vorbis has "Ogg" as the first 3 characters in the file, but mp3 uses the last 128 if memory serves.  Here is link found with with a quick search on Google for wma metatags so you can see what might be involved - i.e. using the file endings is the only realistic solution. [http://blogs.msdn.com/tims/articles/100730.aspx](http://blogs.msdn.com/tims/articles/100730.aspx)

---

### Post by duff on 2007-09-15
You can use xdg-mime to get the mime type, which is based on magic number.
```
# xdg-mime query filetype 01-Cells.mp3 
audio/mpeg
```

---

### Post by jreis on 2007-09-17
I do agree with you dwblas, it is not going to productive spending my time (for now), trying to retrive metadata from a file, when i could use  other techniques - like file extension. Witch is by far much more easier.

Mean while, and just for the record, i found out that using ffmpeg i could retrive the audio or/and video codec and other data with out encoding the file, for that i just need to create an error, something like this:

[INDENT]*$ffmpeg -i myfile.wmv*[/INDENT]

it will return, something like this:

[B][INDENT]Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'myfile.wmv':
  Duration: 00:02:55.7, start: 2.000000, bitrate: 437 kb/s
  Stream #0.0: Video: msmpeg4v2, yuv420p, 320x239, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 64 kb/s
Must supply at least one output file[/INDENT][/B]

Thanks you all for the ideas.

ps- Duff, you can make the same efect using the **file** command:
[INDENT]$file -bi myfile.wmv[/INDENT]
will return:
[INDENT]**application/octet-stream**[/INDENT]

---

