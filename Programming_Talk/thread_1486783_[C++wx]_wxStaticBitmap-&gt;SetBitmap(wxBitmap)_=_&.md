---
title: "[C++/wx] wxStaticBitmap-&gt;SetBitmap(wxBitmap) = &quot;Segmentation fault&quot;"
date: 2010-05-18
forum: Programming Talk
---

### Post by dodle on 2010-05-18
I get a "Segmentation fault" when I try to change to a different bitmap via a class method:

First I declare the static bitmap in the header:
[php]wxStaticBitmap *image;[/php]

Then I define the bitmap:
[php]bg = new wxPanel(this, -1); // Create panel on which to display bitmaps
image = new wxStaticBitmap(bg, -1, wxBitmap(_T("bananas.png")));[/php]

Then in the method, I try to display a different bitmap:
[php]wxBitmap dog(_T("dog.png")); // get new bitmap
cout << dog.IsOk() << endl; // view output of bitmap check
if (dog.IsOk())
{
    image->SetBitmap(dog); // Segmentation fault
}[/php]

If I set the bitmap in the constructor it works fine:
[php]image = new wxStaticBitmap(bg, -1, wxBitmap(_T("bananas.png")));
wxBitmap dog(_T("dog.png")); // Get new bitmap
image->SetBitmap(dog); // Displays dog[/php]

I've read over [http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault), which seems to explain that there is some kind of memory access violation going on.  But I don't understand why it happens during a call to a class method, but not in the constructor.

---

### Post by Zugzwang on 2010-05-18
I would say that the first thing to do is to execute your program using valgrind.

Segmentation faults may occur at strange positions because a problem occured earlier but did not had any immediate effects.

Try to compile your program using debugging symbols (unless you do that anyway) and run your program with valgrind (it will be around 10-100x slower during the check):
```

valgrind --tool=memcheck ./yourprogram <yourparameters>

```

It will show you more detailed error information and also tell you about (some, but unfortunately not all) problems that occurred before the fault.

Others will tell you to try the debugger first, which is also fine. It's just my personal impression that the information collected by valgrind is usually more helpful than that of the debugger for a analysis.

---

### Post by dodle on 2010-05-18
Here is what came up with valgrind:
```
~/Programming/C++/ABC$ valgrind --tool=memcheck ./abc
==14519== Memcheck, a memory error detector
==14519== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==14519== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==14519== Command: ./abc
==14519== 
"J" Pressed
1
==14519== Invalid read of size 4
==14519==    at 0x804EF3E: MainWindow::ChangeLetter(wxKeyEvent&) (in /home/user/Programming/C++/ABC/abc)
==14519==    by 0x4785A9E: wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x4824378: wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x4824507: wxEvtHandler::SearchDynamicEventTable(wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x48254F4: wxEvtHandler::ProcessEvent(wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x44F4E7C: ??? (in /usr/lib/libwx_gtk2u_core-2.8.so.0.6.0)
==14519==    by 0x4C752F3: _gtk_marshal_BOOLEAN__BOXED (gtkmarshalers.c:84)
==14519==    by 0x5194251: g_closure_invoke (gclosure.c:767)
==14519==    by 0x51A899C: signal_emit_unlocked_R (gsignal.c:3248)
==14519==    by 0x51A9C32: g_signal_emit_valist (gsignal.c:2991)
==14519==    by 0x51AA255: g_signal_emit (gsignal.c:3038)
==14519==    by 0x4DA2305: gtk_widget_event_internal (gtkwidget.c:4951)
==14519==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==14519== 
==14519== 
==14519== Process terminating with default action of signal 11 (SIGSEGV)
==14519==  Access not within mapped region at address 0x0
==14519==    at 0x804EF3E: MainWindow::ChangeLetter(wxKeyEvent&) (in /home/user/Programming/C++/ABC/abc)
==14519==    by 0x4785A9E: wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x4824378: wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x4824507: wxEvtHandler::SearchDynamicEventTable(wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x48254F4: wxEvtHandler::ProcessEvent(wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==14519==    by 0x44F4E7C: ??? (in /usr/lib/libwx_gtk2u_core-2.8.so.0.6.0)
==14519==    by 0x4C752F3: _gtk_marshal_BOOLEAN__BOXED (gtkmarshalers.c:84)
==14519==    by 0x5194251: g_closure_invoke (gclosure.c:767)
==14519==    by 0x51A899C: signal_emit_unlocked_R (gsignal.c:3248)
==14519==    by 0x51A9C32: g_signal_emit_valist (gsignal.c:2991)
==14519==    by 0x51AA255: g_signal_emit (gsignal.c:3038)
==14519==    by 0x4DA2305: gtk_widget_event_internal (gtkwidget.c:4951)
==14519==  If you believe this happened as a result of a stack
==14519==  overflow in your program's main thread (unlikely but
==14519==  possible), you can try to increase the size of the
==14519==  main thread stack using the --main-stacksize= flag.
==14519==  The main thread stack size used in this run was 8388608.
==14519== 
==14519== HEAP SUMMARY:
==14519==     in use at exit: 1,045,462 bytes in 8,548 blocks
==14519==   total heap usage: 20,174 allocs, 11,626 frees, 3,932,734 bytes allocated
==14519== 
==14519== LEAK SUMMARY:
==14519==    definitely lost: 288 bytes in 3 blocks
==14519==    indirectly lost: 140 bytes in 11 blocks
==14519==      possibly lost: 623,316 bytes in 2,618 blocks
==14519==    still reachable: 412,050 bytes in 5,742 blocks
==14519==         suppressed: 9,668 bytes in 174 blocks
==14519== Rerun with --leak-check=full to see details of leaked memory
==14519== 
==14519== For counts of detected and suppressed errors, rerun with: -v
==14519== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 199 from 13)
Segmentation fault
```

