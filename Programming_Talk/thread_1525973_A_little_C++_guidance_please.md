---
title: "A little C++ guidance please"
date: 2010-07-07
forum: Programming Talk
---

### Post by MaxVK on 2010-07-07
Hi guys. Since moving entirely to Ubuntu a couple of years ago Iv spent quite a bit of time developing with Python and wxWidgets and Iv enjoyed it immensely. I use Geany to develop and I like that too.

So. I decided to try my hand at C++, still with wxWidgets, and having read suggestions here and elsewhere I installed CodeBlocks and wxFormBuilder. I can get a basic app working with CodeBlocks, but it feels really clunky and constricting compared to Geany so I am trying to switch back.

However (and without any surprise) Iv run into a problem. Let me first explain that I am fully aware of how bad it is to have the GUI and the code all in the same file, but I'm only experimenting for now and it wont stay like that for long (I started out like this with Python and soon switched).

Anyway, in pseudo code my file is something like this:
```
< includes >

< defines for control ID's >

class MyApp: public wxApp
{
    virtual bool OnInit();
}

class MyFrame: public wxFrame
{
    Protected controls and Public events
}

bool MyApp::OnInit()
{
    MyFrame *frame = new MyFrame
}

MyFrame::MyFrame
{
    The actual GUI code
}

< Events as defined earlier >
```

Iv tried to follow a few tutorials online, none of which seemed to work, and this is the structure that I ended up with, and it works.

However, although I can click buttons, change control labels/values etc, I am totally unable to change or return the Caption for the window. For example:

*btnEdit->SetLabel( _("New Label") );*

changes the label of the button btnEdit. However:

*MyFrame->SetLabel( _("New Label") );*

does not change the label of the window and gives me an error:"*expected unqualified-id before '->' token*"

Iv been hunting for an answer and become rather despondent at the way the C++ community seem to behave. Iv not posted a question so far because they are openly rude to newbies, and then spend 10+ posts on a forum arguing semantics among themselves and never bother to answer the original poster!

And then I remembered you guys, who were so patient with me when I changed to Ubuntu! 

So! Can anyone point me in the right direction please. I don't even know if the program is laid out correctly (although it works), and while I would very much like to continue to learn C++, I am rapidly losing interest since the community seem to be so... um... argumentative?

Cheers

M

---

### Post by Zugzwang on 2010-07-07
I don't know anything about this form builder, but I can explain your problem on the C++ level.

"btnEdit->SetLabel( _("New Label") );" is the call of the method "SetLabel" for the object "btnEdit". So far, so good.

However, "MyFrame->SetLabel( _("New Label") );" is not. "MyFrame" is a class and not (the pointer to) an object. Therefore, "SetLabel" cannot be called. Basically, you need to instantiate the "MyFrame" class before you can call a method on the object you instantiated. If you want to the set the label of a frame in one of its methods, you can simply use "SetLabel( _("New Label"));".

---

### Post by xb12x on 2010-07-07
You seem to be a nice, polite person. Are you sure you want to learn C++ ?

People fluent in C++ are the most argumentative, rude, obnoxious people on the planet. Is that what you want to become? No, I didn't think so! 

Find something else to do, and FAST!

---

### Post by MaxVK on 2010-07-07
Thanks Zugzwang
**
I tried this:

```
void MyFrame::btnEDIT_OnClick( wxCommandEvent& event )
{
    SetLabel( _("New Label"));
}
```

But while it compiles it doesnt actually do anything, although the event does do other things. Any ideas?

xb12x: :p

I'm sure they're not *all* like that, but even if they are, Ill be the exception to the rule!

---

### Post by dwhitney67 on 2010-07-07
MaxVK

Did you not state your intent was to change the title of the Frame?  If so, I believe you need to be using SetTitle().

Please read here:  [http://manuales.gfc.edu.co/wxWindows/wxwin163.html#wxframesettitle](http://manuales.gfc.edu.co/wxWindows/wxwin163.html#wxframesettitle)

---

### Post by MaxVK on 2010-07-07
Doh!

Yes, it does work now! <Sigh of relief>

Thanks dwhitney67. I got so confused while trying to change the label of a button that I forgot to change back again. <Phew!>

Things are working as expected again, so thanks for your help everyone.

M

---

