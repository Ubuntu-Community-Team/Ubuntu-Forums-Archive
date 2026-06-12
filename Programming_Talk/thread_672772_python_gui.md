---
title: "python gui"
date: 2008-01-20
forum: Programming Talk
---

### Post by pavel989 on 2008-01-20
I  know that there are a few posts like this otherwise, but i haven't found my answer:

i need a simple GUI system, if u will. ive been messing around with glade and a few other things, but havent really found anything that quenches my thirst. im used to  console based apps, but figured time to move on. 

glade is horribly documented for me. i supposed its rather gtk i should be interested in. BUT im using python, so it makes a bit more difficult since the code is in c, which i understand at least a bit.

i like the way visual studio does its thing, but i understand why and how gtk does it. (methinks)

for example, in a filechooser i wanna give it a filter, ive found the documentation for that, and dont udnerstand it very much. like my python code is gonna use a glade file, if i throw something in the source, my app wouldnt pick it up, would it?

also id like for it to be easier to make it so that there relative custom positions for widgets, that would resize with the window, like columns work, but there should be a better way. if maybe im doing something wrong, please enlighten me.

---

### Post by RIchard James13 on 2008-01-20
Tkinter is simpler but some of the widgets don't have the same functionality you get from the more complicated libraries like GTK

With GLADE and the gtk.glade library you import your GUI as a XML file and then display it. From there you need to connect signals, there are programs that can do this automatically but they often use other python files. 

Once you have loaded the glade file
[PHP]        self.gladefile = "accounts.glade"  
        self.wTree = gtk.glade.XML(self.gladefile) 
[/PHP]

You can access each widget through the wTree

For example in this program I need to add some things to a Combo Box from a database
[PHP]            # populate combo boxes
            lstModel = gtk.ListStore(str)
            cmbPaymentPayee = self.wTree.get_widget("cmbPaymentPayee")
            cmbPaymentPayee.set_model(lstModel)
            cell = gtk.CellRendererText()
            cmbPaymentPayee.pack_start(cell)
            result_set = self.accountsDB.runQuery("SELECT txtPayee FROM tblPayees")
            for row in result_set:
                lstModel.append([row[0]])
[/PHP]

as you can see I used get_widget to get the reference to the widget I want to alter. But because it is a combo-box and not a simple text box widget I have to make the CellRenderer and the lstModel. Whereas in say Visual Studio the widget already has those things. 

In order to alter the spacing and packing of widgets on a resizable form, I fiddle with the properties->packing tab and toggle each widgets expand and fill values depending on the way I want them to act. This doesn't always show up in the GLADE ui designer and I often have to run the app to see the effects. But instead of just putting widgets onto a form like in Visual Studio I now take some time and think about resizing first and then I use vboxes and hboxes and group similar controls into them. So I have a top level window that has one vbox and in that vbox might be several smaller vboxes or hboxes and so on until I start packing widgets into the vbox/hboxes. That doesn't mean I don't put widgets into the higher level vboxes just that I divide my space by vboxes.

---

### Post by pmasiar on 2008-01-20
[http://wiki.python.org/moin/EasyGui](http://wiki.python.org/moin/EasyGui) : very simple, very easy GUI programming in Python. It allows you to get input from a user using simple dialog boxes and a functional (not event-driven) programming style

Homepage looks down ATM :-(

showmedo has tutorials: [http://showmedo.com/videos/series?name=IwrOgqPc9](http://showmedo.com/videos/series?name=IwrOgqPc9)

---

