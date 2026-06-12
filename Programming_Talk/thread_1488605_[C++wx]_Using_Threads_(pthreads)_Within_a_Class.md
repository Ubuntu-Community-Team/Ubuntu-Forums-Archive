---
title: "[C++/wx] Using Threads (pthreads) Within a Class"
date: 2010-05-20
forum: Programming Talk
---

### Post by dodle on 2010-05-20
I don't have a lot of experience with threads so bear with me.

My problem is that I cannot figure out how to process a new thread from a class method.  Here is the error ouput from compilation:
```
$ g++ test.cpp `wx-config --cxxflags --libs` -o test -pthread
test.cpp: In member function ‘void MainWindow::OnButton(wxCommandEvent&)’:
test.cpp:32: error: argument of type ‘void* (MainWindow::)(void*)’ does not match ‘void* (*)(void*)’
```

Here is the source:
[php]#include <iostream>
#include <pthread.h>
#include <wx/wx.h>
using namespace std;

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    void OnButton(wxCommandEvent& event); // Method that creates the thread
    void *StartThread(void *arg);  // Method that starts the thread
  private:
    wxPanel *bg;
    wxButton *button;
    pthread_t thread1;
    int rc; // thread's return code
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, _T(""))
{
    Center();

    bg = new wxPanel(this, -1);
    button = new wxButton(bg, -1, _T("Start Thread"));

    button->Connect(wxEVT_COMMAND_BUTTON_CLICKED, wxCommandEventHandler(MainWindow::OnButton), 0, this);
}

void MainWindow::OnButton(wxCommandEvent& event)
{
    cout << "Button Pressed" << endl;
    rc = pthread_create(&thread1, NULL, MainWindow::StartThread, (void*)NULL); // Compile error here
    if (rc)
    {
        cout << "Error Occurred" << endl;
        exit(-1);
    }
}

void *MainWindow::StartThread(void *arg)
{
    cout << "This is a thread" << endl;
    wxSleep(3);
    pthread_exit(NULL);
}[/php]

I do know how to start the thread using a function outside of the class:

thread handling function:
[php]void *StartThread(void* arg)
{
    cout << "This is a thread" << endl;
    pthread_exit(NULL);
}[/php]

method to create thread:
[php]void MainWindow::OnButton(wxCommandEvent& event)
{
    cout << "Button Pressed" << endl;
    rc = pthread_create(&thread1, NULL, StartThread, (void*)NULL);
    if (rc)
    {
        cout << "Error Occurred" << endl;
        exit(-1);
    }
}[/php]

But I need the thread to have access to the class members, and I don't know how to do that from outside of the "MainWindow" class.

---

### Post by MadCow108 on 2010-05-20
pthread is a C implementation and does not play too well with C++
consider using a C++ threading library like boost threads

probably wx also has its own threads implementation.

concerning your problem:
pthread_create does not take member functions due to restrictions of the language (same reason we need mem_fun, ptr_fun, ... for function objects in C++)

A way around that is to use another normal function and pass in an instance of the object (e.g. the this pointer)
```

void *StartThread(void* arg)
{
  MainWindow *obj = reinterpret_cast<MainWindow *>(arg);
  return obj->StartThread();
}
```

---

### Post by dwhitney67 on 2010-05-20
Two things:  1) your StartThread() method should be declared **static**, and 2) it should preferably be declared **private**, although this is not a requisite.

P.S.  As MadCow indicated, it is typical for one to pass the instance object as the arg via the pthread_create() function.

```

class MainWindow
{
   void OnButton(...);

private:
   static void* StartThread(void* arg);
};

void
MainWindow::OnButton(...)
{
   ...

   pthread_create(tid, NULL, StartThread, this);
}

void*
MainWindow::StartThread(void* arg)
{
   MainWindow* mw = static_cast<MainWindow*>(arg);

   // do whatever the thread needs to do, and use the 'mw' as a reference to your class object.

   return 0;
}

```

---

### Post by dodle on 2010-05-20
Thank you both.  The reason why I wanted to do this was becuase multiple mouse clicks were being caught and processed off a wxButton.  Even if I disabled it after the first click, as soon as it was re-enabled, it would process however many clicks the "user" clicked (don't know if that's clear).

Please tell me what you think of this:
[php]class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    void OnButton(wxCommandEvent& event);
    void EnableButton();
  private:
    static void *StartThread(void *arg);
    wxPanel *bg;
    wxButton *button;
    pthread_t thread1;
    int rc;
};

....

void MainWindow::OnButton(wxCommandEvent& event)
{
    button->Disable(); // Disable button until process is finished
    cout << "Button Pressed" << endl;
    rc = pthread_create(&thread1, NULL, StartThread, this);
    if (rc)
    {
        cout << "Error Occurred" << endl;
        exit(-1);
    }
    else cout << "Thread is OK" << endl;
}

void *MainWindow::StartThread(void *arg)
{
    MainWindow *obj = static_cast<MainWindow*>(arg);
    wxSleep(3);
    cout << "This is a thread" << endl;
    obj->EnableButton();
    pthread_exit(NULL);
}

void MainWindow::EnableButton()
{
    button->Enable();
}[/php]

> **MadCow108 said:**
> pthread is a C implementation and does not play too well with C++
consider using a C++ threading library like boost threads

Thank you, I will have a look into that.

> **MadCow108 said:**
> probably wx also has its own threads implementation.

