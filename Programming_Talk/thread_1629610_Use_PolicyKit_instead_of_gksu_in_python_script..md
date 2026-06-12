---
title: "Use PolicyKit instead of gksu in python script."
date: 2010-11-23
forum: Programming Talk
---

### Post by jurialmunkey on 2010-11-23
Hi Everyone!

Wondering if someone can help me with implementing policykit to use instead of gksu in this script. Its a configuration tool for my theme: [Divergence IV - A New Hope]("http://jurialmunkey.deviantart.com/art/Divergence-IV-quot-A-New-Hope-quot-183377193")

I need root permissions so that the customisation tool can edit the theme in "/usr/share/themes/". Running the whole script as root is not an option as gnome-appearance-preferences has to be called by the user, not root. The issue with gksu is that Fedora does not package/distribute it. Also, policykit just seems like a better way of doing things.

I had the idea of using Zenity to get the user to input their password, saving the password to a global string then passing that string to sudo via echo. But that just seems to have "bad security practice" written all over it.

If anyone could help it would be much appreciated. I had a lot of trouble finding any sort of tutorial on the matter.

```
#!/usr/bin/env python
_app_name = "Orta Configurator"
_version = "0.1"
_bugs = "Please report all bugs to <valiant.wing@gmail.com>."
_config_header = """#
# Orta Config File
#
#
"""

import pygtk
pygtk.require("2.0")
import gtk
import sys
import os
import urllib2
import shutil
import subprocess


_filename = os.path.basename(sys.argv[0])
_curdir = os.path.dirname(os.path.realpath(sys.argv[0]))

# GLOBALS
panel_type = 1
tab_type = 1
scrollbar_type = 1
nautilus_type = 1
menu_type = 1

gtk_breadcrumbs_check = False


class OrtaConfigurator:

# PANEL TAB
	def on_default_panel_toggled(self, widget, data=None):
		global panel_type
		panel_type = 1

	def on_raised_panel_toggled(self, widget, data=None):
		global panel_type
		panel_type = 2

	def on_light_panel_toggled(self, widget, data=None):
		global panel_type
		panel_type = 3

# TABS TAB
	def on_tabs_default_toggled(self, widget, data=None):
		global tab_type
		tab_type = 1

	def on_tabs_dark_toggled(self, widget, data=None):
		global tab_type
		tab_type = 2


# SCROLLBARS TAB
	def on_scrollbars_default_toggled(self, widget, data=None):
		global scrollbar_type
		scrollbar_type = 1

	def on_scrollbars_dark_toggled(self, widget, data=None):
		global scrollbar_type
		scrollbar_type = 2

# NAUTILUS TAB
	def on_nautilus_default_toggled(self, widget, data=None):
		global nautilus_type
		nautilus_type = 1

	def on_nautilus_tesb_toggled(self, widget, data=None):
		global nautilus_type
		nautilus_type = 2

	def on_nautilus_rotj_toggled(self, widget, data=None):
		global nautilus_type
		nautilus_type = 3

	def on_gtk_breadcrumbs_checked(self, widget, data=None):
		global gtk_breadcrumbs_check
		if gtk_breadcrumbs_check :
			gtk_breadcrumbs_check = False
		else :
			gtk_breadcrumbs_check = True

# MENUS TAB
	def on_menu_default_toggled(self, widget, data=None):
		global menu_type
		menu_type = 1

	def on_menu_squared_toggled(self, widget, data=None):
		global menu_type
		menu_type = 2

	def on_menu_raised_toggled(self, widget, data=None):
		global menu_type
		menu_type = 3




# SAVE BUTTON CLICKED		
	def on_save_clicked(self, widget, data=None):
	# PANEL TYPE
		if panel_type == 1 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/panel-sunken.rc gtk-2.0/Styles/panel.rc'")
		elif panel_type == 2 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/panel-raised.rc gtk-2.0/Styles/panel.rc'")
		elif panel_type == 3 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/panel-light.rc gtk-2.0/Styles/panel.rc'")
	# TAB TYPE
		if tab_type == 1 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/notebook-light.rc gtk-2.0/Styles/notebook.rc'")
		elif tab_type == 2 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/notebook-dark.rc gtk-2.0/Styles/notebook.rc'")

	# SCROLLBAR TYPE
		if scrollbar_type == 1 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/scrollbar-light.rc gtk-2.0/Styles/scrollbar.rc'")
		elif scrollbar_type == 2 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/scrollbar-dark.rc gtk-2.0/Styles/scrollbar.rc'")

	# NAUTILUS TYPE
		if nautilus_type == 1 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/toolbar-dark.rc gtk-2.0/Styles/toolbar.rc'")
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/nautilus-ANH.rc gtk-2.0/Styles/nautilus.rc'")
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/breadcrumbs-dark.rc gtk-2.0/Styles/breadcrumbs.rc'")
		elif nautilus_type == 2 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/toolbar-dark.rc gtk-2.0/Styles/toolbar.rc'")
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/nautilus-TESB.rc gtk-2.0/Styles/nautilus.rc'")
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/breadcrumbs-dark.rc gtk-2.0/Styles/breadcrumbs.rc'")
		elif nautilus_type == 3 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/toolbar-light.rc gtk-2.0/Styles/toolbar.rc'")
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/nautilus-ROTJ.rc gtk-2.0/Styles/nautilus.rc'")
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/breadcrumbs-light.rc gtk-2.0/Styles/breadcrumbs.rc'")

	# ELEMENTARY OR GTK BREADCRUMBS CHECK
		if gtk_breadcrumbs_check :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/null.rc gtk-2.0/Styles/breadcrumbs.rc'")

	# MENU TYPE
		if menu_type == 1 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/menu-round.rc gtk-2.0/Styles/menu.rc'")
		elif menu_type == 2 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/menu-lessround.rc gtk-2.0/Styles/menu.rc'")
		elif menu_type == 3 :
			os.system("gksu 'cp --force gtk-2.0/Styles/RES/menu-raised.rc gtk-2.0/Styles/menu.rc'")

		save_dialog = self.builder.get_object("SettingsSavedDialog")
		save_dialog.show()

# SAVE OK DIALOG
	def on_settings_saved_ok_clicked(self, widget, data=None):
		save_dialog = self.builder.get_object("SettingsSavedDialog")
		save_dialog.hide()
		try :
			os.system("killall gnome-appearance-properties")
			subprocess.Popen('gnome-appearance-properties')
		except StandardError :
			no_gnome_dialog = self.builder.get_object("GnomeNotFoundDialog")
			no_gnome_dialog.show()

	
	def on_mainWindow_destroy(self, widget, data=None):
		gtk.main_quit()
    
	def on_quit_clicked(self, widget, data=None):
		gtk.main_quit()
 
	def __init__(self):
		self.builder = gtk.Builder()
		self.builder.add_from_file(os.path.join(_curdir, "ANewHopeConfigurator.ui"))
		self.builder.connect_signals(self)
		self.window = self.builder.get_object("mainWindow")
		self.window.show()
    
	def main_loop(self):
		gtk.main()
		return 0

def main():
    configurator = OrtaConfigurator()
    configurator.main_loop()
    
if __name__ == "__main__":
    main()
```

---

