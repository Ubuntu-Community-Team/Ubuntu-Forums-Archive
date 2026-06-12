---
title: "Music ripping"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by duquer on 2008-09-29
when i try to rip music from a cd  to store in my library it say the encoder is not found. also when i download from  a cd the media listing is also not found. when i say media listing i mean the name of the songs and the name of the cd. what do i need to download to do this  correctly

---

### Post by snova on 2008-09-29
Chances are you're trying to rip them as MP3 files. MP3 is legally encumbered.

Your options are either to install some rather unsavory codecs, or to use another format altogether without any restrictions. Ogg Vorbis is a prime example of this.

Personally, I find Ogg Vorbis to be satisfactory- it compresses well, has tag support, and the sound quality seems good (but what do I know about that?).

See this link for information about getting the MP3 codecs:

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

And this one for using a different format:

[https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen](https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen)

---

### Post by friendofpugs on 2008-09-29
I recommend going the codecs route, so that way you can still use your iPod for the mp3s, instead of Ogg (I dunno if iPod supports Ogg). Follow this and you'll be happy: [http://www.stchman.com/codecs.html]("http://www.stchman.com/codecs.html")
Good luck!

---

### Post by cariboo on 2008-09-29
Why not just install the ubuntu-restricted-extra meta-package and be done with it. It is available  in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and od course the command line. Make sure all the repositories are selected in System-->Administration--Software Sources. For ease of explanation to install the meta-package open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install most of the codecs you need except for the dvd decrypter which you will find if you search the forum using Google instead of the forum search engine as the search function doesn't work very well. Search for ubuntu+libdvdcss and you should find more than enough suggestiions on playing dvd's.

Jim

---

