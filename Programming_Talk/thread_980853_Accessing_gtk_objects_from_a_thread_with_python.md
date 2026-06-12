---
title: "Accessing gtk objects from a thread with python"
date: 2008-11-13
forum: Programming Talk
---

### Post by tjajab on 2008-11-13
Hello, I am trying to create a simple backup application which uses glade for the GUI. When the user presses a button, a new thread will be started backup will be made, using system.os('cp -au ...').

My problem is that the thread does not start until I quit the program (main thread?). I guess this is a locking issue. I also would like my thread to access the statusbar of my main object to tell the user how it is progressing. My code setup looks like this:
```

class BackupThread ( threading.Thread ):
    
    def __init__ ( self, statusbar ):
        self.statusbar = statusbar
        threading.Thread.__init__ ( self )

    def run ( self ):
        self.statusbar.push(1, "Backup started ...")
        os.system('gksudo "cp -au {SOME ARGUMENTS HERE}"')
        self.statusbar.push(1, "Backup finished ...")

class Backup:
    
    def on_window_destroy(self, widget, data=None):
        gtk.main_quit()
        
    def on_backupButton_clicked(self, widget, data=None):
        self.backupThread = BackupThread(self.statusbar).start()
        
    def __init__(self):
        builder = gtk.Builder()
        builder.add_from_file("backup.xml") 
        self.window = builder.get_object("window")
        self.statusbar = builder.get_object("statusbar")
        builder.connect_signals(self)
        self.events=list()
        
if __name__ == "__main__":
    editor = Backup()
    editor.window.show()
    gtk.main()

```

---

### Post by liciuslee on 2008-11-27
good 
it works

---

### Post by tjajab on 2008-11-27
For me it does not work. I found the SimpleBackup utilities so I have no need for this anymore, but I am still interested in how to solve this problem. The problem is that the new thread does not get executed until the main thread is shut down.

---

### Post by kripkenstein on 2008-11-27
The code you posted here appears fine. So my suspicion is that the problem lies with the glade XML file you didn't post.

Perhaps are you not connecting the correct event to catch the button click - maybe you're connecting the exit event to the **on_backupButton_clicked** function? That would explain why the thread starts when you exit. (As they say on House, 'it explains everything' ;) )

---

