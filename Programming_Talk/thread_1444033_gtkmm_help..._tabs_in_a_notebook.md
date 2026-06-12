---
title: "gtkmm help... tabs in a notebook"
date: 2010-03-31
forum: Programming Talk
---

### Post by kennethadammiller on 2010-03-31
I've been trying to create a tabbed window in gtkmm forever. It's been really hard, and basically, I'm looking for someone to show me how it's done. The object is to make it look like the devhelp program's tabs or firefox, close tab button on each window.

This working version will build just fine, and all you have to do is run it to get a picture of what it is that I'm aiming for.
(it dies if you open more than one tab, and then try to hit the close tab button. I think this happens because I'm using the same Gtk::Label to initialize the title of each page)
main: [http://cpp.pastebin.com/SrxzfQ47](http://cpp.pastebin.com/SrxzfQ47)
examplewindow.cc: [http://cpp.pastebin.com/58eRf1pS](http://cpp.pastebin.com/58eRf1pS)
examplewindow.h: [http://cpp.pastebin.com/9zPjCKwx](http://cpp.pastebin.com/9zPjCKwx)

This version is my current version. It's only a little bit different.
It's all pretty well commented, all you have to do is read over it to get a jest of how it goes. It compiles, but it gets a seg fault error when you try to run  it. I don't know why... I ran it in gdb only for it to give me some kind of very terse, impossible to understand message...

Program received signal SIGSEGV, Segmentation fault.
0x002ad658 in Gtk::Box_Helpers::BoxList::erase(Glib::List_Iterator<Gtk::Box_Helpers::Child>)
    () from /usr/lib/libgtkmm-2.4.so.1
(gdb) q


The layout of this more current one it's much the same of the one that I listed above, except I attempted to move the CloseCurrentTab button from below the notebook to inside the title of the page, and instead of having something like a label as a child, I put an empty box inside of each notebook page. That's about all the difference.

main: [http://cpp.pastebin.com/g4yngdwJ](http://cpp.pastebin.com/g4yngdwJ)
examplewindow.h: [http://cpp.pastebin.com/cn0fTVCY](http://cpp.pastebin.com/cn0fTVCY)
examplewindow.cc: [http://cpp.pastebin.com/5dQ8Ntjc](http://cpp.pastebin.com/5dQ8Ntjc)

---

### Post by kennethadammiller on 2010-03-31
wait...
one minor error

this is what the examplewindow.cc should look like:
[http://cpp.pastebin.com/aUuVbgh0](http://cpp.pastebin.com/aUuVbgh0)

---

### Post by SledgeHammer_999 on 2010-04-01
You are new in C++ right?

Anyways, I took a look at your second program. The program starts fine without any gtk-warning in the terminal. If I press the "close tab" without adding a new tab, then everything is ok. If I first add a tab and then try to close it, then the application dies.

This is related to you trying to put the same widgets in different containers. Each widget can belong to only one container. You need to create for each tab a new tab_label widget(and it's child widgets). Can I propose dynamic allocation? or use Gtk::Manage() see here for more info on you available choices-->[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-memory-widgets.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-memory-widgets.html.en)

If you solve this problem you will be able to go forward, because it currently cripples our program.

If I wasn't clear enough or if you have more questions don't hesitate to ask me.

---

### Post by kennethadammiller on 2010-04-01
Yes, I am new to C++. I did have a plan to try and find a way to allocate a new set of stuff that is initialized accordingly each time a new page is created... but of course I'm having trouble.

Right now, I'm making a blog called "making a gtkmm application from the ground up"-I want  to make this for beginners just like me to get some help. I feel that the book provided at the site provides enough help to do basic stuff, when you want that extra little bit, you might want a little more explanation. So this will be good to garner the interaction that I need with other programmers, and plus, the more you help, the more you help the whole community.

I figured out how to put the X button in each of the tabs, but the way that I thought of to allocate the new pieces necessary to initialize each page separately was flawed; I stuck them in a vector<Gtk::[whatever widget] *>. so yea, i get what you are saying about each page needing to be initialized with separate components because when the page is closed, all it's child widgets are killed/deleted as well. 

So what I've currently got is just another version of what's up there, it's broken too, so there's no need in posting it. hahaha. Thanks a lot for the help.

I guess I should mention the end goal; to have an enhanced Gtk::Notebook class that's descendant of Gtk::Notebook, that comes with the x button on each of the tabs, with initializing functions like .set_title(), .set_child_widget() that are virtual, so they can be over ridden. This way, I *really* can make this reusable. :) lol. I've been kind of creatively running this over in my mind, thinking about possible template designs for it and stuff... but couldn't get really started.

Do you have any kind of structure (other than vector haha) that I might place the newly created child and title widgets in? I'm thinking a linked list...

---

### Post by kennethadammiller on 2010-04-01
and hey-
Thanks a lot for being willing enough and kind to help me. I really appreciate the suggestions and ideas, and your time.

---

### Post by SledgeHammer_999 on 2010-04-01
> **kennethadammiller said:**
> 
Right now, I'm making a blog called "making a gtkmm application from the ground up"-I want  to make this for beginners just like me to get some help. ..... So this will be good to garner the interaction that I need with other programmers, and plus, the more you help, the more you help the whole community.

So let's interact :P I have a (new) blog too for this purpose. It is here-->[hammered999.wordpress.com](http://hammered999.wordpress.com/)
What's yours? I like to watch relevant blogs.

>  when the page is closed, all it's child widgets are killed/deleted as well. 

Not necessarily true. This is true for Gtk. In GTKmm child widgets don't "die" when you remove them from their container. 

> I guess I should mention the end goal; to have an enhanced Gtk::Notebook class that's descendant of Gtk::Notebook, that comes with the x button on each of the tabs, with initializing functions like .set_title(), .set_child_widget() that are virtual, so they can be over ridden. This way, I *really* can make this reusable. :) lol. I've been kind of creatively running this over in my mind, thinking about possible template designs for it and stuff... but couldn't get really started.

You could look the source of other Gtk projects that have this feature. Well, if you're capable to read whole codebases and find the right spot :P
Some projects that use them are Anjuta, PCManFM, the newest Nautilus and gnome-terminal.

> Do you have any kind of structure (other than vector haha) that I might place the newly created child and title widgets in? I'm thinking a linked list...

A vector is just fine.

Just a pseudo-code explanation:
[php]
MyWindow::MyWindow()
{
   //this is the constructor of your main window
   //here you pack the notebook in the relevant 
   //containers and then you add the containers 
   // to the main window

  //now let's create the first page
  //my_labels is an std::vector<Gtk::Label*>
  Gtk::Label *temp_label = new Gtk::Label("some example text here");
  my_notebook.append_page(*temp_label, "New Tab");
  my_labels.push_back(temp_label);

  //do some other stuff here, like connecting to button signals etc  
}

MyWindow::~MyWindow()
{
   //this the destructor of you main window
   //here you have to deallocate all the memory
   //that you allocated dynamically(through the 'new' operator)
   //otherwise you will get memory leaks. You can avoid this if
   // you use Gtk::Manage().
   //So let's deallocate all those labels
   for (unsigned int i=0; i < my_labels.size(); i++)
       {
          delete my_labels[i];
       }
   
}

void MyWindow::CreateNewTab()
{ 
  //just repeat the previous code
  Gtk::Label *temp_label = new Gtk::Label("some example text here");
  my_notebook.append_page(*temp_label, "New Tab");
  my_labels.push_back(temp_label);      
}

void MyWindow::DeleteTab()
{
  int count = my_notebook.get_active_page()
   if (count > -1)
    {
       my_notebook.remove_page(count);
       delete my_labels[count];
    }
}
[/php]

Now that I looked at the Gtk::Notebook documentation I think I figured out how you can create the type of tabs you want.

Here are the steps:
1. Create a Gtk::HBox container (let's call it tab_label_container)
2. Create a Gtk::Label with the title you want (let's call it tab_label)
3. Create a Gtk::Button and set the appropriate icon (let's call it tab_close_button)
4. Pack tab_label and tab_close_button into tab_label_container
5. Let's assume another container called my_container that contains all the widgets you want to show IN the tab.
6. The secret is to use the correct append_page() method which is overloaded. Use this one->[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Notebook.html#af7bdf8ec9f703fb21aec6d372085f38a](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Notebook.html#af7bdf8ec9f703fb21aec6d372085f38a)
7. Use it this way--> **my_notebook.append_page(my_container, tab_label_container);**

---

### Post by kennethadammiller on 2010-04-01
Oh yea, that's cool that you were willing to look up that documentatiion for me, but it was actually in the source of the second set of files that I left links for. I'm not being a smart *** or anything, i think what you're doing for me is really cool.

ALright, so I got a little bit further with it. I'm sure you can help me out, I got it to compile. Only thing is, where it was supposed to pack in the HBox containing the tab and the close button for each new tab, it's only like a little blank line... I don't know completely why, I'm guessing when I used that char buf[64] to stuff the titles in there i didn't properly use the buf,... hard to explain without looking a few things up. All you have to do is compile it and you'll see what's wrong with it and know where to look.

main: [http://cpp.pastebin.com/g4yngdwJ](http://cpp.pastebin.com/g4yngdwJ)
examplewindow.cc: [http://cpp.pastebin.com/zzQphEaw](http://cpp.pastebin.com/zzQphEaw)
examplewindow.h: [http://cpp.pastebin.com/efRjHtSh](http://cpp.pastebin.com/efRjHtSh)


Do you want to work together to make an application that we could blog about? Or a blog about an application? it could be fun :)

---

### Post by pbrane on 2010-04-01
If you want to do this in code that's fine, but there is an easier way. Use glade-3 to create the UI. Use Gtk::Builder to manipulate the UI in your code. I created a five tab notebook that has an icon, text, and close button in about ten minutes in Glade Interface Designer and maybe another ten minutes of coding. And the nice thing is that I can make minor changes to the GUI in Glade and not have to recompile. As long as you don't add/remove widgets or change the widget names that is.

You can add all the tabs you may need and show/hide them or you can create a notebook::page base class to help create pages on the fly.

---

### Post by kennethadammiller on 2010-04-01
I've known about glade for a while, I just don't know how every single widget works. Thanks for the advice man. I think I will eventually end up using glade, thing is, I want to know how the API works first. That way, I know what each widget that I'm sticking in there does.

and hey, by the way, how do you do custom widgets in glade?

---

### Post by SledgeHammer_999 on 2010-04-01
> **kennethadammiller said:**
> Oh yea, that's cool that you were willing to look up that documentatiion for me, but it was actually in the source of the second set of files that I left links for. I'm not being a smart *** or anything, i think what you're doing for me is really cool.

Sorry, I hadn't look to all of your code.

> ALright, so I got a little bit further with it. I'm sure you can help me out, I got it to compile. Only thing is, where it was supposed to pack in the HBox containing the tab and the close button for each new tab, it's only like a little blank line... I don't know completely why, I'm guessing when I used that char buf[64] to stuff the titles in there i didn't properly use the buf,... hard to explain without looking a few things up. All you have to do is compile it and you'll see what's wrong with it and know where to look.

main: [http://cpp.pastebin.com/g4yngdwJ](http://cpp.pastebin.com/g4yngdwJ)
examplewindow.cc: [http://cpp.pastebin.com/zzQphEaw](http://cpp.pastebin.com/zzQphEaw)
examplewindow.h: [http://cpp.pastebin.com/efRjHtSh](http://cpp.pastebin.com/efRjHtSh)

I looked at it really FAST. You should call show_all() on the HBox that packs the label+button after you pack them.

Also I suggest you use Glib::ustring::compose or Glib::ustring::format instead of snprintf. snprintf is the C way.

Eg
snprintf (buf, sizeof (buf), "Page %d", 1);
can be written like this:
Gtk::Label label = Glib::ustring::compose("Page %1", 1)


> Do you want to work together to make an application that we could blog about? Or a blog about an application? it could be fun :)

I like to help, but I don't know if I really can commit to a project :p

---

### Post by pbrane on 2010-04-02
> **kennethadammiller said:**
> 
and hey, by the way, how do you do custom widgets in glade?


I have used a couple of techniques. One is to create a "placeholder" widget in glade and then replace it in code. For instance I needed a simple Gtk::ComboTextBox, but Glade 3 doesn't support them. So I used Gtk::ComboBox in glade and replaced them in code with Gtk::ComboTextBox.

Another technique I have used is to use Custom Widget. But this is only supported in libglade, not Gtk::Builder. So I would use the replace method instead. I have changed all my code to use Gtk::Builder instead of libglade.

---

### Post by interval1066 on 2010-06-21
Glade rocks, its supported by a bunch of stuff, not just gtkmm. I know you can use it with Python, Haskell, Perl, Lisp, I think you can use it with shell script with the right modules installed.

---

