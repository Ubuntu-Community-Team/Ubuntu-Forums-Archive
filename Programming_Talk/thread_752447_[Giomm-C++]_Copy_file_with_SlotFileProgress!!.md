---
title: "[Giomm-C++] Copy file with SlotFileProgress?!!"
date: 2008-04-11
forum: Programming Talk
---

### Post by tuanduc on 2008-04-11
I'm trying to make a small program that copy a file using giomm and getting "Segmentation Error"!

```

#include <iostream>
#include <gtkmm.h>
#include <giomm.h>

void cpsl(goffset read, goffset total)
{
  std::cout << read << "/" << total << std::endl;
}

int main(int argc, char *argv[])
{
  Gio::init();
  Glib::ustring from, to;
  std::cin >> from;
  std::cin >> to;
  
  Glib::RefPtr<Gio::File> fin = Gio::File::create_for_path(from);
  Glib::RefPtr<Gio::File> fout = Gio::File::create_for_path(to);
  
  Gio::File::SlotFileProgress sl = sigc::ptr_fun(&cpsl);
  fin->copy(fout, sl);
  
  return 0;
}

```

I cannot find any documents or examples about Giomm. So, can anyone tell me what' wrong???
(Sorry for my bad English)

---

### Post by cl333r on 2009-03-01
Half a year later, has anyone spotted on the internet examples using giomm?

---

### Post by dwhitney67 on 2009-03-01
WTF... I did a google-search on "giomm".  The third item on the list is:  [http://www.murrayc.com/blog/permalink/2008/01/28/giomm-gio-in-c/](http://www.murrayc.com/blog/permalink/2008/01/28/giomm-gio-in-c/)

If you want examples, there you have it.

---

### Post by cl333r on 2009-03-01
> **dwhitney67 said:**
> WTF... I did a google-search on "giomm".  The third item on the list is:  [http://www.murrayc.com/blog/permalink/2008/01/28/giomm-gio-in-c/](http://www.murrayc.com/blog/permalink/2008/01/28/giomm-gio-in-c/)

If you want examples, there you have it.

I've been there, found no actual code, when I click on "giomm examples" I can't find them, they either don't exist or the page should be more user friendly.

---

### Post by cl333r on 2009-03-01
I found what's the matter, when you click a file, it yields the svn diff instead of its contents, from that page you have to click once more on 'view' to actually view the file.. ahh that's not the kind of attitude I get in Java.

---

### Post by dwhitney67 on 2009-03-01
> **cl333r said:**
> I found what's the matter, when you click a file, it yields the svn diff instead of its contents, from that page you have to click once more on 'view' to actually view the file.. ahh that's not the kind of attitude I get in Java.
I know it's lame, but that is a topic for another discussion.  But I'm glad you found some examples.

---

