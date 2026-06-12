---
title: "[Gtkmm] Why this iterator comparison doesn't work?"
date: 2010-11-22
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-11-22
Here is an example code:

main.h
[php]
#ifndef MAIN_H_INCLUDED
#define MAIN_H_INCLUDED

#include <gtkmm.h>

#include <vector>

class MainWindow: public Gtk::Window
{
public:
  MainWindow();
  ~MainWindow(); 
  
  Glib::ustring get_next(const Glib::ustring &path);
  Glib::ustring get_previous(const Glib::ustring &path);
  void set_current(const Glib::ustring &path);

protected:
  //Tree model columns
  class ModelColumns : public Gtk::TreeModel::ColumnRecord
  {
  public:
    ModelColumns();    
    Gtk::TreeModelColumn<Glib::ustring> title;    
  };

  ModelColumns columns;
  Gtk::VBox *vbox;
  Gtk::HBox *hbox;
  Gtk::Button *next, *previous;
  Gtk::TreeView *TreeView;
  Glib::RefPtr<Gtk::ListStore> TreeModel;
  
  void previous_clicked();
  void next_clicked();

private:
  Glib::ustring cur_title;

};




#endif // MAIN_H_INCLUDED
[/php]

main.cpp
[php]
#include "main.h"

MainWindow::ModelColumns::ModelColumns()
{  
  add(title);  
}


MainWindow::MainWindow()
{
  vbox = new Gtk::VBox();
  hbox = new Gtk::HBox();
  next = new Gtk::Button("Next");
  previous = new Gtk::Button("Previous");
  TreeView = new Gtk::TreeView();
  TreeModel = Gtk::ListStore::create(columns);

  TreeView->set_model(TreeModel);  
  TreeView->append_column("Title", columns.title);
  
  Gtk::TreeModel::Row row = *(TreeModel->append());  
  row[columns.title] = "First line";
  row = *(TreeModel->append());  
  row[columns.title] = "Second line";
  row = *(TreeModel->append());  
  row[columns.title] = "Third line";
  
  cur_title = "First line";
  set_current(cur_title);
  
  next->signal_clicked().connect(sigc::mem_fun(this, &MainWindow::next_clicked));
  previous->signal_clicked().connect(sigc::mem_fun(this, &MainWindow::previous_clicked));

  hbox->pack_start(*previous, true, true);
  hbox->pack_start(*next, true, true);
  
  vbox->pack_start(*TreeView, true, true);
  vbox->pack_start(*hbox, true, true);
  

  set_title("List");  

  add(*vbox);
  resize(250, 250);

  show_all_children();
}

MainWindow::~MainWindow()
{
  delete TreeView;
  delete vbox;
  delete hbox;
  delete next;
  delete previous;
}

Glib::ustring MainWindow::get_next(const Glib::ustring &path)
{
  Gtk::TreeModel::Children children = TreeModel->children();
  for(Gtk::TreeModel::Children::iterator iter = children.begin();
      iter != children.end(); ++iter)
    {
      Gtk::TreeModel::Row row = *iter;
      Glib::ustring current;
      current = row[columns.title];
      if (path == current)
        {
          if (iter == children.end())
          {
			  g_print("BREAKING OUT OF THE LOOP!\n");
			  break;
		  }
          Glib::ustring result;
          row = *(++iter);
          result = row[columns.title];
          return result;
        }
    }
  return Glib::ustring("");
}

Glib::ustring MainWindow::get_previous(const Glib::ustring &path)
{
  Gtk::TreeModel::Children children = TreeModel->children();
  for(Gtk::TreeModel::Children::iterator iter = children.begin();
      iter != children.end(); ++iter)
    {
      Gtk::TreeModel::Row row = *iter;
      Glib::ustring current;
      current = row[columns.title];
      if (path == current)
        {
          if (iter == children.begin()) break;
          Glib::ustring result;
          row = *(--iter);
          result = row[columns.title];
          return result;
        }
    }

  return Glib::ustring("");
}

