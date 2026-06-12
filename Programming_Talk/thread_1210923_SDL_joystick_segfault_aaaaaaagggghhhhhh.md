---
title: "SDL joystick segfault aaaaaaagggghhhhhh"
date: 2009-07-12
forum: Programming Talk
---

### Post by HyperHacker on 2009-07-12
I've been tearing my hair out for about an hour trying to figure out why SDL segfaults when calling SDL_JoystickGetButton(). If neither SDL_JoystickUpdate() or SDL_JoystickEventState(SDL_ENABLE) have been called, it returns 25(?), otherwise, it crashes.

If I rely on the event system instead, I do not get any joystick events, ever.

---

### Post by Zugzwang on 2009-07-12
For finding out where an application crashed, use "valgrind". Search in the forums for details.

Apart from that, segfaults are often results of non-checked exceptions/errors/etc. So you do check that "opening" the joystick has been done correctly? On the following page, there is some example you may try:

[http://www.libsdl.org/cgi/docwiki.cgi/SDL_JoystickOpen](http://www.libsdl.org/cgi/docwiki.cgi/SDL_JoystickOpen)

You also called "SDL_InitSubSystem(SDL_INIT_JOYSTICK);"?

If that doesn't help, post some minimal example that doesn't behave as intended here.

---

### Post by HyperHacker on 2009-07-12
Gah, how many hoops do I have to jump through to make them actually usable? Enable them twice and then enable polling separately, enable video even though I don't need it... ffff.

Anyway that seems to have fixed it (thanks!), only to expose the next problem. I made a Joystick class, which has a static function HandleSDLEvent to deal with SDL joystick events. The class also has a static member Instances, which is a std::vector containing a pointer to each instance of the class. The constructor adds itself and the destructor removes itself. HandleSDLEvent iterates this to see which joystick ID given in the event corresponds to which Joystick object.

I create a new instance of this class in the main window's configure_event callback. The insertion works fine and I can see Instances.size() is 1. Then when HandleSDLEvent is called, Instances has become empty again. :?

---

### Post by dwhitney67 on 2009-07-12
Show some freakin' code!

---

### Post by HyperHacker on 2009-07-12
[edit] Gah! I'm an idiot. The temporary copy in cMainWindow_ConfigureEvent() was being deleted and removing the entry from Instances as a result. Need a copy constructor. Doh. [/edit]

Calm down. >_> This should be all the relevant bits. (The entire program is many thousand lines, most of which is just GTK widget creation and callbacks that have nothing to do with joysticks or SDL.)

```
#define SHOWLINE DebugOut(DO_ALL, "%s:%u\n", __FILE__, __LINE__)

class Joystick {
	public:
		int NumButtons, NumAxes, NumHats;
		std::vector<bool> ButtonDown;
		std::vector<s16> AxisPos;
		std::vector<u8> HatState;
		SDL_Joystick* SDLJoy;
		
		static void HandleSDLEvent(SDL_Event *Event);
		
		Joystick();
		Joystick(int SDL_ID);
		~Joystick();
		bool Open(int ID);
		
	protected:
		int SDL_ID; //Which SDL joystick ID this is
		
		void _Create(int SDL_ID);
	
	private:
		static std::list<Joystick*> Instances;
};


class MainWindow: public Window {
	public:
		std::vector<Joystick> Joy;
		
		MainWindow();
		~MainWindow();
		
	protected:
		guint UpdateTimer;
		
	private:
		bool JoysticksInit;
		
		friend gboolean cMainWindow_UpdateTimer(gpointer Win);
		friend gboolean cMainWindow_ConfigureEvent(GtkWidget *Widget, GdkEventConfigure *Event, gpointer Win);
		friend gboolean cMainWindow_ExposeEvent(GtkWidget *Widget, GdkEventExpose *Event, gpointer Win);
};


int main(int argc, char **argv)
{
	//Init GTK
	gtk_init(&argc, &argv);
	
	//Init SDL; enable joysticks, and enable video because it has to be enabled
	//for joysticks to work
	if(SDL_Init(SDL_INIT_VIDEO | SDL_INIT_JOYSTICK) < 0)
		DebugOut(DO_MINOR, "SDL init failed: %s\n", SDL_GetError());
		
	//Maybe creating an SDL window will make joysticks work
	//SDL_putenv("SDL_VIDEODRIVER=dummy");
	if(!SDL_SetVideoMode(640, 480, 16, SDL_SWSURFACE | SDL_ANYFORMAT | SDL_NOFRAME))
		DebugOut(DO_MINOR, "SDL video init failed: %s\n", SDL_GetError());
	
	SDL_InitSubSystem(SDL_INIT_JOYSTICK);
	SDL_JoystickEventState(SDL_ENABLE);
	
	if(!gdk_gl_init_check(&argc, &argv))
		DebugOut(DO_FATAL, "GtkGlExt failed to init.\n");
		
	
	//********If this isn't done, then no joystick events are generated.
	//However, if it is, then Joystick::Instances clears itself.********
	SDL_Joystick *St = SDL_JoystickOpen(0);
	
	MainWnd = new MainWindow();
	gtk_main();
	return 0;
}


MainWindow::MainWindow()
{
	this->JoysticksInit = false;
	
	this->DrawArea = gtk_drawing_area_new();
	g_signal_connect(G_OBJECT(this->DrawArea), "configure_event",
		G_CALLBACK(cMainWindow_ConfigureEvent), this);
	this->UpdateTimer = g_timeout_add(10, cMainWindow_UpdateTimer, this);
}


gboolean cMainWindow_UpdateTimer(gpointer Win)
{
	MainWindow *_this = (MainWindow*)Win;
	SDL_Event Event;
	
	while(SDL_PollEvent(&Event))
	{
		SHOWLINE;
		switch(Event.type)
		{
			case SDL_JOYAXISMOTION:
			case SDL_JOYHATMOTION:
			case SDL_JOYBUTTONDOWN:
			case SDL_JOYBUTTONUP:
				SHOWLINE;
				Joystick::HandleSDLEvent(&Event);
			break;
		}
	}
	
	if(_this->Joy[0].ButtonDown[0]) DebugOut(DO_ALL, "Beep\x07\n");
	return TRUE;
}


gboolean cMainWindow_ConfigureEvent(GtkWidget *Widget,
GdkEventConfigure *Event, gpointer Win)
{
	MainWindow *_this = (MainWindow*)Win;
	GdkGLContext *Context = gtk_widget_get_gl_context(Widget);
	GdkGLDrawable *Drawable = gtk_widget_get_gl_drawable(Widget);

	if(!gdk_gl_drawable_gl_begin(Drawable, Context))
	{
		SHOWLINE;
		return FALSE;
	}
	
	//Connect joysticks
	if(!_this->JoysticksInit)
	{
		DebugOut(DO_STATUS, "Found %u joysticks\n", SDL_NumJoysticks());
		Joystick Joy(0);
		_this->Joy.push_back(Joy);
		_this->JoysticksInit = true;
	}
	
	return TRUE;
}


Joystick::Joystick(int SDL_ID)
{
	Joystick::Instances.push_back(this);
	//********Joystick::Instances.size() is 1********
	DebugOut(DO_ALL, "# joysticks %u\n", Joystick::Instances.size());
	this->SDLJoy = NULL;
	this->SDL_ID = SDL_ID;
	if(SDL_ID >= 0) this->Open(SDL_ID);
}


bool Joystick::Open(int ID)
{
	//********Joystick::Instances.size() is 1, even if not called from constructor********
	DebugOut(DO_ALL, "# joysticks %u, opening %d\n",
		Joystick::Instances.size(), ID);
	this->SDLJoy = SDL_JoystickOpen(ID);
	if(!this->SDLJoy)
	{
		SHOWLINE;
		DebugOut(DO_MINOR, "Failed to open joystick %d\n", SDL_ID);
		return false;
	}
	
	SHOWLINE;
	this->NumButtons = SDL_JoystickNumButtons(this->SDLJoy);
	this->NumHats = SDL_JoystickNumHats(this->SDLJoy);
	this->NumAxes = SDL_JoystickNumAxes(this->SDLJoy);
	
	SHOWLINE;
	for(int i=0; i<this->NumButtons; i++)
		this->ButtonDown.push_back(SDL_JoystickGetButton(this->SDLJoy, i));
		
	for(int i=0; i<this->NumHats; i++)
		this->HatState.push_back(SDL_JoystickGetHat(this->SDLJoy, i));
	
	for(int i=0; i<this->NumAxes; i++)
		this->AxisPos.push_back(SDL_JoystickGetAxis(this->SDLJoy, i));
	
	SHOWLINE;
	return true;
}


void Joystick::HandleSDLEvent(SDL_Event *Event)
{
	Joystick *_this = NULL;
	int ID;
	
	SHOWLINE;
	switch(Event->type)
	{
		case SDL_JOYAXISMOTION: ID = Event->jaxis.which; break;
		case SDL_JOYHATMOTION: ID = Event->jhat.which; break;
		case SDL_JOYBUTTONDOWN: ID = Event->jbutton.which; break;
		case SDL_JOYBUTTONUP: ID = Event->jbutton.which; break;
		default: return;
	}
	
	//********By here, Joystick::Instances.size() is zero again.********
	DebugOut(DO_ALL, "Looking for %d [%u]; ", ID, Joystick::Instances.size());
	for(std::list<Joystick*>::iterator i = Joystick::Instances.begin();
		i != Joystick::Instances.end(); i++)
	{
		DebugOut(DO_ALL, " %d, ", (*i)->SDL_ID);
		if((*i)->SDL_ID == ID)
		{
			_this = *i;
			break;
		}
	}
	
	DebugOut(DO_ALL, "Done\n");
	if(!_this) return;
	SHOWLINE;
	
	
	switch(Event->type)
	{
		case SDL_JOYAXISMOTION:
			_this->AxisPos[Event->jaxis.axis] =
				(abs(Event->jaxis.value) >= _this->DeadZone)
					? Event->jaxis.value : 0;
		break;
		
		case SDL_JOYHATMOTION:
			_this->HatState[Event->jhat.hat] = Event->jhat.value;
		break;
		
		case SDL_JOYBUTTONDOWN:
			SHOWLINE;
			_this->HatState[Event->jbutton.button] = true;
		break;
		
		case SDL_JOYBUTTONUP:
			_this->HatState[Event->jbutton.button] = false;
		break;
	}
}
```DebugOut() is just a wrapper for printf() and fprintf() that filters messages by importance and writes to both stdout and a file.

---

