---
title: "loading images to RefPtr's in a map Glib::FileError signal 11 (Segmentation fault)"
date: 2011-05-04
forum: Programming Talk
---

### Post by vivichrist on 2011-05-04
I'm having problems loading images using:
i.e Gdk::Pixbuf::create_from_file("box.png"))
these images are in the same dir as the project and exec.

```
typedef std::map<char ,Cell::Cell> CCMap;
	typedef std::pair<char ,Cell::Cell> CCPair;
	typedef std::map<Cell::Cell, Glib::RefPtr<Gdk::Pixbuf> > IMMap;
	typedef std::pair<Cell::Cell, Glib::RefPtr<Gdk::Pixbuf> > IMPair;
	typedef std::map<Direction::Direction,Glib::RefPtr<Gdk::Pixbuf> > AMMap;
	typedef std::pair<Direction::Direction,Glib::RefPtr<Gdk::Pixbuf> > AMPair;
	typedef std::map<char ,Direction::Direction> KMMap;
	typedef std::pair<char ,Direction::Direction> KMPair;
	CCMap cellMapping;
	IMMap imageMapping;
	AMMap agentMapping;
	KMMap keyMapping;
```

```
	try {
		imageMapping.insert(IMPair(Cell::OUTOFBOUNDS, Gdk::Pixbuf::create_from_file("box.png")));
		imageMapping.insert(IMPair(Cell::EMPTY, Gdk::Pixbuf::create_from_file("empty.png")));
		imageMapping.insert(IMPair(Cell::WALL, Gdk::Pixbuf::create_from_file("wall.png")));
		imageMapping.insert(IMPair(Cell::BOX, Gdk::Pixbuf::create_from_file("box.png")));
		imageMapping.insert(IMPair(Cell::SHELF, Gdk::Pixbuf::create_from_file("shelf.png")));
		imageMapping.insert(IMPair(Cell::BOXONSHELF, Gdk::Pixbuf::create_from_file("boxOnShelf.png")));

		agentMapping.insert(AMPair(Direction::UP, Gdk::Pixbuf::create_from_file("agent-up.png")));
		agentMapping.insert(AMPair(Direction::DOWN, Gdk::Pixbuf::create_from_file("agent-down.png")));
		agentMapping.insert(AMPair(Direction::LEFT, Gdk::Pixbuf::create_from_file("agent-left.png")));
		agentMapping.insert(AMPair(Direction::RIGHT, Gdk::Pixbuf::create_from_file("agent-right.png")));
	}catch(const Glib::FileError& e)
	  {
		  Gtk::MessageDialog * dialog = new 
			  Gtk::MessageDialog(*this->get_tooltip_window(), e.what(), 
			                     false, Gtk::MESSAGE_WARNING);
		  dialog->run();
		  dialog->hide();
	  }
```

---

### Post by vivichrist on 2011-05-04
there was some confusion on my part as to where these images should reside and it would seem that if the Anjuta project is in say "/home/myname/projects/bla-project" and the source is compiled and run in that directory + "src/" then the images should be in the "/home/myname/projects/bla-project" and not "/home/myname/projects/bla-project/src" directory or any other.

---

