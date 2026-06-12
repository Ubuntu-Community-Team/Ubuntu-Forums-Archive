---
title: "Tkinter Mainloop vs My Socket Loop"
date: 2008-04-30
forum: Programming Talk
---

### Post by era86 on 2008-04-30
I wrote some code for a client (using sockets of course) to stream an mp3 file from a server.  The loop is pretty basic:

connect to server
loop:
    get 512 bytes at a time
    play the data in speakers
close the connection

Now I want to use Tkinter to make a GUI for my streamer.  The problem is, I can't have the Tk.mainloop() running at the same time as my stream loop.  Obviously, it will do one or the other first.  I would like them to work at the same time.

Would threading solve this?

Any input helps.  Thanks.

---

### Post by LaRoza on 2008-04-30
> **era86 said:**
> I wrote some code for a client (using sockets of course) to stream an mp3 file from a server.  The loop is pretty basic:

connect to server
loop:
    get 512 bytes at a time
    play the data in speakers
close the connection

Now I want to use Tkinter to make a GUI for my streamer.  The problem is, I can't have the Tk.mainloop() running at the same time as my stream loop.  Obviously, it will do one or the other first.  I would like them to work at the same time.

Would threading solve this?

Any input helps.  Thanks.

Yes, threading is the answer.

---

### Post by era86 on 2008-05-01
I have tried the threading, but then there is no way to tie the GUI to the runnning process of the stream.  Does anybody know any other ways to work around this?

---

