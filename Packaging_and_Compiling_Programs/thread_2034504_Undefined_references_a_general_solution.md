---
title: "Undefined references a general solution?"
date: 2012-07-28
forum: Packaging and Compiling Programs
---

### Post by Disane on 2012-07-28
Hi all!

I'm relatively new to Linux and your forum. I'm trying to create a pulse audio application which monitors the incoming signals from the external microphone. I've found Pulse Audio Volume Control or PAVU for short and I'm currently using using its source code to get things done. Unfortunately I keep running into missing reference and I fail to find out which library do I need when I want a reference to. (I'm using the latest version of codelite ver 4.0+. )

```
#include <stdio.h>
#include <iostream>
#include <gtkmm.h>
#include <canberra-gtk.h>

#include <pulse/pulseaudio.h>
#include <pulse/glib-mainloop.h>
#include <pulse/ext-stream-restore.h>
#include <pulse/ext-device-manager.h>
using namespace std;

#define GLADE_FILE_NAME "pa_ms.glade"
#define APP_NAME "org.gtkmm.Pulse_Audio_Microphone_Stream"
#define MAIN_WINDOW_NAME "winMain"

Gtk::Window* pwinMain = NULL;

static void on_button_quit_clicked()
{
    if(pwinMain)
        pwinMain->hide(); // closes the main window and main::run() ends
}

int main(int argc, char **argv)
{
        printf("Welcome to Pulse Audio Microphone Stream App.\n");
    
        // ignore SIGPIPE
        signal(SIGPIPE, SIG_IGN);
    
        // this should be made failsafe somehow using try-catch
        Glib::RefPtr<Gtk::Application> app = Gtk::Application::create(argc,argv,APP_NAME);
    
        // initializing libcanberra ,FAILS cause it uses old GTK 2+ modules
        //ca_context* ca_cx = ca_gtk_context_get();
        /*if(ca_cx)
        {
            int ca_err = ca_context_set_driver(ca_cx,"pulse");
            //cout << "ERROR: "<< ca_strerror(ca_err) << endl;
        }
        else
        {
            cout << "ERROR: Unable to access canberra context!" << endl;
        }*/
        
        pa_glib_mainloop *m = pa_glib_mainloop_new(g_main_context_default());
        
        // this stuff should be done elsewhere (create a MainWindow class)
        Glib::RefPtr<Gtk::Builder> refBuilder = Gtk::Builder::create();
        if(refBuilder)
        {
            try
            {
                // loading .glade file
                refBuilder->add_from_file(GLADE_FILE_NAME);
            }
            catch(const Glib::FileError& ex)
            {
                std::cerr << "FileError: " << ex.what() << std::endl;
                return 1;
            }
            catch(const Glib::MarkupError& ex)
            {
                std::cerr << "MarkupError: " << ex.what() << std::endl;
                return 1;
            }
            catch(const Gtk::BuilderError& ex)
            {
                std::cerr << "BuilderError: " << ex.what() << std::endl;
                return 1;
            }
        }
        
        // extracting winMain 
        refBuilder->get_widget(MAIN_WINDOW_NAME, pwinMain);
        if(pwinMain)
        {
            Gtk::Button *pbtnQuit = NULL;
            refBuilder->get_widget("btnQuit", pbtnQuit);
            if(pbtnQuit)
            {
                pbtnQuit->signal_clicked().connect( sigc::ptr_fun(on_button_quit_clicked) );
            }
            
            app->run(*pwinMain);
        }
        
        // release mainWindow
        delete pwinMain;
    
    
    return 0;
}
```


I've listed the following libraries in the Linker options in codelite: 

libpulse-simple.so
libpulse.so
libgtkmm-3.0.so
libcanberra.so
libglibmm-2.4.so
libgiomm-2.4.so

but i still get Missing reference to pa_glib_mainloop_new().

My question is: Is there a way to find out how the library is named and where it can be found?
For example by typing the name of the install package into the Terminal and getting a list of installed library files and their install Dir?

---

### Post by Disane on 2012-07-28
Right guys, I think I've found the solution to my question. Not sure how you guys are doing it, but to make this thread actually useful to someone. Here's what I did:

I used: ```
 dpkg --get-selections | grep libpulse
```
to find ```
libpulse-mainloop-glib0
```
after that I've searched for the installed files inside the package mentioned above using: ```
dpkg -L libpulse-mainloop-glib0
```
this listed all the installed files. That was a very educational material there. i didn't know that Ubuntu actually installs doc files too xD (Cool)
To get back to the topic, I've noticed:

```
/usr/lib/i386-linux-gnu/libpulse-mainloop-glib.so.0
```

So I've added ```
libpulse-mainloop-glib.so
``` to my libraries in Codelite
and it worked :-)

I also solved a nasty incompatibility issue with GTK2+ and GTK3+ when calling
```
ca_gtk_context_get();
```

I hope this will help n00bs like me to solve development issues quickly under Linux and sorry for wasting your times...

---

### Post by MadCow108 on 2012-07-31
if you have the required library installed you can also search for the missing symbol directly to get the package that contains it:
```
grep pa_glib_mainloop_new /var/lib/dpkg/info/*symbols
/var/lib/dpkg/info/libpulse-mainloop-glib0:i386.symbols: pa_glib_mainloop_new@PULSE_0 1:0.99.1
```
you then just have to check how the library is named in the package with dpkg -L

apt-file is also a very useful program, it lets you search for packages based on the files they contain and they do not need to be installed.
(The equivalent for installed packages is dpkg -S)

---

