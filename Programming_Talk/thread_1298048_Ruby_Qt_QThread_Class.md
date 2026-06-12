---
title: "Ruby Qt QThread Class???"
date: 2009-10-22
forum: Programming Talk
---

### Post by davertron on 2009-10-22
Does ruby qt not implement the QThread class?  If I try to subclass via something like:

```

require 'Qt'

class MyThread < QThread
  ...
end

```

I get "'const_missing': uninitialized constant Qt::QThread (NameError)", which sounds to me like it's not even implemented.  Is there another way I'm supposed to be doing this?  If I use regular ruby threads, how do I integrate this with Qt to make sure I'm not locking up the interface, etc.?

---

### Post by davertron on 2009-10-22
From #kde-ruby:

```

<rdale> ...ruby 1.8 threads aren't compatible with QThreads
<rdale> ruby 1.9 threads might be, but nothing has been done yet

```

So it sounds like you can't use QThreads in ruby qt.  Bummer!  Does anyone have suggestions about a similar way to accomplish not locking up the gui using regular ruby threads?

---

### Post by davertron on 2009-10-22
Just in case anyone was curious, you can achieve similar results using either QTimer or QProcess.  QTimer works great if you have something you want to fire off at a designated timeout, and QProcess works well if you have a one-time, long-running job you want to kick off and not lock up the UI.  

If anyone is curious for an example, just let me know.

---

