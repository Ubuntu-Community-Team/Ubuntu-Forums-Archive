---
title: "how to specify the compiler path for wxBitmap"
date: 2008-12-27
forum: Programming Talk
---

### Post by Jonas thomas on 2008-12-27
Hello,
I've been working my way through the zetcode tutorial using the gnu compiler and code::blocks IDE and I've run into a bit of a snag in this  [tutorial]("http://www.zetcode.com/tutorials/wxwidgetstutorial/widgets/") in the wxBitmapbutton code sample

Basically here is the code snippet I'm having an issue with:

```
void BitmapButton::OnScroll(wxScrollEvent& event)
{
  pos = slider->GetValue(); 

  if (pos == 0) {
      button->SetBitmapLabel(wxBitmap(wxT("mute.png"), wxBITMAP_TYPE_PNG));
  } else if (pos > 0 && pos <= 30 ) {
      button->SetBitmapLabel(wxBitmap(wxT("min.png"), wxBITMAP_TYPE_PNG));
  } else if (pos > 30 && pos < 80 ) {
      button->SetBitmapLabel(wxBitmap(wxT("med.png"), wxBITMAP_TYPE_PNG));
  } else {
      button->SetBitmapLabel(wxBitmap(wxT("max.png"), wxBITMAP_TYPE_PNG));
  }
}

```

I'm assuming that you would normally expect to see mute.png(et.al) in the same directory as the executables right???  
What would be the correct way to have the compiler to know where to look so I don't get this error?:
> obj/Debug/bitmapbutton.o||In function `BitmapButton::OnScroll(wxScrollEvent&)':|
/home/jonas/projects/zedcode_tutorials/Widgets I/wxBitmapButton/bitmapbutton.cpp|25|undefined reference to `wxBitmap::wxBitmap(wxString 


---

### Post by monkeyking on 2008-12-27
I have no idea what wxbitmap is.

But I don't think what you're seeing has something with your png file.
The problem is that it cant linker can't find the .so file that has the actual implementation of wxbitmap.

You should try including it like

g++ yourprog.cpp -lwxbitmap 

or something similar

---------------
edit

I checked your tutorial
[http://www.zetcode.com/tutorials/wxwidgetstutorial/firstprograms/](http://www.zetcode.com/tutorials/wxwidgetstutorial/firstprograms/)

it says to compile like
g++ main.cpp main.h simple.cpp simple.h  `wx-config --cxxflags --libs` -o simple

Did you go through the entire tutorial, otherwise post your comple command for compiling.

---

### Post by Jonas thomas on 2008-12-28
Ok... Thank you for your thoughts... It didn't solve my problem.. but it did get me closer..
Perhaps I should elaborate further..
I'm basically trying to learn about c++, the gnu compiler, Code::blocks IDE and wxWidgets simultaneously.  I've been pretty rigorous about working through every zetcode wxwidgests example and have learned much. Basically I learned there is a lot more to learn:rolleyes::rolleyes:

I actually ran across a a unreported wxwidgets bug in another example.
Anyway, this example that has thrown me for a loop. 

I created the required png files and moved them over to the same directory as the source.  When I compile from the terminal prompt:
```
 g++ main.cpp main.h bitmapbutton.cpp bitmapbutton.h `wx-config --cxxflags --libs` -o runthisjunk
```
The program compiles and runs just fine....
So the issue is basically with my IDE, and the compiler or more specifically my lack of understanding.

My current folder structure looks like this.
```
jonas@Ubuntu4:~/projects/zetcode_tutorials/Widgets_I/wxBitmapButton$ ls -R
.:
bin               bitmapbutton.h  main.h   med.png  mute.png  runthisjunk         wxBitmapButton.depend
bitmapbutton.cpp  main.cpp        max.png  min.png  obj       wxBitmapButton.cbp  wxBitmapButton.layout

./bin:
Debug

./bin/Debug:

./obj:
Debug

./obj/Debug:
bitmapbutton.o  main.o
jonas@Ubuntu4:~/projects/zetcode_tutorials/Widgets_I/wxBitmapButton$ 
```

I'm missing some pc to this puzzle.. The Code::Block IDE is not telling the compiler where to look for the png files. So...(sorry thinking out loud here) I guess the questions is how tell it where to look?  
I don't think I want to set up an environment path or put the images in a user library at this point.
This info would be stored in the Code::Block project file to
The executable seems to be create here:
```
/home/jonas/projects/zetcode_tutorials/Widgets_I/wxBitmapButton/bin/Debug
```
So... wouldn't I want to but the PNG's there also?? I just not sure if I'm looking at this correctly.:confused:

---

### Post by Jonas thomas on 2008-12-29
Man,
Talking about barking up the wrong tree...:oops:

If your setting up a blank project in code::blocks and and your using wxwidgets you need to setup compiler and linker options.
I've been knocking off one project after another and was just copying these settings over from a previous project.
Apparently, I copied the compiler setting to the linker setting, which if I looked at what the error's where... would have told me..
Man.... was that was a stupid mistake...

---

