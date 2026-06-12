---
title: "Is it possible to bind a function pointer to a menu element?"
date: 2010-12-28
forum: Programming Talk
---

### Post by rotohead on 2010-12-28
Hi, I'm new to this forum. :)

I'm using:
   gtkmm 2.4
   emacs 23
   g++ 4.4

I'm working on a cad program which uses a gtk::notebook for command/settings. I have one page which has menus for actions to be performed ( create line etc). But I don't want a menu selection to be performed until the notebook 'OK' button is clicked, so that the settings on other pages can be made.

So I want to record the menu selection until it will be later accomplished. 

I'm trying to bind a function pointer to a menu element so that the function can be called later.

Here's what I'm trying:

here's the function pointer syntax:
bool (*fptr) ()

these are dummy functions for testing:

// doit is the function that the function pointer should point to
bool Cnb::doit () { std::cout << "doit 0" << std::endl;; return true; }

// this is the callback function
void Cnb::on_X( bool (*vp) ())
    { spit( "cnb on_X"); std::cout << "vp = " << vp << std::endl; }

In my menu creation function:
.......
        Gtk::Menu::MenuList apml_lin = apm_lin->items();
.......

apml_lin.push_back(Gtk::Menu_Helpers::MenuElem(
                   "2 Pos", sigc::bind<bool (*) ()> (
                       sigc::mem_fun(*this, &Cnb::on_X), &Cnb::doit )));
.....

This yields the following compiler error:

prompts.cpp:162: no matching function for call to 'mem_fun( geode::Cnb&, void (*) ( bool (*) () ))'


I'm stumped. I can't find anything on the web about binding function pointer.

Any ideas?

Should I be doing this differently? I've never used function pointers before. I've tried using a void pointer, but that always gave me a compiler warning.

Thanks in advance.
Marty

---

### Post by worksofcraft on 2010-12-29
> **rotohead said:**
> Hi, I'm new to this forum. :)

I'm using:
   gtkmm 2.4
   emacs 23
   g++ 4.4

I'm working on a cad program which uses a gtk::notebook for command/settings. I have one page which has menus for actions to be performed ( create line etc). But I don't want a menu selection to be performed until the notebook 'OK' button is clicked, so that the settings on other pages can be made.

So I want to record the menu selection until it will be later accomplished. 

I'm trying to bind a function pointer to a menu element so that the function can be called later.

Here's what I'm trying:

here's the function pointer syntax:
bool (*fptr) ()

these are dummy functions for testing:

// doit is the function that the function pointer should point to
bool Cnb::doit () { std::cout << "doit 0" << std::endl;; return true; }

// this is the callback function
void Cnb::on_X( bool (*vp) ())
    { spit( "cnb on_X"); std::cout << "vp = " << vp << std::endl; }

In my menu creation function:
.......
        Gtk::Menu::MenuList apml_lin = apm_lin->items();
.......

apml_lin.push_back(Gtk::Menu_Helpers::MenuElem(
                   "2 Pos", sigc::bind<bool (*) ()> (
                       sigc::mem_fun(*this, &Cnb::on_X), &Cnb::doit )));
.....

This yields the following compiler error:

prompts.cpp:162: no matching function for call to 'mem_fun( geode::Cnb&, void (*) ( bool (*) () ))'


I'm stumped. I can't find anything on the web about binding function pointer.

Any ideas?

Should I be doing this differently? I've never used function pointers before. I've tried using a void pointer, but that always gave me a compiler warning.

Thanks in advance.
Marty

I think the problem is that the syntax is just getting to complicated...

I would start with a typedef for your function pointer... well actually what might be just the ticket is this class I made for state machines that you can simply inherit from: You call "start(...)" to set the state and then just call operator () to do it.
[php]
struct cs_state {
	typedef bool (cs_state::*state)(void); // current state "method"
	state fState; // current state of machine

	// set initial state	
	template<typename tState> bool start(tState fInitialState) {
		return (fState = (state) fInitialState) != NULL;
	}

