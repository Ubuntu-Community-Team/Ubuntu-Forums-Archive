---
title: "Phonon and Ruby"
date: 2008-01-03
forum: Programming Talk
---

### Post by t1m on 2008-01-03
I recently did [this]("http://techbase.kde.org/Development/Tutorials/Qt4_Ruby_Tutorial") Qt/Ruby tutorial on the Kde TechBase.

I've been trying to make a multimedia player using ruby, and I would like to be using Phonon. It's been a bit confusing, and I haven't been able to get it to play any sound or anything (!).

When I try running this: (tranlated from [this wikipedia page]("http://en.wikipedia.org/wiki/Phonon_(KDE)"))
```

require 'korundum4'
require 'Qt4'

media = MediaObject.new(self)
Qt::Object.connect(media, SIGNAL('finished()'), SLOT('slotFinished()'))
media.setCurrentSource("/home/kde-devel/ruby/oops.mp3")
media.play()
```
I get:
```
ruby/test5.rb:4: uninitialized constant MediaObject (NameError)
```
What's wrong?

Any help would be much appreciated.

Thanks. :KS

---

### Post by nathandelane on 2008-01-04
The problem is that MediaObject must be part of some module that you're not including, like Qt.

Try:

media = Qt::MediaObject.new(self)

Nathan

---

### Post by nathandelane on 2008-01-04
Take a look at this page: [http://phonon.kde.org/cms/1022](http://phonon.kde.org/cms/1022).  It looks like I'm wrong too:

MediaObject::MediaObject.new(self) might work.

I think that because of this #include <Phonon/MediaObject> on this page [http://api.kde.org/4.0-api/kdelibs-apidocs/phonon/html/classPhonon_1_1MediaObject.html](http://api.kde.org/4.0-api/kdelibs-apidocs/phonon/html/classPhonon_1_1MediaObject.html)

Nathan

---

### Post by t1m on 2008-01-07
Thanks Nathan. Please forgive my slowness, I have been quite bussy.

I tried your ideas--still not working. Hmmmmm. I think I'll try looking in some more places........

---

### Post by frogface on 2009-08-24
My understanding is that to use the VideoPlayer class (I'm using Qt version 4.5.0) you would use the following code

```

require 'Qt'
require 'phonon'

Phonon::VideoPlayer

```

In other words, you would prefix with **Phonon::** to access the VideoPlayer class.

I would image that's the same for MediaObject. So perhaps Phonon::MediaObject.new(self) would work.

---

### Post by t1m on 2009-08-24
Thanks for the reply, but I have ended the project. (Note how old this thread is.) It may have been also that Phonon/KDE4 was still very new when I tried this.

But thank you anyway.

---

