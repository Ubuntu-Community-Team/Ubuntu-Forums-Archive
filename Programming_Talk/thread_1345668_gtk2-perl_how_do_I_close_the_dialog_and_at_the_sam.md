---
title: "gtk2-perl how do I close the dialog and at the same time run a subroutine"
date: 2009-12-04
forum: Programming Talk
---

### Post by lointaineimage on 2009-12-04
hello!
I want to destroy the dialog and call a subroutine when I click the
"yes" button,here is part of my code ,but it doesn't work well,the
dialog is closed until the subroutine is finished.waiting for your
help,thanks!

here is part of my code:
#=========================================
my $dialog =Gtk2::MessageDialog->new
  ($window,'destroy-with-parent','something to confirm','yes-no',");
  my $response = $dialog->run;
  if($response eq "yes"){
      $dialog->destroy;
      &mysubroutine;
  }

---

### Post by slavik on 2009-12-04
threads, have the dialog start a new detached thread for the subroutine.

---

### Post by lointaineimage on 2009-12-06
> **slavik said:**
> threads, have the dialog start a new detached thread for the subroutine.
thank you for replying;
i found another way by add "Gtk2->main_iteration while Gtk2->events_pending;" in my subroutine, it's simple but may not be security.

---