	// constructor: has no state yet!
	cs_state(): fState(NULL) {}

	// run the state machine current state
	bool operator() (void) {
		if (!fState) throw cs_state_error(); 
		return (this->*fState)();
	} // tail recursion

	// set new state and call it
	// Unlike setting new state and returning this does not fetch
	// a new token/event so it processes the current one in the
	// next state. 
	template<typename tState> bool operator() (tState fNewState) {
		start(fNewState);
		return (*this)(); // tail recursion
	}
};
[/php]

Sadly I don't know much about gtkmm as I found it too convoluted to use. Instead I created my own wrapper class for the C language Gtk Api

---

### Post by dwhitney67 on 2010-12-29
> **rotohead said:**
> ... I have one page which has menus for actions to be performed ( create line etc). But I don't want a menu selection to be performed until the notebook 'OK' button is clicked, so that the settings on other pages can be made.

This is not a typical GUI layout; could you consider using check-boxes that are laid out on the notebook tab instead?  If not, then incorporate the check-boxes into the menu itself.

I recently have begun tinkering with gtkmm, and implemented a series of check-boxes in the menu with something like:
```

class MyWindow : public Gtk::Window
{
   ...

private:
   ...
   Glib::RefPtr<Gtk::UIManager>    m_refUIManager;
   Glib::RefPtr<Gtk::ActionGroup>  m_refActionGroup;

   Glib::RefPtr<Gtk::ToggleAction> m_optionToggle;
   ...
};

MyWindow::MyWindow()
{
   ...

   m_refActionGroup = Gtk::ActionGroup::create();

   m_optionToggle = Gtk::ToggleAction::create("Option", "Some Option", "", true);

   m_refActionGroup->add(Gtk::Action::create("OptionsMenu", "Options"));
   m_refActionGroup->add(m_optionToggle);   // note that no callback routine is defined for the toggle button.

   m_refUIManager = Gtk::UIManager::create();
   m_refUIManager->insert_action_group(m_refActionGroup);

   ...
}

```

P.S.  I forgot to add, that within the callback routine for your OK button, you can check the state of the m_optionToggle using something like:
```

void
MyWindow::okCB()
{
   bool optionSelected = m_optionToggle->get_active();

   ...
}

```

---

### Post by worksofcraft on 2010-12-29
... so I just put a quick app together to see if this what you mean:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179612&stc=1&d=1293625290[/IMG]

you select what you want it to do from the combo box, then whenever you click the button it does that... in this case I just made it write the name of the current state to the label:
[php]
#include "cs_glade.h" // the gui interface module
#include "cs_state.h"
#include <gtk/gtk.h> // gtk_init, gtk_main

using namespace cs;

struct my_app: cs_glade, cs_state {
	bool act1() { widget("label1").set("act 1"); return true; }
	bool act2() { widget("label1").set("act 2"); return true; }
	bool act3() { widget("label1").set("act 3"); return true; }
	my_app() { start(&my_app::act1); }
};

// callbacks not name mangled so gtk module can find them
extern "C" {
	bool on_button1_clicked(void *, my_app *pGlade) {
		(*pGlade)(); // do current state
		return false; // also do standard button update
	}

	bool on_comboboxentry1_changed(void *, my_app *pGlade) {
		integer iChoose = pGlade->open("comboboxentry1");
		switch (iChoose) {
		case 0: pGlade->start(&my_app::act1); break;
		case 1: pGlade->start(&my_app::act2); break;
		case 2: pGlade->start(&my_app::act3); break;
		}
		return false; // also do standard button update
	}
} // end extern "C"

int main(int argc, char *argv[], char *envp[]) {
	gtk_init(&argc, &argv); // standard gtk command line options
	my_app sApp; // get .glade file definition of user interface
	sApp.show("window1"); // display the main app window
	gtk_main(); // process gui events
	return 0;
}
[/php]
I know it uses my own glade wraper but I'm sure you can do same with proper gtkmm functions.:popcorn:

