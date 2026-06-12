---
title: "Python binary problems"
date: 2007-01-01
forum: Programming Talk
---

### Post by Hairy_Palms on 2007-01-01
this is probably a really obvious thing but for the life of me i cant find out how.
i need to read a byte of a binary file out as an integer,
the numbers is 33 (hex 21) but the read(1) method doesnt work gives me an ! , please help this poor newb :)

---

### Post by po0f on 2007-01-01
Hairy_Palms,

```
[FONT="Courier New"]int(read(1))[/FONT]
```

0x21 is ASCII for "!", [link](http://www.asciitable.com/).

---

### Post by Hairy_Palms on 2007-01-01
thanks, that works for one charactor, but it doesnt work when i want a 2 byte value to be read in :(
i have a 2 byte value of 44374 or hex (ad 56) it doesnt work on

---

### Post by ghostdog74 on 2007-01-01
what is your input file like? show some samples.

---

### Post by dwblas on 2007-01-01
Assuming you want to read an unsigned short, it's something like:```

import array

a1 = array.array('H')
fp = file(filename, 'rb')
a1.fromfile(fp, 1)
```See here for a description of array [http://docs.python.org/lib/module-array.html](http://docs.python.org/lib/module-array.html)

---

### Post by Hairy_Palms on 2007-01-01
thanks dwblas, 

@ghostdog, my sample files are any music files :) im trying to port over an old tagging program i wrote in VB to python just as a learning experiance.

---

### Post by Hairy_Palms on 2007-01-02
to save starting a new thread, i was wondering if i can ask another question here,

i have this code

```
chooser.set_select_multiple(True)
	filenames = chooser.get_filenames()
	chooser.show()	

	response = chooser.run()

	if response == gtk.RESPONSE_OK:            
            print chooser.get_filename(), 'selected'
	    self.import_meta_info(chooser.get_filename())
```

it workds fine for single files but i want to be able to  run the import_meta_info on multiple files selected in the dialog. any ideas how i can do this? ty

i presume i need a string array of sorts but i cant figure out how id use it

---

