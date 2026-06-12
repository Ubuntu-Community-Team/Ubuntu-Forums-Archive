---
title: "pygtk passing data back from dialog"
date: 2010-09-08
forum: Programming Talk
---

### Post by kadil on 2010-09-08
Hi,

I am using Quickly and use the  "quickly add dialog" to create a datechoosedialog. In this dialog I inserted a calendar widget.

When I create the dialog in the program, I want to pass it an entry so the calendar selection can pass data back to the correct place.

What changes do I need to make to the dialog to allow me to pass it the entry?

Is this a good approach at all?

---

### Post by kadil on 2010-09-08
I found a way, and I think it is fairly clean. 

In the dialog I added a new method and edited the OK method as below:
    def setwidget(self,w1):
	self.w1=w1

    def ok(self, widget, data=None):
        """The user has elected to save the changes.

        Called before the dialog returns gtk.RESONSE_OK from run().
        """
	self.cal1=self.builder.get_object("calendar1")
	self.w1.set_text('%i/%i/%i'%(self.cal1.get_date()[2],self.cal1.get_date()[1]+1,self.cal1.get_date()[0]))
        pass


and in the calling method I also called the setwidget prior to run:

    def datechoose(self, widget, data=None):
        """Display the about box for timesheet."""
	print "edit pressed"
	print self.entry3.get_text()
        datechoose = DatechooseDialog.DatechooseDialog()
	datechoose.setwidget(self.entry3)
        response = datechoose.run()
        datechoose.destroy()

---