Also, I'm a big noob when it comes to programming.  I'm not familiar with how to debug C++.  I'm using the GNU C++ compiler: [gnu g++ debug how to](http://www.google.com/search?client=ubuntu&channel=fs&q=gnu+g%2B%2B+debug+how+to&ie=utf-8&oe=utf-8)

**Edit:** Here is with the -v option:
```
==16895== 1 errors in context 1 of 1:
==16895== Invalid read of size 4
==16895==    at 0x804EF3E: MainWindow::ChangeLetter(wxKeyEvent&) (in /home/user/Programming/C++/ABC/abc)
==16895==    by 0x4785A9E: wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==16895==    by 0x4824378: wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==16895==    by 0x4824507: wxEvtHandler::SearchDynamicEventTable(wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==16895==    by 0x48254F4: wxEvtHandler::ProcessEvent(wxEvent&) (in /usr/lib/libwx_baseu-2.8.so.0.6.0)
==16895==    by 0x44F4E7C: ??? (in /usr/lib/libwx_gtk2u_core-2.8.so.0.6.0)
==16895==    by 0x4C752F3: _gtk_marshal_BOOLEAN__BOXED (gtkmarshalers.c:84)
==16895==    by 0x5194251: g_closure_invoke (gclosure.c:767)
==16895==    by 0x51A899C: signal_emit_unlocked_R (gsignal.c:3248)
==16895==    by 0x51A9C32: g_signal_emit_valist (gsignal.c:2991)
==16895==    by 0x51AA255: g_signal_emit (gsignal.c:3038)
==16895==    by 0x4DA2305: gtk_widget_event_internal (gtkwidget.c:4951)
==16895==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==16895== 
--16895-- 
--16895-- used_suppression:    181 glib type registry
--16895-- used_suppression:    199 dl-hack3-cond-1
==16895== 
==16895== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 199 from 13)
Segmentation fault
```

**Edit:** Here is the output of the debugger:
```
Program received signal SIGSEGV, Segmentation fault.
0x0804ef3e in MainWindow::ChangeLetter (this=0x80e5780, event=...)
    at src/abc.cpp:41
41	        image->SetBitmap(dog);
```

**Edit:** From what I can understand of all this is that at some point the memory that holds "image" is being cleared or something, so when I try to get the information that is held in the address where "image" was stored an error occurs.  Am I close?

**Edit:** Here is the source:
abc.h:
[php]#include <wx/wx.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    void ChangeLetter(wxKeyEvent& event);
    wxPanel *bg;
    wxStaticBitmap *image;
};[/php]

abc.cpp:
[php]#include "abc.h"
#include <iostream>
using namespace std;

const int ID_WINDOW = wxNewId();
const int ID_BG = wxNewId();

MainWindow::MainWindow(const wxString& title)
  : wxFrame(NULL, ID_WINDOW, title, wxDefaultPosition, wxSize(600,600),
            wxDEFAULT_FRAME_STYLE &~(wxRESIZE_BORDER|wxMAXIMIZE_BOX))
{
    Center(); // Center the window

    bg = new wxPanel(this, ID_BG);
    bg->SetFocus(); // Put focus on panel to catch keyevents

    bg->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::ChangeLetter));

    image = new wxStaticBitmap(bg, -1, wxBitmap(_T("pixmaps/bananas.png")));
}

void MainWindow::ChangeLetter(wxKeyEvent& event)
{
    int key = event.GetKeyCode();
    cout << "\"" << char(key) << "\" Pressed" << endl;
    wxBitmap dog(_T("pixmaps/dog.png")); // Get new bitmap
    cout << dog.IsOk() << endl; // View output of bitmap check
    if (dog.IsOk())
    {
        image->SetBitmap(dog); // Display new bitmap (segfault)
    }
    event.Skip();
}[/php]

---

### Post by Zugzwang on 2010-05-18
Hmm, ist is possible that the key handler is called before the line " image = new wxStaticBitmap(bg, -1, wxBitmap(_T("pixmaps/bananas.png")));" has been executed? 

If this was the case, "image" would still be uninitialised, which would correspond to the error given. putting the "image = new wxStaticBitmap(bg, -1, wxBitmap(_T("pixmaps/bananas.png")));" line as the first line in the constructor.

---

### Post by dodle on 2010-05-18
I can't put it as the first line in the constructor because "bg" has to be defined first.  But I did put it after defining "image" and got the same result:
[php]MainWindow::MainWindow(const wxString& title)
  : wxFrame(NULL, ID_WINDOW, title, wxDefaultPosition, wxSize(600,600),
            wxDEFAULT_FRAME_STYLE &~(wxRESIZE_BORDER|wxMAXIMIZE_BOX))
{
    Center(); // Center the window

    bg = new wxPanel(this, ID_BG);
    bg->SetFocus();

    image = new wxStaticBitmap(bg, -1, wxBitmap(_T("pixmaps/bananas.png")));

    bg->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::ChangeLetter));
}[/php]

---

### Post by dodle on 2010-05-18
[http://wxforum.shadonet.com/viewtopic.php?t=27847](http://wxforum.shadonet.com/viewtopic.php?t=27847)

[quote="tan"]OK, all is clear :)
With **image** all is OK, the problem is **Connect**, it must be:
```

bg->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::ChangeLetter), 0, this);

```
It is tipical error with Connect() :)[/quote]

---

