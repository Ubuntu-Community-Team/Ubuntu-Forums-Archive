---
title: "Java Library for pulling album artwork from mp3"
date: 2013-02-05
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-02-05
Hi

I'm making an mp3 player in Java.

I need a small library to pull album artwork from the mp3 file.
Can you please suggest one

Regards

---

### Post by ofnuts on 2013-02-06
> **3v3rgr33n said:**
> Hi

I'm making an mp3 player in Java.

I need a small library to pull album artwork from the mp3 file.
Can you please suggest one

RegardsThe artwork in the MP3 is coded as an ID3v2 tag, so if you can display the rest you have a library that already supports that. Otherwise have a look at: [http://javamusictag.sourceforge.net/](http://javamusictag.sourceforge.net/)

---

### Post by Leuchten on 2013-02-06
[http://mvnrepository.com/artifact/org/jaudiotagger/2.0.3](http://mvnrepository.com/artifact/org/jaudiotagger/2.0.3)

It looks like this library can read/write tags on mp3s and other formats. It also has a mvn repo for your gradle/sbt/maven needs.

---

### Post by slickymaster on 2013-02-06
[Jaudiotagger]("http://www.jthink.net/jaudiotagger/") fully supports Mp3, Mp4 (Mp4 audio, M4a and M4p audio) Ogg Vorbis, Flac and Wma, there is limited support for Wav and Real formats.

---

### Post by 3v3rgr33n on 2013-02-06
> **ofnuts said:**
> The artwork in the MP3 is coded as an ID3v2 tag, so if you can display the rest you have a library that already supports that. Otherwise have a look at: [http://javamusictag.sourceforge.net/](http://javamusictag.sourceforge.net/)

I decided to use your suggestion, I tested the library by getting the album name and stuff --- it works!

You were sayin' the artwork is coded as an ID3v2 tag ryt?
I created an MP3File object:```
MP3File song = new MP3File(new File(someMedia.getPath()));
```The problem now is getting the actual picture, I've been looking at  [http://javamusictag.sourceforge.net/api/index.html](http://javamusictag.sourceforge.net/api/index.html) ,I don't know which method to use for getting the picture in the AbstractID3v2 class. Please help

---

### Post by 3v3rgr33n on 2013-02-07
Nvm. I ended up using [https://github.com/mpatric/mp3agic](https://github.com/mpatric/mp3agic)

It's easier to use it.

Here's a sample of my code.
```

Mp3File song = new Mp3File(someMedia.getPath());
                if (song.hasId3v2Tag()){
                    ID3v2 id3v2tag = song.getId3v2Tag();
                    byte[] imageData = id3v2tag.getAlbumImage();
                    if (imageData!=null){
                        System.out.println("debug:: imageData is not null");
                        BufferedImage img = ImageIO.read(new ByteArrayInputStream(imageData));
                        ImageIcon icon = new ImageIcon(img);
                        label.setIcon(icon);
                    }
                }

```

Thnks guys!

---

