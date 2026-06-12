---
title: "[C++/wx] Have I created a memory leak?"
date: 2010-04-30
forum: Programming Talk
---

### Post by AntumDeluge on 2010-04-30
Would someone mind looking over this code for a simple window to see if I have created a memory leak?  I don't know much about allocating memory.  I've read over some documents about memory leaks, and according to what I understand, memory leaks happen when memory allocated is not freed up after the object/program is closed.  I'm not sure how to free up this memory.  

main.h[php]#include <wx/wx.h>

class App : public wxApp
{
  public:
    virtual bool OnInit();
};
[/php]main.cpp
[php]#include "main.h"
#include "test.h"

IMPLEMENT_APP(App)

bool App::OnInit()
{
    MainWindow *frame = new MainWindow(_T("Test Window"));
    frame->Show();
    
    return true;
}
[/php]test.h
[php]#include <wx/wx.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    
    void OnQuit(wxCommandEvent& event);
};
[/php]test.cpp
[php]#include "test.h"

MainWindow::MainWindow(const wxString& title)
  : wxFrame(NULL, -1, title, wxDefaultPosition, wxSize(800,650))
{
    SetIcon(wxIcon(_T("bitmaps/icon.png")));  // Give the window an icon
    SetMinSize(wxSize(640,400));
    Centre();
    
    wxMenuBar *menu = new wxMenuBar();  // Create a menubar
    wxMenu *file = new wxMenu();  // File menu
    
    file->Append(wxID_EXIT, _T("Exit"));  // Add "Exit" to the file menu
    
    // Close the window when "Exit" is selected
    Connect(wxID_EXIT, wxEVT_COMMAND_MENU_SELECTED, wxCommandEventHandler(MainWindow::OnQuit));
    
    menu->Append(file, _T("File"));  // Add "File" to the menubar
    this->SetMenuBar(menu);  // Show the menubar in the main window
}

void MainWindow::OnQuit(wxCommandEvent& WXUNUSED(event))
{
    Close();
}
[/php]

---

### Post by tookyourtime on 2010-04-30
To be sure, you can run valgrind and find out.

There may need to be some sort of
```
delete frame
```
 after
```
[COLOR=#000000][COLOR=#0000BB]MainWindow [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]frame[/COLOR][/COLOR]
```

at some point.

But I'm not sure with the specifics of wx
[COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR]

---

### Post by AntumDeluge on 2010-05-01
Okay, I have learned that generally wxWidgets takes care of freeing up memory when the parent widget is destroyed, unless otherwise specified in the documentation.  But I'm still confused about avoiding memory leaks in c++ in general.  

From what I have read, if I understand correctly, one way memory leaks can happen is by using the "new" statement.  When objects are created using "new" they need to be manually deleted.  

So let's say I have a custom class called "MyClass":
[php]MyClass *steve = new MyClass();[/php]At some point I have to say:
[php]delete steve;[/php]...or the memory that was allocated for "steve" will not be freed up.  Is this correct, or am I way off?

---

### Post by FinalShot on 2010-05-01
That's correct, you would most likely delete when you no longer need it, or before exiting the program.

Also note if your delete an array:
```
delete **[]** aArray;
```

---

### Post by AntumDeluge on 2010-05-01
Oh, good.  I am glad that I am starting to understand.  But there are different ways that memory leaks can happen, correct?  I've been reading over this: [http://www.yolinux.com/TUTORIALS/C++MemoryCorruptionAndMemoryLeaks.html](http://www.yolinux.com/TUTORIALS/C++MemoryCorruptionAndMemoryLeaks.html)

---

### Post by FinalShot on 2010-05-01
Yeah, using the *new* keyword you dealing with the stack.

---

### Post by AntumDeluge on 2010-05-01
Okay, that's very helpful, thanks.  I will keep reading.

---

### Post by dwhitney67 on 2010-05-01
> **FinalShot said:**
> Yeah, using the *new* keyword you dealing with the stack.

Actually, *new* allocates from the heap, not the stack.

As for leaks, some people have different interpretations.  For recurring allocations, that are never freed after use, these are definitely considered a leak; for an object that is allocated for use throughout the lifetime of the application, this would not be considered a leak.

For example, of what is considered a leak:
```

int* allocArray(const size_t size)
{
   return new int[size];
}

int main()
{
   size_t num = 0;

   while (true)
   {
      std::cout << "Enter a number between 1 and 50, or 0 to quit: ";
      std::cin  >> num;

      // error checking of input should be done here.

      if (num == 0) break;

      std::cout << "Here are " << num << " random numbers:" << std::endl;

      int* array = allocArray(num);

      // populate array with random numbers.

      std::copy(array, array + num, std::ostream_iterator<int>(std::cout, " "));

      // array is never freed, hence the leak.  (I know... a lame example).
   }
}

```
This on the other hand, may not be considered a leak because the array is allocated only once, and it will be automatically recovered by the system when the application terminates (gracefully or not):
```

int* allocArray(const size_t size)
{
   return new int[size];
}

int main()
{
   int*   array = allocArray(50);
   size_t num   = 0;

   while (true)
   {
      std::cout << "Enter a number between 1 and 50, or 0 to quit: ";
      std::cin  >> num;

      // error checking of input should be done here.

      if (num == 0) break;

      std::cout << "Here are " << num << " random numbers:" << std::endl;

      // populate array with random numbers.

      std::copy(array, array + num, std::ostream_iterator<int>(std::cout, " "));
   }
}

```
With GUIs, there are essential elements (ie a frame) that are best to allocate, but since these are only done once, I think it is safe to not classify this as a memory leak.

There are other alternatives of course; you could consider using the STL auto_ptr, or TR1's (or Boost's) shared-pointer.  I rarely use these myself, and if I recall correctly, they do not work for arrays, but only for single objects.

An example of auto_ptr:
```

#include <memory>

class MainWindow
{
};

class MyGUI
{
public:
   MyGUI() : myWindow(new MainWindow) {}

private:
   std::auto_ptr<MainWindow> myWindow;
};

int main()
{
   MyGUI gui;
}

```

---

### Post by nvteighen on 2010-05-01
On the line of what dwhitney67 said, there are different interpretations. Not deallocating objects that have to live until the application exits isn't that grave at least in modern mainstream OSs which will deallocate that memory for you (but, in an embedded system, this could be different...).

Something totally different is when you lose track of an object dynamically allocated in a procedure by not returning its pointer or any other mean (e.g. using a pointer parameter... or even a global variable). If this happens and the procedure is executed multiple times in an application's execution flow, you may end up wasting memory on unreachable objects.

In C++ the best way to avoid leaks is to avoid using 'new'. Good C++ uses it as least as possible; you can easily go along with stack allocation and limiting the objects' lifetime to the procedures where they really are needed. And those cases where dynamic allocation is needed are usually wrapped in classes that manage that allocation in their constructors and the deallocation in their destructors, such that you can then use that wrapper class allocating it in stack and take advantage of the fact that stack-allocated classes call their destructors when the function returns.

---

### Post by CptPicard on 2010-05-01
Regarding nvteighen's post above... in particular, getting familiar with the boost library smart pointers is very helpful. I tend to stick pretty much everything I ever "new" in C++ into one of those, and I'm done with most allocation issues.

---

