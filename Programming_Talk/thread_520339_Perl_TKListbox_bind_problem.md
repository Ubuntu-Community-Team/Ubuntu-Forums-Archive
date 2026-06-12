---
title: "Perl TK::Listbox bind problem"
date: 2007-08-08
forum: Programming Talk
---

### Post by jaime77 on 2007-08-08
HI,
im having a problem in a program i made that use Tk::Listbox.
basically in documentation say that by default it create some default binds, particular im trying to use the Up and Down, it say that inside the widget i can browse it by the keys Up and Down, but they are not working.

I read the documentation from activestate
[http://aspn.activestate.com/ASPN/docs/ActivePerl/5.8/lib/Tk/Listbox.html](http://aspn.activestate.com/ASPN/docs/ActivePerl/5.8/lib/Tk/Listbox.html)
maybe is diferent package that i have installed but i checked my Listbox.pm and it have the functions and bind for the keys... so i dont know how to make work as expected.

I have ubuntu, last version, patched at today, and Tk modules were installed from synaptic, dont know if was from ubuntu,universe or multiverse.

Even this short program dont work the bind Up and Down keys
[COLOR="Gray"]   use Tk;
   my ( @array, $scalar, $other );
   my %options = ( ReturnType => "index" );
   my $MW = MainWindow->new();
   my $lbox = $MW->Listbox()->pack();
   my @list = ( "a", "b", "c", "d", "e", "f" );
   $lbox->insert('end', @list );[/COLOR]

---

### Post by PaulFr on 2007-08-08
Add the following two lines after your $lbox->insert(...) call:```
$lbox->activate(0);
$lbox->focus;
```Basically, your widget does not have the focus. Even if you did not add these lines, pressing the Tab key would give the widget the focus and you would be able to see the effect of the Up/Down and other key bindings. See **[http://aspn.activestate.com/ASPN/docs/ActivePerl/5.8/lib/Tk/focus.html](http://aspn.activestate.com/ASPN/docs/ActivePerl/5.8/lib/Tk/focus.html)** for details on focus management.

---

### Post by jaime77 on 2007-08-08
The focus thing cross my mind since in my program (is not the example i post) i use Optionmenu for select and open files and show them in a Frame with ROtext, so i think the focus could be in ROtext after the callback from the Optionmenu (i become in problems when try to swicth from Optionmenu to Listbox) but since i actually can select and open the files (bind <<ListBoxselect>> with the callback) with the mouse but not Up and Down i dont think the focus were the problem.
But after you give me the 2 lines code, i give it a try... it works now, even the -ActiveStyle now works as expected, actually only $lbox->focus make the trick.
Thank You very much for taking the time to solve my problem, i really was hiting a wall because the frustation.

---

### Post by PaulFr on 2007-08-08
Glad to be of help :KS

---

