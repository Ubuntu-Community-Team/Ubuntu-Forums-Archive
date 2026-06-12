---
title: "Can anyone play this stream?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by cartisdm on 2008-07-31
Please check out **[this website]("http://dc101.com/main.html").  **Locate the "Listen Live" link on the right-hand side.  Is there any way to get this player to work?  According to the FAQs it says they don't support Linux right now.  You can play it in Windows using FireFox 3 with a certain plugin but that plugin isn't available for Linux either.

Can anyone find a way around this?  This is my favorite radio station and I hate booting to Windows to play it:(

---

### Post by CloudFX on 2008-07-31
Seems to work fine for me.

---

### Post by cartisdm on 2008-08-01
weird....anyone else?

---

### Post by tuxxy on 2008-08-01
You could try installing user agent switcher add on for firefox, this will allow you to change your browser identity to IE7, or even you could install windows on virtualbox or run ie4linux.

I cant try the link as im not in the US it says

---

### Post by sdowney717 on 2008-08-01
Tried it with opera in wine and got this message

Windows Media Player is a multimedia player by Microsoft. It comes bundled with most Windows computers, and upgrades are available as a download.

A new installation of Opera will find and copy the Windows Media plug-ins from C:Program FilesWindows Media Player to C:Program FilesOperaprogramplugins.

You can confirm that the plug-ins have been installed correctly by lookingfor the the following files: npds.zip, npdsplay.dll, and npwmsdrm.dll in Opera's plugins directory.

In case of doubt, copy these files to Opera's plugins directory, and restart Opera to make Opera aware of the new plug-in.

[http://www.liutilities.com/products/wintaskspro/processlibrary/npwmsdrm/](http://www.liutilities.com/products/wintaskspro/processlibrary/npwmsdrm/)
is one of those pesky drm related files


[http://www.streamingfestival.com/files/](http://www.streamingfestival.com/files/)
site says download and install and maybe it will work in wine

---

### Post by cartisdm on 2008-08-01
> **tuxxy said:**
> You could try installing user agent switcher add on for firefox, this will allow you to change your browser identity to IE7, or even you could install windows on virtualbox or run ie4linux.

I cant try the link as im not in the US it says


I tried the User Switching.  No such luck there, I think it has to do with either I'm missing a plugin OR it's trying to play the media in the wrong type of player:confused:

---

### Post by roquefilipe on 2008-08-01
can you find out what is the link to listen live?

---

### Post by cartisdm on 2008-08-01
> **roquefilipe said:**
> can you find out what is the link to listen live?

[http://dc101.com/cc-common/ondemand/player.html?world=st](http://dc101.com/cc-common/ondemand/player.html?world=st)

---

### Post by roquefilipe on 2008-08-01
that was not what I mentioned. I am talking about a direct link to the audio stream. 
I am not in the US, so can't really help.

---

### Post by cartisdm on 2008-08-01
> **roquefilipe said:**
> that was not what I mentioned. I am talking about a direct link to the audio stream. 
I am not in the US, so can't really help.

I don't quite know what you mean.  Where would I find that?

---

### Post by billgoldberg on 2008-08-01
I would test it, but it's US only.

did you install the 'w32codecs" package and the 'non-free-codecs' from the medibuntu repo?

Those should play the stream.

---

### Post by cartisdm on 2008-08-01
> **billgoldberg said:**
> 
did you install the 'w32codecs" package and the 'non-free-codecs' from the medibuntu repo?

Those should play the stream.

Yup I just installed all those and restarted FF, no luck.  The stream window opens, says Loading Content... then nothing happens.  It's only this website for me, I can play streams from other sites:(

---

### Post by sdowney717 on 2008-08-01
I would be surprised if anyone running linux can play that live since it is demanding the windows media player plugin.

Maybe you should contact them and ask them to please support linux.

---

### Post by dc101 on 2008-08-14
There are known issues with any OS other than Windows and any browser other than IE sadly. Also we don't even support Fx 3 at the moment for our streams. Fx 2 works fine as far as I know.

As for the Windows Media player issue we are moving to a new platform soon. When I'm not sure, as it is a massive undertaking (500+ radio stations). Anyway just thought I'd chime in as I noticed a number of hits coming from this forum. :)

---

