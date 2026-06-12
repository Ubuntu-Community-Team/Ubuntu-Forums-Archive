---
title: "glibmm ustring::compose"
date: 2008-05-19
forum: Programming Talk
---

### Post by graham-cracker on 2008-05-19
I'm trying to do some gtkmm programming, specifically to change the text on a Gtk::Label to a sequence of strings and numbers (converted to strings). I am trying to use this Glib::ustring::compose method. However, it doesn't seem to exist in the packaged versions of libglibmm-2.4 for Gutsy.

When I try to compile my program, I get errors on these lines

```
using Glib::ustring;
ustring labelText = ustring::compose("dX: %1 ms | dY: %2 Volts",Gnsamples / 10.0 * 1000.0 / Gfrequency,0.2 * GyScale);
```

Here is the error:
```
main.cpp: In member function ‘virtual bool GraphDrawingArea::on_expose_event(GdkEventExpose*)’:
main.cpp:202: error: ‘compose’ is not a member of ‘Glib::ustring’
make: *** [main] Error 1

```

When I looked through the local docs (installed with libglibmm-2.4-dev), ustring::compose doesn't seem to exist, however it is listed in the online documentation for glibmm-2.4 [http://www.gtkmm.org/docs/gtkmm-2.4/docs/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/index.html)

Am I doing something wrong or does ustring::compose just not exist in the packaged version of libglibmm?

Thanks in advance for your help.

---

### Post by JupiterV2 on 2008-05-19
I developed just a super-basic example to see if I could replicate your error but couldn't. I used the following code:

[PHP]#include <gtkmm.h>
#include <iostream>

using std::cout;

int main()
{
	Glib::ustring us, str = "test";
	
	us = Glib::ustring::compose("%1\n", str);
	cout << us;
	
	return 1;
}[/PHP]

The Glib::ustring::compose() member function requires you pass a variable by reference. See one of its prototypes (as taken from the gtkmm doc's):

[PHP]static ustring 	compose (const ustring& fmt, const T1& a1, const T2& a2)[/PHP]

Unlike C's printf() family of functions, you can't pass a string literal or otherwise to this function. In order to get your code to work you will have to store your calculations in a variable first before passing them as an argument.

---

### Post by graham-cracker on 2008-05-20
Hmmmm, I tried to compile the example you provided, and I'm still getting the following error:
```
main.cxx: In function ‘int main()’:
main.cxx:10: error: ‘compose’ is not a member of ‘Glib::ustring’
```
I attempted to compile it with the following command:
```
g++ main.cxx `pkg-config --libs --cflags gtkmm-2.4`
```
Are you using Hardy or Gutsy. I tend to think that the Gutsy version of gtkmm is just slightly out of date. I found a workaround:
```
char labelText[50];
snprintf(labelText,49, "dX : %4.4f ms | dY : %4.4f Volts", dx, dy);
pLabel->set_text(labelText);
```
When I get a chance I'll test this out on my laptop (which has Hardy) and see if I'm getting the same problems.

---

### Post by JupiterV2 on 2008-05-20
I am using Hardy.

I compiled and ran with the following (which is essentially, identical to what you typed):

```
g++ -o test compose.cpp `pkg-config gtkmm-2.4 --cflags --libs` && ./test
```

Another alternative would be to use a stringstream but yours should work just fine. Glad you found a solution.

---

