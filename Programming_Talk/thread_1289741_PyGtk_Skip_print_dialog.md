---
title: "PyGtk: Skip print dialog"
date: 2009-10-12
forum: Programming Talk
---

### Post by falconindy on 2009-10-12
Scenario: I've written a bash script that logs into the NY times website and pulls down the daily puzzle. Once I've got the puzzle, I'd like to be able to print it without any user input. I've looked at the code from XWord, and I'm able to essentially borrow that code to print it, but I'm unable to skip the print dialog box.

Below is the relevant code from xword.
```
    def do_print(self, dialog, res, job):
        config = job.get_config()

        if res == gnomeprint.ui.DIALOG_RESPONSE_CANCEL:
            dialog.destroy()
        elif res == gnomeprint.ui.DIALOG_RESPONSE_PREVIEW:
            self.do_preview(config, dialog)
        elif res == gnomeprint.ui.DIALOG_RESPONSE_PRINT:
            dialog.destroy()
            self.gpc = job.get_context()
            self.draw(config)
            job.close()
            job.print_()

    def print_puzzle(self, win):
        job = gnomeprint.Job(gnomeprint.config_default())
        dialog = gnomeprint.ui.Dialog(job, "Print...", 0)
        dialog.connect('response', self.do_print, job)
        dialog.set_transient_for(win)
        dialog.show()

    def print_puzzle_now(self, win):
        job = gnomeprint.Job(gnomeprint.config_default())
        job.print_()

```
I added in print_puzzle_now() so as not to disturb the other functionality.

Calling print_() brings up the print dialog box, and based on the pyGTK reference for [gnomeprint](http://www.pygtk.org/pygnomeprint/class-gnomeprintjob.html), it's not clear to me how to avoid the dialog box.

Anyone know how to accomplish this?

---

### Post by diesch on 2009-10-12
In a shell script you can use the lp command to print.

---

### Post by falconindy on 2009-10-12
> **diesch said:**
> In a shell script you can use the lp command to print.
That'd be all well and good if the file I was trying to print was text, and not binary. I need the functionality of xword to properly  parse and layout the file before printing. Sorry for not making that clear.

---

### Post by jzacsh on 2010-01-29
Did you ever figure this out?

---

### Post by Can+~ on 2010-01-29
> **jzacsh said:**
> Did you ever figure this out?

Maybe use the "lp" command?

---

### Post by louis--taylor on 2010-04-17
In case anyone finds this thread via google (like me):
I find that in this case the command
```
lpr <document to print>
```
works nicely for me

---

