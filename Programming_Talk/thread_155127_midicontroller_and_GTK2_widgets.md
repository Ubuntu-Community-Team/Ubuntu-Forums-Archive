---
title: "midicontroller and GTK2 widgets"
date: 2006-04-04
forum: Programming Talk
---

### Post by philipacamaniac on 2006-04-04
I'm not a programmer, by any means. I used to know very basic C, Visual Basic and QBasic. I need help with a program I found on Sourceforge. [MidiController]("http://sourceforge.net/projects/midicontrol/") is a very small C++ program that loads a Glade design and transfers the outputs of widgets to MIDI CC data. Very useful for creating software controllers for all my hardware (specifically, in this case, for a Line6 PODxt).

Problem is, the code only loads Scrollbars, Scales and SpinButtons. But, I really really need to be able to use Toggles and buttons (all MIDI hardware have certain settings that are just ON/OFF).

Designing the Glade interface is a piece of cake, but I don't know what to add to midicontroller.cpp to make it recognize and load (and do something with) toggle buttons.

Since it is GPL and only 12K, I've attached the cpp file in case someone can look it over and maybe hold my hand through the process.

If someone can tell me how I can use Buttons and ToggleButtons (and maybe also ComboBoxes and ListBoxes) with midicontroller.cpp, then I will design MIDI interfaces for any hardware you have (as long as it has a MIDI ref manual).

---

### Post by philipacamaniac on 2006-04-06
Okay, how about this.

Is there anyway from within Glade to translate the actions of one widget to a numerical value in another widget?

EXAMPLE: I have a combobox with 22 text entries. When I select the first entry, it sends a signal to a SpinButton widget to change to the number "1".

It is convoluted, but it would work, since the midicontroller program at this point can only read "adjustment value" type widgets, so I would have it read all the second-level SpinButton widgets, which are really controlled by first-level ToggleButtons and ComboBoxes.

Am I crazy? Like I said, I'm not a programmer.

---

