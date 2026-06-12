---
title: "[SOLVED] pointer to object tries to call non-existant constructor"
date: 2008-12-10
forum: Programming Talk
---

### Post by Bulletbeast on 2008-12-10
Hi again. Here's something that seems curious to me. The following code:

```
// settingswindow.h
#include "guitk.h"

class SettingsWindow
{
...
    private:
...     
        Button* _ok, _quit;
        Label* _l;
        Widget* _w;
...
};
```

```
// settingswindow.cpp
#include "settingswindow.h"

SettingsWindow::SettingsWindow(SDL_Surface* s)
{
    ver = SDL_Linked_Version();

    surface = s; isrunning = false;
    
    widget_manager = new WidgetManager();
}
```

```
// guitk.h
class Widget
{
    public:
        Widget(SDL_Surface* s);
...
};

class Label: public Widget
{
    public:
        Label(SDL_Surface* s);
...
};

class Button: public Label
{
    public:
        Button(SDL_Surface* s);
...
};

```

fails to compile, with the error:

```
settingswindow.cpp: In constructor ‘SettingsWindow::SettingsWindow(SDL_Surface*)’:
settingswindow.cpp:4: error: no matching function for call to ‘Button::Button()’
guitk.h:73: note: candidates are: Button::Button(SDL_Surface*)
guitk.h:71: note:                 Button::Button(const Button&)
make: *** [settingswindow.o] Error 1
```

Curiously, this happens only once, for the Button, which isn't mentioned in the constructor implementation anyway (although I intend to initialize some Buttons with *new Button(surface)*). What could I be doing wrong?

---

### Post by dwhitney67 on 2008-12-10
It took me a few minutes to duplicate the problem your having, and then to resolve it.

The problem lies here in settingswindow.h (which btw, is poor programming practice):
[php]
Button* _ok, _quit;
[/php]
Best practice is to code it like:
[php]
Button* _ok;
Button* _quit;
[/php]

P.S.  Alternatively, but not recommended:
[php]
Button *_ok, *_quit;
[/php]

---

### Post by Bulletbeast on 2008-12-11
Ah yes, I understand now. Silly me. Thanks (:

---

