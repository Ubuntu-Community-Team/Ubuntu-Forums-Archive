---
title: "Vala texteditor with tabs"
date: 2011-02-09
forum: Programming Talk
---

### Post by spookykid on 2011-02-09
Hi all,

I've been cooking up a new text editor written in Vala in the line of Leafpad, but I want mine to have Tabs support. The problem is that implementing Tabs with Vala is not easy (at least for me), so any help from you vala gurus would be extremely apreciated.

```

/*
Multipad - A simple Gtk text editor with tabs

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.
      
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
      
You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
MA 02110-1301, USA.

Written by spookykid using Vala 0.11.2

Compile with valac --pkg gtk+-2.0 multipad.vala
*/

using Gtk;

class MainWindow : Window
{	

	//public DocumentTab tab {get; set;}
	//public DocumentTextView view {get; set;}	
	private DocumentNotebook note_book;
	private FileChooserDialog file_chooser_dialog;	
	private File file_name {get; default = null; set;}
	
	construct
	{
		/* TODO - Fallback defaults go here */
		stdout.printf ("MainWindow constructed\n");
	}
	
	private MainWindow ()
	{
		title = "Multipad";
		position = WindowPosition.CENTER;
		set_default_size (700, 500);
		
		note_book = new DocumentNotebook ();
		
		var h_box_main = new HBox (false, 0);
		h_box_main.border_width = 6;
		var v_box_body = new VBox (false, 0);
		v_box_body.pack_start (create_menu_bar (), false, true, 0);
		v_box_body.pack_end (h_box_main, true, true, 0);
		h_box_main.pack_start (note_book, true, true, 0);
		
		add (v_box_body);
		note_book.add_tab ("123");
	}
	
	private Widget create_menu_bar ()
	{
		var menu_file = new Menu ();
		
		var image_menu_item_new = new ImageMenuItem.from_stock (Stock.NEW, null);
		image_menu_item_new.activate.connect (on_new_clicked);
		menu_file.add (image_menu_item_new);
			
		var image_menu_item_open = new ImageMenuItem.from_stock (Stock.OPEN, null);
		image_menu_item_open.activate.connect (on_open_clicked);
		menu_file.add (image_menu_item_open);

		var image_menu_item_save = new ImageMenuItem.from_stock (Stock.SAVE, null);
		//image_menu_item_save.activate.connect (on_save_clicked);
		menu_file.add (image_menu_item_save);

		var image_menu_item_save_as = new ImageMenuItem.from_stock (Stock.SAVE_AS, null);
		//image_menu_item_save_as.activate.connect (on_save_as_clicked);
		menu_file.add (image_menu_item_save_as);
			
		var separator_menu_item = new SeparatorMenuItem();
		menu_file.add (separator_menu_item);

		var image_menu_item_quit = new ImageMenuItem.from_stock (Stock.QUIT, null);
		//image_menu_item_quit.activate.connect (on_quit_clicked);
		menu_file.add (image_menu_item_quit);

		var menu_item_file = new MenuItem.with_mnemonic ("_File");

		menu_item_file.set_submenu (menu_file);
		var menu_bar = new MenuBar ();
		menu_bar.add (menu_item_file);
		
		return menu_bar;
	}

	public void on_new_clicked ()
	{
		note_book.add_tab ("321---2nd");
	}

	private void on_open_clicked ()
	{
		file_chooser_dialog = new FileChooserDialog ("Open file", this, FileChooserAction.OPEN, Stock.CANCEL, ResponseType.CANCEL, Stock.OPEN, ResponseType.ACCEPT);
		if (file_chooser_dialog.run () == ResponseType.ACCEPT)
			{
				file_name = file_chooser_dialog.get_file ();
				//document_text_view.text_buffer.open_file (file_name);
			}
		file_chooser_dialog.destroy ();
	}
	
	public static int main (string [] args)
	{
		Gtk.init (ref args);
		var window = new MainWindow ();
		window.destroy.connect (Gtk.main_quit);
		window.show_all ();
		Gtk.main ();
		return 0;
	}
}



class DocumentTextBuffer : TextBuffer
{
    public DocumentTab tab;
	private File file_name {get; default = null; set;}
	
	construct
	{
		/* TODO - Fallback defaults go here */
		stdout.printf ("DocumentTextBuffer constructed\n");
	}
	
	public DocumentTextBuffer ()
	{
		/* TODO - send file_name to update tab label with new file_name */
		notify["file-name"].connect (() =>
		{
			stdout.printf (file_name.get_uri () + "\n");
		});
		
	}
	
	/* TODO - Use GIO instead (File.load_contents ()) */
	public void open_file (File file_name)
	{
		this.file_name = file_name;
		try
		{
			string text;
			FileUtils.get_contents (file_name.get_basename (), out text);
			this.set_text (text);
		}
		catch (Error e)
		{
			stdout.printf ("ERROR: %s\n", e.message);
		}
	}

	/* TODO - Use GIO instead (File.replace_contents ()) */
	public void save_file (File file_name)
	{
		try
		{
			string text;
			TextIter start_iter, end_iter;
			this.get_bounds (out start_iter, out end_iter);
			text = this.get_text (start_iter, end_iter, true);
			FileUtils.set_contents (file_name.get_basename (), text, -1);
			this.file_name = file_name;
		}
		catch (Error e)
		{
			stdout.printf ("ERROR: %s\n", e.message);
		}
	}
}



class DocumentTextView : TextView
{	
	construct
	{
		/* TODO - Fallback defaults go here */
		stdout.printf ("DocumentTextView constructed\n");
	}
	
	public DocumentTextView (DocumentTextBuffer doc = new DocumentTextBuffer ())
	{
			this.buffer = doc;
	}
}



class DocumentTab : HBox
{	
	public Label label_notebook;
	public Button button_notebook_close;
	private Image image_button_notebook_close;
	public signal void on_button_notebook_close_clicked ();

	construct
	{
		/* TODO - Fallback defaults go here */
		stdout.printf ("DocumentTab constructed\n");
	}
	
	public DocumentTab (string tab_label)
	{			
	    Gtk.rc_parse_string ("""
	        style "my-button-style"
	        {
	            GtkWidget::focus-padding = 0
	            GtkWidget::focus-line-width = 0
	            xthickness = 0
	            ythickness = 0
	        }
	        widget "*.my-close-button" style "my-button-style"
	    """);
		button_notebook_close = new Button ();
		button_notebook_close.set_relief (Gtk.ReliefStyle.NONE);
		button_notebook_close.name = "my-close-button";
		image_button_notebook_close = new Image.from_stock (Stock.CLOSE, Gtk.IconSize.MENU);
		button_notebook_close.add (image_button_notebook_close);
		button_notebook_close.tooltip_text = (" Close document ");
		button_notebook_close.clicked.connect (() => this.on_button_notebook_close_clicked ());
		label_notebook = new Label (tab_label);
		this.pack_start (label_notebook, true, true, 0);
		this.pack_end (button_notebook_close, true, true, 0);
		this.show_all ();
	}
}



class DocumentNotebook : Notebook
{
	public DocumentNotebook ()
	{		
		this.set_tab_pos (PositionType.TOP);
		this.set_scrollable (true);	
		this.page_added.connect (() =>
        {
			stdout.printf ("NB: New Page added: " + (this.get_n_pages () -1).to_string () + "\n");
		});
		this.page_removed.connect (() =>
        {
			stdout.printf ("NB: Page removed: " + (this.get_current_page () + 1).to_string () + "\n");
		});
		this.switch_page.connect ((page, page_num) =>
		{
			stdout.printf ("NB: Page switched: " + (this.get_current_page () + 1).to_string () + "\n");
		});		
		this.page_reordered.connect (() =>
        {
			stdout.printf ("NB: Page reordered to: " + this.get_current_page ().to_string () + "\n");
        });
	}

	public void add_tab (string tab_label)
	{
		var tab = new DocumentTab (tab_label);
		var view = new DocumentTextView ();
		
		tab.on_button_notebook_close_clicked.connect (() => this.on_button_notebook_close_clicked ());
		
		var	v_box_text_editor_body = new VBox (false, 3);
		var	scrolled_window = new ScrolledWindow (null, null);
		scrolled_window.set_policy (PolicyType.AUTOMATIC, PolicyType.AUTOMATIC);
		scrolled_window.shadow_type = ShadowType.ETCHED_IN;
		scrolled_window.add (view);
		v_box_text_editor_body.pack_start (scrolled_window, true, true, 0);

		var v_box_notebook_body = new VBox (false, 0);
		v_box_notebook_body.border_width = 2;
		v_box_notebook_body.add (v_box_text_editor_body);

		this.append_page (v_box_notebook_body, tab);
		this.child_set (v_box_notebook_body, "tab-expand", false, null);
		this.set_tab_reorderable (v_box_notebook_body, true);
		this.show_all ();
		this.set_current_page (this.get_n_pages () - 1);		
	}

	public void on_button_notebook_close_clicked ()
	{
		var note_book_page = this.get_nth_page (this.get_current_page());
		note_book_page.destroy();
	}	
}

```

Many thanks,
spook

---

### Post by timpieee on 2011-09-20
Its much easier if you use a gtk.notebook for the tabs. I'm working on a text editor too so
I'll post it soon (when its ready) but the problem for me is: How can i add a close button to a gtk.notebook?

---