---

### Post by rotohead on 2010-12-29
Wow!
You've given me a lot to think about. Thanks! 

The state change class sound similar to functors, or at least what little I know about them. I'm going to spend so time to understand your code, and play.

Thanks a lot for getting me unstuck!
Marty

---

### Post by rotohead on 2010-12-31
Hi again... I SOLVED the problem!!! ):P

Here's what works:

I took your advice to make an alias for the function pointer... it sure cleaned up the code.

typedef void (*Fptr) (void);   // function pointer to the function to be executed later

Fptr exe_function;   // where function address will be saved

these are dummy functions for testing:

// doit is the function that the function pointer should point to, and will be executed later

bool Cnb::doit () { std::cout << "doit 0" << std::endl;; return true; }

// this is the callback function that stores the function address in exe_function

static void Cnb:on_X( Fptr fp) { exe_function = fp; }

In my menu creation function:
.......
        Gtk::Menu::MenuList apml_lin = apm_lin->items();
.......

// this passes the address of 'Cnb::doit' to 'Cnb::on_X':
        apml_lin.push_back( Gtk::Menu_Helpers::MenuElem(
                    "2 Pos", sigc::bind<0> (
                    &Cnb::on_X, &Cnb::doit )));
.....

Thanks for your help. I actually found this sigc::bind syntax while trying to get the functor method to work ( which I still haven't figured out). You got me thinking about functors, which made me google sigc::bind_functor, which yielded the page which had examples of sigc::bind. 

The functor method is supposed to be type safe, but this is adequate for what I need.

Thanks again for the mental reboot. ):P
Marty

---

### Post by worksofcraft on 2011-01-01
> **rotohead said:**
> ...
Thanks for your help. I actually found this sigc::bind syntax while trying to get the functor method to work ( which I still haven't figured out).


Hum... well I wasn't really thinking functors, but Finite State Machines (FSM) See here is part of a coffee vending machine simulator I made:
[php]
// Simulating a coffee vending Finite State Automaton
struct vending_machine: cs_glade, cs_state {
	// The possible events
	enum event { E_COFFEE, E_COIN, E_REFUND, E_TIMETICK } iEvent;

	int iFill; // Fullness of the cup of coffee in percent
	int iCredit; // Total credit

	// display status message text on status bar
	void status(const char *pText) {
		widget("Activity").set(pText);
	}
	// event handler: record the event and then run the current state
	bool have_event(event iE) {
		iEvent = iE;
		return (*this)();
	}

	// for each state I make a method to enter that state
	void start_ready();
	// ... and a method to execute the state
	bool ready();

	void start_being_annoyed();
	bool I_am_annoyed();

	void start_credit();
	bool have_credit();

	void start_making_coffee();
	bool making_coffee();

	void start_take();
	bool take();

	// and we start with credit 0 and ready for input
	vending_machine(): iCredit(0) { start_ready(); }
};

// enter the ready state
void vending_machine::start_ready() {
	status("please insert coins");
	start(&vending_machine::ready);
}
// handle event in the ready state
bool vending_machine::ready() {
	// in each state the events are handled differently
	switch (iEvent) {
	case E_COFFEE: start_being_annoyed();
	break;
	case E_COIN: start_credit(); // coin inserted -> You have credit
	break;
	case E_REFUND: start_ready(); // refund all coins and go back to ready
	break;
	default: break;
	}
	return true;
}

// just for fun scold people who ask for coffee without inserting coins
void vending_machine::start_being_annoyed() {
	status("You must insert coins first");
	start(&vending_machine::I_am_annoyed);
}
bool vending_machine::I_am_annoyed() {
	switch (iEvent) {
	case E_COFFEE: status("I said... put some money in first!");
	break;
	case E_COIN: start_credit();
	break;
	case E_REFUND: start_ready();
	break;
	default: break;
	}
	return true;
}
[/php]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=179830&stc=1&d=1293859123[/IMG]

---

