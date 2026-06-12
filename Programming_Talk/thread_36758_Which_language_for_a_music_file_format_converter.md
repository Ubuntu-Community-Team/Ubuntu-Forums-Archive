---
title: "Which language for a music file format converter"
date: 2005-05-24
forum: Programming Talk
---

### Post by Haegin on 2005-05-24
Which language should I learn (I don't know any but I want to do this) if I want to make a music file format converter (to convert mp3 to oggs to wmas originally). The only limitation is that it has to be able to make the gui using glade so it blends with gnome. If anybody can recommend an editor for the project as well please do.

All comments welcome and encouraged - I have done no research into this, I was just looking to see how I could get my assortment of wmas and mp3s into ogg format and I couldn't find a nice easy method. If anybody wants to help please say.

---

### Post by tread on 2005-05-24
Mostly, just a script will suffice. You can use mplayer in commandline mode and write the output to a file, and encode the wav file to ogg. There are tools to doing everything already, so as I said, a PERL or even bash script might suffice.

---

### Post by Haegin on 2005-05-24
I really don't like the command line - its fine for fixing small things but I have 1.2GB of music sorted into a nice folder system (~/Music/<artist name>/<song title>.mp3 (or .wma in a few cases).

I also want to learn the language as I go along and get used to glade and making things using the gnome interface as well.

---

### Post by LordHunter317 on 2005-05-24
A shell script is best for this.  Really.

Perl if your needs are more complicated than what bash can provide.  But they're really probably not.  If they are, your probably overthinking the problem.

However, converting lossy formats is a bad idea.  Really.  Sounds terrible.

---

### Post by alive on 2005-05-24
[QUOTE=LordHunter317]However, converting lossy formats is a bad idea.  Really.  Sounds terrible.[/QUOTE]
Can Free Software play WMA and MP3 files?

A bad sounding file may be better than one you can't listen to. The only real alternative is to convert the decoded WMAs and MP3s to a lossless format, like FLAC.

---

### Post by LordHunter317 on 2005-05-25
[QUOTE=alive]Can Free Software play WMA and MP3 files?[/quote]I seem to be able to play them just fine through a variety of software packages.  Whether those packages are free enough for you is  a personal decison.

> The only real alternative is to convert the decoded WMAs and MP3s to a lossless format, like FLAC.That doesn't save you the quality loss when if you shift-formats again.

Once you've gone lossy you're stuck with it essentially.

---

### Post by Haegin on 2005-05-25
How hard would it be to write a series of shell scripts to do the individual tasks and then use glade and another language to tie them all together?

---

### Post by lorap on 2005-05-25
well, C's the best of all.
it grants you the possibility to compress convert and encode files.
sent the packages of information over the network, work with the hardware, everything you just ever need.
moreover, ubuntu as well as unix and microsoft have been created with C...
have a nice day.
pavel

---

### Post by Haegin on 2005-05-25
thanks :)
does anybody know of a c tutorial (would c++ be better as its more modern?) I seem to remember something about them havnig inbuit glade and gtk support but where can I find basically a total beginners guide that can hopefully explain the basics of c++, how to work with it in glade and how to work with the gtk? As you can probably tell I don't have a clue about any of this and unfortunatly my school doesn't even offer a basic computing course - the teachers ask my help when teaching about websites, never mind trying to teach programming.

Thanks in advance - I'll go looking for something and will post if I find anything. If you have had similar problems before please can you point me in the right direction.

---

### Post by tread on 2005-05-25
Hmm, you could use perl-gtk or pygtk .. I think pygtk also has glade bindings. It might be worth a look.

---

### Post by alive on 2005-05-25
[QUOTE=LordHunter317]I seem to be able to play them just fine through a variety of software packages.  Whether those packages are free enough for you is  a personal decison.[/QUOTE]
I just want to answer this and explain why one would want files that can be played by free software.

When the software is not free, you may be fine with using it now, but you have no assurance that you can continue using it. What happens when you buy a new computer that can no longer run that software? A lot of documents created by word processors in the 90's are now lost, because programs that can read them are no longer available. Maybe you can count on a format's ubiquity and hope the patent will expire and then someone will write a free program. That might happen, but you're taking a chance.

For an example of this, see the forum for the 64-bit version of Ubuntu. People are complaining about having to configure 32-bit chroots and do a lot of setup in order to use Flash, Windows codecs, etc. -- it's only by a happy coincidence (AMD64's backward compatibility) that they can still use those formats at all.

So feel free to use whatever codec you're comfortable with, but maybe now you can understand why some of us don't.

> That doesn't save you the quality loss when if you shift-formats again.

Once you've gone lossy you're stuck with it essentially.
Hmm? I can shift lossless formats at any time -- FLAC to WAV, WAV to TTA. You're right that it's impossible to get them back to a lossy format without further quality loss.

I guess I don't understand the objection, unless it's that you have to use more disk space for the same quality, which is true.

---

### Post by LordHunter317 on 2005-05-25
[QUOTE=alive]I just want to answer this and explain why one would want files that can be played by free software.[/quote]They can be.  You obviously didn't read what I said above.

Your campaging for free **formats** which may be all well and good, but is irrelevant here.

> . What happens when you buy a new computer that can no longer run that software?I shift formats?  It's pretty rare that buying a new computer or even hardware changes cause inability to access data.  That's a pretty rare thing.

>  A lot of documents created by word processors in the 90's are now lost, because programs that can read them are no longer available.I think you're grossly overstating it here.  The program(s) that came out on top could read a multitude of word processor formats.  If you lost data, it's your own fault.

>  Maybe you can count on a format's ubiquity and hope the patent will expireMost formats aren't patented.

> For an example of this, see the forum for the 64-bit version of Ubuntu. People are complaining about having to configure 32-bit chroots and do a lot of setup in order to use Flash, Windows codecs, etc. -- it's only by a happy coincidence (AMD64's backward compatibility) that they can still use those formats at all.This is completely and totally incorrect.  The formats would be usable as soon as 64-bit codecs for them were developed.

Macintoshes use a completley different ISA as well yet people using them seem to be able to play all the media I can.  Your reasoning is spurious and incorrect.  

> Hmm? I can shift lossless formats at any time -- FLAC to WAV, WAV to TTA.If the data is lossy to begin with, shifting it to lossless doesn't gain you thing.  This is what I'm pointing out.

---

### Post by Haegin on 2005-05-26
I understand that once you shift to a lossy format you lose sound quality and that by shifting again you lose more but there is still a need to be able to shift between formats and this is what I am hoping to facilitate. There is a program (SoX) which I looked at but there doesn't seem to be a GUI and if I use a program regularly I want to be able to use a GUI. As I am also interested in learning to program then I decided I should attempt to write either an entire program of a SoX frontend. As I am learning the program will probably not be great and the code will be hideous but i just don't like writing tiny little "hello world" programs.

---

### Post by Haegin on 2005-05-26
Sorry about the double post but I have been reading more about SoX and I have a question.

Is it possible to write a GUI in glade then shove in shell script bits so when you click a button it takes the contents of fields, shoves them intop various places in a shell script command and then executes the command?

As SoX can convert loads of formats (check their website [http://sox.sourceforge.net/](http://sox.sourceforge.net/)) the program could then be used to convert various ways instead of just transcoding from one lossy format to another.

---

