---
title: "Eclipse"
date: 2006-02-21
forum: Programming Talk
---

### Post by ignorance on 2006-02-21
Well everything installed fine and the java application is working nicely, but since we also get cobol and i don't like going to windows for that i installed the cobol-plugin, but it isn't working when i try to start a new cobol project it refuses and gives me an error which is posted in the error log which i can't find. Now where can i find that error log, how can i fix the problem so i can run cobol in eclipse and does anyone knows a free compiler for compiling cobol?

---

### Post by JoshuaPDavis on 2006-02-21
I don't know anything about COBOL, but I can help you with the eclipse side of your question.

You can find your eclipse error log from inside eclipse by selecting from the menu Window -> Show View -> Error Log.  If you don't see Error Log under Show View, then select Other... and then select PDE Runtime -> Error Log.

You can also find your error log on the file system under <workspace_dir>/.metadata/.log .

Josh

---

### Post by ignorance on 2006-02-21
thnx now i had a view on it and it gave me this error

Problems occurred when invoking code from plug-in: "org.eclipse.jface".

so does this means bad plug-in?

---

### Post by JoshuaPDavis on 2006-02-21
Without knowing any specifics about your COBOL plug-in or your Eclipse version, my best guess is that your plug-in expects a different version of Eclipse, or more specifically, a different version of SWT.

My suggestion would be to check your plug-in's documentation to find out what  version of eclipse it works with, or to try another COBOL plug-in (if such exists) or another COBOL IDE.  I can't make any recommendations, as I am not a COBOL programmer, and the few COBOL programmers that I have met used Microsoft WordPad as their "IDE".

Josh

---

### Post by ignorance on 2006-02-21
well i suppose using gedit is just as good as WordPad but i need a decend compiler. and that is what i cannot find.

---

### Post by Moonbuzz on 2006-04-27
The [Eclipse plugin]("http://www.eclipse.org/cobol/") only allows you to use Eclipse as an IDE over an existing compiler, I checked, and it uses Fujitsu' NetCOBOL compiler, but I think that ACUcobol has their own plugin. At either case you'll need to have the compiler installed on your machine prior to using Eclipse.
As it is, I don't find Eclipse or other IDE's that important with COBOL, they're more needed when you're using a library/class heavy OO language like Java. With COBOL, you should be fine and dandy with vi or emacs.

---

### Post by Moonbuzz on 2006-04-27
[QUOTE=ignorance]well i suppose using gedit is just as good as WordPad but i need a decend compiler. and that is what i cannot find.[/QUOTE]
For Windows or GNU/Linux?

---

### Post by adssse on 2006-08-10
If you are looking for a free cobol compiler, take a look at tinycobol. I believe it implements the 85 standard and it is cli, but its what I use when I need to do some cobol.

---

