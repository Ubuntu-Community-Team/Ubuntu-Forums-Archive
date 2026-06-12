---
title: "pygtk, howto verify dialog before closing?"
date: 2010-04-13
forum: Programming Talk
---

### Post by ben72 on 2010-04-13
I'd like to verify some fields in my dialog before closing it and present a warning if all fields are not ok and avoid the closing of the dialog. It should always be possible to press the Cancel dialog. I have a Cancel button and a Save button. I'm using pygtk and glade.

My code looks like this..

class EditPatientDialog():
    def on_CancelButton_clicked(self, response, data=None):
        pass

    def on_SaveButton_clicked(self, response, data=None):
        if len(self.PnrEntry.get_text()) != 12:
            print len(self.PnrEntry.get_text())
            # here I want to cancel the ckosing of the dialog...
        self.result = gtk.RESPONSE_OK
        ....

    def __init__(self, db, patientId = -1):
        self.result = gtk.RESPONSE_CANCEL
        ....

    def run(self):
        self.dialog.run()
        self.dialog.destroy()
        return self.result, self.patientId

---

