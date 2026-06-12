---
title: "X window system error when calling XInternAtom"
date: 2017-03-18
forum: Programming Talk
---

### Post by Oinos on 2017-03-18
This is an error that I and one or two more people are experiencing when trying to run [SFML]("http://www.sfml-dev.org/"), integrated in [WxWidgets]("https://www.wxwidgets.org/") on Linux. The error ocurrs during the creation of a SFML window.

Here are the specs common to both of us:
gtk version 2
sfml version > 2.4
wxwidgets version 3.0.2
32 bit system
I'm on Ubuntu 14.04, don't know about them.

Here's the error message we both get:
> The program 'MAGEditor' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 54 error_code 10 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
AL lib: ReleaseALC: 1 device not closed
The only difference is that serial can be 54, 45 or 52.

And here's the relevant part of the backtrace the other guy posted: (I myself couldn't make a backtrace for some reason)

> #0  0x00007ffff4ec7770 in gdk_x_error (display=0x75d000, error=0x7fffffffdec0) at gdkmain-x11.c:458
#1  0x00007fffeff476fd in _XError (dpy=dpy@entry=0x75d000, rep=rep@entry=0x9c3db0) at XlibInt.c:1434
#2  0x00007fffeff44627 in handle_error (dpy=0x75d000, err=0x9c3db0, in_XReply=<optimized out>) at xcb_io.c:199
#3  0x00007fffeff446e5 in handle_response (dpy=0x75d000, response=0x9c3db0, in_XReply=<optimized out>)
    at xcb_io.c:311
#4   0x00007fffeff455f8 in _XReply (dpy=dpy@entry=0x75d000,  rep=rep@entry=0x7fffffffe0a0, extra=extra@entry=0,  discard=discard@entry=1) at xcb_io.c:621
#5  0x00007fffeff302ff in  XInternAtom (dpy=dpy@entry=0x75d000, name=0x7fffffffe1c0 "WM_PROTOCOLS",  onlyIfExists=onlyIfExists@entry=0) at IntAtom.c:181
Further below it just continues with:
> #6 sf::priv::getAtom(std::__cxx11::basic_string<char,  std::char_traits<char>, std::allocator<char> >  const&, bool) 
#7 sf::priv::WindowImplX11::setProtocols()
#8 sf::priv::WindowImplX11::WindowImplX11(unsigned long)
#9 sf::priv::WindowImpl::create(unsigned long) 
#10 sf::Window::create(unsigned long, sf::ContextSettings const&)
    return reply->atom;
}
And all those seem to be fine.

SFML is open source, so here's where it calls XInternAtom (although, for some reason, under another name):

```
xcb_atom_t getAtom(const std::string& name, bool onlyIfExists)
{
    AtomMap::const_iterator iter = atoms.find(name);

    if (iter != atoms.end())
        return iter->second;

    ScopedXcbPtr<xcb_generic_error_t> error(NULL);

    xcb_connection_t* connection = OpenConnection();

    ScopedXcbPtr<xcb_intern_atom_reply_t> reply(xcb_intern_atom_reply(
        connection,
        xcb_intern_atom(
            connection,
            onlyIfExists,
            name.size(),
            name.c_str()
        ),
        &error
    ));

    CloseConnection(connection);

    if (error || !reply)
    {
        err() << "Failed to get " << name << " atom." << std::endl;
        return XCB_ATOM_NONE;
    }

    atoms[name] = reply->atom;

    return reply->atom;
}
```
This is called from:
```
void WindowImplX11::setProtocols()
{
    xcb_atom_t wmProtocols = getAtom("WM_PROTOCOLS"); //this very first line gives the error.
//...
```


I tried reading the documentation of XInternAtom and when it throws errors, but this didn't help me with indentifying the problem. Trying to search for X window system error was even less successful - the search returned all sorts of results, but none relevantly close to mine.

What could be the cause of this problem?

---