Yes it does, but the reason I am not using it is this: I wanted to be able to cross-compile for Win32, so I compiled wxWidgets for MinGW.  But if I compiled wxWidgets with its threading abilities enabled, I would have to include the mingw10.dll with all of my applications.

---

### Post by dribeas on 2010-05-20
> **MadCow108 said:**
> pthread is a C implementation and does not play too well with C++
consider using a C++ threading library like boost threads


I agree in using higher abstractions like boost::thread instead of plain pthreads if you are going to work in C++, but note that all C++ thread libraries I know of are implemented on top of pthreads, so at the end it has to play at least regularly well with C++, and it is not really that complex.

This is a simple implementation that calls a member method that takes no arguments:
```

template <typename T, void (T::*member)() >
void member_method_dispatch( void * obj ) {
   (static_cast<T*>(obj)->*member)();
}
struct test {
   explicit test(int value) : value(value) {}
   void the_member() {
      std::cout << "Hi there! " << value << std::endl;
   }
   int value;
}
int main() {
   // ... 
   test t( 5 );
   pthread_create( &the_thread, &the_attrs,
             &member_method_dispatch<test,&test::the_member>, &t );
   pthread_join( the_thread, NULL );
}

```

The code is harder to read than it should just to keep it to a minimal example.

---

### Post by dodle on 2010-05-25
I was told that I shouldn't "touch" wxWidgets' objects from within a secondary thread.  So, with some help, I came up with this code that uses wxPostEvent to pass an event to the main thread.

threading.h:
[php]class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    void OnButton(wxCommandEvent& event);
    void EnableButton(wxCommandEvent& event);
  private:
    static void *StartThread(void *arg);
    wxPanel *bg;
    wxButton *button;
    pthread_t thread1;
    int rc;
};[/php]

threading.cpp:
[php]MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, _T(""))
{
    Center();

    bg = new wxPanel(this, -1);
    button = new wxButton(bg, -1, _T("Start Thread"));

    // Event handler to disable button and start thread
    button->Connect(wxEVT_COMMAND_BUTTON_CLICKED, wxCommandEventHandler(MainWindow::OnButton), 0, this);

    // Event handler to re-enable button
    Connect(0, 0, wxCommandEventHandler(MainWindow::EnableButton), 0, this);
}

void MainWindow::OnButton(wxCommandEvent& event)
{
    button->Disable();
    cout << "Button Pressed" << endl;
    rc = pthread_create(&thread1, NULL, StartThread, this);
    if (rc)
    {
        cout << "Error Occurred" << endl;
        exit(-1);
    }
    else cout << "Thread is OK" << endl;
}

void *MainWindow::StartThread(void *arg)
{
    MainWindow *obj = static_cast<MainWindow*>(arg);
    wxSleep(3); // Give the thread a few seconds to finish
    cout << "This is a thread" << endl;
    wxCommandEvent nullevent(0, 0); // Create an event to pass to main thread
    wxPostEvent(obj, nullevent); // Pass null event
    pthread_exit(NULL);
}[/php]

If something doesn't look right in this code, please let me know.

**Edit:** Here is my final code (in one file):
[php]#include <iostream>
#include <pthread.h>
#include <wx/wx.h>
#include <wx/sound.h>
using namespace std;

const int ID_NULL = wxNewId();

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    void OnButton(wxCommandEvent& event);
    void EnableButton(wxCommandEvent& event);
  private:
    static void *StartThread(void *arg);
    wxPanel *bg;
    wxButton *button;
    wxString *cur_sound;
    pthread_t thread1;
    int rc;
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, _T(""))
{
    Center();

    bg = new wxPanel(this, -1);
    bg->SetFocus();
    button = new wxButton(bg, -1, _T("Start Thread"));
    cur_sound = new wxString();

    // Event handler to disable button and start thread
    button->Connect(wxEVT_COMMAND_BUTTON_CLICKED, wxCommandEventHandler(MainWindow::OnButton), 0, this);

    // Event handler to re-enable button
    Connect(ID_NULL, 0, wxCommandEventHandler(MainWindow::EnableButton), 0, this);
}

void MainWindow::OnButton(wxCommandEvent& event)
{
    button->Disable();
    cout << "Button Pressed" << endl;
    cur_sound->Clear();
    cur_sound->Append(_T("dog.wav"));
    wxSound dog(*cur_sound);
    dog.Play(wxSOUND_SYNC);
    rc = pthread_create(&thread1, NULL, StartThread, this);
    if (rc)
    {
        cout << "Error Occurred" << endl;
        exit(-1);
    }
    else cout << "Thread is OK" << endl;
    bg->SetFocusIgnoringChildren();
}

void *MainWindow::StartThread(void *arg)
{
    wxEvtHandler *obj = wxDynamicCast(arg, wxEvtHandler);
    if (obj)
    {
        cout << "Playing Sound" << endl;
        wxCommandEvent nullevent(0, ID_NULL); // Create an event to pass to main thread
        wxPostEvent(obj, nullevent); // Pass null event
    }
    pthread_exit(NULL);
}

void MainWindow::EnableButton(wxCommandEvent& event)
{
    button->Enable();
}

class App : public wxApp
{
  public:
    virtual bool OnInit();
};

IMPLEMENT_APP(App)

bool App::OnInit()
{
    MainWindow *frame = new MainWindow(_T("Testing Threads"));
    frame->Show();
    SetTopWindow(frame);
    return true;
}[/php]

---