void MainWindow::set_current(const Glib::ustring &path)
{
  Gtk::TreeModel::Children children = TreeModel->children();
  for(Gtk::TreeModel::Children::iterator iter = children.begin();
      iter != children.end(); ++iter)
    {
      Gtk::TreeModel::Row row = *iter;
      Glib::ustring current;
      current = row[columns.title];
      if (path == current)
        {
          TreeView->set_cursor(TreeModel->get_path(iter));
          break;
        }
    }
}

void MainWindow::next_clicked()
{
	Glib::ustring res = get_next(cur_title);
	if (res != "")
	{
		cur_title = res;
		set_current(cur_title);
	}
}

void MainWindow::previous_clicked()
{
	Glib::ustring res = get_previous(cur_title);
	if (res != "")
	{
		cur_title = res;
		set_current(cur_title);
	}
}

int main(int argc, char *argv[])
{
	Gtk::Main loop(argc, argv);
	
	MainWindow window;
	loop.run(window);
}
[/php]

Compile with:
```
g++ main.cpp -o test `pkg-config gtkmm-2.4 --cflags --libs`
```

The problem:
In get_next() I want to check if the matching row is the last. If yes, I want to break the loop and return an empty string. The iterator comparison doesn't work though... 

Just click the next button until you reach the last row. Then click again. A gtk-warning appears in the console but my g_print doesn't which means that my comparison doesn't work.

The **Gtk::TreeModel::Children::iterator** should behave like an STL iterator, but I haven't any experience with them either, so I suppose I am overlooking something.

Can you help?

---

### Post by spjackson on 2010-11-22
> **SledgeHammer_999 said:**
> 
[php]
          if (iter == children.end())
          {
              g_print("BREAKING OUT OF THE LOOP!\n");
              break;
          }
          Glib::ustring result;
          row = *(++iter);
          result = row[columns.title];
          return result;
[/php]The problem:
In get_next() I want to check if the matching row is the last. If yes, I want to break the loop and return an empty string. The iterator comparison doesn't work though... 

Just click the next button until you reach the last row. Then click again. A gtk-warning appears in the console but my g_print doesn't which means that my comparison doesn't work.

The **Gtk::TreeModel::Children::iterator** should behave like an STL iterator, but I haven't any experience with them either, so I suppose I am overlooking something.

I don't know about gtkmm, but if the iterator is like an STL iterator, then just before you use it, it is pointing to the last item in the set, then you increment it to become end(), then dereference it. You can't dereference end().

Surely you mean this, don't you?
```

          row = *iter;

```

I've just realised that you are trying to find the last one, so here's how to do it with STL.
```

#include <list>
#include <string>
#include <iostream>

typedef std::list<std::string> s_list;

int main()
{
    s_list a_list;

    a_list.push_back("a");
    a_list.push_back("b");
    a_list.push_back("c");

    s_list::const_iterator iter = a_list.begin();
    while (iter != a_list.end())
    {
        std::string current_item = *iter;
        if (++iter == a_list.end())
        {
            std::cout << "The last one ==> ";
        }
        std::cout << current_item << std::endl;

    }
    return 0;
}

```

---

### Post by SledgeHammer_999 on 2010-11-22
I am going to sleep now. I will take a better look at your response tomorrow.

---

### Post by SledgeHammer_999 on 2010-11-24
Hmmm. I had the impression that .end() pointed to the last item in the list. I read your example code and I fixed mine. Here's how get_next() looks:

[php]Glib::ustring MainWindow::get_next(const Glib::ustring &path)
{
  Gtk::TreeModel::Children children = TreeModel->children();
  for(Gtk::TreeModel::Children::iterator iter = children.begin();
      iter != children.end(); ++iter)
    {
      Gtk::TreeModel::Row row = *iter;
      Glib::ustring current;
      current = row[columns.title];
      if (path == current)
        {
          ++iter;
          if (iter == children.end())
          {
              g_print("BREAKING OUT OF THE LOOP!\n");
              break;
          }
          Glib::ustring result;
          row = *iter;
          result = row[columns.title];
          return result;
        }
    }
  return Glib::ustring("");
}[/php]

(the g_print() should be removed. It was put there for debugging purposes)

**spjackson** thanks for your time.

---

