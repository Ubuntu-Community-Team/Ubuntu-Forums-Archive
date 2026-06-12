---
title: "Menubar and Notebook"
date: 2008-08-14
forum: Programming Talk
---

### Post by hannulan on 2008-08-14
I'm working with a gui for a program which should contain a notebook and a menubar. I'm using python and pygtk. But I can't figure out how to make the notebook and menubar visible at the same time.

This is my code. 

> 
	def __init__(self):
		window = gtk.Window()
		window.set_title("TextBox")
		#.set_size_request(200,200)
		window.connect("delete_event", lambda w,e:gtk.main_quit())
		table = gtk.Table(3,6,False)
        	window.add(table)
	
		notebook = gtk.Notebook()
		notebook.show()

		menu_bar = self.create_menu()
		
		#vbox = gtk.VBox(False,0)
		#vbox.pack_start(menu_bar,False,2)
		#på raden nedanför var det nåt fel.
		#vbox.pack_start(notebook,False,2)
		#vbox.show()

		window.add(menu_bar)
		menu_bar.show()

		notebook.set_tab_pos(gtk.POS_TOP)
        	table.attach(notebook, 0,6,0,1)
        	self.show_tabs = True
        	self.show_border = True

		main_frame1 = gtk.Frame()
		main_frame1.show()
		main_label1 = gtk.Label("Inmatning")
		self.create_main_frame1(main_frame1,main_label1)

		main_frame2 = gtk.Frame()
		main_frame2.show()
		main_label2 = gtk.Label("Visning")
		self.create_main_frame2(main_frame2,main_label2)		

		notebook.append_page(main_frame1,main_label1)
		notebook.append_page(main_frame2,main_label2)
		table.show()
		#frame2 = gtk.Frame()
		#m

		window.show()


It does work, accept that the menubar isn't visible. Does someone have a clue on what I'm doing wrong, or maybe an example on how it should be written?

Thanks!

---

