---
title: "PyGTK and interface update"
date: 2010-06-23
forum: Programming Talk
---

### Post by Voland on 2010-06-23
I've got a problem with interface update when I work with os.system() command.  I've got a progressbar on my form which I want to pulse until os.system() finished. I've tried to add 
```
while gtk.events_pending():
    gtk.main_iteration(False)
```
but still no go.
Here it is my code:
```

        self.pages = self.builder.get_object("pagesspinbutton")
        pagescount = self.pages.get_value_as_int()  
        self.progressbar = self.builder.get_object("progressbar")
        
        tmpfile = filepath + "/book.ps"     
        workingfile = string.replace(filename,".pdf","") + ".ps"
        outputfile = string.replace(filename,".pdf","") + "_booklet.pdf"        
        
        command_list = ('pdf2ps \"%s\" \"%s\"' %(filename, workingfile),
                        'psbook -s%d \"%s\" \"%s\"'  %(pagescount, workingfile, tmpfile),
                        'psnup -2 -P a5 -p a4 \"%s\" > \"%s\"' %(tmpfile, workingfile),
                        'ps2pdf \"%s\" \"%s\"' %(workingfile, outputfile),
                        'rm -f  \"%s\" \"%s\"' %(tmpfile, workingfile)
                                        )
        message_list = ('Converting into PostScript...',
                        'Making broshures...',
                        'Creating booklet...',
                        'Converting into PDF...',
                        'Job has been done...'
                        )
        
        if (pagescount % 4 != 0):           
            self.builder.get_object("hbox7").show()
        else:
            self.builder.get_object("makebutton").set_sensitive(0)
            
            for i in range(len(command_list)):
                self.progressbar.set_text(message_list[i])
                keep_pulsing = True
                gobject.timeout_add(200, do_pulse)              
                print "Executing command: %s" %command_list[i]
                os.system(command_list[i])
                while gtk.events_pending():
                    gtk.main_iteration(False) 
            
            keep_pulsing = False 
            self.progressbar.set_fraction(0)
    
    def do_pulse(self,*args):
        global keep_pulsing
        if keep_pulsing:
            self.progressbar.pulse()
            return True
        return False	

```

---

### Post by alterpinguin on 2010-06-23
you should use module subprocess,
check, google for examples with it and using poll
like this one:
> [http://stackoverflow.com/questions/1378974/is-there-a-way-to-start-stop-linux-processes-with-python](http://stackoverflow.com/questions/1378974/is-there-a-way-to-start-stop-linux-processes-with-python)

look at the example 2:
Here's a little python script that starts a process, checks if it is running, waits a while, kills it, waits for it to terminate, then checks again. It uses the 'kill' command. Version 2.6 of python subprocess has a kill function. 
and so on.....

you cannot run a process and keep the parent-prog (=python) idle until the other program finishes. One way is to use the output of the started child-program and update the progressbar while you get some feedback back from stdout of the running child-program
(you did check the progressbar.py example in pygtk?)

---

### Post by Voland on 2010-06-23
[PHP][/PHP]Thank you for your reply. I've changed my code, but my goal still is not achived. I want to run Popen() and progressbar.pulse() simultaneously.
```

def do_work(self,*args):
		
		self.pages = self.builder.get_object("pagesspinbutton")
		self.margin =  self.builder.get_object("marginspinbutton")
		self.border = self.builder.get_object("borderspinbutton")
		pagescount = self.pages.get_value_as_int()
		marginvalue = self.margin.get_value_as_int()
		bordervalue = self.border.get_value_as_int()
		
		tmpfile = filepath + "/book.ps"	 
		workingfile = string.replace(filename,".pdf","") + ".ps"
		outputfile = string.replace(filename,".pdf","") + "_booklet.pdf"		
		
		command_list = (
						'pdf2ps \"%s\" \"%s\"' %(filename, workingfile),
						'psbook -s%d \"%s\" \"%s\"'  %(pagescount, workingfile, tmpfile),
						'psnup -2 -P a5 -p a4 -m %d -b %d \"%s\" > \"%s\"' %(marginvalue, bordervalue, tmpfile, workingfile),
						'ps2pdf \"%s\" \"%s\"' %(workingfile, outputfile),
						'rm -f  \"%s\" \"%s\"' %(tmpfile, workingfile)
						)
		message_list = (
						'&#1042;&#1099;&#1087;&#1086;&#1083;&#1085;&#1103;&#1077;&#1084; &#1082;&#1086;&#1085;&#1074;&#1077;&#1088;&#1090;&#1072;&#1094;&#1080;&#1102; &#1074; PostScript...',
						'&#1056;&#1072;&#1079;&#1073;&#1080;&#1074;&#1072;&#1077;&#1084; &#1085;&#1072; &#1090;&#1077;&#1090;&#1077;&#1088;&#1072;&#1076;&#1080;...',
						'&#1057;&#1086;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1073;&#1088;&#1086;&#1096;&#1102;&#1088;&#1091;...',
						'&#1042;&#1099;&#1087;&#1086;&#1083;&#1085;&#1103;&#1077;&#1084; &#1082;&#1086;&#1085;&#1074;&#1077;&#1088;&#1090;&#1072;&#1094;&#1080;&#1102; &#1074; PDF...',
						'&#1056;&#1072;&#1073;&#1086;&#1090;&#1099; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1072;...'
						)
				
		for i in range(len(command_list)):
			self.progressbar.set_text(message_list[i])			
			print "Executing command: %s" %command_list[i]
			proc = Popen(command_list[i], shell=True, stdin=PIPE, stdout=PIPE)
			proc.wait()
			self.progressbar.pulse()
			while gtk.events_pending():
				gtk.main_iteration()			
			yield True
		self.progressbar.set_fraction(0)
		yield False
	
	#making book	
	def make_book (self, widget):
		
		global pagescount
		
		self.builder.get_object("hbox7").hide()
						
		if (pagescount % 4 != 0):		   
			self.builder.get_object("hbox7").show()
		else:
			self.builder.get_object("makebutton").set_sensitive(0)
			task = self.do_work()			
			glib.idle_add(task.next)

```

---

### Post by ssam on 2010-06-23
you are using wait(), which will may your program wait until the child process has finished.

you should probably use poll(), to check if it has finished yet. [http://docs.python.org/library/subprocess.html#subprocess.Popen.poll](http://docs.python.org/library/subprocess.html#subprocess.Popen.poll)

---

### Post by StephenF on 2010-06-23
Something like this:
```

proc = Popen(command_list[i], shell=True, stdin=PIPE, stdout=PIPE)
while proc.poll() is None:
    while gtk.events_pending():
        gtk.main_iteration()
    time.sleep(0.1)

```

You probably want close_fds=True in your Popen to prevent X server IO going astray into your child process.

---

### Post by Voland on 2010-06-24
**ssam**, **StephenF**, thank you very much! It solved my problem!

---

