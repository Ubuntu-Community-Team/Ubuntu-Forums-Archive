---
title: "[SOLVED] Conditional widget"
date: 2008-01-14
forum: Programming Talk
---

### Post by srikrishnan on 2008-01-14
Hi All,

I have created a simple perl TK Dialog Box. In this I created a
radiobutton in order to select either one of the option. If the user
select first, I want to display a widget below that to choose some
more option. If user select second, I want to destroy the widget. I
have successfully done this using "Destroy" in the if condition.

But if user going to change their mind and again select the first. It
will not display the widget.

My sample coding is as follows:

use Tk 800.000;
use strict;
use Warnings;
use Win32::GUI;

my $tagVar;
my $TxVar;

my $mw = MainWindow -> new;

my $sel3 = $mw -> Frame -> pack(-anchor => 'w', -padx => '10', -pady
=> '0');
$sel3 -> Label (-text => 'Tags:') -> pack(-side => 'left');

foreach (qw(optional all)) {
$sel3 -> Radiobutton(-text => $_,
-value => $_,
-variable => \$tagVar,
-command => \&set_Tag)->pack(-side => 'left');
}

my $sel4 = $mw -> Frame -> pack(-fill => 'both', -expand => '1', -padx
=> '10', -pady => '0');

MainLoop;

sub set_Tag {
if ($tagVar eq "optional") {
$sel4 -> Checkbutton (-text => 'Text', -variable => \$TxVar) ->
pack(-side => 'left', -fill => 'both', -expand => '1');
}
else {
$sel4->destroy if Tk::Exists($sel4);
}
}

Please anybody help me to solve this problem.

Regards,
Srikrishnan

---

### Post by popch on 2008-01-14
Have you considered not destroying but just hiding the widget or even only disabling it? Un-hiding would presumably be much simpler than un-destryoing.

Widgets disappearing from view and popping into view from out of nothing are not usually expected behaviour of a GUI.

---

### Post by srikrishnan on 2008-01-14
Hi,

Thanks for your response.

Can you give me an example for hiding and unhiding a widget. I have tried many times but unable to succeed.

Thanks,

Srikrishnan

---

### Post by srikrishnan on 2008-01-15
Hi All,

Can anybody give me an example for hide and unhide a widget by checking or uncheck through a radiobutton?

Regards,
Srikrishnan

---

