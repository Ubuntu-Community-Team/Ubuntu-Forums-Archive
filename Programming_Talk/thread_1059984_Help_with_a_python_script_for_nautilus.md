---
title: "Help with a python script for nautilus"
date: 2009-02-04
forum: Programming Talk
---

### Post by Major_Kong on 2009-02-04
I'm trying to make a python script that adds a new column for nautilus (a image size column). A new column is added, but it doesn't seem to work... 

Problems: I am unable to add just one column, so i made a 'dummy' column, date.
And i can't seem to get the size of the image...

The code:
```

#!/usr/bin/python

# this script can installed to the user account by running the following commands:

# sudo apt-get install python-nautilus
# mkdir ~/.nautilus/python-extensions
# cp dimc.py ~/.nautilus/python-extensions
# chmod a+x ~/.nautilus/python-extensions/dimc.py


import nautilus
import urllib
# for extracting the image size
import Image

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
	def __init__(self):
		pass

	def get_columns(self):
		return (
			nautilus.Column("NautilusPython::img_dimensions_column",
					"img_dimensions",
					"Dimensions",
					"Image dimensions"),
			nautilus.Column("NautilusPython::date_column",
				"date",
				"Date",
				"Date")
			)

	def update_file_info(self, file):
		if file.get_uri_scheme() != 'file':
			return

		if file.is_mime_type('image/jpeg') or file.is_mime_type('image/png') or file.is_mime_type('image/gif'):
			filename = urllib.unquote(file.get_uri()[7:])
			im = Image.open(filename)		
			file.add_string_attribute('dimensions', str(im.size[0]) + " x " + str(im.size[1]) )
		else:
			file.add_string_attribute('dimensions', '')

		file.add_string_attribute('date', '')
		self.get_columns() 	
```

Help please ?

---

### Post by Major_Kong on 2009-02-04
Found out the problem for myself:

```
#!/usr/bin/python

# this script can installed to the user account by running the following commands:

# sudo apt-get install python-nautilus
# mkdir ~/.nautilus/python-extensions
# cp imgsc.py ~/.nautilus/python-extensions
# chmod a+x ~/.nautilus/python-extensions/imgsc.py


import nautilus
import urllib
# for extracting the image size
import Image

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
	def __init__(self):
		pass

	def get_columns(self):
		return (nautilus.Column("NautilusPython::img_size_column",
					"img_size",
					"Image Size",
					"Image Size"),
			nautilus.Column("NautilusPython::img_width_column",
					"img_width",
					"Width",
					"Image Width"),
			nautilus.Column("NautilusPython::img_height_column",
					"img_height",
					"Height",
					"Image height")
			)

	def update_file_info(self, file):
		if file.get_uri_scheme() != 'file':
			return

		if file.is_mime_type('image/jpeg') or file.is_mime_type('image/png') or file.is_mime_type('image/gif'):
			filename = urllib.unquote(file.get_uri()[7:])
			im = Image.open(filename)		
			file.add_string_attribute('img_size', str(im.size[0]) + ' x ' + str(im.size[1]) )
			file.add_string_attribute('img_width', str(im.size[0]))
			file.add_string_attribute('img_height', str(im.size[1]))
		else:
			file.add_string_attribute('img_size', '')
			file.add_string_attribute('img_width', '')
			file.add_string_attribute('img_height', '')


		self.get_columns() 		
		
```

Didn't find a solution for adding just one column, but i guess it's not that important.

---

