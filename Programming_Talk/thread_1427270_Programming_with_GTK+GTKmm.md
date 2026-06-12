---
title: "Programming with GTK+/GTKmm"
date: 2010-03-11
forum: Programming Talk
---

### Post by jmichel on 2010-03-11
I'm writing an application in C++ with GTKmm and I have some problems with file inputs. It seems difficult to find some help with GTK+/GTKmm. Is there any good forum or website where I could find some help?

And if someone could help with me problem, I trying to read from a file and I use a Gio::Cancellable to stop the operation. But even after I call cancel, the read operation never exits and my reading thread is blocked. See code below:

-------------------------------------------------------

```
main() {

  Glib::RefPtr<Gio::FileInputStream> fileinputstream;
  Glib::RefPtr<Gio::Cancellable> fileinputcancellable;

  //Create cancel object for file reads
  fileinputcancellable = Gio::Cancellable::create();

  //Open input file
    Glib::RefPtr<Gio::File> file = Gio::File::create_for_commandline_arg(file_opt);
    fileinputstream = file->read();

  if (main_win) {
    Glib::Thread* thread;
    thread = Glib::Thread::create(sigc::ptr_fun(&file_thread), true);
    //Start main loop
    Gtk::Main::instance()->run(*main_win);
    //Cancel last file read operation
    fileinputcancellable->cancel();
    //Wait end of file read
    thread->join();
  }
}

//Thread to read file
static void file_thread() {
  while (!quit_flag) {
    try {
      size = fileinputstream->read(buffer, buffer_size, fileinputcancellable);
    } catch (const Gio::Error &err) {
      std::cerr << err.what() << std::endl;
    }
    Glib::Thread::self()->yield();
  }
}
```

-------------------------------------------------------

---

### Post by Compyx on 2010-03-11
> **jmichel said:**
> 

```

  while (!quit_flag) {

```


I'm not a C++ programmer, but quit_flag looks like a (global) variable to me and I don't see any other reference to it in the code you posted. Perhaps you meant 'someObject->quit_flag' or 'someObject->quit_flag()' ?

---

### Post by jmichel on 2010-03-12
The code I have posted is not complete but only the subset related to my problem. But this flag is present and the code compiles.

---

### Post by kahumba on 2010-03-12
Well, in such cases I usually post a simple but complete example that compiles to make it easier for people help me.

---

### Post by pbrane on 2010-03-12
Have a look at this page. 
[http://www.mail-archive.com/svn-commits-list@gnome.org/msg85270.html]("http://www.mail-archive.com/svn-commits-list@gnome.org/msg85270.html")
There may be something here you can use. One thing, in your example you don't show how *quit_flag* is getting set. Also I'm not sure you should call the read function in a loop.

---

### Post by kennethadammiller on 2010-03-24
if you haven't already (which I don't know) you could try the devhelp program, it has a lot of documentation on gtkmm and these different interfaces.

Anyway, I'm using gtkmm as well, and I was wondering if you could help me some. it would be great if we could help each other out along the way.
what do you say?

---

### Post by SledgeHammer_999 on 2010-03-24
Just post a thread in the forum and if I(or anyone else) can help, I will.

---

