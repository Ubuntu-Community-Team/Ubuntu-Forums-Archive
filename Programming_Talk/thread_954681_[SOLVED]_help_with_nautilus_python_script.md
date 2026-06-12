---
title: "[SOLVED] help with nautilus python script"
date: 2008-10-21
forum: Programming Talk
---

### Post by giuspen on 2008-10-21
Hi, I'm working on a python script which adds to nautilus the option to send a copy of the selected file(s)/folder(s) similar to the windows option.
My script works but during the copy nautilus freezes and comes back to life only at the end of the copying.
This is very bad, I would like to disjoin the copy from keeping nautilus busy, the best would be to have access to the same process who starts with Ctrl+C and Ctrl+V.
I copy here the code, if somebody has some idea please help me. Thanks.
PS to make it work: install python-nautilus, copy the script in .nautilus/python-extensions, make the script executable, killall nautilus.

#!/usr/bin/env python

import nautilus
import gconf
import os
import urllib

choose_destination = 'zenity --title="Choose the destination" --file-selection --directory'
file_already_exists = 'zenity --question --text "Warning: the file %s already exists in %s, shall I replace?"'
dir_already_exists = 'zenity --question --text "Warning: the folder %s already exists in %s, shall I replace?"'
err_same_source_dest = 'zenity --error --text "Error: destination and source are the same!"'
err_no_write_access = 'zenity --error --text "Error: you have no write access to %s"'
err_unexpected = 'zenity --error --text "Unexpected error: copy aborted"'
progress_info = '|zenity --progress --pulsate --auto-close --text="Copying %s to %s..."'
nautilus_menu_label = 'Copy to Browsed Place'
nautilus_menu_help = 'Copy the selected file(s)/folder(s) to a browsed place'

class CopyToBrowsedPlace(nautilus.MenuProvider):
	def __init__(self):
		self.client = gconf.client_get_default()

	def open_dialog(self, menu, sel_items):
		try:
			destination_root = os.popen(choose_destination).read().replace('\n', '')
			if destination_root == "":
				return
			if not os.access(destination_root, os.W_OK):
				os.system(err_no_write_access % destination_root)
				return	
			for sel_item in sel_items:
				source_path = urllib.unquote(sel_item.get_uri()[7:])
				basename = os.path.basename(source_path)
				destination_path = os.path.join(destination_root, basename)
				if destination_path == source_path:
					os.system(err_same_source_dest)
					break
				if os.path.exists(destination_path):
					if os.path.isfile(source_path):
						if os.system(file_already_exists % (basename, destination_root)) != 0:
							continue
					else:
						if os.system(dir_already_exists % (basename, destination_root)) != 0:
							continue	
				os.system('cp -af \'' + source_path + '\' ' + '\'' + destination_path + '\'' + progress_info % (basename, destination_root))
		except:
			os.system(err_unexpected)

	def get_file_items(self, window, sel_items):
		item = nautilus.MenuItem('NautilusPython::gtk-copy', nautilus_menu_label, nautilus_menu_help)
		item.set_property('icon', 'gtk-copy')
		item.connect('activate', self.open_dialog, sel_items)
		return item,

---

### Post by alberto ferreira on 2008-10-21
Please insert the code portion within PHP brackets:

[ PHP]
your code
[ /PHP]

without the spaces after the [

(or select the code and press the "php" in a sheet of paper icon in the advanced editing mode)

---

### Post by unutbu on 2008-10-21
Try changing

```
				os.system('cp -af \'' + source_path + '\' ' + '\'' + destination_path + '\'' + progress_info % (basename, destination_root))
```

to
```

				os.system(('cp -af \'' + source_path + '\' ' + '\'' + destination_path + '\'' + progress_info + ' &') % (basename, destination_root))
```


The ampersand (&) should tell os.system to run the cp command in the background, thus allowing the python script to continue before the cp command finishes.

Also, you'll need to wrap your string concatenation in a big parenthesis so the 
" %(basename, destination_root)" will be applied to progress_info, and not just to the ' &' I tacked onto the end.

---

### Post by giuspen on 2008-10-22
> **alberto ferreira said:**
> Please insert the code portion within PHP brackets:

[ PHP]
your code
[ /PHP]

without the spaces after the [

(or select the code and press the "php" in a sheet of paper icon in the advanced editing mode)

this evening I will do this thanks (in office now)

---

### Post by giuspen on 2008-10-22
> **unutbu said:**
> Try changing

```
				os.system('cp -af \'' + source_path + '\' ' + '\'' + destination_path + '\'' + progress_info % (basename, destination_root))
```

to
```

				os.system(('cp -af \'' + source_path + '\' ' + '\'' + destination_path + '\'' + progress_info + ' &') % (basename, destination_root))
```


The ampersand (&) should tell os.system to run the cp command in the background, thus allowing the python script to continue before the cp command finishes.

Also, you'll need to wrap your string concatenation in a big parenthesis so the 
" %(basename, destination_root)" will be applied to progress_info, and not just to the ' &' I tacked onto the end.

Thanks a lot, I will try asap (hope this evening).

---

### Post by giuspen on 2008-10-22
The code wrapped in php tags:
[PHP]
#!/usr/bin/env python

import nautilus
import gconf
import os
import urllib

choose_destination = 'zenity --title="Choose the destination" --file-selection --directory'
file_already_exists = 'zenity --question --text "Warning: the file %s already exists in %s, shall I replace?"'
dir_already_exists = 'zenity --question --text "Warning: the folder %s already exists in %s, shall I replace?"'
err_same_source_dest = 'zenity --error --text "Error: destination and source are the same!"'
err_no_write_access = 'zenity --error --text "Error: you have no write access to %s"'
err_unexpected = 'zenity --error --text "Unexpected error: copy aborted"'
progress_info = '|zenity --progress --pulsate --auto-close --text="Copying %s to %s..."'
nautilus_menu_label = 'Copy to Browsed Place'
nautilus_menu_help = 'Copy the selected file(s)/folder(s) to a browsed place'

class CopyToBrowsedPlace(nautilus.MenuProvider):
	def __init__(self):
		self.client = gconf.client_get_default()

	def open_dialog(self, menu, sel_items):
		try:
			destination_root = os.popen(choose_destination).read().replace('\n', '')
			if destination_root == "":
				return
			if not os.access(destination_root, os.W_OK):
				os.system(err_no_write_access % destination_root)
				return	
			for sel_item in sel_items:
				source_path = urllib.unquote(sel_item.get_uri()[7:])
				basename = os.path.basename(source_path)
				destination_path = os.path.join(destination_root, basename)
				if destination_path == source_path:
					os.system(err_same_source_dest)
					break
				if os.path.exists(destination_path):
					if os.path.isfile(source_path):
						if os.system(file_already_exists % (basename, destination_root)) != 0:
							continue
					else:
						if os.system(dir_already_exists % (basename, destination_root)) != 0:
							continue	
				os.system('cp -af \'' + source_path + '\' ' + '\'' + destination_path + '\'' + progress_info % (basename, destination_root))
		except:
			os.system(err_unexpected)

	def get_file_items(self, window, sel_items):
		item = nautilus.MenuItem('NautilusPython::gtk-copy', nautilus_menu_label, nautilus_menu_help)
		item.set_property('icon', 'gtk-copy')
		item.connect('activate', self.open_dialog, sel_items)
		return item,
[/PHP]

---

