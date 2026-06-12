---
title: "[SOLVED] QFileDialog - remembering the directory (python)"
date: 2007-11-22
forum: Programming Talk
---

### Post by NeillHog on 2007-11-22
At the moment I use

filename=QFileDialog.getOpenFileName("", "*.*", self, "Source File")
		if filename:		
			self.lineEditInputFile.setText(filename)

I would like to be able to remember the directory where the user found the file last time he/she used the dialog and present it next time that they use the dialog

The dialog does this its self between calls but not between sessions. 
Is there some easy method I am missing.

As always - a bit of code speaks a thousand words.
And - as always - thank you!

Neill

---

### Post by bongobonga on 2007-11-22
This is a coding question and does not belong in this thread. In future go to one of the Qt forums. 

But to answer your question, there is no automatic way of doing this with the Qt library. You are going to need to save the previous directory in a variable somewhere and pass that address to 'getOpenFileName' in future calls. The tidiest way of doing this is to sub-class QFileDialog

---

### Post by bongobonga on 2007-11-22
Oos, sorry!! :confused::confused: I thought that this was the 'general discussion' thread and not the programming thread. This is the correct place to ask questions like this if

---

### Post by happysmileman on 2007-11-22
I'd suggest getting the directory using the 'os' module in Python instead of trying to do it with QT (if the answer isn't obvious after reading the class reference for QFileDialog then it's probably not worth the effort)

```

import os.path

...

pathname = dirname(filedialog)

```

This assumes that filedialog is a string containing path to file, and the result will not contain a slash (it will return '/home/paul' instead of '/home/paul/') so if you need the slash add it.

---

### Post by NeillHog on 2007-11-22
Thank you happysmileman.

I'll go and read the class reference again and try and really understand it this time.

I thought there would be an easy way (easy for me that is - rather than easy for a programming guru) but I will try and do it the hard (hard for me) way.

maybe in another 40 years I'll really understand programming and no longer have to ask so many questions.

Thanks anyway.
Neill

---

### Post by NeillHog on 2007-11-24
I don't know if it is elegant but it works :-)

```
	
def _selectInputFile(self):
  # begin by getting the directory from last time		
  # initial value in case the value can not be read from the config file		
  theInputDir = ""
  # if the configuration file exists and has a directory saved
  if os.path.exists(configFile):		
    # Initialise all the fields from the .conf file
    config = ConfigParser.ConfigParser()
    config.read(configFile)  #(configFile is global)
    # if the section "dirs" exists in the .conf file
    if config.has_section("dirs"):						
       # if an entry exists then add the value to the form		
       if config.has_option("dirs", "inputdir"):				
        theInputDir = config.get("dirs", "inputdir")

  filename=QFileDialog.getOpenFileName(theInputDir, "*.*", self, "Source File")
  if filename:		
    self.lineEditInputFile.setText(filename)
    inputDirName=os.path.dirname(filename.ascii())
    self.textEditInfo.append('Input Dir: ' + inputDirName)
    # write the directory to the config file for next time			
    config = ConfigParser.ConfigParser()
    config.read(configFile)		
    if not config.has_section("dirs"):			
      config.add_section("dirs")		
    config.set("dirs", "inputdir", inputDirName)
    fpConf=open(configFile, "w")  #(configFile is global)      
    config.write(fpConf)
    fpConf.close()

```

---

